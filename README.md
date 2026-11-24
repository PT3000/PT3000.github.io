# PT3000 블로그

운영 주소: <https://pt3000.github.io>

[Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) 테마와
[공식 Chirpy Starter](https://github.com/cotes2020/chirpy-starter)를 사용하는 Jekyll 블로그입니다.
Starter 기준 커밋은 `beffc88713242da8bf49325674be38d171071213`이며,
원본의 MIT 라이선스와 저작권 표시는 `LICENSE`에 보존했습니다.

## 설정과 소개

- `_config.yml`: 블로그 제목, 설명, 언어, 시간대, GitHub 계정과 주소를 설정합니다.
- `_tabs/about.md`: 소개 페이지를 작성합니다.
- `_posts/YYYY-MM-DD-title.md`: 날짜와 제목을 파일 이름으로 사용해 글을 추가합니다.

사이트 주소는 `https://pt3000.github.io`, `baseurl`은 빈 문자열입니다.
화면 크기에 맞추는 기본 레이아웃과 시스템 설정을 따르는 밝은/어두운 테마를 사용합니다.

## 글 작성

다음은 새 글의 형식 예시입니다. 실제 게시글은 `_posts/`에 별도로 작성하세요.
파일 이름 예: `_posts/2026-11-12-first-post.md`

```markdown
---
title: 첫 번째 기록
date: 2026-11-12 09:00:00 +0900
categories: [기록]
tags: [블로그]
---

여기에 Markdown으로 본문을 작성합니다.
```

## 알고리즘 정리

왼쪽 메뉴의 [알고리즘](https://pt3000.github.io/algorithms/)에서 알고리즘 글을 모아 볼 수 있습니다.
목록은 풀이 사이트별로 나뉘며, 글의 front matter에 지정한 두 번째 카테고리로 구분합니다.

- 백준: `categories: [알고리즘, 백준]`
- 프로그래머스: `categories: [알고리즘, 프로그래머스]`

글에 넣는 이미지는 `assets/img/algorithms/<글 슬러그>/`에 둡니다.
목록 페이지는 `_tabs/algorithms.md`에서 관리합니다.

## ABC 프로젝트

왼쪽 메뉴의 [ABC 프로젝트](https://pt3000.github.io/abc-project/)에서 프로젝트 글을 모아 볼 수 있습니다.
글의 front matter에 `categories: [ABC 프로젝트]`를 지정하면 목록에 자동으로 표시됩니다.
카테고리 이름은 대소문자와 띄어쓰기까지 정확히 일치해야 합니다.
목록 페이지는 `_tabs/abc-project.md`에서 관리합니다.

## 메뉴 탭 추가

`_tabs/`에 새 탭을 만들면 `_data/locales/ko-KR.yml`의 `tabs`에도 제목을 등록해야 합니다.
등록하지 않으면 브라우저 탭 제목이 ` | PT3000`처럼 비어 보입니다.
키는 탭의 `title`을 소문자로 바꾼 값입니다. 예: `abc 프로젝트: ABC 프로젝트`

## 로컬 실행과 배포

Ruby 3.4와 Bundler를 준비한 뒤 저장소 루트에서 `bundle install`을 실행합니다.
`bundle exec jekyll serve`로 로컬 서버를 시작하고 <http://127.0.0.1:4000>에서 확인합니다.

`main`을 대상으로 하는 Pull Request에서는 GitHub Actions가 사이트를 빌드하고
HTMLProofer로 내부 링크를 검사합니다. `main` 브랜치에서만 GitHub Pages로 배포합니다.
워크플로는 `.github/workflows/pages-deploy.yml`에 있습니다.
