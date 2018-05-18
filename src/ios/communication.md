# Communication

## 기본 설정

통신을 하기 전에 프로젝트 설정을 진행 합니다.

{% page-ref page="../getting-started-livecasting/ios.md" %}

## 개발

통신을 기능은 이용하기 위해서는 RemonCall 클래스를 이용합니다. RemonCall클래스의 connectChannel\(\) 함수를 이용하여 채널 생성 및 접속이 가능합니다. 

connectChannel\(\) 함수에 전달한 chid 값에 해당하는 채널이 존재하지 않으면 채널이 생성되고, 다른 사용자가 해당 채널에 연결하기를 대기 하는 상태가 됩니다. 이때 해당 chid로 다른 사용자가 연결을 시도 하면 연결이 완료 되고, 통신이 시작 됩니다.

```
remonCall.connectChannel("chid")
```

통신 기능을 해발 하다 보면 진행 상태를 알아야 하는 경우가 왕왕 발생 합니다. 이때는 Remon이 제공 하는 Observer 함수를 이용하면 쉽게 진행 상태를 추적할 수 있습니다.

```text
remonCall.onInit {
    // UI 처리등 remon이 초기화 되었을 때 처리하여야 할 작업
}

remonCall.onCreate {
    // 해당 'chid'로 미리 생성된 채널이 없다면 다른 사용자가 해당 'chid'로 연결을 시도 할때 까지 대기 상태가 됩니다. 
}

remonCall.onComplete {
    // 통신 연결 완료. 영상 및 음성 전송이 시작 됩니다.
}
```

Remon은 onInit\(\)와 onCreate, onComplete 이외에도 많은 Observer 함수를 제공 합니다. 더 많은 내용은 Observer 가이드 문서를 참조 하세요.

{% page-ref page="observer.md" %}


