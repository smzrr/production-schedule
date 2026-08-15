# SMZRR 관제탑

SMZRR 2027 Hero Film 제작 로드맵 + AI 영화제 출품 데이터베이스 대시보드.
정적 HTML 한 파일(`index.html`)로만 이루어져 있어 별도 서버 없이 GitHub Pages로 바로 올릴 수 있습니다.

- 상태(모집중/마감임박/마감)는 **접속하는 시점의 실제 날짜**를 기준으로 자동 계산됩니다.
- 로드맵/축제 DB/전략 등 나머지 데이터는 2026-08-15 기준으로 조사된 스냅샷이며, 엑셀 원본이 바뀌면 아래 "데이터 갱신" 절차로 다시 반영해야 합니다.

## 처음 온라인에 올리기 (GitHub Pages, 1회만)

1. https://github.com/new 에서 새 저장소 생성
   - Repository name: 원하는 이름 (예: `smzrr-control-tower`)
   - **Private 대신 Public**으로 만들어야 GitHub Pages 무료 배포가 됩니다. 검색엔진 노출은 `robots.txt`(`Disallow: /`)와 `<meta name="robots" content="noindex">`로 이미 막아뒀으니, URL을 아는 사람만 접근하게 됩니다.
2. 이 폴더에서 아래 명령 실행 (터미널):

   ```bash
   cd "smzrr-control-tower"
   git remote add origin https://github.com/<본인계정>/<저장소이름>.git
   git branch -M main
   git push -u origin main
   ```

3. GitHub 저장소 페이지 → **Settings → Pages** → Source를 `Deploy from a branch`, Branch를 `main` / `(root)`로 설정 후 Save.
4. 1~2분 후 `https://<본인계정>.github.io/<저장소이름>/` 에서 접속 가능.

## 데이터 갱신하기 (엑셀이 바뀌었을 때)

1. Claude에게 새로 바뀐 엑셀 파일 1~2개를 다시 첨부해서 "관제탑 데이터 갱신해줘"라고 요청
2. Claude가 이 `index.html`을 새 내용으로 다시 작성해줌
3. 아래 명령으로 반영:

   ```bash
   cd "smzrr-control-tower"
   git add index.html
   git commit -m "데이터 갱신: YYYY-MM-DD"
   git push
   ```

4. 1분 정도 후 사이트에 자동 반영됨 (GitHub Pages가 push마다 자동 재배포).

## 파일 구성

- `index.html` — 사이트 전체 (HTML+CSS+JS 단일 파일, 외부 의존성 없음)
- `robots.txt`, `<meta name="robots">` — 검색엔진 비노출 (링크 아는 사람만 접근)
- `.nojekyll` — GitHub Pages가 Jekyll로 파일을 가공하지 않도록 하는 빈 파일
