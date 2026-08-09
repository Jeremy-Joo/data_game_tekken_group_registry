# data_game_tekken_group_registry

철권8 단체 대화방(단톡방 등) 그룹의 멤버 등록 데이터. [tekkenstats.com](https://tekkenstats.com)
"그룹 분석" 기능이 런타임에 `raw.githubusercontent.com`으로 이 저장소를 읽는다
(`web_game_tekken_stats_wavu`의 `lib/tekken/player-index.ts`가 자기 저장소의
`player-index-data.json`을 읽는 것과 같은 방식).

## 구조

- `index.json` — 전체 그룹 목록: `{ groups: [{ slug, name, createdAt }] }`
- `groups/<slug>.json` — 그룹 하나의 멤버 명단: `{ slug, name, createdAt, members: [{ nick, id }] }`

## 쓰기 경로

이 파일들은 사람이 직접 편집하지 않는다 — 전부 `web_game_tekken_stats_wavu`의
API 라우트가 GitHub Contents API로 커밋한다.

- 그룹 생성/삭제: `app/api/admin/group-create`, `app/api/admin/group-delete`
  (관리자 비밀번호 필요)
- 멤버 등록: `app/api/group/[slug]/register` (링크만 있으면 누구나, 비밀번호 불필요)

담는 값(단톡방 닉네임 + 철권8 폴라리스 ID)은 원래 각 그룹 대화방 안에서 공유되던
정보이고, 민감정보가 아니다.
