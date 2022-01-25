# RPA 실행방법

1. [Uipath Studio 설치방법](https://uipath.tistory.com/81)을 읽고 Studio 버전을 다운로드합니다.
2. **KeywordSearch/**[SearchKeyword.xaml](https://github.com/skguma/Fedi-image-scraper/blob/main/KeywordSearch/SearchKeyword.xaml)이 잘 열리는지 확인합니다. (이 파일이 지금 테스트 할 계정별 이미지를 수집하는 RPA 입니다.)
3. 기본 셋팅

- Flowchart > Use browser edge: google > Sequence > Sequence > 실행 > while
    - 여기에서 조건 ctrVar은 구글 검색 결과에서 계정을 얻을 때 페이지 다운 화살표를 누르는 횟수를 관리하는 변수입니다. 
    - 페이지 다운 화살표를 누르고 싶은 횟수를 정합니다.
    - (ex. 5번 누르고 싶으면 ctrVar ≤ 5 로 변경)
    - cf. 10번을 내렸을 때 중복 제거한 계정 25개를 얻었습니다.

![Untitled (37)](https://user-images.githubusercontent.com/71035113/150901732-cfca3064-3551-4924-87e5-4a81e5b93102.png)

- Flowchart > Use browser edge: google > Sequence > Sequence > 실행 > Write Range
    - 중복제거한 datatable을 엑셀에 저장하는 액티비티입니다.
    - 파일을 저장할 위치를 자신의 컴퓨터에 맞게 변경합니다.

![Untitled (38)](https://user-images.githubusercontent.com/71035113/150901738-29acc953-e3bc-4499-920f-01ceb19f6ec5.png)

- Flowchart > For Each Row in Data > Body > Use Broswer Edge > 실행 > Check App State > 타겟이 나타남 > 첫 번째 사진
    - 첫번째 사진을 캡쳐해서 저장하는 액티비티입니다.
    - 파일이 저장될 경로인 File name을 변경합니다.

![Untitled (39)](https://user-images.githubusercontent.com/71035113/150901740-5ee1fdfb-815b-4dd4-902a-39b264876468.png)

- 아래에 있는 Save Image 액티비티에서 이미지가 저장되는 경로를 변경합니다.
    - (이미지를 저장하는 방법을 테스트하기 위해 위와 다른 방법으로 시도했습니다.)

![Untitled (40)](https://user-images.githubusercontent.com/71035113/150901742-9df42434-0033-450c-9f34-19889498244c.png)

- Flowchart > For Each Row in Data의 제일 아래에 있는 Write Range
    - tweetUrl, fileName, accountName을 담은 datatable을 엑셀에 저장하는 액티비티입니다.
    
    ![Untitled (41)](https://user-images.githubusercontent.com/71035113/150901743-7ab58fec-b47f-410e-953f-fe71dcf3d150.png)

    - 첫째 줄에 파일이 저장되는 위치를 변경합니다.

![Untitled (42)](https://user-images.githubusercontent.com/71035113/150901744-5f25413e-1a6e-4666-8b08-bcdbfc336bae.png)

4. 다음 항목들이 잘 실행되면 됩니다.
    
    1) 사진이 잘 캡쳐되는지 확인 (엑셀X)
    
    - 사진을 캡쳐할 때, 첫 번째 사진만 저장되고 두 번째 사진부터는 저장이 안 되는 오류가 발생합니다.
    
    2) 동영상이 있을 때 뒤의 사진 잘 캡쳐되는지 확인
    
    - 사진 모아보기 탭에 동영상이 있는 경우, 화살표를 클릭해 다음 사진으로 넘기는데 오류가 나서 뒤쪽의 사진들이 잘 캡쳐되지 않습니다.
