---
layout: post
title: 특정 경로의 파일리스트 가져오기(listdir)
subtitle: os.listdir()
tags: [python]
comments: true
---

1. 현재 디렉토리 확인     
~~~                 
import os    
os.getcwd    
~~~           

2. 특정 경로의 파일리스트 가져오기     
~~~             
os.listdir('파일경로')     
# 이 때 폴더 내에 있는 숨겨진 파일들도 불러낸다.    
# 예를 들면, .ipynb_checkpoints 와 같은 파일들    
# 그래서 이런 숨겨진 파일을 제외한 파일들을 데려오려면 추가 코딩이 필요하다.    
# 아래의 코드는 해당 파일 경로에 있는 파일들(숨겨진 파일 제외)의 파일명을 가져오는 코드      
filenames = [f for f in os.listdir("../image") if not f.startswith('.')]     
~~~                 
