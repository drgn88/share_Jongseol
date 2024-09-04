# Vitis 이용법: Unified Vs Classic

## 1. Classic(Old Version)

### 1) Vitis 실행하기
> [!abstract] 명령어
> $vitis --classic

### 2) Workspace 지정
>[!question] workspace란?
>vitis프로젝트를 진행하며 생성되는 파일들을 관리하는 공간

![[Screenshot from 2024-09-04 15-51-27.png|700]]

#### 내가 사용할 Workspace를 Browser를 통해 지정
### 3) "Create Application Project" 선택
![[Screenshot from 2024-09-04 15-54-15.png]]

### 4) Vivado에서 생성한 .xsa 플랫폼 지정
![[Screenshot from 2024-09-04 15-54-57.png]]

### 5) Processor 지정하기
![[Screenshot from 2024-09-04 15-58-11 1.png]]

#### 1. Application project name 설정
#### 2. 우측 Processor에서 ps7_cortexa9_0 선택 후 Next
*듀얼 코어이지만 싱글만 사용할거기 떄문에 하나만 선택해주는 것*
*SMP(Symmetric Multi-Processing)으로 듀얼 코어임*

### 6) OS 지정하기
![[Screenshot from 2024-09-04 16-01-43.png]]
#### petalinux 사용시 standalone -> linux로 변경

### 7) 프로젝트에 필요한 도구들
![[Screenshot from 2024-09-04 16-03-35.png]]

#### 좌측 하단에 프로젝트를 빌드, 디버그 등을 하기위한 도구들 존재

## 2. Unified (Recently Version) - 수동으로 해줄게 많음
>[!abstract]- 참고
>[Vitis Embeded SW tutorial](https://github.com/Xilinx/Vitis-Tutorials/tree/2024.1/Embedded_Software/Getting_Started)

### 1) Vitis 실행하기
>[!abstraction] 코드
>$ vitis
#### Classic과 달리 별도의 옵션없이 실행
### 2) Workspace 지정해주기
![[Screenshot from 2024-09-04 16-11-22.png]]

#### Open workspace를 통해 workspace를 지정해준다
*시작부터 워크스페이스 지정하는 Classic과 달리 직접 생성해줘야 함*

### 3) Platform 생성하기
#### 방법 1)
![[Screenshot from 2024-09-04 16-14-11.png]]
##### File -> New Component -> Platform
#### 방법 2)
![[Screenshot from 2024-09-04 16-15-18.png]]

##### Embedded Development -> Create Platform component
>[!note] 참고
>Platform: Application(SW)이 실행될 하드웨어
>Application: Platform(HW)위에서 실행되는 응용프로그램(SW)

### 4) Platform 이름 및 위치 지정하기
![[Screenshot from 2024-09-04 16-18-37.png]]

### 5) XSA 파일 지정하기
![[Screenshot from 2024-09-04 17-42-01.png]]
#### "Hardware Design" check -> XSA파일 지정
### 6) OS 및 코어(Processor) 지정하기
![[Screenshot from 2024-09-04 17-43-28 1.png]]
#### Classic과 동일함
### 7) Platform 생성 완료
![[Screenshot from 2024-09-04 17-45-19.png]]

### 8) Application 생성하기
>[!note] 참고
>Application 생성시 자동으로 플랫폼이 생기는 Classic과 달리 
>Unified는 플랫폼을 수동으로 생성 후에 Application을 생성합니다

![[Screenshot from 2024-09-04 17-49-13.png]]
#### File -> New Component -> Application
##### Platform처럼 이름과 브라우저(위치) 지정

### 9) Platform 선택
![[Screenshot from 2024-09-04 17-51-02.png]]
#### 기존에 생성한 플랫폼을 지정해줌
![[Screenshot from 2024-09-04 17-51-49.png]]
#### 내가 생성한 플랫폼 포맷에 맞는지 확인 후 Next
### 10) Application 작업 환경 생성 완료
![[Screenshot from 2024-09-04 17-53-02.png]]

## REF) IDE 참고 사항

### 1)  Template
![[Screenshot from 2024-09-04 17-56-36.png]]
#### 예시 템플릿들 이용가능(**종종 예제에 필요한 파일 없는 경우 존재**)
### 2) 필요 툴
![[Screenshot from 2024-09-04 17-58-25.png]]
#### classic과 달리 아이콘과 내용이 같이 표기(직관적)
