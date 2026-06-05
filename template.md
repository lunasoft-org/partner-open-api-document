# 알림톡 템플릿 관리 API

## 공통 정보

### Domain
- bizmsg-center-api.blumn.ai

### 인증 헤더
- x-api-key: {api-key}

## 1. 템플릿 생성
- METHOD: POST
- URL: /v2/template/create

### 요청 본문
| 이름 | 타입 | 설명 | 필수 |
| --- | --- | --- | --- |
| Request Body | [Template[]](#template) | 템플릿 목록 | O |

### 응답 본문
| 이름 | 타입 | 설명 | 필수 |
| --- | --- | --- | --- |
| Request Body | [Template[]](#templateCreateResult) | 템플릿 목록 | O |

### templateCreateResult
| 이름 | 타입 | 설명 | 필수 |
| --- | --- | --- | --- |
| code | string | 성공: success<br>실패: fail | O |
| message | string | 실패 사유 | X |
| data | string | 템플릿 코드 | X |

### 요청 예시
```
curl -X POST \
  -H 'x-api-key: {api-key}' \
  -H 'Content-type: application/json' \
  -d '[
  {
    "senderKey": "{senderKey}",
    "senderKeyType": "S",
    "templateCode": "template_001",
    "templateName": "템플릿 명",
    "templateMessageType": "BA",
    "templateEmphasizeType": "NONE",
    "templateContent": "템플릿 내용",
    "categoryCode": "001001",
    "buttons": [
      {
        "ordering": 1,
        "linkType": "WL",
        "name": "웹링크버튼",
        "linkMo": "http: //www.sweettracker.co.kr"
      },
      {
        "ordering": 2,
        "linkType": "AL",
        "name": "앱링크버튼",
        "linkIos": "daumapps: //open",
        "linkAnd": "daumapps: //open"
      },
      {
        "ordering": 3,
        "linkType": "DS",
        "name": "배송 조회하기"
      }
    ],
    "quickReplies": [
      {
        "name": "봇키워드",
        "linkType": "BK",
        "linkTypeName": "봇키워드"
      },
      {
        "name": "바로가기",
        "linkType": "WL",
        "linkTypeName": "웹링크",
        "linkMo": "http: //daum.net",
        "linkPc": null,
        "linkIos": null,
        "linkAnd": null
      }
    ]
  }
]' \
  https://bizmsg-center-api.blumn.ai/v2/template/create
```

### 응답 예시
```
[
  {
    "code":"fail",
    "data":"template_001",
    "message":"senderKey is required"
  }
]
```

## 2. 템플릿 수정
- METHOD: POST
- URL: /v2/template/update

### 요청 본문
| 이름 | 타입 | 설명 | 필수 |
| --- | --- | --- | --- |
| senderKey | text(40) | 발신프로필 키 | O |
| senderKeyType | text(1) | 발신프로필 키 타입<br>G: 그룹<br>S: 발신프로필 (기본값) | X |
| templateCode | text(30) | 템플릿 코드 | O |
| newSenderKey | text(40) | 발신프로필 키 (senderKeyType이 G인 경우 발신프로필 그룹키) | O |
| newSenderKeyType | text(1) | 발신프로필 키 타입<br>G: 그룹<br>S: 발신프로필 (기본값) | X |
| newTemplateCode | text(30) | 템플릿 코드 | O |
| newTemplateName | text(200) | 템플릿 이름 | O |
| newTemplateMessageType | text | [템플릿 메시지 타입](#templateMessageType) | O |
| newTemplateEmphasizeType | text | [템플릿 메시지 강조 타입](#templateEmphasizeType) | O |
| newTemplateContent | text | 템플릿 내용 | O |
| newTemplatePreviewMessage | text | 템플릿 미리보기 메시지(템플릿 검수 가이드 참고) | X |
| newTemplateExtra | text | 부가 정보(템플릿 검수 가이드 참고) | X |
| newTemplateImageUrl | text | 템플릿 이미지 링크 (템플릿 검수 가이드 참고) | X |
| newTemplateTitle | text | 템플릿 내용 중 강조 표기할 핵심 정보 (템플릿 검수 가이드 참고) | X |
| newTemplateSubtitle | text | 강조 표기 보조 문구 (템플릿 검수 가이드 참고) | X |
| newTemplateHeader | text(16) | 헤더 (템플릿 검수 가이드 참고) | X |
| newTemplateItemHighlight | [TemplateItemHighlight](#templateItemHighlight) | 아이템 하이라이트 (템플릿 검수 가이드 참고) | X |
| newTemplateItem     | [TemplateItem](#templateItem) | 아이템 리스트 (템플릿 검수 가이드 참고) | X |X |
| newTemplateRepresentLink | [TemplateRepresentLink](#templateRepresentLink) | 대표링크 | X |
| newCategoryCode     | text | 템플릿 카테고리코드 | O |
| securityFlag     | boolean | 보안 템플릿 여부<br>true: 설정<br>false: 미설정 | X |
| adultFlag        | boolean | 연령 인증 설정 여부<br>true: 설정<br>false: 미설정 | X |
| newButtons          | [Button[]](#buttons) | 버튼 정보 | X |
| newQuickReplies     | [QuickReply[]](#quickReplies) | 바로연결 정보 | X |

### 응답 본문
| 이름 | 타입 | 설명 | 필수 |
| --- | --- | --- | --- |
| code | string | 성공: success<br>실패: fail | O |
| message | string | 실패 사유 | X |
| data | [Template](#template) | 실패 사유 | X |

### Example CURL
```
curl -X POST \
  -H 'x-api-key: {api-key}' \
  -H 'Content-type: application/json' \
  -d '{
  "senderKey": "2a1ea83fb57b2c21096f994d1ab3091b0dac3c63",
  "senderKeyType": "S",
  "templateCode": "template_002",
  "newSenderKey": "2a1ea83fb57b2c21096f994d1ab3091b0dac3c63",
  "newTemplateCode": "template_003",
  "newTemplateName": "테스트템플릿",
  "newTemplateMessageType": "BA",
  "newTemplateEmphasizeType": "NONE",
  "newTemplateContent": "템플릿 내용",
  "newButtons": [
    {
      "ordering": 1,
      "linkType": "WL",
      "name": "웹링크버튼",
      "linkMo": "http://www.sweettracker.co.kr"
    },
    {
      "ordering": 2,
      "linkType": "AL",
      "name": "앱링크버튼",
      "linkIos": "daumapps://open",
      "linkAnd": "daumapps://open"
    },
    {
      "ordering": 3,
      "linkType": "DS",
      "name": "배송 조회하기"
    }
  ]
}' \
  https://bizmsg-center-api.blumn.ai/v2/template/update
```

### 응답 예시
```
{
  "code":"success",
  "data":"template_001",
  "message":null
}
```

## 기타

#### template

| 이름 | 타입 | 설명 | 필수 |
| --- | --- | --- | --- |
| senderKey        | text(40) | 발신프로필 키 | O |
| senderKeyType    | text(1) | 발신프로필 키 타입 <br> G: 그룹 <br> S: 발신프로필 (기본값) | O |
| templateCode     | text(30) | 템플릿코드 | O |
| templateName     | text(200) | 템플릿이름 | O |
| templateMessageType | text | [템플릿 메시지 타입](#templateMessageType) | O |
| templateEmphasizeType | text | [템플릿 메시지 강조 타입](#templateEmphasizeType) | O |
| templateContent  | text | 템플릿내용 | O |
| templatePreviewMessage | text | 템플릿 미리보기 메시지(템플릿 검수 가이드 참고)                 | X |
| templateExtra    | text | 부가 정보(템플릿 검수 가이드 참고) | X |
| templateImageName | text | 템플릿 이미지 파일명 (템플릿 검수 가이드 참고) | X |
| templateImageUrl | text | 템플릿 이미지 링크 (템플릿 검수 가이드 참고) | X |
| templateTitle    | text | 템플릿 내용 중 강조 표기할 핵심 정보 (템플릿 검수 가이드 참고) | X |
| templateSubtitle | text | 강조 표기 보조 문구 (템플릿 검수 가이드 참고) | X |
| templateHeader   | text | 헤더 (템플릿 검수 가이드 참고) | X |
| templateItemHighlight | [TemplateItemHighlight](#templateItemHighlight) | 아이템 하이라이트 (템플릿 검수 가이드 참고) | X |
| templateItem     | [TemplateItem](#templateItem) | 아이템 리스트 (템플릿 검수 가이드 참고) | X |
| templateRepresentLink | [TemplateRepresentLink](#templateRepresentLink) | 대표링크 | X |
| inspectionStatus | text | 검수 상태<br>REG: 등록<br>REQ: 심사요청<br>APR: 승인<br>REJ: 반려 | O |
| createdAt        | text(19) | 등록일 | O |
| modifiedAt       | text(19) | 수정일 | O |
| status           | text(1) | 템플릿 상태<br>S: 중지<br>A: 정상<br>R: 대기(발송전) | O |
| block            | boolean | 템플릿 차단 여부(true:차단, false:해제) | O |
| dormant          | boolean | 템플릿 휴면 여부 | O |
| categoryCode     | text | 템플릿 카테고리코드 | O |
| securityFlag     | boolean | 보안 템플릿 여부<br>true: 설정<br>false: 미설정 | O |
| adultFlag        | boolean | 연령 인증 설정 여부<br>true: 설정<br>false: 미설정 | O |
| comments         | [Comment[]](#comments) | 검수결과 댓글리스트 | O |
| buttons          | [Button[]](#buttons) | 버튼 정보 | O |
| quickReplies     | [QuickReply[]](#quickReplies) | 바로연결 정보 | O |

##### TemplateItemHighlight

| 이름         | 타입  | 설명 |
| ----------- | ---- | --- |
| title       | text(30) | 타이틀 |
| description | text(19) | 설명 |
| imageUrl    | text(500) | 썸네일 이미지 주소 |

##### TemplateItem

| 이름     | -    | 타입 | 설명 |
| ------- | ---- | ------ | --- |
| list    |      | json[]   | 아이템 리스트 |
|  | title       | text(6)  | 타이틀 |
|  | description | text(23) | 설명 |
| summary |      | json     | 아이템 요약 정보 |
|  | title       | text(6)  | 타이틀 |
|  | description | text(14) | 설명 |

##### TemplateRepresentLink

| 이름          | 타입 | 설명 |
| ----------- | ---- | --- |
| linkMo   | text | 모바일 웹 링크주소 |
| linkPc   | text | PC 웹 링크주소 |
| linkIos  | text | IOS 앱 링크주소 |
| linkAnd  | text | Android 앱 링크주소 |

##### comments

| 이름               | -   | 타입 | 설명 |
| ----------------- | --- | ---- | --- |
| id                |  | number  | 댓글 아이디 |
| content           |  | text | 댓글 내용 |
| userName          |  | text | 작성자 |
| createdAt         |  | text | 등록일 |
| status            |  | text | 댓글 상태<br>INQ: 문의<br>APR: 승인<br>REJ: 반려<br>REP: 답변<br>REQ: 검수요청 |
| attachment        |  | json[] | 첨부파일 |
|   | originalFileName | text | 업로드 당시 기존 파일명 |
|   | filePath         | text | 파일 다운로드 경로 |

##### buttons

| 이름           | 타입 | 설명 |
|--------------| ---- | --- |
| ordering     | number | 버튼 노출 순서 |
| name         | text   | 버튼명 |
| linkType     | text   | [버튼 링크 타입](#linkType) |
| linkTypeName | text | 버튼의 링크 타입 이름 |
| linkMo       | text   | 모바일 웹 링크주소 |
| linkPc       | text   | PC 웹 링크주소 |
| linkIos      | text   | IOS 앱 링크주소 |
| linkAnd      | text   | Android 앱 링크주소 |
| pluginId     | text   | 비즈플러그인 ID |
| bizFormId    | number | 비즈니스폼 ID |
| telNumber    | text | 전화번호 |

##### quickReplies

| 이름 | 타입 | 설명 |
| -------- | ---- | --- |
| name     | text | 바로연결명 |
| linkType | text | [바로연결 링크 타입](#linkType) |
| linkTypeName | text | 버튼의 링크 타입 이름<br>웹링크<br>앱링크<br>봇키워드<br>상담톡전환<br>봇전환<br>비즈니스폼 |
| linkMo   | text | 모바일 웹 링크주소 |
| linkPc   | text | PC 웹 링크주소 |
| linkIos  | text | IOS 앱 링크주소 |
| linkAnd  | text | Android 앱 링크주소 |
| bizFormId | number | 비즈니스폼 ID |


### linkType

알림톡 템플릿 버튼 링크 타입별 사용 가능한 버튼 파라미터와 필수 파라미터는 아래와 같습니다.

| linkType | 설명                                                 | 사용 가능 파라미터                                                     | 필수 파라미터 |
|---------|----------------------------------------------------|----------------------------------------------------------------| --- |
| WL      | 지정한 웹 링크로 이동                                       | name<br>linkType<br>linkMo<br>linkPc                        | name<br>linkType<br>linkMo |
| AL      | 지정한 앱 스킴 또는 웹 링크로 이동                           | name<br>linkType<br>linkAnd<br>linkIos<br>linkMo<br>linkPc | name<br>linkType<br><br>다음 중 2가지 이상<br>linkAnd<br>linkIos<br>linkMo |
| DS      | 버튼 클릭 시 배송조회 페이지로 이동                               | name<br>linkType                                              | name<br>linkType |
| BK      | 해당 버튼 텍스트 발송                                       | name<br>linkType                                              | name<br>linkType |
| MD      | 해당 버튼 텍스트 + 메시지 본문 발송                              | name<br>linkType                                              | name<br>linkType |
| BC      | 상담톡 전환<br>상담톡을 이용하는 카카오톡 채널만 이용 가능                | name<br>linkType                                              | name<br>linkType |
| BT      | 봇 전환<br>카카오 I 오픈빌더의 챗봇을 사용하는 카카오톡 채널만 이용 가능       | name<br>linkType                                              | name<br>linkType |
| AC      | 버튼 클릭 시 카카오톡 채널 추가템플릿 메시지 타입이 AD, MI인 경우에만 사용 가능 | name<br>linkType                                              | name<br>linkType |
| P1      | 이미지 보안 전송 플러그인                                     | name<br>linkType<br>pluginId                                 | name<br>linkType<br>pluginId |
| P2      | 개인정보이용 플러그인                                        | name<br>linkType<br>pluginId                                 | name<br>linkType<br>pluginId |
| P3      | 원클릭 결제 플러그인                                        | name<br>linkType<br>pluginId                                 | name<br>linkType<br>pluginId |
| BF      | 카카오 비즈니스폼을 실행                                      | name<br>linkType<br>bizFormId                                | name<br>linkType<br>bizFormId |
| TN      | 전화 앱 실행<br>모바일 환경에서만 이용 가능                        | name<br>linkType<br>telNumber                                         | name<br>linkType<br>telNumber |
| MP      | 버튼 클릭 시 지도 보기                                      | name<br>linkType                                              | name<br>linkType |

### templateMessageType

알림톡 템플릿에 사용하는 메시지 타입을 설명합니다.

| templateMessageType | 설명 |
| --- | --- |
| BA | [기본](https://kakaobusiness.gitbook.io/main/ad/bizmessage/notice-friend/content-guide#id-1-1) |
| EX | [부가 정보](https://kakaobusiness.gitbook.io/main/ad/bizmessage/notice-friend/content-guide#id-1-2) |
| AD | [채널 추가](https://kakaobusiness.gitbook.io/main/ad/bizmessage/notice-friend/content-guide#id-1-3) |
| MI | [복합](https://kakaobusiness.gitbook.io/main/ad/bizmessage/notice-friend/content-guide#id-1-4) |

### templateEmphasizeType

알림톡 템플릿에 사용하는 메시지 강조 타입을 설명합니다.

| templateEmphasizeType | 설명 |
| --- | --- |
| NONE | 선택안함 |
| IMAGE | [이미지](https://kakaobusiness.gitbook.io/main/ad/bizmessage/notice-friend/content-guide#id-2-1) |
| TEXT | [강조표기](https://kakaobusiness.gitbook.io/main/ad/bizmessage/notice-friend/content-guide#id-2-2) |
| ITEM_LIST | [아이템리스트](https://kakaobusiness.gitbook.io/main/ad/bizmessage/notice-friend/content-guide#id-2-3) |
