---
layout: post
title: Pandora's Music Genome Project(1)
tags: [recommender system, pandora, music, recommendation]
---
> Spotify 이전, 음악 개인화 추천의 시작이었던 Pandora

![Pandora](https://upload.wikimedia.org/wikipedia/commons/7/76/Pandora_Wordmark_2016_RGB.png){: .center-block :}
# Pandora

글로벌 음악 스트리밍 서비스 중, 가장 인기가 많은 서비스는 `Spotify`지만 Apple Music, Soundcloud, Amazon Music Unlimited 등 다양한 서비스가 존재한다.

| Service | Category |
| :------ | :------ |
| Spotify | Best overall |
| Apple Music | Best for Apple users |
| Pandora | Best service for passive listening |
| Amazon Music Unlimited | Best value |
| Soundcloud | Best for indie music discovery |
| Tidal | Best fidelity |

그 중 `Pandora`는 사실 음악 추천시스템을 공부하면서 새로이 알게 된 서비스인데, Spotify가 생겨나기 훨씬 이전인 2000년부터 `Music Genome Project`를 통해 개인화된 음악 추천을 제공했다고 한다. 사실상 음악 스트리밍 업계에서 최초로 음원 및 이용자 청취 데이터에 기반한 음악 추천 시스템을 제안한 것이다. 그래도 Pandora와 Spotify가 제공하는 서비스의 결은 조금 다른 것 같다. Pandora를 이용해본 경험이 없어서 잘 모르겠지만, 아래 포스트들에 의하면 Spotify보다 `Pandora`에서 이용자의 취향에 맞춰 음악을 추천해주는 'Music discovery'가 서비스의 중추적인 역할을 한다고 한다. Spotify는 'Discover Weekly playlist'라는 단순 기능부터 시작해 개인화된 추천 서비스의 영역을 확장하고 있다면, Pandora는 이미 서비스의 시작부터 `Music Genome Project`에 기반한 음원 분석으로 사용자가 좋아할만한 노래를 radio-style로 추천해주었다는 것이다.

Pandora와 Spotify를 비교하는 포스트들
+ <https://www.digitaltrends.com/music/spotify-vs-pandora/>
+ <https://www.digitaltrends.com/music/best-music-streaming-services/?itm_medium=editors>

---

# Music Genome Project
이번 포스트에는 Pandora를 견인하고 있는 `Music Genome Project`에 대하여 공부한 것을 정리해보려고 한다.

![Music Genome Project - About](https://joyae.github.io/images/pandora-about.png){: .center-block :}
위는 Pandora 홈페이지에서 `Music Genome Project`에 대하여 간단히 설명하고 있는 글이다. 이에 따르면, Musicologist들로 이루어진 팀이 모든 시대 및 장르의 노래를 들으며 450개의 musical attributes를 분석했다고 한다.

Scientific Computing에 실린 John R. Joyce 박사의 ['Pandora and the Music Genome Project: Song structure analysis tools facilitate new music discovery'](https://www.researchgate.net/publication/295343382_Pandora_and_the_music_genome_project_Song_structure_analysis_tools_facilitate_new_music_discovery)에 따르면, `Music Genome Project`는 2000년에 런칭되었고 5년이 지나서야 실용성을 지닌 데이터베이스를 구축했는데, 그 이유는 30명의 음악 전문가들이 노래를 일일이 들으며 그 450여개의 musical attributes를 분석했기 때문이라고 한다(!)

[Wikipedia](https://en.wikipedia.org/wiki/Music_Genome_Project)에서는 `Music Genome Project`에서 노래들이 어떻게 분석되었는지 좀더 자세하게 서술되어있다. `Music Genome Project`의 목표는 'capture the essence of music at the most fundamental level'이다. 현재 `Music Genome Project`는 5개의 sub-genomes - Pop/Rock, Hiphop/Electronica, Jazz, World Music, Classical로 이루어져있다.

하나의 곡은 450 genes의 값을 가진 vector로 표현된다. 각 gene은 음악의 특성 - 예를 들어, gender of lead vocalist, prevalent use of groove, level of distortion on the electric guitar, type of background vocals - 과 연결된다. Pop/Rock 장르는 150개의 genes가 있으며, Rap은 350개 genes, jazz는 약 400개, World Music과 Classical은 약 300~450개의 genes를 가지고 있다고 한다. 각 gene은 0.5 단위로 0과 5 사이 의 값을 지닌다.

Pandora에서 하나 혹은 다수의 곡의 vector를 가지고, 유사한 곡들의 리스트를 뽑아내는 것을 'matching algorithm'이라고 부른다. 곡 하나당 분석 시 소요되는 시간은 한 전문가 당 20 ~ 30분 정도이며, 전체의 약 10%의 노래들은 1명 이상의 전문가가 함께 분석하여 conformity in-house standards와 statistical reliability를 보증한다.

---

# Podcast Genome Project
2018년 11월, Pandora는 기존의 `Music Genome Project`를 확장시켜 `Podcast Genome Project`를 런칭한다. Podcast는 음악보다 뽑아낼 attribute가 많다. NLP를 활용해 episode의 내용을 뽑아낼 수도 있고, production style, 호스트의 프로필 등 사용할 수 있는 attribute가 무궁무진하다는 점에서 좀더 면밀하게 이용자의 취향에 맞는 podcast를 추천해주는 것이 가능해진다.

다만 음악은 한번 들어보는데 약 2 ~ 3분의 시간이 걸리는 반면, podcast는 상당한 시간을 필요로 한다는 점이 제약이 될 수 있다. 음악은 추천되었을 때 적은 비용(시간)으로 한번씩 들어보고 '좋아요'와 '싫어요'로 가볍고 빠르게 그 추천 리스트를 평가할 수 있기 때문에, 이용자의 취향에 대한 학습이 원만하게 진행된다. 반면 podcast는 한번 들어보는데 상당한 시간이 걸리기 때문에, 이용자의 취향에 대한 학습이 좀더 더딜 것이기 때문에 추천의 정확도가 낮을 수 있다.

그럼에도 불구하고, Music Genome Project가 그랬던 것처럼, 기존에 잘 알려지지 않았던 podcast에 길을 열어주고 이용자의 취향에 기반해 타겟팅된 podcast 광고를 진행할 수 있다는 점에서 긍정적인 효과를 지닐 것으로 예상된다.
