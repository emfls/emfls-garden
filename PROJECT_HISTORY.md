# Project History

## 2026-09-16 — 최초 구축 착수

- Objective: Notion Master Plan 기준 Garden P0/P1 구축.
- 확인 기준: `EMFLS Network 관제탑`, `emfls-garden`, `Network Baseline v1`, `Network QA`, `Network Master Plan`.
- 결정: 충돌 없음. Site Control Page Build Status를 `IN_PROGRESS`로 갱신. Review Status는 관제 리뷰 전까지 승인하지 않음.
- 구현: Astro static, typed plant data 8종, 동적 Plant/Guide/Problem route, Finder, Watering Guide, Trust 페이지, metadata/canonical/robots/sitemap/404 기반.
- 안전: 독성 미확인은 `unknown`, 전용 Analytics·Search·Ads 발급값은 추가하지 않음.
- QA: `npm run check` PASS (0 errors, 2 non-blocking Astro hints). `npm run build` PASS, 29 pages generated.
- Known Issues: GitHub 원격 접근은 현재 환경 DNS 제한으로 live 확인 보류. Notion AI Search는 요금제 제한이나 기본 Search/Fetch는 사용 가능. Production/Visual QA 미완료.
- Next: check/build, responsive/live QA, 문서·Notion Work Report 갱신, `READY_FOR_REVIEW` 판정.

## 2026-09-16 — P3 Launch / QA

- GitHub: `main` commit `93be19275836c8e817825d54ac508b53afcab125`를 `origin/main`에 push.
- Cloudflare Pages: project `emfls-garden` 생성. GitHub source `emfls/emfls-garden`, production branch `main`, build `npm run build`, output `dist` 연결.
- Deployment: production deployment `d8f0dfb2-46af-4183-ac5d-88c3c08c3d96` 성공. Pages URL `https://d8f0dfb2.emfls-garden.pages.dev/`.
- Custom domain: `garden.emfls.com` Pages domain 등록 및 CNAME `garden.emfls.com → emfls-garden.pages.dev` 추가. Cloudflare 검증은 `pending / CNAME record not set`, 실제 URL은 522이므로 Live QA는 BLOCKED.
- Pages Live QA: 기본 Pages URL `/`, `/robots.txt`, `/sitemap.xml`, `/plants/`, `/plants/pothos/`, `/guides/watering/`, `/problems/yellow-leaves/`, `/tools/plant-finder/`, `/tools/watering-guide/` 모두 HTTP 200; invalid route는 404.
- Sitemap: 단일 `/sitemap.xml`, 28개 URL, sitemap index 0개. sitemap URL 상태 이상 없음.
- Metadata: title, description, canonical, OG title/description/url/type, Twitter card 확인. localhost/preview 문자열 0.
- Browser QA: Homepage, Plant List/Detail 링크 구조, Finder 결과, Watering Guide 결과, skip link, semantic navigation, form labels, focusable controls를 확인.
- Visual snapshot: Homepage Production mobile 캡처 완료. 320/360/375/390/desktop의 명시적 viewport별 캡처는 브라우저 연결 제약으로 미완료.
- Analytics: Garden 전용 GA4 ID 없음. Google Search/Naver/AdSense 실제 발급값 없음. 모두 Pending이며 placeholder 미삽입.
- Assessment: custom domain과 명시적 viewport Visual QA가 남아 `READY_FOR_REVIEW` 아님.

## 2026-09-16 — 운영체계 재동기화 / custom domain QA

- Objective: 최신 Notion 운영체계 기준으로 Garden P3 Launch Gate와 Review 준비 상태를 재확인하고 상태 드리프트를 제거.
- Source check: 관제탑 → Garden → Site Status Sync/Registry → Baseline → Network QA → Automation Protocol → Master Plan → Repo 문서 순서로 확인. 다른 EMFLS 프로젝트는 범위에서 제외.
- Cloudflare: `emfls-garden`은 GitHub `emfls/emfls-garden`, production branch `main`, `npm run build`, output `dist`로 연결됨. 최신 deployment `466c709b` 성공.
- Domain: Cloudflare Pages API에서 `garden.emfls.com`이 `active`/HTTP validation active로 전환되었고, 브라우저에서 custom domain Homepage와 핵심 경로가 정상 렌더링됨.
- Live QA: Homepage, Plant List, Plant Detail, Guide, Plant Finder, Watering Guide, 404의 custom-domain 접근성 트리를 확인. `/robots.txt`는 브라우저 제어기의 client block으로 직접 읽지 못했으므로 이전 HTTP 증거와 구분해 기록.
- Accessibility/UX: skip link, semantic navigation, visible focus styling, form labels/controls, reduced-motion CSS, keyboard-focusable controls 확인. Garden botanical editorial hierarchy와 no-image specimen layout 유지.
- Visual QA/Screenshots: custom-domain Homepage desktop snapshot을 캡처했고, 기존 Production mobile Homepage 및 대표 List/Detail/Finder/Watering 확인 기록을 유지. 320/360/375/390 명시적 viewport별 screenshot gate는 미완료.
- Assets: 사실성 있는 식물 사진을 임의 추가하지 않음. 현재 Plant data/specimen editorial layout에는 이미지가 필수 아님. AI image generation 또는 외부 이미지 asset은 사용하지 않음.
- Search/Analytics: Garden 전용 GA4, Google/Naver/Daum Search 및 sitemap 제출, IndexNow, AdSense 실제 근거 없음. placeholder를 넣지 않음.
- Code QA: 기존 기준 `npm run check` PASS (0 errors, 2 non-blocking Astro hints), `npm run build` PASS (29 static pages).
- Blockers: 명시적 viewport별 screenshot 미완료; Search Launch 외부 등록/제출 미완료; 관제 리뷰 전이 대기.
- Next Action: viewport 캡처 가능한 브라우저 환경에서 Visual Snapshot 최소 세트를 완성하고, 실제 외부 발급값이 생길 때만 Registry를 갱신한 뒤 `READY_FOR_REVIEW`를 검토.

## 2026-09-16 — Final Playwright Visual Review Gate evidence sync

- Objective: 관제 리뷰의 `CHANGES_REQUESTED`에 따라 이미 통과한 Visual QA 결과를 Repo history, checklist, tasks, screenshot evidence와 정합화.
- QA environment: Playwright 1.63.0 + Chromium, Production `https://garden.emfls.com/`.
- Base commit: `8bef4be4384843f76a565219450dcc794aa0872d`.
- Viewports: 320×1000, 360×1000, 375×1000, 390×1000, 1440×1000.
- Pages: `/`, `/plants/`, `/plants/pothos/`, `/guides/watering/`, `/tools/plant-finder/`, `/tools/watering-guide/`.
- Result: 총 30개 조합 모두 HTTP 200. 모든 viewport에서 `scrollWidth == clientWidth`, overflow element 0, navigation clipping 0, hero clipping 0, heading/text clipping 0, specimen layout clipping 0, form control viewport escape 0.
- Interaction: Plant Finder PASS, Watering Guide PASS, keyboard Tab PASS, skip link focus PASS, reduced-motion/accessibility 유지.
- Code QA: `npm run check` PASS (0 errors, 2 non-blocking Astro hints), `npm run build` PASS (29 pages).
- Code changes: 로직 변경 없음. Review evidence를 `docs/review/`에 영속 저장하고 checklist/tasks/history만 갱신.
- Screenshot evidence: `docs/review/home-desktop.png`, `home-390.png`, `plants-desktop.png`, `plant-detail-desktop.png`, `guide-desktop.png`, `plant-finder-desktop.png`, `watering-guide-desktop.png`. 각 파일은 Production URL, viewport, 환경, base commit, capture date 2026-09-16을 이 기록과 함께 관리한다.
- Known Issues: Search Launch / GA4 / AdSense 외부 등록값은 여전히 `NOT_SET`; Visual Review blocker는 해소.
- Assessment: `READY_FOR_REVIEW`.
- Next Action: Control Tower visual/launch review.
