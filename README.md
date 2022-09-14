<img width="700" alt="스크린샷 2022-09-14 오후 4 45 40" src="https://user-images.githubusercontent.com/97447841/190093051-e6801b66-f911-47e9-90d6-c61235ca94ed.png">

Date : 2022.5.19~2022.5.24

Tags : `Yolov5`  `Roboflow`  

Link : [https://github.com/heezzing/project4.git](https://github.com/heezzing/project4.git)

발표영상 : [https://youtu.be/1hdlN3YwENA](https://youtu.be/1hdlN3YwENA)

## 개요
- 주제 : 차종별 object detection
- 데이터 출처  :  Roboflow
    
    [Vehicles-OpenImages Object Detection Dataset](https://public.roboflow.com/object-detection/vehicles-openimages)
    
- 기여 내용 : Yolov5를 이용한 차종별 Object detection

## 프로젝트 내용

### 주제 및 주제 선정 이유
<img width="700" alt="스크린샷 2022-09-14 오후 4 49 12" src="https://user-images.githubusercontent.com/97447841/190093848-e6992157-4e00-4462-8f65-afddfca1df4c.png">

- 주제 : 차종별 object detection
- 주제 선정 이유 : ‘만약 자동차의 종류를 인식한다면 더 안전하게 주행이 가능하지 않을까?’ 라는 생각을 하게되어 주제를 선정하게 되었습니다.

### 가설
<img width="700" alt="스크린샷 2022-09-14 오후 4 50 02" src="https://user-images.githubusercontent.com/97447841/190094059-1b1531c0-0768-419a-9c09-554468d9e66d.png">

- 가설 1 : 구급차나 소방차를 감지하면 위급한 상황이라고 판단해 길을 비켜줄 것이다.
- 가설 2 : 큰 트럭을 감지하면 트럭 뒤나 사이를 피하여 사고를 예방할 것이다.
- 가설 3 : 갑자기 튀어나오는 오토바이를 감지하여 사고를 예방할 것이다.
- 자율주행의 목적은 사고예방이기에 위 가설들이 채택이 된다면 더 안전하게 주행할 것이라 생각합니다.

### 데이터 파이프라인
<img width="700" alt="스크린샷 2022-09-14 오후 4 50 29" src="https://user-images.githubusercontent.com/97447841/190094167-9b036b28-6bb1-4a5d-a73b-9b5233b8d545.png">

1. Yolov5 
    
    [https://github.com/ultralytics/yolov5](https://github.com/ultralytics/yolov5)
    
    - 첫번째로 깃허브에서 yolov5 라이브러리를 깃클론 하였습니다.
    - one stage detection방법을 고안해서 실시간으로 object detection이 가능하여 선택하였습니다.
    - 후보영역을 추출하기 위해 별도의 네트워크를 적용하지 않아서  빠릅니다.
2. Roboflow
    - bounding box 툴입니다.
    - 이미지별 Label 텍스트 파일을 함께 제공하여 라벨링할 필요가 없어 사용하였습니다.
3. yaml 파일 생성
    - 학습 데이터의 경로와 클래스 갯수 및 종류가 적인 yaml파일을 생성하였습니다.
4. Tensor Board
    - Tensor Board를 이용하여 결과를 시각화 하였습니다.
    - yolov5는 평가지표 mAP를 이용하여 성능을 확인합니다.
    - mAP값이 0.5 이상이면 제대로 검출 되었다고 판단할 수 있습니다.

### 데이터 학습 결과
<img width="700" alt="스크린샷 2022-09-14 오후 4 52 50" src="https://user-images.githubusercontent.com/97447841/190094661-36bdb3a5-dc61-4226-9ad5-c135988c2829.png">

- 텐서보드를 이용해 데이터 결과를 시각화해 보았습니다.
- 차종별로 mAP값이 다릅니다.
<img width="700" alt="스크린샷 2022-09-14 오후 4 53 21" src="https://user-images.githubusercontent.com/97447841/190094786-8ed51d86-c20e-4df3-94ea-562fb04a44f9.png">
  
    - Car의 경우 데이터의 양이 충분하지만 나머지 차종의 경우 데이터가 작은걸 볼 수 있습니다.
- 데이터의 양이 가장 많은 Car의 mAP가 가장 높지 않은걸 보니 데이터의 양이 정확도에 영향을 미치는건 아닌걸 알 수 있습니다.
- 모델 전체적인 mAP가 0.48이므로 성능이 좋은편 같습니다.
<img width="700" alt="스크린샷 2022-09-14 오후 4 53 55" src="https://user-images.githubusercontent.com/97447841/190094930-e920a9be-9d1a-46f2-828d-073344cf06f4.png">

### 마무리
<img width="798" alt="스크린샷 2022-09-14 오후 4 54 39" src="https://user-images.githubusercontent.com/97447841/190095087-c2375937-948f-48cc-b442-62c191e49815.png">

- 아쉬운점
    - 데이터가 작아 학습하는데 한계가 있었습니다.
    - mAP가 0.5 미만이라 아쉽습니다.
- 발전 방향
    - 다음번엔 영상을 이용해서 object detection을 해보고 싶습니다.
