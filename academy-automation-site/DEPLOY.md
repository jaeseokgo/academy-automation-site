# 학원ON 랜딩페이지 · 배포 가이드

## 🚀 추천 배포 플로우 (소요 15분, 비용 0원)

### 1단계. Vercel 배포 (5분)

1. [vercel.com](https://vercel.com) 가입 (GitHub 계정 추천)
2. 이 폴더(`academy-automation-site`)를 GitHub 새 저장소로 올리기
3. Vercel 대시보드에서 **Add New → Project → GitHub 저장소 선택 → Deploy**
4. 끝. 자동으로 `https://academy-automation-site.vercel.app` 같은 주소가 생깁니다.

> **왜 Vercel?**
> - 무료 (개인 프로젝트)
> - `git push`만 하면 자동 재배포
> - 나중에 Next.js로 업그레이드할 때 그대로 사용 가능
> - 한국에서도 속도 빠름 (Edge Network)

### 2단계. 도메인 연결 (10분, 연 15,000원)

1. [가비아](https://www.gabia.com) 또는 [후이즈](https://whois.co.kr)에서 도메인 구매
   - 예시: `hagwon-on.kr`, `auto-academy.co.kr`
2. Vercel 프로젝트 → **Settings → Domains → Add** → 구매한 도메인 입력
3. 도메인 관리 페이지에서 Vercel이 알려주는 **A / CNAME 레코드** 등록
4. 5~30분 대기 후 HTTPS까지 자동 적용

### 3단계. 문의 폼 연결 (5분)

현재 문의 폼은 alert만 뜨는 데모 상태입니다. 실제로 문의를 받으려면:

**옵션 A — [Formspree](https://formspree.io) (추천)**
- 무료 플랜: 월 50건까지 문의 접수
- `<form>` 태그의 `action` 속성만 바꾸면 끝
- 접수 시 이메일로 자동 전달

```html
<!-- index.html에서 이 부분을 찾아서 -->
<form class="inquiry" onsubmit="handleSubmit(event)">

<!-- 이렇게 바꾸세요 -->
<form class="inquiry" action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
```

**옵션 B — Google Form**
- 완전 무료 · 무제한
- 기존 폼을 Google Form 링크로 교체하거나 iframe 임베드

**옵션 C — 카카오톡 채널 상담**
- 카카오 비즈니스 채널 개설 (무료)
- CTA 버튼을 카카오 채널 링크로 변경

---

## 📂 파일 구조

```
academy-automation-site/
├── index.html    # 랜딩페이지 (단일 파일, 모든 CSS/JS 포함)
└── DEPLOY.md     # 이 문서
```

---

## 🎨 커스터마이징 포인트

### 브랜드명 / 로고
`index.html`에서 "학원ON"을 원하는 이름으로 일괄 변경 (Ctrl+F)

### 색상 (토스 블루 → 다른 컬러)
```css
/* :root 섹션에서 아래 변수만 바꾸면 전체 색상 톤 교체 */
--brand-500: #3182F6;  /* 메인 컬러 */
--brand-600: #1B64DA;  /* hover 컬러 */
```

### 가격 / 통계 수치
`#pricing`, `#stats` 섹션에서 직접 수정

### 실제 사례 추가
`.problem-card` 아래 또는 새 섹션으로 도입 학원 후기 추가 추천

---

## 🔜 다음 단계 (v2 로드맵)

랜딩페이지로 문의가 쌓이기 시작하면:

1. **관리자 페이지** — 도입 학원 리스트 / 구독 관리 → Next.js + Supabase
2. **실제 결제 연동** — 토스페이먼츠 (수수료 1.8~2.9%) 또는 아임포트
3. **대시보드 SaaS** — 이미 보유 중인 출결/채점/수업료 스킬을 웹 서비스로 이식
4. **사업자등록 · PG 계약** — 실제 결제 받으려면 필수

단, v1 랜딩 + 계좌이체만으로도 첫 10개 학원까지는 충분합니다. 빠르게 시작하고 고객 반응 보고 증설하세요.

---

## 📞 배포 중 막히면

각 단계에서 막히면 스크린샷이나 에러 메시지 공유해주세요. 단계별로 도와드릴게요.
