# Add File

['Write Smart Contract without solidity'](../../aolda/aolda-multi-vm/how-to-use/write-smart-contract-without-solidity.md)서 언급한 것과 같이 solidity 외의 언어로 작성된 smart contract를 저장하기 위해서 user는 따로 code를 작성한 후 node를 통해 이를 aolda-network에 등록해야 합니다.

등록한 code는 아래와 같은 방법으로 등록됩니다.

## 1. Upload to IPFS And Make Tx

<figure><img src="../../.gitbook/assets/1. RegisterFile.png" alt=""><figcaption><p>Fig1. Upload to IPFS And Make Tx</p></figcaption></figure>

(1) Node를 운영하는 USER가 file을 업로드한다.

(2) Node는 USER가 업로드한 file을 IPFS에 등록한다.

(3) IPFS 네트워크는 file을 저장하고 Hash값을 반환한다.

(4) Node는 IPFS 네트워크에서 반환한 Hash값을 이용해서 Transaction을 생성한다.

## 2. Broadcast And Push to Mempool&#x20;

<figure><img src="../../.gitbook/assets/2. Upload.png" alt=""><figcaption><p>Fig2. Broadcast And Push to Mempool</p></figcaption></figure>

(1) Node는 트랜잭션을 다른 Node들에게 Broadcasting한다.

(2) 생성된 트랜잭션은 Mempool에 저장된다.

## 3. Create Block

이전 블럭이 생성된 후 충분한 시간이 지나면 Node는 Mempool에서 트랜잭션을 추출하여 새로운 블럭을 생성합니다. 블럭 생성에 대한 자세한 내용은 [Create Block 페이지](../create-aolda-block.md)에서 확인하세요.

