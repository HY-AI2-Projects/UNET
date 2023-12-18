# UNET
2020025087 강경원 -UNET

U-Net은 주로 의료 이미지 분석과 같은 응용 분야에서 사용되는 딥러닝 아키텍처 중 하나입니다. 이는 이미지 세그멘테이션(semantic segmentation) 작업에 특히 효과적이며, 입력 이미지를 픽셀 수준에서 분류하여 각 픽셀을 특정 클래스로 할당합니다.

![image](https://github.com/HY-AI2-Projects/UNET/assets/153083879/602fe49f-92d2-4a49-85bd-8d67fde43357)


U-Net은 2015년에 독일의 연구자들이 제안한 것으로, 그 구조가 U자 형태로 생겼다고 해서 U-Net이라는 이름이 붙었습니다. 이 아키텍처는 크게 Contracting Path와 Expansive Path로 나뉘어져 있습니다.

1. **Contracting Path (Encoder):**
   - 입력 이미지에서 정보를 추출하는 부분입니다.
   - 일련의 합성곱(Convolution)과 풀링(Pooling) 연산을 통해 이미지의 공간 해상도를 줄이면서 특징을 추출합니다.
   - 각 단계에서는 합성곱 연산에 ReLU 활성화 함수가 사용됩니다.

2. **Bottleneck:**
   - Contracting Path의 중간에 위치한 부분으로, 이미지의 추상적인 특징을 표현하는 역할을 합니다.
   - 여기서는 더 많은 합성곱 레이어가 쌓여 복잡한 특징을 학습합니다.

3. **Expansive Path (Decoder):**
   - 추출된 특징을 기반으로 입력 이미지의 해상도를 복원하는 부분입니다.
   - 각 단계에서는 역합성곱(Transposed Convolution 또는 Deconvolution)이 사용되어 공간 해상도를 높이면서 특징을 복원합니다.
   - 이 과정에서 Contracting Path에서 생성된 특징 맵들을 이용하여 세그멘테이션을 수행합니다.

4. **Skip Connections:**
   - Contracting Path의 각 단계에서 생성된 특징 맵을 Expansive Path에서 동일한 해상도의 특징 맵과 결합합니다.
   - 이는 저해상도 특징과 고해상도 특징 간의 정보 손실을 최소화하고 더 정확한 세그멘테이션을 도출하기 위한 것입니다.

U-Net은 작은 데이터셋에서도 효과적으로 학습되며, 세그멘테이션 작업에서 좋은 결과를 내는 데 강점을 가지고 있습니다. 특히 의료 이미지에서는 병변의 정확한 위치 및 경계를 찾는 데 유용하게 사용됩니다.

![image](https://github.com/HY-AI2-Projects/UNET/assets/153083879/c940aafe-20c0-4153-9c3f-a5e1d8b403f7)





U-Net: Convolutional Networks for Biomedical Image Segmentation은 2015년에 독일의 연구자인 Olaf Ronneberger, Philipp Fischer, Thomas Brox에 의해 발표된 논문입니다. 이 논문은 주로 의료 이미지 세그멘테이션에 적용되는 딥러닝 아키텍처인 U-Net을 소개하고 있습니다.

### 주요 아이디어:

1. **U-자 형태의 아키텍처:**
   - 논문에서 제안하는 U-Net은 그 형태가 U자 형태로 되어 있습니다. 이는 Convolutional Neural Network (CNN)의 일종으로, Contracting Path와 Expansive Path로 이루어진 구조를 가지고 있습니다.
![image](https://github.com/HY-AI2-Projects/UNET/assets/153083879/c97b4659-06e2-469b-af43-d532e57da175)

2. **Contracting Path (Encoder):**
   - Contracting Path에서는 이미지의 공간 해상도를 줄이기 위해 합성곱(Convolution)과 풀링(Pooling) 레이어가 사용됩니다.
   - 각 단계에서는 다운샘플링을 통해 특징을 추출하고, ReLU 활성화 함수를 사용하여 비선형성을 도입합니다.
![image](https://github.com/HY-AI2-Projects/UNET/assets/153083879/97ecc0a0-9192-4bd5-9755-85dfa88daf6e)

3. **Expansive Path (Decoder):**
   - Expansive Path에서는 Contracting Path에서 추출된 특징을 이용하여 입력 이미지의 공간 해상도를 높입니다. 이는 역합성곱(Transposed Convolution 또는 Deconvolution)을 사용하여 수행됩니다.
   - 각 단계에서는 업샘플링을 통해 특징을 복원하고, 이를 이용하여 세그멘테이션을 수행합니다.
![image](https://github.com/HY-AI2-Projects/UNET/assets/153083879/57aa7c1c-bfbe-4c56-94b1-63b90cf38889)

4. **Skip Connections:**
   - U-Net에서는 Contracting Path의 각 단계에서 생성된 특징 맵을 Expansive Path에서 동일한 해상도의 특징 맵과 결합합니다.
   - 이로써 모델은 저해상도와 고해상도 간의 정보 손실을 최소화하고, 더 정확한 세그멘테이션을 이끌어내는데 도움을 줍니다.

5. **손실 함수:**
   - 논문에서는 세그멘테이션 작업에 효과적인 손실 함수로 교차 엔트로피 손실 함수(Cross-Entropy Loss)를 사용하였습니다.

### 의의:

- U-Net은 주로 의료 이미지 분야에서 성공적으로 사용되어 왔습니다. 세포 이미지, 의료 영상 등 다양한 의료 관련 작업에 적용되어 정확한 세그멘테이션 결과를 도출하면서도 데이터가 부족한 상황에서도 잘 작동합니다.
  
- 이 논문은 세그멘테이션 작업에 특화된 구조를 제안하였으며, 특히 이미지의 정확한 위치 및 경계를 찾는데 중점을 두고 있습니다.

U-Net은 이미지 세그멘테이션 분야에서의 혁신적인 모델 중 하나로, 그 효과와 간결한 구조로 인해 다양한 응용 분야에서 널리 사용되고 있습니다.
