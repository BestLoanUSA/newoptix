# New Optix — 고객 웹사이트 (BizHigher 제작 실험 1호)

가든그로브 안경점 New Optix의 정적 사이트. Cloudflare Pages가 이 레포를 빌드해 newoptix.com에 배포한다.

## 빌드
```
node build.js      # → dist/
```

## 어디를 고치나
| 바꾸고 싶은 것 | 파일 |
|---|---|
| 주소·전화·영업시간·브랜드·보험·결제수단·연차·언어·도메인 | `site.json` |
| 서비스 7종 문구·FAQ | `services.json` |
| 디자인 | `src/style.css` |
| 페이지 구조 | `build.js` |
| OG 이미지 | `src/og/og.html` → `node src/og/make-og.js` |

## ⚠️ 공개 전 체크
- `site.json`의 `_assumed` 목록은 **가정값**이다(일부 브랜드·운영 연수·도메인 등). 업주 확인 후 수정
- `draft: true` 동안은 모든 페이지 `noindex` + `robots.txt` 전면 차단(검색 비노출). 확인이 끝나면 `false`로 바꾸고 재빌드
- 매장 실사진이 아직 없다 — 들어오면 히어로·소개 페이지에 교체
- 소개 페이지의 `TODO(owner)` 자리에 사장님 이야기
- 구글 리뷰 원문은 사이트에 옮기지 않는다(리뷰 주제만 요약 + 구글 링크)

## 배포 (Cloudflare Pages)
| 설정 | 값 |
|---|---|
| Production branch | `main` |
| Root directory | (비워 둠) |
| Build command | `node build.js` |
| Build output directory | `dist` |

`main`에 push하면 1~2분 뒤 newoptix.com에 반영된다. `dist/`는 빌드 결과물이라 커밋하지 않는다.
