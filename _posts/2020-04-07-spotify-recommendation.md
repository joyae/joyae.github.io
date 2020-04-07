---
layout: post
title: How Spotify recommends music
subtitle: study
tags: [recommender system, spotify, CNN]
comments: true
---
> Spotify의 음악 추천 알고리즘은 어떨까?

딥러닝 기반 음악 추천 프로젝트를 진행하기 전, 교수님께서 건네주신 읽어볼 material 리스트를 읽어보는데 흥미로운 포스트가 있어 정리 겸 공유하고자 한다. 이 글은 먼저 해당 [포스트]('https://benanne.github.io/2014/08/05/spotify-cnns.html')를 참고했음을 밝힌다.

# Spotify
지금은 Youtube Music을 사용하고 있지만, 예전에 잠시 Spotify를 사용한 경험이 있다. 우선 내가 주로 듣는 노래들이 해외 팝송인데, 멜론에서 일반인 DJ들이 만들어놓은 팝송 플레이리스트에는 주로 이미 유명한 메이저 가수들밖에 없었다. 당시 Youtube의 추천알고리즘을 통해 톡톡히 재미를 보고 있었던터라, 한번 음악계의 유투브라고 불리는 Spotify를 쓰고싶었다. 한국에서 spotify 서비스를 이용하기 위해서는 조금 귀찮은 방법을 써야했지만, Spotify는 신세계였다. 내 취향의 노래들이 추천된다는 것이 확실히 느껴졌다. 과연 Spotify는 어떠한 추천시스템을 쓰고 있을까?

이 [포스트]('https://benanne.github.io/2014/08/05/spotify-cnns.html')는 뉴욕 Spotify에서 인턴을 하며 *CNN을 활용한 content-based music recommendation* 을 작업한 사람이 자신의 접근방법과 결과에 대해서 얘기한다. 이 포스트의 주된 내용에 대해서 정리해보고자 한다.

--

# Spotify's Recommendation System
## Spotify의 기존 추천시스템 - Collaborative Filtering

Spotify는 기존에 collaborative filtering 방법을 통해 추천했다. collborative filtering 방법은 사용자들의 과거 서비스 아용 데이터를 통해 사용자들의 취향을 알아낸다. 만약 두 사용자가 서로 정말 비슷한 노래들은 듣는다면, 그들의 취향은 비슷할 것이다. 반대로 만약 두 노래가 같은 그룹의 사용자들에게 많이 재생된다면, 그 두 노래는 아마도 비슷할 것이다. 이러한 정보들이 추천에 쓰이는 것이다. Pure collaborative filtering 방법은 추천되는 item에 대한 정보를 이용하지 않는다. 이러한 접근법은 같은 모델이 책을 추천하기도, 영화를 추천하기도 혹은 음악을 추천할 수도 있으므로 다양한 분야에 접목하는 것을 도와준다. 그러나 이는 큰 단점이 될 수 있다.

< CF의 단점 >
* 과거 이용 데이터에 의존하면, 이용 데이터가 많은 인기있는 item들만 주로 추천되므로 다양한 추천이 힘들어진다.
* 비슷한 이용 데이터를 지니지만, 이질적인 content를 지닌 item들이 있다.
* 과거 이용 데이터에 의존하므로, 새로운 노래나 비인기 노래들이 추천되지 않는다. 이는 cold-start 문제라고 불린다.

## Different Approach - Content-based recommendation

최근 Spotify는 위의 문제들을 완화하기 위해 다른 유형의 정보들을 추천 파이프라인에 추가하는 것에 큰 관심을 가지고 있다. 음악에는 추천을 도울 수 있는 다양한 정보들이 있는데, 예를 들면 tag, artist, 앨범 정보, 가사, 노래에 대한 review와 같은 text data, audio signal 등이 있다. 아마 이 중에서는 audio signal이 효과적으로 사용하기에 가장 힘든 데이터일 것이다. audio signal과 사용자의 음악 취향에 영향을 미치는 다른 요소 간에는 의미적인 차이가 크다. 물론 audio signal에서 음악의 장르나 어떤 악기를 썼는지, 음악의 무드와 같은 정보들은 추출할 수 있겠지만, artist의 출신 지역과 가사의 테마는 추출하기 힘들 것이다. 그러나 음악이 정말 어떤 소리를 가지고 있는지 나타내는 audio signal은 사용자가 이 노래를 좋아할 것인지를 결정하는데 분명 큰 역할을 할 것이다.

## Deep Learning을 활용한 음악 성향 예측
