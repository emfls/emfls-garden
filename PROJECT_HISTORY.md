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
