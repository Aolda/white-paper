# Call From EVM

유저들은 Ethereum 환경에서 AOLDA-Smart Contract를 호출해 solidity 외의 언어로 작성된 컨트랙트를 호출하고 값을 사용할 수 있습니다. 이 방식은 Ethereum의 높은 보안성을 이용하여 서비스의 보안성을 높이고 싶을 때 적합합니다.

['Use Smart Contract without solidity'](../../aolda/aolda-multi-vm/how-to-use/use-smart-contract-without-solidity.md)방법으로 Smart Contract를 호출하면 아래 방식으로 작동합니다.

## 1. Emit Event

<figure><img src="../../.gitbook/assets/1. Call Function From EVM.png" alt=""><figcaption><p>Fig1. Emit Event</p></figcaption></figure>

(1) USER가 커스텀한 컨트랙트에서 AOLDA-SC를 호출합니다.

(2) AOLDA-SC는 USER가 컨트랙트에서 넘겨준 parameter를 포함한 Event를 emit하고 ethereum block에 저장합니다.

## 2. Listen Event And Make Tx

<figure><img src="../../.gitbook/assets/2. Listen Event And Make Tx.png" alt=""><figcaption><p>Fig2. Listen Event And Make Tx</p></figcaption></figure>

(1) AOLDA-NETWORK에 있는 Node들은 각자 Ethereum network를 구독하고 있습니다. 트래킹하던 중 새로운 Event가 발생하면 이를 트래킹하여 처리합니다.

(2) Node는 `fileHash`, `functionName`, `arguments`를 포함한 Transaction을 생성합니다.

## 3. Broadcast And Push to Mempool&#x20;

<figure><img src="../../.gitbook/assets/3. Broadcast And Push to Mempool (1) (1).png" alt=""><figcaption><p>Fig3. Broadcast And Push to Mempool</p></figcaption></figure>

(1) 가장 먼저 트랜잭션을 생성한 Node는 자신이 생성한 트랜잭션을 나머지 Node들에게 Broadcast합니다.

(2) 트랜잭션을 받은 Node들은 해당 Transaction의 유효성을 검사하고 문제가 없으면 트랜잭션을 생성한 Node는 트랜잭션을 Mempool에 저장합니다.

## 4. Create Block

이전 블럭이 생성된 후 충분한 시간이 지나면 Node는 Mempool에서 트랜잭션을 추출하여 새로운 블럭을 생성합니다. 블럭 생성에 대한 자세한 내용은 [Create Block 페이지](../create-aolda-block.md)에서 확인하세요.
