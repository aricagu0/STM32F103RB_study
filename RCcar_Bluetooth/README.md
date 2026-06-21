# Rccar_Driving_bluetooth
CSR_BC41C
CSR_BC41C
* HC-06 슬레이브 전용 모듈
* HC-06 마스터 모듈 1개와 1:1 통신 가능
* CSR Bluetooth Chip이 장착된 모듈
* Bluetooth V2.0 표준2 프로토콜 적용
* 3.3V 에서 동작
* UART : 1200,2400,4800,9600,19200,38400,57600,115200 bps
* 사이즈 : 28mm * 15mm * 2.35mm
* 동작전류
  * 페어링 될때 까지 30~40mA
  * 통신대기시 2~8mA
  * 페어링시 8mA
  * 슬립시 슬립
*GPS 네비게이션 시스템, 각종 응용 검침 시스템, 산업현장 마이닝 제어 시스템 및 기타 장치에 다양하게 응용 가능.
*블루투스 장착된 노트북, 컴퓨터, PDA, 스마트폰 등 기타 장치와 원활한 여결이 가능.
```
(base) C:\Users\Administrator\Desktop>python HC06_v2.py
HC-06/HC-05 모듈 연결 시도 중...

==================================================
자동 Baudrate 탐지 시작...
==================================================

[시도] Baudrate: 9600... ✓ 성공!

==================================================
모듈 발견!
  - Baudrate: 9600
  - 명령어 형식: v1
  - 응답: OK
==================================================


=== 연결 테스트 ===
  [전송] AT... 응답: OK
✓ 연결 성공!

=== 펌웨어 버전 확인 ===
  [전송] AT+VERSION... 응답: DX_smartv2.0
버전 정보: DX_smartv2.0

=== 블루투스 이름 설정: MyHC06-011 ===
  [전송] AT+NAMEMyHC06-011... 응답: OKsetname
✓ 이름 설정 성공!

=== PIN 코드 설정: 1234 ===
  [전송] AT+PIN1234... 응답: OKsetPIN
✓ PIN 설정 성공!

=== 통신 속도 설정: 115200 ===
  [전송] AT+BAUD115200... 응답 없음
  [전송] AT+UART=115200,0,0... 응답 없음
  [대체 시도] AT+UART=115200,0,0... 응답 없음
  [대체 시도] AT+BAUD115200... 응답 없음
  [전송] AT+BAUD8... 응답: OK115200
✓ 통신 속도 설정 성공!
⚠ 모듈 전원을 껐다 켜면 115200로 변경됩니다.

==================================================
설정 완료!
==================================================
⚠ 중요: 모듈의 전원을 껐다 켜야 새 설정이 적용됩니다.
전원 재시작 후 다음 설정으로 연결하세요:
  - Baudrate: 115200
  - 이름: MyHC06
  - PIN: 1234
==================================================

시리얼 연결이 종료되었습니다.

(base) C:\Users\Administrator\Desktop>
```
```c
void forward(void)
	{
	 int a=1;
	 int b=0;

	 HAL_GPIO_WritePin(LFF_GPIO_Port, LFF_Pin, a);
	 HAL_GPIO_WritePin(LFB_GPIO_Port, LFB_Pin, b);
	 HAL_GPIO_WritePin(LBF_GPIO_Port, LBF_Pin, a);
	 HAL_GPIO_WritePin(LBB_GPIO_Port, LBB_Pin, b);


	 HAL_GPIO_WritePin(RFF_GPIO_Port, RFF_Pin, a);
	 HAL_GPIO_WritePin(RFB_GPIO_Port, RFB_Pin, b);
	 HAL_GPIO_WritePin(RBF_GPIO_Port, RBF_Pin, a);
	 HAL_GPIO_WritePin(RBB_GPIO_Port, RBB_Pin, b);

	 }

	void backward()
	{
		 int a=1;
		 int b=0;

		 HAL_GPIO_WritePin(LFF_GPIO_Port, LFF_Pin, b);
		 HAL_GPIO_WritePin(LFB_GPIO_Port, LFB_Pin, a);
		 HAL_GPIO_WritePin(LBF_GPIO_Port, LBF_Pin, b);
		 HAL_GPIO_WritePin(LBB_GPIO_Port, LBB_Pin, a);

		 HAL_GPIO_WritePin(RFF_GPIO_Port, RFF_Pin, b);
		 HAL_GPIO_WritePin(RFB_GPIO_Port, RFB_Pin, a);
		 HAL_GPIO_WritePin(RBF_GPIO_Port, RBF_Pin, b);
		 HAL_GPIO_WritePin(RBB_GPIO_Port, RBB_Pin, a);

		 }
	void leftward(void)
	{
			  int a=1;
			  int b=0;

				 HAL_GPIO_WritePin(LFF_GPIO_Port, LFF_Pin,b );
				 HAL_GPIO_WritePin(LFB_GPIO_Port, LFB_Pin,a );
				 HAL_GPIO_WritePin(LBF_GPIO_Port, LBF_Pin,b );
				 HAL_GPIO_WritePin(LBB_GPIO_Port, LBB_Pin,a );

				 HAL_GPIO_WritePin(RFF_GPIO_Port, RFF_Pin,a );
				 HAL_GPIO_WritePin(RFB_GPIO_Port, RFB_Pin,b );
				 HAL_GPIO_WritePin(RBF_GPIO_Port, RBF_Pin,a );
				 HAL_GPIO_WritePin(RBB_GPIO_Port, RBB_Pin,b );
	}
	void rightward(void)
	{
        int a=1;
		int b=0;

		 HAL_GPIO_WritePin(LFF_GPIO_Port, LFF_Pin,a );
		 HAL_GPIO_WritePin(LFB_GPIO_Port, LFB_Pin,b );
		 HAL_GPIO_WritePin(LBF_GPIO_Port, LBF_Pin,a );
		 HAL_GPIO_WritePin(LBB_GPIO_Port, LBB_Pin,b );
		 HAL_GPIO_WritePin(RFF_GPIO_Port, RFF_Pin,b );
		 HAL_GPIO_WritePin(RFB_GPIO_Port, RFB_Pin,a );
		 HAL_GPIO_WritePin(RBF_GPIO_Port, RBF_Pin,b );
		 HAL_GPIO_WritePin(RBB_GPIO_Port, RBB_Pin,a );

	}
	void forwards(int speed)
		{
		 int a=1;
		 int b=0;

	 HAL_GPIO_TogglePin(LFF_GPIO_Port, LFF_Pin);
	 HAL_GPIO_TogglePin(LBF_GPIO_Port, LBF_Pin);
	 HAL_GPIO_TogglePin(RFF_GPIO_Port, RFF_Pin);
	 HAL_GPIO_TogglePin(RBF_GPIO_Port, RBF_Pin);

	 HAL_GPIO_WritePin(LFB_GPIO_Port, LFB_Pin, b);
     HAL_GPIO_WritePin(LBB_GPIO_Port, LBB_Pin, b);
	 HAL_GPIO_WritePin(RFB_GPIO_Port, RFB_Pin, b);
	 HAL_GPIO_WritePin(RBB_GPIO_Port, RBB_Pin, b);
	 HAL_Delay(speed);

		 }

	void stop(void)
	{
		int a=1;
		int b=0;

		HAL_GPIO_WritePin(LFF_GPIO_Port, LFF_Pin,b);
	    HAL_GPIO_WritePin(LBF_GPIO_Port, LBF_Pin,b);
	    HAL_GPIO_WritePin(RFF_GPIO_Port, RFF_Pin,b);
	    HAL_GPIO_WritePin(RBF_GPIO_Port, RBF_Pin,b);

	    HAL_GPIO_WritePin(LFB_GPIO_Port, LFB_Pin, b);
		HAL_GPIO_WritePin(LBB_GPIO_Port, LBB_Pin, b);
		HAL_GPIO_WritePin(RFB_GPIO_Port, RFB_Pin, b);
		HAL_GPIO_WritePin(RBB_GPIO_Port, RBB_Pin, b);

	}
```
```c
if (HAL_UART_Receive(&huart2, &rx_char, 1, 100) == HAL_OK)
	        {
	            switch(rx_char){
	                case 'w': forward(); break;
	                case 'a': leftward();    break;
	                case 's': backward();break;
	                case 'd': rightward();   break;
	                case 'x': stop();    break;
	                default:  break;
	            }
```
### 시연
![](8.gif)

