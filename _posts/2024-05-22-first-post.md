---
title: "Welcome to YellowBalloon!"
date: 2024-05-22 13:14:00 -0000
categories: notice
author: yellowballoon
tags: notice
---
안녕하세요~

환영합니다. 노랑풍선 개발 블로그 입니다.

아래 가이드를 지켜주세요.

# 가이드
## 포스트(글쓰기)
- _posts 폴더 하위에 작성.
- YYYY-MM-DD-[Title].md 파일 형식으로 포스트 생성.
- 아래 내용 템플릿 필수.
```
---
title: "Welcome to YellowBalloon!"
date: 2024-05-22 13:14:00
categories: notice
author: yellowballoon
tags: notice
---
포스트 내용~
```

## 작성자 등록
- _data/authors.yml 파일에 작성.
- 작성자로 사용할 닉네임을 정하고 지정한 닉네임만 사용.
- name, email은 필수 작성.

```yaml
yellowballoon:
  name: "yellowballoon(관리자)"
  avatar: /assets/images/avatar/ybcloud.png # path of avatar image, e.g. "/assets/images/avatar/bio-photo.jpg"
  bio: "**관리자**"
  location: "서울, 대한민국"
  email: "front.one@ybtour.com"
{본인 닉네임}:
  name: {닉네임}
  email: {본인 이메일 주소}
  ...
```