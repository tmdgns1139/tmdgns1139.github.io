---
title: 블로그 시작해보기 (With Jekyll Chirpy Theme)
author: three.balance
date: 2021-09-04 22:46:00 +0900
categories: [Blogging, Tutorial]
tags: [tutorial]
#pin: true
---

<b>Notice</b> : 이 글은 [링크](https://chirpy.cotes.info/posts/getting-started/)를 참조하여 작성하였습니다.

## 전제조건
1. [링크](https://jekyllrb.com/docs/installation/)로 들어가서 요구사항에 맞는 `Ruby`, `RubyGems`, `Jekyll`, `Bundler`를 설치한다.
2. `Ruby`의 버전은 반드시 [RubyGems.prg](https://rubygems.org/gems/jekyll-theme-chirpy)의 테마 요구사항을 충족시켜야한다.

## 설치
테마 설치에는 두가지 방식이 있다.
- **[Install from RubyGems](#install-from-rubygems)** - 업데이트 하기 쉽다고 한다. (저는 시도 안해봤습니다.)
- **[Fork on GitHub](#fork-on-github)** - 업데이트는 어렵지만 개발 상의 편리함이 있어서 웹 개발자들에게 좋아보인다고 한다.

### Install from RubyGems
<b>Notice</b> : 이 부분은 제가 시도해 본 것이 아니라 그냥 번역만 한 것이기 때문에 부디 저를 믿지 마시기 바랍니다.

1. 나만의 Jekyll site 의 `Gemfile`에 아래의 ruby 명령어를 추가한다.
```ruby
gem "jekyll-theme-chirpy"
```

2. 나만의 Jekyll site 의 `_config.yml` 파일에 아래를 yaml 코드를 추가한다.
```yaml
theme: jekyll-theme-chirpy
```

3. 그 다음 실행시킨다.
```console
$ bundle
```

4. 설치된 로컬 테마 경로로 이동한다.
```console
$ cd "$(bundle info --path jekyll-theme-chirpy)"
```

5. 테마 gem에서 중요 파일들을 나만의 Jekyll site 에 복사한다. (자세한 사항은 [링크](https://github.com/cotes2020/chirpy-starter)를 참고


> ⚠️ **복사 파일들을 조심하라고 한다.**
>
> 나만의 Jekyll site 가 `jekyll new` 명령어를 통해 만들어졌다면, 나의 Jekyll site 의 root 디렉토리에 `index.markdown`, `about.markdown` 파일이 있을 텐데 이 2개의 파일을 없애거나 링크의 `index.html` 과 `_tabs/about.html` 파일로 각각 덮어씌우기를 권장한다.


### Fork on GitHub
먼저 깃허브에 있는 Chirpy를 Fork 하여 나의 레포지토리로 가져오고 나의 로컬에 clone 한다. (기본 branch 코드가 development에 있는지 확인하고 블로그가 안정적이기를 바란다면 [latest tag](https://github.com/cotes2020/jekyll-theme-chirpy/tags)로 변경하고 글을 쓰라고 한다.)
* **[Fork](https://github.com/cotes2020/jekyll-theme-chirpy/fork)**
* 로컬에 clone : 아래 명령어 실행
  ```console
  $ git clone https://github.com/(username)/(username).github.io
  ```

그 다음, 아래 명령어로 gem dependencies 를 설치한다.
```console
$ bundle
```
그리고 아래 명령어를 실행한다.
```console
$ bash tools/init.sh
```
> **Note** : deploy를 할 생각이 없다면 위의 명령어에서 `--no-gh` 옵션을 붙여서 실행한다.

해당 명령어가 수행하는 것들은 아래와 같다.
1. 나의 레포지토리에서 아래의 파일들과 폴더를 없앤다.
  * `.travis.yml`
  * `_posts` 아래의 파일들
  * `docs` 폴더
2. `--no-gh` 옵션을 사용했다면, `.github` 폴더는 사라지고 그렇지 하지 않으면 `.github/workflows/pages-deploy.yml.hook` 파일의 `.hook` 확장자를 제거하여 GitHub Action 의 워크플로우를 설정한다.
3. 변화를 저장하는 commit 을 자동으로 생성한다.

## 사용

### 설정
`_config.yml` 파일의 변수들을 원하는대로 변경하는데 아래의 옵션들은 변경하는걸 권장한다.
* `url` : 'https://(username).github.io'
* `avatar` : PC 기준, 홈페이지의 왼쪽 상단에 있는 이미지의 경로를 넣어준다.
* `timezone` : 한국인은 'Asia/Seoul' 로 지정하면 편하다.
* `lang` : 기본으로 en으로 설정되어 있는데 바꾸지 않아도 한글이 잘되는 것 같다.

### Style-sheet 커스텀
style-sheet 를 커스텀하고 싶다면, 테마의 `assets/css/style.scss` 를 나의 Jekyll site 의 같은 경로에 복사하고 해당 파일의 끝에 나만의 custom style 을 추가한다.

`v4.1.0` 으로 시작하며, `_sass/addon/variables.scss` 에 정의되어 있는 SASS 변수들을 덮어씌우고 싶다면, 새 파일 `_sass/variables-hook.scss` 을 추가하고 덮어씌우려는 변수에 새로운 값들을 할당하면 된다.

### 로컬 서버에서 실행하기
블로그를 정식으로 오픈하기전 내 블로그의 내용들을 확인하고 싶을 수 있다. 아래의 명령어들 중 하나를 선택해 로컬에서 블로그를 띄우고 블로그 상태를 확인하면서 글을 써보자.
```console
$ bundle exec jekyll serve
```
혹은 아래의 명령어를 통해 docker 를 이용할 수도 있다.
```console
$ docker run -it -rm \
    --volume="$PWD:/srv/jekyll"
    -p 4000:4000 jekyll/jekyll \
    jekyll serve
```
명령어를 실행하면 [http://localhost:4000](http://localhost:4000)에서 블로그 상태를 확인할 수 있다.

### Deployment
> Deployment? 내 블로그를 실제로 서비스해보자!

먼저 deploy를 하기 전, `_config.yml` 파일에서 `url` 에 올바른 옵션을 주었는지 꼭 체크해야한다. 커스텀 도메인 말고 **[project site](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages#types-of-github-pages-sites)** 를 선호하거나 **GitHub Pages** 외의 웹 서버에서 base URL 을 통해 블로그에 방문하고 싶은 경우, `baseurl` 을 슬래쉬(`/`)로 시작하는 프로젝트 이름으로 변경해야 한다. (예를 들면 `/project-name`)

이제, 나의 Jekyll site 를 deploy 하기 위해 아래의 방법들 중 **하나**를 선택한다.

#### 1. GitHub Pages 에 Deploy 하기

보안 상의 이유로, GitHub Pages 는 `safe` 모드로 빌드를 하는데 이는 플러그인 사용과 추가적인 페이지 파일 생성을 막는다. 그러므로, site 빌드를 위해 **GitHub Actions**를 사용할 수 있고 새로운 브랜치에 빌드된 site 파일들을 보관할 수 있으며 그 브랜치를 GH Pages 서비스의 원천으로 사용한다.

GitHub Actions 빌드를 위해 필요한 파일들을 빠르게 체크:
* Jekyll site가 `.github/workflows/pages-deploy.yml` 파일을 가지고 있는지 확인해서 없으면 해당 파일을 새로 만들어서 [링크](https://github.com/cotes2020/jekyll-theme-chirpy/blob/master/.github/workflows/pages-deploy.yml.hook)의 내용을 복붙한다.
* `tools/test.sh` 파일과 `tools/deploy.sh` 파일이 있는지 확인하고 없으면 [링크](https://github.com/cotes2020/jekyll-theme-chirpy/tree/master/tools)에서 가져온다.

그리고 레포지토리의 이름을 `<GH-USERNAME>.github.io`로 변경한다.

이제 아래의 순서에 따라 Jekyll site 를 서비스해보자:
1. 아무 commit 이나 push 하여 GitHub Actions workflow 를 동작시켜보자. 빌드가 성공적으로 완료되면 `gh-pages` 라는 **새로운 브랜치**가 빌드된 사이트 파일에 저장되어 나타날 것이다.
2. 레포지토리의 _Settings_ → _Options_ → _GitHub Pages_ 에 들어가서 Source 의 브랜치를 `gh-pages`로 바꾸고 save 버튼을 누른다.
![gh-pages-source](https://camo.githubusercontent.com/d15855ed187b5dffcf2408679f0abdfafb535ad17380d9b7a92e58b34329210e/68747470733a2f2f63646e2e6a7364656c6976722e6e65742f67682f636f746573323032302f6368697270792d696d616765732f706f7374732f32303139303830392f67682d70616765732d736f75726365732e706e67)
3. 나의 웹사이트에 접속해본다.

#### 2. 다른 플랫폼에 Deploy 하기
GitHub 외의 플랫폼의 경우, **GitHub Actions**의 편리함을 사용할 수 없다. 그러므로 site 를 로컬이나 서드 파티 CI 플랫폼에서 빌드하여 사용자가 쓰려는 플랫폼의 서버에 site 파일들을 넣어주어야 한다.

소스 프로젝트의 루트로 가서, 아래의 명령어를 실행해 site 를 빌드한다.
```console
$ JEKYLL_ENV=production bundle exec jekyll b
```
혹은 docker 를 가지고 site 를 빌드할 수도 있다.
```console
$ docker run --it --rm \
    --env JEKYLL_ENV=production \
    --volume="$PWD:/srv/jekyll" \
    jekyll/jekyll \
    jekyll build
```
만약 output 경로를 명시하지 않으면, 생성된 site 파일들이 프로젝트 루트 폴더의 `_site` 폴더에 있을 것이다. 그럼 그 파일들을 웹서버에 업로드하면 된다.
