# https和ssl

## 0. 实用命令

- 阅读一个pem格式的证书

```
$ openssl x509 -in certificate.pem -text -noout
```

- 阅读一个pem格式的私钥

```
# rsa私钥
$ openssl rsa -in private_key.pem -text -noout

# 椭圆曲线私钥
$ openssl ec -in private_key.pem -text -noout
```

- 阅读一个pem格式的公钥
```
# rsa公钥
$ openssl rsa -in public_key.pem -pubin -text -noout

# 椭圆曲线公钥
$ openssl ec -in public_key.pem -pubin -text -noout
```

- 阅读一个p12文件的证书内容
```
$ openssl pkcs12 -info -in keystore.p12 -nokeys
```

```
$ openssl pkcs12 -info -in keystore.p12 -nodes -nocerts
```

## 1. 非对称加密算法

### 1.1 RSA算法

- 设计理念

根据数论，寻求两个大素数比较简单，将他们的乘积进行因式分解却很困难。因此将乘积公开作为加密密钥的一部分。

- 加解密过程

对于明文$M$、密文$C$。用$(e,n)$表示公钥，$(d,n)$表示私钥。

则加解密过程可表示为：

$$C=M^e\mod n,$$

$$M=C^d\mod n.$$

- 密钥生成过程 $(e,d,n)$

准备两个较大的素数p,q。n=p*q。

n的欧拉函数$\varphi(n)$值为(p-1)(q-1)。

选取公钥e，e是一个质数，且1<e<$\varphi(n)$，e与$\varphi(n)$互质。（实际应用中，e一般为65537）。

计算私钥d，用小欧拉定理计算d的乘法逆元，d要满足$(d*e)\mod \varphi(n)=1$。

至此(e,d,n)全部得出。

- 安全的原因

由于攻击者很难用n分解到p和q。因此也无法计算到欧拉函数$\varphi(n)=(p-1)(q-1)$。无法通过公钥反推出私钥。

### 1.2 ECDHE算法

- 离散对数

对于一个整数b和质数p的一个原根，可以找到一个唯一的指数i，使得：

$$a^i \mod p = b$$

那么指数i称为b的以a为底数的模p的离散对数。

已知a和p，知道i可以很容易算出b，但是知道b却无法算出i，这就是DH算法的数学基础。

- DH算法

双方先约定模数p和底数g。小红和小明各自生成一个随机整数作为私钥。小红的私钥为a，小明的私钥为b。

小红计算公钥A：$A = g^a \mod p$

小明计算公钥B：$B = g^b \mod p$

此外，由于离散对数的幂运算有交换律，所以

$$A=g^a,\ B=g^b$$

$$\Rightarrow B^a=A^b=K$$

这个K就是小红和小明之间的对称加密密钥。

- DHE算法

static DH算法不具有前向安全性：随着客户端公钥变化，黑客可以根据海量密钥协商过程逐渐提升推断能力，大大提升破解会话密钥的能力。

既然固定一方的私钥有被破解的风险，那就干脆让双方的私钥在每次密钥交换通信时，都是随机生成的。这就是DHE算法。

- ECDHE算法

DHE性能不佳，要做大量的乘法。现在广泛用于密钥交换的ECDHE算法解决了这个问题。

ECDHE算法在DHE算法基础上利用了ECC椭圆曲线特性，可以用更少的计算量计算出公钥，以及最终的会话密钥。

双方约定一个椭圆曲线C，在曲线上选定一个基点G，公开C和G。

小红随机生成一个随机数作为私钥d1（作为初始点的横坐标），从基点G出发d此后获取公钥Q1，可以表示为$Q_1=d_1G$。（第一次可以看作G点连G点，切线，得到d=2的点，一直连下去得到d=d1的点）。

小明同理生成公私钥$Q_2$和$d_2$。

双方交换公钥，小红按照反复连线的方式计算$K_1=d_1 Q_2$点的坐标，小明计算$K_2=d_2Q_1$。由于椭圆曲线有某种奇妙的类似于乘法交换结合律的性质，所以$K_1$和$K_2$的x坐标是一样的，这个就是会话密钥。

## 2. SSL和TLS

### 2.1 简介

SSL是TLS的前身，实际上现在很多浏览器支持的是TLS协议而不是SSL协议，但是SSL名气很大，大多数人都这么说。

### 2.2 证书签名和验证方法

- SHA256哈希算法

搁置

- 证书签名

证书颁发机构（CA）将证书的部分字段（如域名、公钥等）进行哈希（例如SHA-256、SHA-384），得到一个摘要。

然后，CA使用自己的私钥对摘要进行加密（如RSA、ECDHE、DSA），生成一个签名，随着证书一起发给服务器。

- 证书验证

客户端拿到证书和签名后，用CA的公钥对证书的签名进行解密，将得到的内容和证书内容进行比对，验证证书的合法性。

### 2.3 ECDHE四次握手

#### 1) 客户端发送第一次握手

- Client Hello

包括：
客户端TLS版本、
客户端随机书（client random）、
客户端密码套件列表（每一个套件都是密钥协商算法、签名算法、会话钥对称加密算法、摘要哈希算法的组合）

#### 2) 服务端发送第二次握手

- Server Hello

包括：
服务端确认的TLS版本、
客户端随机书（client random）、
服务端选择的密码套件（从客户端密码套件列表中选择1个）

- Certificate

包括：签了名的服务端证书

- Server Key Exchange

包括：选择的椭圆曲线和基点G、
（生成随机数作为椭圆曲线私钥）、
根据基点G和私钥计算出服务端的椭圆曲线公钥（公钥发送给客户端）

- Server Hello Done

表示第二次握手结束

#### 3) 客户端发送第三次握手

（客户端收到上面服务端发送的证书后，先验证一下证书的合法性）

- Client Key Exchange

（生成随机数作为椭圆曲线私钥）、
根据基点G和私钥算出客户端的椭圆曲线公钥（公钥发送给服务端）

（客户端使用客户端私钥和服务端公钥算出共享密钥，结合这个算出的共享密钥、client random、server random，生成最终的会话钥）

- Change Cipher Spec

告诉服务端后续使用会话钥，对称加密通信

- Encrypted Handshake Message

客户端把之前发送过的握手数据作一个摘要，再用会话钥加密一下，发送给服务端，让服务端验证服务端生成的会话钥是否可以正常使用，服务端验证完后回复ACK

#### 4) 服务端发送第四次握手

（服务端使用服务端私钥和客户端公钥算出共享密钥（由于加密算法性质，与客户端算出来是一样的），结合这个算出的共享密钥、client random、server random，生成最终的会话钥）

- Change Cipher Spec

告诉客户端后续使用会话钥，对称加密通信

- Encrypted Handshake Message

服务端把之前发送的握手数据作为一个摘要，再用会话钥加密一下，发送给客户端，让客户端验证客户端生成的会话钥是否可以正常使用，客户端验证完后回复ACK

### 2.4 ECDHE握手注意事项

1. 现在TLS主要用ECDHE，因为前向安全并且性能更高


2. 相较于RSA四次握手，ECDHE在客户端第三次握手时，客户端就会直接抢跑，用会话钥加密并传输部分应用数据，提高了效率

3. 用公私钥算出一个共享密钥还不够，还额外用一个client random和一个server random，是因为协议设计者认为客户端或服务器的伪随机数还不够可靠，所以最终把三个随机的因子混合起来，提高随机性

## 3. 用openssl生成自签名ssl证书

- openssl生成的密钥的证书格式默认是pem（Privacy Enhanced Mail），通常包含BEGIN和END标签，并且内容经过Base64编码，要阅读的话需要进行Base64解码。

- 在生成证书时，也可以通过-subj参数方式指定证书主题信息，替代命令行交互输入，例如：

```
$ openssl req -new -x509 -key private_key.pem -out certificate.pem -days 365 -subj "/C=CN/ST=ZheJiang/L=HangZhou/O=Fang Jiahao/CN=myecs.com"
```

### 3.1 生成rsa密钥对和证书

- 一行命令生成私钥和证书

```
$ openssl req -x509 -newkey rsa:2048 -keyout private_key.pem -out certificate.pem -days 365 -nodes
```

- 分开生成

```
# 生成私钥
$ openssl genpkey -algorithm RSA -out private_key.pem

# 生成公钥（可选）
$ openssl rsa -in private_key.pem -pubout -out public_key.pem

# 生成有效期为365天的自签名证书
$ openssl req -x509 -new -nodes -key private_key.pem -days 365 -out certificate.pem
```

### 3.2 生成prime256v1曲线密钥对和证书

- 查看支持的椭圆曲线
```
$ openssl ecparam -list_curves
```

- 分开生成
```
# 生成私钥
$ openssl ecparam -genkey -name prime256v1 -out private_key.pem

# 生成公钥（可选）
$ openssl ec -in private_key.pem -pubout -out public_key.pem

# 生成有效期为365天的自签名证书
$ openssl req -x509 -new -nodes -key private_key.pem -days 365 -out certificate.pem
```

## 4 将自签名证书用于应用

### 4.1 用于springboot（jdk不低于11）

- 将证书和私钥转为PKCS12格式并放在classpath下（resources）

```
$ openssl pkcs12 -export -in certificate.pem -inkey private_key.pem -out keystore.p12
```

keystore可以改成自己想要的名字，生成过程中需要输入.p12文件的访问密码，自己设置，例如123456。

- 在springboot里配置

application.yml
```yml
server:
  port: 8443    # 自己设置
  ssl:
    key-store: classpath:keystore.p12
    key-store-type: PKCS12
    key-store-password: 123456
    key-alias: 1    # 自己设置
```

- 启动即可

- 注意：springboot2.4.0以上的版本可以直接用pem格式的证书，不再需要PKCS12格式

### 4.2 用于springboot jdk8

- 将证书和私钥转为PKCS12格式（要加-legacy参数，否则后续无法和keytool适配）

```
$ openssl pkcs12 -export -in certificate.pem -inkey private_key.pem -out keystore.p12 -legacy
```

- 将PKCS12转化为jks

```
keytool -importkeystore -srckeystore keystore.p12 -srcstoretype pkcs12 -destkeystore keystore.jks
```

keystore可以改成自己想要的名字，生成过程中需要输入jks文件的访问密码，自己设置，例如123456.

- 在springboot里配置

application.yml
```yml
server:
  port: 8443    # 自己设置
  ssl:
    key-store: classpath:keystore.jks
    key-store-type: JKS
    key-store-password: 123456
    key-alias: 1    # 自己设置
```

- 注意

至少6位的keystore密码是必须的。创建p12时，可以不输入密码。但是创建jks必须有6位密码，而且创建jks时必须要输入非空的p12密码，所以p12密码不能为空。

### 4.3 用于nginx

### 4.4 用于kube api-server

### 4.5 用于docker registry

## 5 对称加密算法

## 6 哈希算法
