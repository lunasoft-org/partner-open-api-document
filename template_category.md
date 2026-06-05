# 알림톡 템플릿 카테고리

## 공통 정보

### Domain
- bizmsg-center-api.blumn.ai

### 인증 헤더
- x-api-key: {api-key}

## 1. 템플릿 카테고리 리스트 조회

### Endpoint
- METHOD: GET
- URL: /v2/template/category/all

### 요청 예시
```
curl -X GET \
  https://bizmsg-center-api.blumn.ai/v2/template/category/all
```

### 응답 예시
```
{
  "code": "success",
  "message": "",
  "data": {
    "firstBusinessType": [
      {
        "parentCode": "",
        "code": "001",
        "groupName": "회원",
        "name": "",
        "inclusion": "",
        "exclusion": ""
      }
    ],
    "secondBusinessType": [
      {
        "parentCode": "001",
        "code": "001",
        "groupName": "회원",
        "name": "회원가입",
        "inclusion": "회원가입 완료 내용의 템플릿이 대상입니다. 가입에 따른 축하적립금/쿠폰을 포함합니다.",
        "exclusion": "상품/서비스가입은 구매 > 상품가입 (002002)로 분류합니다."
      }
    ]
  }
}
```
