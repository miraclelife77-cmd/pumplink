# PUMPLINK

펌프 선정 · 화학물질 호환성 검색 · 실무 자료를 제공하는 정적 사이트.

## 폴더 구조

```
pumplink/
├─ index.html                          # 메인 페이지 (펌프 빠른 검색/추천 포함)
├─ resources/
│  ├─ index.html                       # 실무 자료 목록
│  └─ chemical-compatibility.html      # 케미칼 호환성 검색 도구
├─ assets/
│  ├─ css/
│  │  └─ site.css                      # 공통 스타일(브랜드 토큰 포함)
│  └─ data/
│     └─ chemical-compat.json          # 화학물질 호환성 데이터
├─ _redirects                          # Netlify 클린 URL 리다이렉트
├─ netlify.toml                        # Netlify 빌드/배포 설정
├─ README.md
├─ CHANGELOG.md
└─ REGRESSION_CHECKLIST.md
```

## 로컬 실행

정적 파일이므로 별도 빌드 없이 임의의 정적 서버로 루트(`pumplink/`)를 서빙하면 된다.

```bash
python -m http.server 8765 --directory .
```

이후 `http://localhost:8765/index.html`, `http://localhost:8765/resources/index.html`,
`http://localhost:8765/resources/chemical-compatibility.html` 로 접속해 확인한다.

`file://` 로 직접 열면 브라우저에 따라 `fetch()` 요청(chemical-compat.json 로딩)이 차단될 수 있으므로
반드시 로컬 서버를 통해 확인한다.

## 배포

Netlify 배포 기준은 `netlify.toml`의 `publish = "."` 구조를 그대로 유지한다. 별도 빌드 스텝 없음.

## 하위 페이지 경로 규칙

- `resources/` 하위 페이지는 루트 자산을 `../assets/...` 상대 경로로 참조한다.
- 루트 `index.html`은 `assets/...` 상대 경로로 참조한다.
- 경로 변경 시 [REGRESSION_CHECKLIST.md](REGRESSION_CHECKLIST.md)를 따라 검증한다.
