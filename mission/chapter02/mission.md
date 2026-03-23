### 피어리뷰(주니꺼)
아직 안함

---
## 홈화면

**API Endpoint:** /api/v1/home

**Method:** GET

**Request Header:** Authorization: Bearer {token}

**Query Parameter**

```sql
{
	"regionName": "안암동"
}
```

**Path Variable:** X

**Request Body**

```sql

```

**Response Body**

```sql
{
  "isSuccess": true,
  "code": "HOME200",
  "message": "홈 화면이 성공적으로 조회되었습니다.",
  "result": {
    "currentRegion": "안암동",
    "successMission": 7,
    "alarmCount": 99999,
    "missions": [
	    {
	      "missionId": 1,
	      "storeName": "반이학생마라탕",
	      "missionContent": "10000원 이상의 식사시",
	      "missionPoint": 500,
	      "missionDeadline": 7
	    },
	    {
	      "missionId": 2,
	      "storeName": "반이학생마라탕",
	      "missionContent": "10000원 이상의 식사시",
	      "missionPoint": 500,
	      "missionDeadline": 7
	    },
    ]
  }
}
```

## 마이페이지 리뷰 작성

**API Endpoint:** /api/v1/stores/{store_id}/reviews/

**Method:** POST

**Request Header:** 

Authorization: Bearer {token}

Content-type: multipart/form-data

**Query Parameter:** X

**Path Variable:** 

```sql
{
	"storeId": 1
}
```

**Request Body**

|  |  |
| --- | --- |
| star | 5 |
| content | “맛있어여ㅕ” |
| photo_url | 사진 파일 |

**Response Body**

```sql
{
  "isSuccess": true,
  "code": "REVIEW200",
  "message": "리뷰 작성이 성공했습니다.",
  "result": {
    "reviewId": "1"
  }
}
```

## 미션 목록 조회

**API Endpoint:** /api/v1/users/user-missions

**Method:** GET

**Request Header:** Authorization: Bearer {token}

**Query Parameter**

```sql
{
	"isComplete"= true 이나 false
}
```

**Path Variable:** X

**Request Body**

```sql
필요없음
```

**Response Body**

```sql
{
  "isSuccess": true,
  "code": "USER_MISSION200",
  "message": "내 미션이 성공적으로 조회되었습니다.",
  "result": {
    "myMissions": [
	    {
	      "userMissionId": 1,
	      "storeName": "반이학생마라탕",
	      "missionContent": "10000원 이상의 식사시",
	      "missionPoint": 500,
	      "missionDeadline": 7
	    },
	    {
	      "userMissionId": 2,
	      "storeName": "반이학생마라탕",
	      "missionContent": "10000원 이상의 식사시",
	      "missionPoint": 500,
	      "missionDeadline": 7
	    },
    ]
  }
}
```

## 미션 성공 누르기

**API Endpoint:** /api/v1/users/user-missions/{user_mission_id}

**Method:** POST

**Request Header:** Authorization: Bearer {token}

**Query Parameter**

```sql
필요없음
```

**Path Variable**

```sql
{
	"userMissionId": 1
}
```

**Request Body**

```sql
필요없음
```

**Response Body**

```sql
{
  "isSuccess": true,
  "code": "USER_MISSION_REQUEST200",
  "message": "내 미션 완료 요청 완료",
  "result": {
    "userMissionId": 1
  }
}
```

## 회원가입하기

**API Endpoint:** /api/v1/auth/signup

**Method:** POST

**Request Header:** X

**Query Parameter**

```sql
필요없
```

**Path Variable:** X

**Request Body**

```sql
{
	"email": "ddd@naver.com",
  "password": "1234",
  "name": "레오",
  "gender": "MALE",
  "birth": "2003-12-02",
  "address": "경기도 안산시",
  "agreedTerms": [1, 3],
  "userFoods": [0, 1, 3]
}
```

**Response Body**

```sql
{
  "isSuccess": true,
  "code": "MY_MISSION200",
  "message": "내 미션이 성공적으로 조회되었습니다.",
  "result": {
		"email": "ddd@naver.com",
	  "password": "1234",
	  "name": "레오",
	  "gender": "MALE",
	  "birth": "2003-12-02",
	  "address": "경기도 안산시",
	  "agreedTerms":[
      { "termId": 1, "termName": "위치정보제공" },
      { "termId": 3, "termName": "마케팅수신동의" }
    ],
	  "userFoods":[
      { "foodId": 0, "foodName": "한식" },
      { "foodId": 1, "foodName": "일식" },
      { "foodId": 3, "foodName": "양식" }
    ]
	}
}
```