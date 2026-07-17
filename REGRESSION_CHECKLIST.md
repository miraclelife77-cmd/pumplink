# Regression Checklist

경로/구조 변경 후 반드시 아래 항목을 로컬 서버 기준으로 확인한다. (`file://` 직접 열기 금지 —
`fetch()`가 차단되어 화학호환성 페이지가 깨진 것처럼 보일 수 있음)

```bash
python -m http.server 8765 --directory .
```

## 1. index.html (메인)

- [ ] `assets/css/site.css` 로드 (네트워크 탭 200 OK)
- [ ] 상단 네비게이션 "실무 자료" 링크 → `resources/index.html` 이동
- [ ] "펌프 빠른 검색" 위젯에서 유체 유형/유량/양정 입력 후 "추천 펌프 찾기" 클릭 시
      추천 결과(모델명, 모델 코드, 유량/양정, 재질) 정상 표시
- [ ] "비교하기" 클릭 시 브랜드별 비교 모달 정상 오픈
- [ ] "점도를 몰라요" 체크 시 점도 등급 드롭다운 노출

## 2. resources/index.html (실무 자료)

- [ ] `../assets/css/site.css` 로드 (네트워크 탭 200 OK)
- [ ] 네비게이션 로고/메뉴 링크가 `../index.html`로 정상 이동
- [ ] "케미칼 호환성 검색" 카드 클릭 → `chemical-compatibility.html` 이동

## 3. resources/chemical-compatibility.html (케미칼 호환성 검색)

- [ ] `../assets/css/site.css` 로드 (네트워크 탭 200 OK)
- [ ] `../assets/data/chemical-compat.json` fetch 200 OK, 콘솔 에러 없음
- [ ] "화학물질로 찾기" 입력창에 예: `Acetone` 입력 시 자동완성 목록 표시
- [ ] 자동완성 항목 클릭 시 재질별 호환 등급(A~D) 결과 렌더링
- [ ] "재질로 찾기" / "소재 개요" / "전체 표" 탭 전환 정상 동작

## 4. 배포 설정

- [ ] `netlify.toml`의 `publish = "."` 유지 확인
- [ ] `_redirects`의 `/resources`, `/resources/chemical-compatibility` 클린 URL 규칙 유지 확인
