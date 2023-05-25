# Call With API

Ethereum 환경에서 solidity 외의 언어로 작성된 컨트랙트를 호출하고 값을 사용하는 방식은 Ethereum의 낮은 TPS때문에 속도가 느리다는 단점이 있습니다.

User는 AOLDA Network에 포함된 Node의 endpoint를 직접 찾아 API를 호출할 수 있습니다. 이 방식은 Ethereum에서 호출하는 방식과 달리 즉각적인 result를 반환하고 빠르게 사용할 수 있습니다. 하지만 보안성이 다소 떨어질 수 있다는 단점이 있습니다. 그렇기 때문에 User는 신뢰성이 높은 Node의 endpoint를 찾아서 적절하게 호출해야 합니다.

['Use Smart Contract without solidity'](../../aolda/aolda-multi-vm/how-to-use/use-smart-contract-without-solidity.md)방법으로 Smart Contract를 호출하면 아래 방식으로 작동합니다.

## 1. Return Value

<figure><img src="../../.gitbook/assets/1. Call Function With API.png" alt=""><figcaption><p>Fig1. Return Value</p></figcaption></figure>

(1) USER가 AOLDA-NETWORK에 포함된 Node의 endpoint에 직접 api 호출을 합니다.

(2) 호출받은 Node는 내장되어있는 compiler를 이용하여 함수를 실행하고 결과값을 얻습니다.

(3) 얻은 결과값을 USER에게 반환해줍니다.

## 2. Make Txs

<figure><img src="../../.gitbook/assets/2. Make Txs.png" alt=""><figcaption><p>Fig2. Make Txs</p></figcaption></figure>

(1) USER에게 결과값을 반환해준 후 Node는 `fileHash`, `functionName`, `arguments`를 포함한 트랜잭션을 생성합니다.

(2) Node는 (1)에서 생성된 트랜잭션을 이미 생성된 블럭에서 찾습니다. 만약 블럭이 있고 이에 대한 confirm value 트랜잭션도 존재한다면 (3)과정은 생략합니다.

(3) 만약 (2)에서 confirm value 트랜잭션을 찾지 못했다면 `fileHash`, `functionName`, `arguments`, `result`를 포함하는 트랜잭션을 생성합니다.

## 3. Broadcast And Push to Mempool

<figure><img src="../../.gitbook/assets/3. Broadcast And Push to Mempool (1).png" alt=""><figcaption><p>Fig3. Broadcast And Push to Mempool</p></figcaption></figure>

(1) Node는 생성된 트랜잭션들을 모두 다른 Node에게 Broadcast합니다.

(2) 다른 Node들은 트랜잭션의 유효성을 검사하고 이상이 없다면 트랜잭션을 처음 생성한 Node는 트랜잭션을 Mempool에 저장합니다.

## 4. Create Block

이전 블럭이 생성된 후 충분한 시간이 지나면 Node는 Mempool에서 트랜잭션을 추출하여 새로운 블럭을 생성합니다. 블럭 생성에 대한 자세한 내용은 [Create Block 페이지](../create-aolda-block.md)에서 확인하세요.
