
# Vivado-Vitis Design Flow

> [!note] ⭐꼭 지키세요!⭐
> Vivado 프로젝트 생성시 **"extensbiel Vitis"** 체크 해제하기
> [[1. Extensible Vitis Platform이란?]]


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
![[Screenshot from 2024-09-04 10-54-02.png]]
- IP INTEGRATOR에서 "Create Block Design"을 통해 IP 생성

### 2) IP setting
![[Screenshot from 2024-09-04 10-55-40.png]]
- 생성된 IP를 더블클릭하여 IP Setting하기
      *REF) 현 강의에서는 UART1 블록만을 이용하므로 해당 블록 기준으로  세팅함*
![[Screenshot from 2024-09-04 10-57-57.png]]
- 해당 블록에서 UART1을 선택하여 체크박스를 통해 활성화 해주기

**주의사항!** 
![[Screenshot from 2024-09-04 11-00-05.png]]
**UART에 대한 Zybo-z7-20의 Schematic을 참고하여 Bank 1의 I/O Voltage를 세팅해줘야 햠! 
(고장의 우려)

### 3) Run Block Automation
![[Screenshot from 2024-09-04 11-02-22.png]]
- 자동으로 외부 인터페이스와 IP Block을 연결해주는 역할을 해준다

> [!note] ⭐ "Run Automation"후 꼭 해주기!!
> 반드시 "F6"를 눌러서 BD의 Validation을 체크하기!!

### 4) BD 파일 Wrapping하기

> [!question] 왜 이런 작업을 할까?
> 
> BD file != Verilog 그러므로 BD를 Verilog로 변환해주는 작업 필요
>     Wrapping을 통한 "wrapper"를 생성하여 Tool이 합성가능하게 만들어줌

![[Screenshot from 2024-09-04 11-16-57.png]]
1. Source -> BD 우클릭 -> Create HDL Wrapper
   
 
![[Screenshot from 2024-09-04 11-19-25.png]]

#### 그럼 이렇게 Verilog(.v)파일 생성!!

### 5) Bitstream File 생성하기

### 6) XSA(HW Platform) 추출하기

![[Screenshot from 2024-09-04 14-26-44.png]]

#### File -> Export -> Export Hardware

![[Screenshot from 2024-09-04 15-01-33.png]]

#### "include bitstream" 선택하기(implement까지된 HW 이용)
*Vitis에서도 bitstream을 fpga에 올릴 수 있음*

# 2. Vitis setting
