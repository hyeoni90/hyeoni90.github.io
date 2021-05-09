---
layout: post
title:  "[개발 환경 세팅] Mac Terminal 꾸미기"
date:   2021-04-30
categories: etc
---

> Mac OS Catalina 이후부터는 zsh 쉘이 기본입니다.

우선, Mac의 패키지 매니저 인 [Homebrew 설치](https://brew.sh/) 합니다.

## oh-my-zsh 설치 하기
oh-my-zsh로 zsh에 플러그인을 설치해 테마를 적용할 수 있습니다.

```shell
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
<img width="100%" alt="oh my zsh install 2021-04-30 " src="https://user-images.githubusercontent.com/47413225/116677967-c30cd300-a9e3-11eb-920e-67dbddac8d8a.png">

## zsh 설정 하기
zsh 설정 파일에 들어가서 설정을 변경해보겠습니다.
```shell
$ vi ~/.zshrc
```
### 테마 변경

설정 파일에 들어가면, `ZSH_THEME="robbyrussell"` 라인을 확인할 수 있습니다.

저는, agnoster 테마로 변경 하겠습니다.
```
ZSH_THEME="agnoster"
```

다른 테마를 [ohmyzsh Github](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes) 을 참고하세요.


### zsh 설정 반영
```shell
$ source ~/.zshrc
```

그렇다면, 아래와 같이 폰트가 깨진다.

<img width="100%" alt="break font on terminal 2021-04-30 " src="https://user-images.githubusercontent.com/47413225/116682919-db7fec00-a9e9-11eb-84a2-bf6cb6171a95.png">

## 폰트 변경

[Meslo LG M Regular for Powerline.ttf](https://github.com/powerline/fonts/blob/master/Meslo%20Slashed/Meslo%20LG%20M%20Regular%20for%20Powerline.ttf) 서체 다운로드 및 설치

* [여기](https://github.com/powerline/fonts) 를 참고 하여 원하는 폰트를 설치 해서 사용하면 됩니다.


<img width="100%" alt="change font on iterm2 2021-04-30 " src="https://user-images.githubusercontent.com/47413225/116684745-4a5e4480-a9ec-11eb-81b2-c86c70bbc40a.png">

iTerm2 > Preperences > Profiles 에서 Text 탭에서 Font 변경 하면 아래와 같이 됩니다.

<img width="100%" alt="fix font on terminal 2021-04-30 " src="https://user-images.githubusercontent.com/47413225/116684856-77125c00-a9ec-11eb-9d4d-b74fc3c5e755.png">


## 사용자 이름 숨기기
`vi ~/.zshrc` 하단에 아래 코드 추가 후 `source ~/.zshrc` 명령어를 실행하여 반영한다.
```
DEFAULT_USER="$(whoami)"
```


## 유용한 플러그인 추가

oh-my-zsh 플러그인 추가 하기 위해서 해당 디렉토리로 이동.
```
$ cd ~/.oh-my-zsh/custom/plugins/
```

### zsh-syntax-highlighting 설치
```
$ git clone https://github.com/zsh-users/zsh-syntax-highlighting.git

```
### zsh-autosuggestions 설치
```
$ git clone https://github.com/zsh-users/zsh-autosuggestions
```

### 설정 파일에 플러그인 추가
`vi ~/.zshrc` 로 설정 파일을 열어 하단 plugins에 설치한 플러그인을 추가

```
plugins= (
  git
  zsh-syntax-highlighting
  zsh-autosuggestions
)
```
