### 리뷰 작성하는 쿼리

```sql
// 유저ID(1), 가게ID(3)
INSERT INTO review(member_id, store_id, content, star, create_at)
VALUES(1,3,'음 너무 맛있어요 ...', 5, NOW());
```

### 마이 페이지 화면 쿼리

```sql
// 유저ID(1)
SELECT profile_url, name, phone_number, phone_certification, user_point
FROM user
WHERE user_id = 1
```

### 진행 중, 진행 완료한 미션 모아서 보는 쿼리(페이징 포함)

유저 미션에서 성공 여부,

미션에서 미션 내용, 미션 포인트,

스토어에서 가게 이름을 가져오고,

유저 id가 1 인 것들만 불러온 뒤 페이징 하기

```sql
SELECT m.mission_info, m.point, um.is_complete, s.name
FROM user_mission AS um
JOIN mission AS m ON um.mission_id = m.mission_id
JOIN store AS s ON m.store_id = s.store_id
WHERE um.user_id = 1 AND um.is_complete = 'SUCCESS'
ORDER BY um.user_mission.id DESC
LIMIT 10 OFFSET 0;
```

### 홈 화면 쿼리 (현재 선택 된 지역에서 도전이 가능한 미션 목록, 페이징 포함)

```sql
//유저ID(1), 지역ID(안암동 = 2)
SELECT s.name, s.category_id, m.mission_info, m.point, m.mission_id
FROM mission AS m
JOIN store AS s ON m.store_id = s.store_id
WHERE s.region_id = 2
	AND m.mission_id NOT IN(
		SELECT mission_id
		FROM user_mission
		WHERE user_id = 1
	)
ORDER BY m.mission_id DESC
LIMIT 10 OFFSET 0

-----------------------------------------------------------------
// 해당 지역에서 미션 몇개 성공했나?
SELECT COUNT(*) FROM user_mission AS um
JOIN mission AS m ON um.mission_id = m.mission_id
JOIN store AS s ON m.store_id = s.store_id
WHERE um.user_id = 1 AND s.region_id = 2 AND um.is_complete = true
```