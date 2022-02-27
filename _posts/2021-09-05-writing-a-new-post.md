---
title: 새로운 글 작성하기
author: three.balance
date: 2021-09-05 11:46:00 +0900
categories: [Blogging, Tutorial]
tags: [tutorial]
---

**Notice** : 이 글은 [링크](https://chirpy.cotes.info/posts/write-a-new-post/)를 참조하여 작성하였습니다.

## 이름과 경로
새로운 파일의 이름을 `YYYY-MM-DD-TITLE.EXTENSION` 으로 만들어서 `_posts` 폴더 안에 넣어야하고 `EXTENSION` 은 `md` 혹은 `markdown` 중 하나여야 한다.

## Front Matter
기본적으로 파일의 최상단에 아래와 같은 [Front Matter](https://jekyllrb.com/docs/front-matter/) 를 채워넣어야 한다.
```yaml
---
title: title
date: YYYY-MM-DD HH:MM:SS +/-TTTT
categories: [TOP_CATEGORY, SUB_CATEGORY]
TAGS: [TAG] # TAG 이름은 반드시 소문자여야 한다.
---
```
> **Note** : 파일의 **layout** 은 기본적으로 `post`에 세팅이 되어있고 Front Matter 블록에 **layout** 변수를 추가할 필요는 없다.

### Timezone of date
글의 발매일을 정확하게 기록하기 위해, `_config.yml`의 `timezone`을 잘 설정하고 글의 Front Matter 블록 내의 `date` 에도 timezone 을 넣어야한다.

### Categories and Tags
각 글의 `categories`는 최대 2개의 요소 포함하도록 설계되었고 태그는 원하는대로 넣어줄 수 있다. 예를 들면 ...
```yaml
categories: [Animal, Insect]
tags: [bee]
```
## Table of Contents
기본적으로 **T**able **o**f **C**ontents 는 글의 오른쪽에 띄워주도록 되어있다.
만약 모든 글에 대해 ToC 를 끄고 싶으면 `_config.yml`의 `toc` 변수의 값을 `false`로 변경시키면 된다.
만약 특정 글에 대해서만 ToC 를 끄고 싶으면 Front Matter 블록에 `toc: false`를 아래와 같이 추가해준다.
```yaml
---
toc: false
---
```

## 댓글
TOC와 비슷하게, [Disqus](https://disqus.com/) 댓글이 각 글에 기본적으로 로딩된다.
만약 모든 글에 댓글 기능을 끄려면 `_config.yml` 의 `comments` 변수의 값을 `false`로 변경해주면 된다.
만약 특정 글에 대해서만 댓글 기능을 끄려면 Front Matter 블록에 `comments: false`를 아래와 같이 추가해준다.
```yaml
---
comments: false
---
```

## Mathematics
사이트의 성능상의 이유로, 수학적 특징 혹은 지표들은 기본적으로 로딩되지 않는다. 그러나 아래의 코드를 넣어 로딩시킬수 있다.
```yaml
---
math: true
---
```

## Mermaid
**[Mermaid](https://github.com/mermaid-js/mermaid)**는 아주 좋은 다이어그램 생성 도구로 글에서 Mermaid를 활성화시키려면 아래의 YAML 블록을 추가해준다.
```yaml
mermaid: true
```
그러면 다른 markdown 언어처럼 mermaid 를 사용할 수 있다.
```` ```mermaid ```` 와 ```` ``` ```` 사이에 그래프 코드를 삽입하면 된다.

## 이미지

### Preview image
글 컨텐츠의 상단에 이미지를 넣고 싶으면, `src`, `width`, `height`, `alt` 속성을 아래의 예시처럼 명시해주면 된다.
```yaml
image:
  src: /path/to/image/file
  width: 1000 # 픽셀단위
  height: 500 # 픽셀단위
  alt: 이미지가 안 나올 경우 띄울 문구
```
`alt` 를 제외한 나머지 옵션들은 필수이다. 특히, `width` 와 `height` 옵션의 경우, UX와 페이지 로딩 성능과도 연관되어있다.

### Image caption
이미지의 다음줄에 이태릭 글자를 넣으면 그 글자는 caption(자막)이 되고 이미지의 아래에 나타난다.
```markdown
![img-description](/path/to/image)
_Image Caption_
```

### Image size
이미지 로딩시 페이지 내용 레이아웃이 이동하지 않도록 하려 각 이미지에 width 와 height 를 설정해야한다.
```markdown
![Desktop View](/assets/img/sample/mockup.png){: width="700" height="400"}
```

### Image position
기본적으로 이미지는 중앙에 위치하지만 `normal`, `left`, `right` 중 하나를 골라 위치를 명시해줄 수 있다.

* **Normal Position**
  ```markdown
  ![Desktop View](/assets/img/sample/mockup.png){: .normal }
  ```
* **Float to the left**
  ```markdown
  ![Desktop View](/assets/img/sample/mockup.png){: .left }
  ```
* **Float to the right**
  ```markdown
  ![Desktop View](/assets/img/sample/mockup.png){: .right }
  ```
> Limitation : 이미지 위치를 명시하면 Image caption 을 사용할 수 없다.

### Image shadow
프로그램 창의 스크린샷은 그림자 효과를 보여주는 것으로 간주할 수 있고 그림자는 `light` 모드에서 볼 수 있다.
```markdown
![Desktop View](/assets/img/sample/mockup.png){: .shadow }
```

### CDN URL
[CDN](https://www.akamai.com/ko/our-thinking/cdn/what-is-a-cdn) 에 이미지를 호스트했다면, `_config.yml` 의 `img_cdn` 변수에 값을 할당하여 반복적으로 CDN url 을 쓰는 시간을 절약할 수 있다.
```yaml
img_cdn: https://cdn.com
```
`img_cdn` 이 한번 할당되면, CDN url 은 `/` 로 시작하는 모든 이미지의 경로에 추가될 것이다.

예를 들면, 아래와 같이 이미지를 사용할 경우:
```markdown
![The flower](/path/to/flower.png)
```
parsing 의 결과에는 아래와 같이 자동으로 CDN prefix 인 `https://cdn.com` 이 이미지 경로 앞에 붙어서 나온다.
```html
<img src="https://cdn.com/path/to/flower.png" alt="The flower">
```

## Pinned Posts
홈페이지 상단에 원하는 만큼의 글을 고정시킬 수 있고 고정된 글은 발행일 역순으로 정렬된다.
아래의 코드를 Front Matter 블록에 추가한다.
```yaml
---
pin: true
---
```

## Code Block
마크다운 기호 ```` ``` ```` 를 사용하여 코드 블록을 쉽게 만들 수 있다.
```plaintext
This is a common code snippet, without syntax highlight and line number.
```

## Specific Language
```` ```language ```` 를 사용하여 언어에 맞게 문법 강조와 줄에 순서를 표시한 코드 블록을 만들 수 있다.
> **Note** : Jekyll style 인 `{% raw %}{%{% endraw %} highlight LANGUAGE {% raw %}%){% endraw %}` 혹은 `{% raw %}{%{% endraw %} highlight LANGUAGE linenos {% raw %}%}{% endraw %}`는 이 테마에서는 사용할 수 없다.

```yaml
# Yaml code snippet
items:
  - part_no: A4786
    descrip: Water Bucket (Filled)
    price: 1.47
    quantity: 4
```

### Liquid Codes
**Liquid** snippet 을 띄우고 싶다면 `{% raw %}{%{% endraw %} raw {% raw %}%}{% endraw %}` 와 `{% raw %}{%{% endraw %} endraw {% raw %}%}{% endraw %}` 사이에 liquid code 를 삽입하면 된다.

{% raw %}
```liquid
{% if product.title contains 'Pack' %}
  This product's title contains the word Pack
{% endif %}
```
{% endraw %}

## Learn More
이 테마에 대해 더 많은 것을 알고 싶다면 [Jekyll Docs: Posts](https://jekyllrb.com/docs/posts/)를 방문하면 된다.
