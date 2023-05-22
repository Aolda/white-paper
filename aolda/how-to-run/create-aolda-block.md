# Create Aolda Block

## What is Block?

Aolda Network에서는 계속해서 생성되는 smart contract와 이를 호출하고 결과값을 도출하는 과정을 블록체인 구조로 저장하고 관리합니다.

블록체인 구조를 사용함으로써 위변조를 방지할 수 있고 보안에 사용되는 기업단위의 비용을 절약할 수 있습니다. 뿐만 아니라 기업 정책에 따라 퍼블릭 아올다 네트워크를 사용하거나 기업에서 사용하는 네트워크를 공개함으로써 사용자의 신뢰를 확보할 수 있습니다.

## How will be Block created?

Aolda는 **PoW**(Proof of Work)방식을 채택합니다. PoW는 문제를 해결한 Node에게 보상을 지급하고 블럭 생성 권한을 주는 합의 알고리즘으로 가장 탈중앙적이고 보안적인 방법입니다.

블록을 생성하는 Node는 Mempool에 있는 트랜잭션들을 모두 모아 유효성을 검증하고 이를 Block구조에 포함하여 difficulty를 충족시키는 nonce값을 찾기 시작합니다. nonce값을 가장 먼저 찾은 Node는 보상을 획득하고 Block을 생성합니다.

블록은 30초단위로 생성됩니다. 이전 블록이 생성되고 Broadcast되면 이를 받은 Node들은 nonce값을 확인한 후 다음 블록을 생성하기 시작합니다.

