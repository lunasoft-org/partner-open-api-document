# 알림톡 이미지 업로드 API

## Domain
- bizmsg-center-api.blumn.ai

### 인증 헤더
- x-api-key: {api-key}

## 1. 알림톡 템플릿 이미지 업로드
- METHOD: POST
- URL: /v1/image/alimtalk/template

### Request Body

| 키 | 데이터 타입 | 필수 | 설명 |
|----|------------|------|------|
| image | file | Y | 이미지 파일 1개 (jpg, jpeg, png / 최대 500KB) |
| imageNickname | string | N | 이미지 닉네임 |

### 요청 예시

```bash
curl -X POST \
  -H 'x-api-key: {api-key}' \
  -F "image=@template.png" \
  -F "imageNickname=template_image_1" \
  https://bizmsg-center-api.blumn.ai/v1/image/alimtalk/template
```

### 응답 예시

```json
{
  "code": "success",
  "data": {
    "imageUrl": "https://mud-kage.kakao.com/dn/example/template_image.jpg",
    "imageName": "template.png"
  },
  "message": null
}
```

## 2. 알림톡 아이템 이미지 업로드
- METHOD: POST
- URL: /v1/image/alimtalk/itemHighlight

### Request Body

| 키 | 데이터 타입 | 필수 | 설명 |
|----|------------|------|------|
| image | file | Y | 이미지 파일 1개 (jpg, jpeg, png / 최대 500KB) |
| imageNickname | string | N | 이미지 닉네임 |

### Example CURL

```bash
curl -X POST \
  -H 'x-api-key: {api-key}' \
  -F "image=@item.png" \
  -F "imageNickname=item_highlight_1" \
  https://bizmsg-center-api.blumn.ai/v1/image/alimtalk/itemHighlight
```

### Example Success Response

```json
{
  "code": "success",
  "data": {
    "imageUrl": "https://mud-kage.kakao.com/dn/example/item_image.jpg",
    "imageName": "item.png"
  },
  "message": null
}
```
