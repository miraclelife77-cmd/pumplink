# Changelog

## 2026-07-17

- AI COMPANY 작업공간 내 별도 하위 프로젝트(`pumplink/`)로 정리.
- 파일 경로만 정리 대상 구조로 배치 (`index.html`, `resources/index.html`,
  `resources/chemical-compatibility.html`, `assets/css/site.css`,
  `assets/data/chemical-compat.json`, `netlify.toml`). 기능 변경 없음.
- 구버전 백업 `index.html기존`을 `AI COMPANY/Archive/pumplink-backups/`로 이동.
- README.md, CHANGELOG.md, REGRESSION_CHECKLIST.md 추가.
- 로컬 서버(`python -m http.server`) 기준으로 index.html, resources/index.html,
  resources/chemical-compatibility.html 정상 동작 확인 (콘솔 에러 없음,
  `assets/data/chemical-compat.json` fetch 200 OK, 화학물질 검색 자동완성 정상).
