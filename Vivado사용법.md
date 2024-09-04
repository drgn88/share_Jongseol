# !참고사항!
## 1. 하나의 IP(UART)를 예시로 설명한 내용입니다. -> IP의 용도에 대해서는 크게 생각 마세요
## 2. 1-2)의 주의사항에서 Bank Vlotage에 대한 내용은 중요합니다. 명심하세요. 안 지키면 보드 고장납니다.
## 3. 1-3)의 "Run automation"이후 F6를 눌러 IP 블럭의 유효성 체크하는 것을 명심하세요. 이걸 안하고 wrapping하면 불량인지 체크 안하고 하드웨어 만드는 것과 같습니다.

# Vivado-Vitis Design Flow

 ⭐꼭 지키세요!⭐
 Vivado 프로젝트 생성시 **"extensbiel Vitis"** 체크 해제하기
 [[1. Extensible Vitis Platform이란?]]


## 1) Vivado Flow
1. Project 생성하기
2. Zynq Processor IP 생성하기 _➝_ ARM Processor 사용하기 위함
3. Generate Bitstream _➝_ .xsa 파일 생성(하드웨어 플랫폼)
        *REF) SW가 구동되기 위한 하드웨어 플랫폼이 필요함*

## 2) Vitis Flow
1. Vivado에서 만든 .xsa파일을 이용하여 프로젝트 생성하기
2. PS에 코딩
3. Serial interface로 동작확인 

# 1. Vivado setting

### 1) Zynq processor IP 생성
![Screenshot from 2024-09-04 10-54-02](https://github.com/user-attachments/assets/4c61df44-54ec-478a-9a10-0d38da9754a6)

- IP INTEGRATOR에서 "Create Block Design"을 통해 IP 생성

### 2) IP setting
![Screenshot from 2024-09-04 10-55-40](https://github.com/user-attachments/assets/bebb0601-3a92-47ed-af6e-d70a47a6114b)

- 생성된 IP를 더블클릭하여 IP Setting하기
      *REF) 현 강의에서는 UART1 블록만을 이용하므로 해당 블록 기준으로  세팅함*
![Screenshot from 2024-09-04 10-57-57](https://github.com/user-attachments/assets/e93d6175-fe59-40c8-b90b-d9f621470d73)

- 해당 블록에서 UART1을 선택하여 체크박스를 통해 활성화 해주기

**주의사항!** 
![Screenshot from 2024-09-04 11-00-05](https://github.com/user-attachments/assets/9385de59-81ca-41d2-b630-be2daff12764)

**UART에 대한 Zybo-z7-20의 Schematic을 참고하여 Bank 1의 I/O Voltage를 세팅해줘야 햠! 
(고장의 우려)

### 3) Run Block Automation
![Screenshot from 2024-09-04 11-02-22](https://github.com/user-attachments/assets/3926222a-f9eb-4ba7-b3ec-ff613c46625c)

- 자동으로 외부 인터페이스와 IP Block을 연결해주는 역할을 해준다

 ⭐ "Run Automation"후 꼭 해주기!!
 반드시 "F6"를 눌러서 BD의 Validation을 체크하기!!

### 4) BD 파일 Wrapping하기

 왜 이런 작업을 할까?
 
 BD file != Verilog 그러므로 BD를 Verilog로 변환해주는 작업 필요
     Wrapping을 통한 "wrapper"를 생성하여 Tool이 합성가능하게 만들어줌

![Screenshot from 2024-09-04 11-16-57](https://github.com/user-attachments/assets/34754104-e9bc-4db9-be48-7d1ce6e257ce)

1. Source -> BD 우클릭 -> Create HDL Wrapper
   
 
![Screenshot from 2024-09-04 11-19-25](https://github.com/user-attachments/assets/f70957f4-a47a-48d6-8030-5f2d99177d0f)


#### 그럼 이렇게 Verilog(.v)파일 생성!!

### 5) Bitstream File 생성하기

### 6) XSA(HW Platform) 추출하기

![Screenshot from 2024-09-04 11-27-56](https://github.com/user-attachments/assets/5ae4e4c4-0f14-48b9-b1e5-1bee7e7d32e1)


#### File -> Export -> Export Hardware

![Screenshot from 2024-09-04 13-42-02](https://github.com/user-attachments/assets/13fd5634-a18f-437b-95cd-8eb54327304b)


#### "include bitstream" 선택하기(implement까지된 HW 이용)
*Vitis에서도 bitstream을 fpga에 올릴 수 있음*

#### 이렇게 하면 XSA 파일 생성 완료
