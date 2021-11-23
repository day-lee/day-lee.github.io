---
title:  "[Jekyll] 블로그 포스팅 예시"
excerpt: "md 파일에 마크다운 문법으로 작성하여 Github 원격 저장소에 업로드 해보자. 에디터는 Visual Studio code 사용! 로컬 서버에서 확인도 해보자. "

categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

toc: true
toc_sticky: true
 
date: 2020-05-25
last_modified_at: 2020-05-25
---

Curly brackets 

```
{{ page.categories}}
{{ page.title }}
{{ page.last_modified_at }}
```
<br>

# 외부 랜딩 페이지로 연결하는 경우


## 1. static
메인 화면 index.html의 img src의 .png 파일 경로를 정해줘야함
```
# 예시 static image 파일 경로
common/static/images/example_banner.jpg
```

## 2. Template
### 1) 메인 페이지
- 경로: lms/templates/index.html 

메인 화면에 배너 이미지, 랜딩페이지 경로 추가 
line 374
```				
<a href="example-url" target="_blank"><img src="${STATIC_URL}images/example_banner.jpg" alt="페이지 바로가기" style="width: 100%"></a>						
```

<br>

# 내부 랜딩 페이지로 연결하는 경우

## 1. static
메인 화면 index.html의 img src의 .png 파일 경로를 정해줘야함
```
# 예시 static image 파일 경로
common/static/images/example_banner.jpg
```


## 2. URL
랜딩 페이지 url
- 경로: lms/urls.py 
```
urlpatterns = [
	~
	url(r'^banner_example$', branding_views.banner_example, name='banner_example'),
]
```