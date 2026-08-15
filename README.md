# SMZRR 관제탑

SMZRR 2027 Hero Film 제작 로드맵 + AI 영화제 출품 데이터베이스 대시보드.
정적 HTML 한 파일(`index.html`)로만 이루어져 있어 별도 서버 없이 GitHub Pages로 바로 올릴 수 있습니다.

- 상태(모집중/마감임박/마감)는 **접속하는 시점의 실제 날짜**를 기준으로 자동 계산됩니다.
- 로드맵/축제 DB/전략 등 나머지 데이터는 2026-08-15 기준으로 조사된 스냅샷이며, 엑셀 원본이 바뀌면 아래 "데이터 갱신" 절차로 다시 반영해야 합니다.

## 배포 정보

- 저장소: https://github.com/smzrr/production-schedule
- 사이트 주소: https://smzrr.github.io/production-schedule/
- GitHub Pages: `main` 브랜치 `/` (root) 배포로 설정됨. `git push`할 때마다 1~2분 내 자동 재배포됨.

## 데이터 갱신하기

**방법 A — 엑셀 원본이 바뀐 경우**

1. 이 대화(Claude)에 새로 바뀐 엑셀 파일을 다시 첨부해서 "관제탑 데이터 갱신해줘"라고 요청
2. Claude가 이 `index.html`을 새 내용으로 다시 작성
3. 아래 명령으로 반영:

   ```bash
   cd "/Users/smzrr_sy/Downloads/SMZRR 영화제:광고제/smzrr-control-tower"
   git add index.html
   git commit -m "데이터 갱신: YYYY-MM-DD"
   git push
   ```

**방법 B — 엑셀 없이 항목 몇 개만 추가/수정하고 싶은 경우**

채팅으로 바로 요청하면 됨 (예: "OO 영화제 마감일이 9/30으로 바뀌었어", "새 영화제 하나 추가해줘 — 이름/국가/마감일/링크는 이거야"). Claude가 `index.html`의 해당 데이터 배열만 수정.

두 방법 모두 마지막엔 `git add / commit / push` 세 줄이 필요합니다 — 이 세션에서는 `git push`가 harness 정책상 자동 실행이 막혀 있어 직접 실행해야 합니다.

## 파일 구성

- `index.html` — 사이트 전체 (HTML+CSS+JS 단일 파일, 외부 의존성 없음)
- `robots.txt`, `<meta name="robots">` — 검색엔진 비노출 (링크 아는 사람만 접근)
- `.nojekyll` — GitHub Pages가 Jekyll로 파일을 가공하지 않도록 하는 빈 파일
