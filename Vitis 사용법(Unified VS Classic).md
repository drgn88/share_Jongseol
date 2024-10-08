# Vitis 이용법: Unified Vs Classic

## 1. Classic(Old Version)

### 1) Vitis 실행하기
명령어
$vitis --classic

### 2) Workspace 지정
workspace란?
vitis프로젝트를 진행하며 생성되는 파일들을 관리하는 공간
![Screenshot from 2024-09-04 15-51-27](https://github.com/user-attachments/assets/f517e48f-bd9b-4c0a-bdf7-b81dc7e869a1)



#### 내가 사용할 Workspace를 Browser를 통해 지정
### 3) "Create Application Project" 선택
![Screenshot from 2024-09-04 15-53-20](https://github.com/user-attachments/assets/08d8cdd2-a1eb-45b6-b08b-ff7a4ec0b7ac)


### 4) Vivado에서 생성한 .xsa 플랫폼 지정
![Screenshot from 2024-09-04 15-54-57](https://github.com/user-attachments/assets/9984b741-db89-4066-8b95-3b68a5a3a071)


### 5) Processor 지정하기
![Screenshot from 2024-09-04 15-58-11](https://github.com/user-attachments/assets/4621f014-7426-417a-8af7-b8a5d116a10f)

#### 1. Application project name 설정
#### 2. 우측 Processor에서 ps7_cortexa9_0 선택 후 Next
*듀얼 코어이지만 싱글만 사용할거기 떄문에 하나만 선택해주는 것*
*SMP(Symmetric Multi-Processing)으로 듀얼 코어임*

### 6) OS 지정하기
![Screenshot from 2024-09-04 16-01-43](https://github.com/user-attachments/assets/99bae758-9ee7-430c-a7ea-5ba91251c44a)

#### petalinux 사용시 standalone -> linux로 변경

### 7) 프로젝트에 필요한 도구들
![Screenshot from 2024-09-04 16-03-35](https://github.com/user-attachments/assets/5b08bfbd-c93d-44d4-83d5-3f666adac9ba)

#### 좌측 하단에 프로젝트를 빌드, 디버그 등을 하기위한 도구들 존재

## 2. Unified (Recently Version) - 수동으로 해줄게 많음
참고
[Vitis Embeded SW tutorial](https://github.com/Xilinx/Vitis-Tutorials/tree/2024.1/Embedded_Software/Getting_Started)

### 1) Vitis 실행하기
코드
$ vitis
#### Classic과 달리 별도의 옵션없이 실행
### 2) Workspace 지정해주기
![Screenshot from 2024-09-04 16-11-22](https://github.com/user-attachments/assets/1c8182d3-88f2-448c-a52b-ff2ac10ae4f3)

#### Open workspace를 통해 workspace를 지정해준다
*시작부터 워크스페이스 지정하는 Classic과 달리 직접 생성해줘야 함*

### 3) Platform 생성하기
#### 방법 1)
![Screenshot from 2024-09-04 16-14-11](https://github.com/user-attachments/assets/d09cd040-f1c7-475c-86ae-8c30706111ef)

##### File -> New Component -> Platform
#### 방법 2)
![Screenshot from 2024-09-04 16-15-18](https://github.com/user-attachments/assets/fa9a0fcc-c12f-4cac-87b5-0f81c09d68bb)


##### Embedded Development -> Create Platform component
참고
Platform: Application(SW)이 실행될 하드웨어
Application: Platform(HW)위에서 실행되는 응용프로그램(SW)

### 4) Platform 이름 및 위치 지정하기
![Screenshot from 2024-09-04 16-18-37](https://github.com/user-attachments/assets/a5d02b49-d33d-4af3-89a3-8ced65e092f3)

### 5) XSA 파일 지정하기
![Screenshot from 2024-09-04 17-42-01](https://github.com/user-attachments/assets/d8ad3752-57e8-4782-ac57-2defda93c7a1)

#### "Hardware Design" check -> XSA파일 지정
### 6) OS 및 코어(Processor) 지정하기
![Screenshot from 2024-09-04 17-43-28](https://github.com/user-attachments/assets/48636233-1831-409c-aee3-da82ba10fd73)

#### Classic과 동일함
### 7) Platform 생성 완료
![Screenshot from 2024-09-04 17-45-19](https://github.com/user-attachments/assets/c4d44ba7-bcae-475d-bc03-19511bbafc24)


### 8) Application 생성하기
 참고
Application 생성시 자동으로 플랫폼이 생기는 Classic과 달리 
Unified는 플랫폼을 수동으로 생성 후에 Application을 생성합니다
![Screenshot from 2024-09-04 17-49-13](https://github.com/user-attachments/assets/067bd4b6-ee94-4e7b-9651-4ed0a1d26f24)

#### File -> New Component -> Application
##### Platform처럼 이름과 브라우저(위치) 지정

### 9) Platform 선택
![Screenshot from 2024-09-04 17-51-02](https://github.com/user-attachments/assets/4b9f9dd1-4d9b-4a81-b529-aceaa92e02e8)

#### 기존에 생성한 플랫폼을 지정해줌
![Screenshot from 2024-09-04 17-51-49](https://github.com/user-attachments/assets/a11a3cad-a4cb-4406-b6c4-1fbfb1dfaff9)

#### 내가 생성한 플랫폼 포맷에 맞는지 확인 후 Next
### 10) Application 작업 환경 생성 완료
![Screenshot from 2024-09-04 17-53-02](https://github.com/user-attachments/assets/54664ae3-d9da-4ca4-ab4c-a7f3bc47386b)

## REF) IDE 참고 사항

### 1)  Template
![Screenshot from 2024-09-04 17-56-36](https://github.com/user-attachments/assets/68150e22-c542-4af2-8b0c-47e881883b60)

#### 예시 템플릿들 이용가능(**종종 예제에 필요한 파일 없는 경우 존재**)
### 2) 필요 툴
![Screenshot from 2024-09-04 17-58-25](https://github.com/user-attachments/assets/8b075a00-419d-42d1-8363-ef69ebdec9ee)

#### classic과 달리 아이콘과 내용이 같이 표기(직관적)
