# VAE(Variational Auto-Encoder) 
[VAE](https://arxiv.org/abs/1312.6114 "VAE")


Generative model의 한 종류이다. 입력 데이터의 feature을 추출하여 Lantent vector z에 담고, 이를 x와 유사하지만 완전히 새로운 데이터를 생성하는 것을 목표로함. \
이때 **각 feature가 가우시안 분포를 따른다고 가정하고 latent z는 각 feature의 평균과 분산을 나타냄.**



## 구조
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb30Uzl%2FbtrxY4wKngj%2FSucVwitDrRtQvi1xTHdrR0%2Fimg.png)

VAE는 generative model로써, 현실과 비슷한 데이터들을 만들어내는 것을 목적으로 한다. VAE는 AE(Auto Encoder)의 구조와 비슷하지만, 실제로는 다른 모델이다.\
AE의 핵심은 원래의 데이터를 복원 $x -> x$으로, 핵심은 Z를 잘 임베팅하는 것이다 **(Manifold learning)**\
	- 고차원의 공간을 잘 표현하는 것이 manifold learning의 목적\
VAE의 핵심은 원래의 데이터를 새로운 유사한 데이터로 재생성하는$(x->x^{'})$ 것으로, 핵심은 생성된 데이터가 실제 데이터와 거의 유사해야하는 것이다 **(Generative model)**

VAE는 Encoder, Latent space, Decoder로 이루어져있음.

#### Encoder
input을 Latent space로 변환하는 역활. 이때, encoder는 input 데이터의 posterior, 달리 input x가 주어졌을 때 latent vector z의 분포, 즉 $q{z|x}$를 approximate하는 것을 목적으로 함.\
$q{z|x}$를 apporximate할 때는 정규분포를 나타내는 평균($\mu$)과 표준편차($\sigma$)의 papameter를 찾는 것이 목적이 될것이다. 
#### Reparametereriazation Trick(Latent space)
Latent space는 어떤 숨겨진 vector들을 나타내는 말이다. 현 latent space를 활용하여 decoder에서 data를 generate할 수 있음. 이는 일반적인 AE에서 주로 이용하지만, VAE에서는 새로은 데이터를 생성하지 위해 noise를 sampling하여 이로부터 latent space를 만든다.\
표준 정규분포(평균: 0, 표준편차: 1)로부터 하나의 noise epsilon을 샘플링하여 얻고, 앞에서 encoder로부터 얻은 분산을 곱하고 평균을 더하여 latent vector z를 얻는 것이다. 
#### Decoder
encoder는 축소하고 말하면 decoder는 확대라고 말할 수 있다. decoder는 latent space를 input으로 변환하는 역할임. latent vector z가 주어졌을 때 x의 분포 즉, $p(z|x)$를 approximate하는 것을 목적으로 함.

## 증명
## 장단점
## 코드
