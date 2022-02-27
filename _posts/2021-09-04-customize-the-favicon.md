---
title: 나만의 favicon 적용해보기
author: three.balance
date: 2021-09-04 21:58:00 +0900
categories: [Blogging, Tutorial]
tags: [tutorial]
---

<b>Notice</b> : 이 글은 [링크](https://chirpy.cotes.info/posts/customize-the-favicon/)를 참조하여 작성하였습니다.

favicon 파일들은 `assets/img/favicons/` 디렉토리 아래에 저장되어야한다. 그래서 나만의 favicon 파일들을 만들어 해당 디렉토리 아래에 집어넣으면 되는데 Chirpy 에서는 <b>아래의 방식</b>으로 favicon 파일을 만들 것을 권장하고 있다.

## Generate the favicons
1. Real Favicon Generator에서 요구하는 파일 확장자의 정사각형의 이미지를 준비한다.
2. Select your Favicon버튼을 눌러 준비한 이미지를 업로드한다.
3. 업로드 후 페이지의 제일 아래로 내려가서 Generate your Favicons and HTML code 버튼을 누른다.
4. Favicon package 버튼을 눌러 압축 파일을 다운받는다.


## Replace
다운로드 받은 압축 파일을 풀고 favicon 파일들은 그대로 두고 아래의 파일들은 지운다.

* `browserconfig.xml`
* `site.webmanifest`

나머지 남은 파일들을 `assets/img/favicons/` 디렉토리 아래로 옮긴다.

이렇게 하고 빌드를 하면 다음 버전에 favicon 파일들이 적용된 것을 확인할 수 있다.

아래의 표는 png 파일과 ico 파일은 제시한 온라인 도구를 사용하라는 것이고 `browserconfig.xml` 파일과 `site.webmanifest` 파일은 기존 파일을 사용하라는 것으로 받아들이면 될 것 같다.
