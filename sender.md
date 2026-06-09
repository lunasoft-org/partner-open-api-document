# 카카오 발신 프로필

## 공통 정보

### Domain
- bizmsg-center-api.blumn.ai

### 인증 헤더
- x-api-key: {api-key}

## 1. 템플릿 카테고리 리스트 조회

### Endpoint
- METHOD: GET
- URL: /v1/senders

### 응답 본문
| 이름 | 타입 | 설명 | 필수 |
| --- | --- | --- | --- |
| code | string | 성공: success<br>실패: fail | O |
| message | string | 실패 사유 | X |
| data | [senders[]](#sender) | 템플릿 코드 | X |

#### sender
| 이름 | 타입 | 설명 | 필수 |
| --- | --- | --- | --- |
| senderKey | string | 발신 프로필 키 | O |
| brandId | number | 브랜드 번호 | O |
| uuid | string | 카카오 채널 식별값 | O |
| brandName | string | 브랜드 명 | O |

### 요청 예시
```
curl -X GET \
  -H 'userId: {user_id}' \
  'https://bizmsg-center-api.blumn.ai/v1/senders
```

### 응답 예시
```
{
    "code": "success",
    "data": [
        {
            "senderKey": {senderKey},
            "brandId": 1,
            "uuid": "@루나엠",
            "brandName": "루나엠 알림톡"
        },
    ],
    "message": null
}
```
