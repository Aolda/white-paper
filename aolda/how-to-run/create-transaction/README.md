# Create Transaction

## What is Transaction?

트랜잭션(Tx, Transaction)은 블록체인에서 데이터베이스의 상태를 변환시키는 하나의 논리적 기능을 수행하기 위한 작업의 단위라고 할 수 있습니다. 블록체인 네트워크는 하나의 커다란 데이터베이스로, 블록체인 내 트랜잭션 역시 다른 데이터베이스에서 트랜잭션의 안전성을 보장하기 위한 성질인 A.C.I.D를 가지고 있습니다.

## Tx Struct

```json
{
	"header":{
		"type":,
		"hash":"",
		"blockNumber":"",
		"blockHash":"",
		"transactionIndex":"",
		"from":"",
		"nonce":"",
		"signature":{
			"r":"",
			"s":"",
			"v":""
		}
		"timestampe":""
	}
	"body":{
		"fileHash":"",
		"functionName":"",
		"arguments":["",""],
		"result": ""
	}
}
```

* header : 트랜잭션의 생성에 대한 정보가 들어있습니다.
* type : 트랜잭션의 종류를 나타내는 값으로 0\~4 중 하나입니다.
  * 0 : 파일 생성 (solidity 외의 언어로 작성된 스마트 컨트랙트 생성)
  * 1 : EVM에서 AOLDA를 호출한 기록
  * 2 : USER가 API를 사용해 직접 Aolda Node를 호출한 기록
  * 3 : type1과 type2에 대한 결과값
  * 4 : 블록 채굴에 대한 트랜잭션
* hash : 트랜잭션 body에 대한 해쉬값입니다.
* blockNumber :&#x20;
* blockHash :&#x20;
* transactionIndex :&#x20;
* from : 트랜잭션을 생성한 Node입니다.
* nonce :&#x20;
* signature : 트랜잭션 유효성 검증을 위한 전자 서명입니다.
* timestamp : 트랜잭션이 생성된 시간입니다.
* body : 트랜잭션 데이터에 대한 실질적인 정보가 들어있습니다. 각 값들은 type에 따라 다르게 해석됩니다.
* fileHash : IPFS에서 반환된 fileHash입니다.
  * type0 : 파일을 IPFS 네트워크에 저장하고 반환된 Hash값입니다.
  * type1, type2, type3 : 호출할 때 입력된 인자 중 fileHash에 해당하는 값입니다.
  * type4 : null값입니다.
* functionName : 인자값으로 type1, type2, type3에서만 사용됩니다.
  * type0, type4 : null값입니다.
  * type1, type2, type3 : 호출할 때 입력된 인자 중 functionName에 해당하는 값입니다.
* arguments : 인자값으로 type1, type2, type3에서만 사용됩니다.
  * type0, type4 : null값입니다.
  * type1, type2, type3 : 호출할 때 입력된 인자 중 arguments에 해당하는 값입니다. 인자들은 모두 string으로 들어와야 합니다.
* result : 결과값입니다.
  * type0, type1, type2 : null값입니다.
  * type3 : 함수 호출에 대한 결과값입니다.
  * type4 : 보상으로 지급되는 토큰의 수입니다.
