---
layout: post
title: How to download files at once on jupyter notebook
subtitle: Jupyter Notebook에서 파일 한번에 다운로드하는 방법
tags: [python]
comments: true
---

> 하나씩 클릭해서 다운로드할 필요없다!

프로젝트 중 서버에서 만들어진 수백장의 이미지들을 개인 랩탑에 다운로드 하려고 하는데           
Jupyter Notebook의 경우, 하나씩 개별로만 클릭해서 다운로드 가능했다.               
폴더를 클릭하면 다운로드 버튼이 나타나지 않고.. 수백장의 이미지들을 언제 하나씩 다운로드하나..      
그래서 한번에 다운로드 받는 방법을 찾았다.        

1. 다운로드받고 싶은 폴더의 경로 확인      
내가 다운로드받고 싶은 이미지들이 있는 폴더(image)의 경로는          
~~~           
/home/da/jupyter/조예린/Recosys/image       
~~~          

2. 터미널에 들어가서, 해당 디렉토리 이전으로 이동    
~~~              
cd /home/da/jupyter/조예린/Recosys       
~~~            

3. 명령어로 폴더 압축      
~~~           
# tar -cvf (압축해서 나올 폴더명).tar (압축할 폴더명)      
tar -cvf image.tar image         
~~~                

이렇게 압축 후에, 압축된 폴더를 다운해서 압축을 풀어주면 된다.       
