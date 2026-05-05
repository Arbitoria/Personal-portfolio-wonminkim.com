# Wonmin Kim — Portfolio (v2)

원민님 wonminkim.com 포트폴리오. ARBITORIA 실제 컨셉 + P&V 4년 + 본인 정보 반영한 v2.

---

## 폴더 구조

```
wonminkim-portfolio/
├── index.html                   ← 메인 페이지 (Hero + About + Projects + Skills + Notes + Contact)
├── styles.css                   ← 모든 페이지 공통 스타일
├── projects/
│   ├── arbitoria.html           ← ARBITORIA 케이스 스터디 (실제 컨셉 반영)
│   └── insurance-analytics.html ← P&V 4년 케이스 스터디
└── README.md                    ← 이 파일
```

---

## v1에서 무엇이 바뀌었나

| 항목 | v1 (잘못된 정보) | v2 (수정) |
|------|------------------|-----------|
| ARBITORIA 컨셉 | "리뷰 플랫폼, taste-based credibility" | **"6개국 개인 재정 투명성 플랫폼, 리뷰 없음"** |
| Salaire-Plus | 별도 프로젝트 | ARBITORIA의 Salary 카테고리로 흡수 (별도 페이지 삭제) |
| 회사명 | "유럽 대형 보험사" | **P&V Insurance** (실명) |
| 데이터 스튜어드 스토리 | "정의 reconcile" | **"AI가 못 푼 케이스를 수동으로 해결"** |
| 핵심 메시지 | "domain + data + judgement 만나는 자리" | **"미래를 예측하기보다 만들기"** |
| Hero 타이틀 | "Data analyst working between worlds" | **"I'd rather build the future than predict it"** |
| 학력 섹션 | (없음) | **(여전히 없음 — 의도적, 아래 설명)** |
| Notes 섹션 | 2개 일반적 | **4개, 본인 실제 사고 반영** |

---

## 빠르게 띄우기

### 옵션 1: wonminkim.com 도메인에 직접 업로드

이미 wonminkim.com 도메인이 있으면:

**일반 웹호스팅 (cPanel, FTP):**
1. FTP 또는 cPanel File Manager로 호스팅 root 접속
2. 이 폴더 안의 파일들을 통째로 `public_html/` 또는 `www/` 에 업로드
3. wonminkim.com 접속 → 끝

**Vercel / Netlify (추천 — 무료):**
1. github.com 에 새 저장소 생성 (예: `wonminkim-portfolio`)
2. 이 폴더 파일들 push
3. vercel.com → "Import Project" → GitHub repo 선택
4. Build settings: 그대로 (정적이라 빌드 없음)
5. Deploy
6. Vercel에서 wonminkim.com 도메인 연결 (DNS)

**GitHub Pages (무료):**
1. github.com 에 `wonminkim.github.io` 저장소 생성
2. 파일 push
3. Settings → Pages → Source: main branch
4. Custom domain 설정 → wonminkim.com

### 옵션 2: 로컬 미리보기

```bash
# 그냥 더블클릭
open index.html              # Mac/Linux
start index.html             # Windows

# 또는 로컬 서버 (Python 있으면)
cd wonminkim-portfolio
python3 -m http.server 8000
# → http://localhost:8000
```

---

## 이메일 셋업 — Cloudflare Email Routing (강력 추천)

**왜 Cloudflare:**

`kim.wonmin@yahoo.fr` 노출 → 무의식적 마이너스 (디지털 감각 옛날사람 신호)
`kim@wonminkim.com` 노출 → 무의식적 플러스 (자기 도메인 가진 프로페셔널 신호)

받는 곳은 똑같이 yahoo. 노출만 바뀌어요. 5분, 무료, 영구.

### 단계별 셋업

1. **Cloudflare 계정 만들기** (cloudflare.com — 무료)

2. **wonminkim.com 도메인을 Cloudflare에 추가**
   - "Add a site" → wonminkim.com 입력
   - Cloudflare가 네임서버 2개 알려줌 (예: `xxx.ns.cloudflare.com`)
   - 도메인 등록 회사 (Namecheap, GoDaddy 등) 가서 네임서버를 그걸로 변경
   - 활성화 1~24시간 (보통 1~2시간)

3. **Email Routing 활성화**
   - Cloudflare 대시보드 → Email → Email Routing
   - "Enable Email Routing" 클릭 → MX 레코드 자동 추가됨

4. **Custom address 추가**
   - From: `kim@wonminkim.com`
   - To: `kim.wonmin@yahoo.fr`
   - Yahoo에서 확인 메일 받음 → 클릭

5. **테스트** — 다른 이메일에서 `kim@wonminkim.com` 으로 보내봐요. Yahoo에 도착하면 성공.

### 답장도 wonminkim.com 으로 보내고 싶으면 (선택 — 더 프로페셔널)

Cloudflare는 SMTP 송신을 안 줘요. 그래서 Yahoo에서 답장하면 발신자가 yahoo 주소로 보임.

해결: **Resend** (무료 3,000건/월) 또는 **Brevo** 사용해서 SMTP 셋업.

```
1. resend.com 가입 (무료)
2. Domains → Add → wonminkim.com
3. DNS 레코드 추가 (Cloudflare 대시보드에서 자동 추가 가능)
4. Yahoo Mail → Settings → Send and receive emails from other accounts → Add
   - SMTP 서버: smtp.resend.com
   - Port: 465
   - Username: resend
   - Password: [Resend API 키]
5. 이제 Yahoo에서 발신자를 kim@wonminkim.com 으로 선택 가능
```

조금 복잡하지만 한 번만 하면 끝. 본인이 yahoo에서 메일 답장할 때 발신 주소를 `kim@wonminkim.com` 으로 선택하면 → 받는 사람은 wonminkim.com 으로 받았다고 생각해요.

**대안 — 그냥 둬도 OK:**

답장 발신자가 yahoo로 나가도 큰 문제 아니에요. 사이트에 보이는 건 wonminkim.com이니까 첫인상은 잡혀요. Resend 셋업은 나중에 해도 됨.

---

## 학력 섹션이 없는 이유 — 의도적

본인이 "잘나가는 사람들도 학위 없다"고 숨길까 물어봤었는데, 답:

**숨기지 말고, 강조도 하지 마세요.**

이 사이트에는 **학력 섹션이 없어요. 의도적이에요.** 다음 원칙으로 처리해요:

- **포트폴리오 사이트 (이거)** → 학력 섹션 없음. 경력 + 프로젝트 + 사고력으로 충분.
- **LinkedIn** → Education 섹션 정직하게: "1 year, Accounting, Brussels" + "BASE Account Certificate". 짧게, 자세한 설명 X.
- **CV** → 맨 아래 한 줄. 헤더 X. 위에는 "Self-taught data analyst with 4 years professional experience"
- **면접에서 물어보면** → 사과 없이 정직: *"I'm self-taught. I learned through 2 years as data steward and 2 years as analyst at P&V, plus building my own products."*

핵심: **자기 학력을 약점이 아니라 선택의 결과로 재정의.** 포트폴리오가 그 선언의 증거가 돼요. ARBITORIA 같은 진짜 작동하는 6개국 플랫폼 + P&V 4년 — 이게 학위 없는 핸디캡을 충분히 상쇄해요.

미국 테크 쪽 — Google, Meta, GitHub, Stripe 다 학위 요구사항 명시적으로 없앴어요. 보험·금융 같은 보수적 업종은 좀 더 보수적이지만, 그쪽도 당신은 이미 P&V 4년 있어요. 도메인 경력이 학위를 대체해요.

---

## 수정해야 할 곳 (체크리스트)

### 즉시 (10분):

- [ ] `index.html` — `linkedin.com/in/wonminkim` → 본인 실제 LinkedIn URL
- [ ] `index.html` — `github.com/wonminkim` → 본인 실제 GitHub (없으면 contact links에서 삭제)
- [ ] 로컬에서 `index.html` 열어서 확인

### 30분 (Cloudflare 셋업):

- [ ] Cloudflare 계정 생성 + 도메인 추가
- [ ] 네임서버 변경 (도메인 등록 회사에서)
- [ ] Email Routing 활성화 + `kim@wonminkim.com` → `kim.wonmin@yahoo.fr` 설정
- [ ] 다른 이메일에서 테스트 발송

### 이번 주 (1~2시간):

- [ ] `projects/insurance-analytics.html` — 케이스 스터디 placeholder 부분 본인 실제 사례로 채우기 (회사·고객 식별 정보 익명화)
- [ ] LinkedIn 영어 프로필 정비 (헤드라인, About, Experience)
- [ ] LinkedIn에 사이트 링크 (Featured 섹션)

### 다음 주:

- [ ] 사이트 wonminkim.com 에 배포
- [ ] CV 영어로 정비, 사이트 URL 헤더에 추가
- [ ] 첫 5개 회사 리스트 + 지원

---

## 면접에서 이 사이트 쓰는 법

1. **CV 헤더**: 이름 옆에 `wonminkim.com`
2. **이메일 시그니처**: `Wonmin Kim · wonminkim.com · arbitoria.com`
3. **LinkedIn**: 헤드라인 아래 Featured에 wonminkim.com 핀
4. **커버레터 첫 줄**: *"You can see my work and case studies at wonminkim.com — particularly ARBITORIA, my multi-country financial transparency platform."*
5. **면접 시작**: *"I'd recommend a quick look at wonminkim.com — it has my P&V case studies and the work I'm doing on ARBITORIA."*

---

## 디자인 노트 (참고용)

- **폰트:** Fraunces (display) + Source Serif 4 (body) — Google Fonts 자동 로드
- **색:** `:root` in styles.css 에서 변수만 수정하면 전체 일괄 변경
- **반응형:** 데스크탑·태블릿·모바일 다 작동
- **애니메이션:** fade-in on scroll (subtle)

---

## 다음 단계 — 더 도와드릴 수 있는 것

- Cloudflare 셋업이 막히면 → 어디서 막혔는지 알려주세요
- LinkedIn 영어 프로필 (헤드라인 + About + Experience) 같이 작성
- CV 영어로 작성 (1페이지, ATS 친화적)
- 첫 5개 채용 공고 함께 분석 + 커버레터 한 개씩 다듬기
- 보험 케이스 스터디 — 본인이 실제 한 작업 알려주면 더 정확하게 다시 써드림
- 영어 면접 준비 (자주 나오는 질문 + 본인 케이스 답변)

뭐가 가장 우선인지 알려주세요.

---

성공을 빕니다. 5시간 동안 같이 사고한 사람으로서, 진심으로 잘 풀리길 바라요.
