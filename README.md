# Basic-RPi-2024
부경대학교 2024 IoT 개발자 과정 - 라즈베리파이 학습 리포지토리 (안성주 T)

# Basic-RasPi-2024

## day01 
- 라즈베리파이 개념

  ![구조](https://raw.githubusercontent.com/hyeily0627/Basic-RPi-2024/main/images/001.png)

  ![핀맵](https://raw.githubusercontent.com/hyeily0627/Basic-RPi-2024/main/images/002.png)

- **옴의 법칙** : V = IR 

    ![옴의법칙](https://raw.githubusercontent.com/hyeily0627/Basic-RPi-2024/main/images/003.png)

    - 전류(암페어,A) : 전하의 흐름
    - 전압(볼트(V)) :  전기장 안에서 전하가 갖는 전위의 차이
    - 저항 : 전기회로에서 전류가 흐르는 것을 방해하는 정도 
    
- 키르히호프의 법칙
  - 1법칙은 전하량 보존 법칙으로 도선이 갈라지거나 합쳐질 때 전류값이 보존된다
  - 2법칙은 에너지 보존 법칙으로 루프(loop) 회로에서 전지가 만든 전위차는 저항에서 감소한 전위차와 같다는 것

![키르히호프](https://raw.githubusercontent.com/hyeily0627/Basic-RPi-2024/main/images/004.png)

- GND(0, 그라운드) 역할 (<-> VCC : 1)
  - 전류를 모이게 한다.
  - 전압의 기준이 되는 역할 (=기준 전압)

- GPIO 설정 함수 (python)
  - GPIO.setmode(GPIO.BOARD) -> wPi
  - GPIO.setmode(GPIO,BCM) -> BCM
  - GPIO.setup(channel, GPIOmode) 
    - channel 핀번호, mode IN/OUT
  - GPIO.cleanup

- GPIO 출력 함수 
  - GPIO.output(channel, state) 
    - channel 핀번호, state HIGH/LOW or 1/0 or TRUE/FALSE

- GPIO 입력 함수
  - GPIO.input(channel)
    - channel : 핀번호, 반환값 H/L or 1/0 or T/F

- 시간지연함수 
  - time.sleep(secs)

- 풀업 저항(PULL UP)과 풀다운 저항(PULL DOWN) 쉽게 이해하기
    - 플로팅 현상 : 스위치가 연결되면 전류가 정상적으로 흐르나, 스위치가 연결되지 않은 상태에서 전류가 흐르는지 흐르지 않는지 알 수 없는 상태가 된 것을 말한다. 

    ![플로팅](https://raw.githubusercontent.com/hyeily0627/Basic-RPi-2024/main/images/005.png)

    - 풀업 저항(PULL UP) : 저항을 앞에 붙여줘서 플로팅 현상을 해결하는 방법
        - 풀업 저항에서 스위치가 열린 상태일 때(OFF)
        : 입력 핀으로 전류가 흐르게 되고, 전원 전압과 같은 5v전압이 걸리게 됨 => 입력핀은 HIGH 값이 읽힘 

        ![풀업스위치](https://raw.githubusercontent.com/hyeily0627/Basic-RPi-2024/main/images/006.png)

        - 풀업 저항에서 스위치가 닫힌 상태일 때(ON)
        : 모든 전류는 GND쪽으로 흐름. 입력핀에는 0v 전압이 걸리게 된다. 

        ![풀업스위치](https://raw.githubusercontent.com/hyeily0627/Basic-RPi-2024/main/images/006-2.png)

        ![정리](https://raw.githubusercontent.com/hyeily0627/Basic-RPi-2024/main/images/007.png)

    - 풀다운 저항(PULL DOWN) : 풀업 저항과는 반대로 밑에다가 저항을 연결하는 방식 
        - 풀다운 저항에서 스위치가 열린 상태일 때(OFF)
        : 스위치가 열린 상태에서는 어디에도 전류가 흐르지 않고 입력핀에는 0v 전압이 걸리게 됨 

        ![풀다운스위치](https://raw.githubusercontent.com/hyeily0627/Basic-RPi-2024/main/images/008.png)

        - 풀다운 저항에서 스위치가 닫힌 상태일 때(ON)
        : 밑의 저항으로 인해 전류는 모두 입력핀 쪽으로 흐르고, 입력핀에는 전원 전압과 같은 5v가 걸리게 됨

        ![풀다운스위치](https://raw.githubusercontent.com/hyeily0627/Basic-RPi-2024/main/images/009.png)

        ![총정리](https://raw.githubusercontent.com/hyeily0627/Basic-RPi-2024/main/images/010.png)