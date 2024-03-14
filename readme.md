# Scala Kyo real world example - tic-tac-toe

## [⚠️] this repository is forked from `https://github.com/jorge-vasquez-2301/kyo-tictactoe`

## Detailed explanation is [here](https://www.scalamatters.io/post/writing-modular-applications-using-the-kyo-library?postId=47ebefe2-32c0-4546-9554-b246bfd9eff8&utm_campaign=5b121e01-39ce-479f-aed0-1d424f4f7088&utm_source=so&utm_medium=mail&utm_content=6706e75d-3ea3-4cbf-b20d-402b657c8ee5&cid=09e15c3f-510a-4597-a187-70d6e6cccdac)


## What is this

이 코드는 Kyo 프레임워크를 사용하여 작성되었으며, Kyo는 함수형 프로그래밍 패러다임을 기반으로 하는 Scala 라이브러리입니다. 


## 주요 구성 요소

Domain Models
- State 등의 도메인 모델이 언급되며, 게임의 상태를 나타내는 데 사용됩니다.

Environments (Envs) & Inputs/Outputs (IOs): 
- Kyo 프레임워크의 주요 개념으로, 외부 시스템이나 사용자와의 상호작용을 추상화합니다. 예를 들어, Terminal과 Controller는 사용자의 입력을 받고 게임의 상태를 업데이트하는 데 사용됩니다.

Layers: 
- 의존성을 관리하고 구성하는 메커니즘입니다. 여기서는 게임의 다양한 모드와 뷰, 로직, AI 등을 연결하는 데 사용됩니다.

Modes: 
- 게임의 다양한 모드를 나타내며, ConfirmMode, MenuMode, GameMode 등이 있습니다. 각 모드는 게임의 특정 상태나 화면을 관리합니다.

Views: 
- 사용자에게 보여질 내용을 렌더링하는 역할을 합니다. 예를 들어, ConfirmView, MenuView, GameView 등이 있습니다.

Parsers: 
- 사용자의 입력을 파싱하고 이해하는 역할을 합니다. 각 모드에 해당하는 파서들이 있으며, 입력을 해당 모드의 명령이나 액션으로 변환합니다.

Logic and AI: 
- 게임 로직(GameLogic)과 인공 지능(OpponentAi)을 처리합니다. 이들은 게임의 규칙을 실행하고 컴퓨터 상대의 행동을 결정합니다.


## 프로그램 흐름

TicTacToe 객체는 KyoApp을 확장하여, 애플리케이션의 진입점을 정의합니다. program은 게임의 주요 루프를 나타내며, layer는 의존성을 구성하는 데 사용됩니다.

### Program Loop:

loop 함수는 게임 상태를 반복적으로 업데이트하며, 각 반복에서 step 함수를 호출합니다.
step 함수는 현재 게임 상태에 따라 다음 상태를 결정합니다. 사용자의 입력을 받고, 해당 입력을 처리하여 게임 상태를 업데이트합니다.

### Layer Composition:

각 모드와 관련된 의존성들이 Layer를 통해 구성됩니다. 예를 들어, confirmModeDeps, menuModeDeps, gameModeDeps는 각 모드의 필요한 의존성들을 정의합니다.
이러한 의존성들은 최종적으로 controllerNoDeps와 함께 결합되어, 게임의 전체 의존성 구조를 형성합니다.

### Execution:

run 메서드는 layer를 사용하여 프로그램을 실행합니다. 이는 모든 의존성이 주입되고, 주 프로그램 루프가 시작됨을 의미합니다.