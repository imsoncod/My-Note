# Bastion Host란?

Bastion Host란 내부, 외부 네트워크 사이에서 외부 침입을 차단하는 일종이 **방화벽, 게이트** 역할을 하는 호스트입니다.

![image](https://user-images.githubusercontent.com/48934537/106884855-2d83df00-6725-11eb-832d-909d9c6e8ec2.png)

위 그림처럼 인스턴스에 접근하는 사용자들을 **필터링**하는 역할을 수행합니다.

사용자들은 Bastion Host(EC2)에 허가되어야만 내부 Private인스턴스에 접근할 수 있습니다.

SSH Public Key를 Bastion Host에 등록해두고 사용자의 Private Key를 받아 인증하는 **RSA**방식을 적용할 수 있습니다.
