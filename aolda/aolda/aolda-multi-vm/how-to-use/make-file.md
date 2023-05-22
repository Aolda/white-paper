# Make File

<figure><img src="../../../.gitbook/assets/FileRegister.png" alt=""><figcaption></figcaption></figure>

## 작동 방식

1. Register File\
   cli를 사용해 파일 경로를 입력한다.
2. Hash File\
   node는 해당 파일을 TX로 생성하고 해쉬화하여 이를 블록에 넣는다.
3. Commit\
   node는 다른 node들에게 해당 블록을 commit한다.
4. Approve\
   다른 블록들이 해당 블록에 대해 승인한다.
5. Save File\
   블록이 정상적으로 생성된다.
