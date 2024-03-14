<p align="center" width="100%">
	<img width="575" alt="Logo" src="https://github.com/naldal/TuistAutoGen/assets/45508297/cd07e010-c205-4e08-a77b-ea248c45128d">
</p>

[🇰🇷 한국어로 읽기](https://github.com/naldal/TuistAutoGen/blob/main/README.Ko.md) |
[🇺🇸 Read in English](https://github.com/naldal/TuistAutoGen/blob/main/README.md)

<h3 align="center">🚀 Tuist 프로젝트를 간단하게 구축할 수 있는 유틸리티 라이브러리 </h3>
<br></br>
TuistAutoGen에 오신것을 환영합니다. TuistAutoGen은 한 번의 스크립트 실행으로 Tuist 프로젝트 라이프사이클을 완벽하게 제어할 수 있습니다. <br></br>
TuistAutoGen은 단순한 프로젝트 생성 도구 이상입니다. 이는 프로젝트의 요구에 맞게 진화하는 도구로, 프로젝트의 필요에 따라 발전하며 손쉽게 수정할 수 있습니다. TuistAutoGen은 뛰어난 디자인으로 신속한 프로젝트 모듈화와 프레임워크 제작을 위한 솔루션입니다. 이 모든 것이 단 한 번의 쉘 실행으로 이루어집니다!

## 왜 TuistAutoGen를 사용해야 할까요?

일반적으로 Tuist를 사용하여 프로젝트를 처음부터 끝까지 생성하는 것은 여러 가지 어려움을 수반합니다:

💀 **복잡성** <br>
Tuist는 강력하지만 특히 초보자에게는 설정과 관리가 다소 복잡합니다. 다양한 구성 파일이 관련되며, 프로젝트를 생성, 조작 및 관리하기 위해 Tuist DSL(Domain Specific Language)을 이해해야 합니다.

⏰ **시간 소요** <br>
프로젝트 설정, 종속성 관리, 타겟 생성 및 Xcode 프로젝트 생성 과정은 특히 여러 모듈과 종속성을 가진 큰 프로젝트의 경우 시간이 많이 소요될 수 있습니다.

🧟 **휴먼에러 취약** <br>
수동으로 구성 및 설정하는 과정에서 인간의 실수가 발생할 수 있으며, 이는 빌드 오류나 실행 시 문제를 일으킬 수 있습니다.

😓 **모듈화의 어려움** <br>
Tuist는 모듈화를 지원하지만, 모듈 프로젝트 설정은 도전적이며 여러 단계를 거칩니다. 개별 모듈 생성, 상호 종속성 관리, 각 모듈이 독립적으로 빌드될 수 있는지 확인하는 것을 포함합니다.

🦿 **프레임워크 생성** <br>
프로젝트의 프레임워크 생성은 타겟 설정, 종속성 연결 및 빌드 설정 관리 등 수많은 수동 작업을 필요로 합니다.

이러한 본질적인 어려움은 개발 속도의 저하, 버그 발생 위험의 증가, 그리고 시스템에 새로운 개발자들에게는 더욱 가파른 학습 곡선을 초래합니다.

반면에 TuistAutoGen은 프로젝트 생성, 모듈화 및 프레임워크 생성을 자동화하여 이러한 단계를 극적으로 단순화하므로 앞서 언급한 장애물을 제거합니다. TuistAutoGen을 사용하면 Tuist를 쉽게 사용할 수 있으며, 프로젝트 설정 과정을 가속화시키고, 휴먼에러 가능성을 줄이며, 복잡하고 모듈화된 프로젝트를 간단하고 직관적으로 관리할 수 있습니다.


## 사용법

### 필수 설치
TuistAutoGen은 Tuist 3.11.0 버전을 기준으로 작성되었습니다.
TuistAutoGen이 정상적으로 작동하려면 반드시 이 버전을 지켜주세요.

하지만 맥에 아무런 설치가 되어있지 않은 상태라면 Homebrew나 mise, curl 등의 유틸리티 소프트웨어가 필요할 수 있습니다.

저는 이 문제를 조금 더 우아하게 풀어보기 위해 TuistInstaller라는 또 다른 쉘 스크립트 파일을 만들어 배포하고 있습니다.
[TuistInstaller 바로가기](https://github.com/naldal/TuistInstaller/tree/master)

TuistInstaller는 Tuist설치에 필요한 요소들을 제공하고 있습니다.



### 기본 사용법
> **Note:** TuistAutoGen 은 bash 5.2.15 릴리즈 버전에서 작성되었습니다. (aarch64-apple-darwin22.1.0)
> 
> 너무 낮은 Bash 버전은 쉘 스크립트의 작동에 문제가 될 수 있습니다.

단일 애플리케이션을 생성하려면 bash 쉘에서 아래 명령을 입력하세요.
```bash
./autoGenerator.sh --main $projectName
```
예를 들면 다음과 같이 사용할 수 있습니다.
```bash
./autoGenerator.sh --main CoreProject
```
설정한 이름은 메인 어플리케이션의 이름이 됩니다!

곧 이어, 프로젝트의 이름을 생성합니다.
```bash
🏃 Start to generate Tuist Projects!
✍️ What is the name of new Project?
✏️ Your Name of Project is :
<프로젝트 이름 설정>
```
설정한 이름은 전체 프로젝트의 이름이 됩니다!

📦TuistAutoGenerator  
┗ 📜 autoGenerator.sh <br>
┣ 📂 temp<br>
┗ 📂 **프로젝트** <br>
&nbsp;&nbsp;┗ 📂 **Main 어플리케이션**

이제 위처럼 설정한 프로젝트 이름 아래에 메인 프로젝트가 생성됐습니다.
Tuist 프로젝트를 시작하려면 설정한 프로젝트 폴더로 이동하세요.
```bash
cd 프로젝트이름
```

이제 tuist 프로젝트를 생성하기 위해 generate 명령어를 실행하면 됩니다.
```bash
tuist generate
```

..이게 끝입니다! 
기본 어플리케이션 생성이 완료되었습니다. 🎉

## "Main" 프로젝트 구조

🖐️ 진행하기 전에, 생성한 Main 프로젝트의 구조를 이해하는 것이 필요합니다. Main 프로젝트 구조를 설명하는 그림을 살펴보겠습니다.

<p align="center" width="100%">
<img width="967" alt="mainProjectHiearchy" src="https://github.com/naldal/TuistAutoGen/assets/45508297/592389f8-cadb-4be8-b876-b2bf90ee39f2">
</p>

Main 프로젝트에는 Supports와 Target라는 두 개의 폴더가 있습니다.
- **Supports 폴더**는 InfoPlist와 BridgingHeader 폴더로 구성되어 있습니다. 각 폴더는 특정 목적을 가지고 있습니다:
  - *InfoPlist 폴더*는 필요에 따라 다양한 유형의 정보를 포함할 수 있는 Info.plist 파일을 보관합니다.
  - *BridgingHeader 폴더*는 Swift와 Objective-C 간의 상호 작용을 용이하게 하는 헤더 파일을 포함합니다.
- **Target 폴더** 는 Resources, Sources, Tests, TestResources, XCConfigs 폴더로 구성됩니다.
	- *Resources 폴더*는 이미지, 색상, 로컬라이즈 문자열 등 애플리케이션의 자산을 관리합니다. TuistAutoGen은 자동으로 Image.xcassets 및 Color.xcassets 카탈로그를 이 폴더 내에 생성합니다.
	- *Sources 폴더*는 자유롭게 코드를 작성할 수 있는 곳입니다.
	- *Tests 폴더*는 단위 테스트를 위해 지정된 폴더입니다. TuistAutoGen은 테스트 라이브러리인 Quick과 Nimble을 자동으로 포함시키며, 테스트 수행을 강력히 권장합니다.
	- *TestResources 폴더*는 특정 테스트용 리소스를 저장할 수 있는 공간입니다.
	- *XCConfigs 폴더*는 사용자 정의 Xcode 구성 파일을 관리하는 데 사용됩니다.

## 입력 옵션 이해하기

TuistAutoGen에는 main, includeOnly, include 및 framework의 네 가지 입력 옵션이 있습니다. 각 옵션은 프로젝트 생성 중에 생성할 프로젝트 유형을 결정합니다.

|입력 옵션   | 설명
|----------------|-------------------------------
`--main`         |Main 어플리케이션             
`--includeOnly`  |Main 애플리케이션을 기반으로 한 애플리케이션          
`--include`      |Main 애플리케이션을 기반으로 하면서 자체 소스와 리소스를 가진 애플리케이션
`--framework`    |프레임워크


### 입력 옵션 사용하기
이제 이러한 옵션들을 사용하여 다양한 경우에 대응해봅시다!

케이스 1) 메인 애플리케이션과 includeOnly 애플리케이션을 만들고 싶다고 가정해봅시다.

```bash
./autoGenerator.sh --main $Main_ProjectName --includeOnly $Include_Only_ProjectName
```

아래와 같은 구조가 만들어집니다.

📦TuistAutoGenerator  
┗ 📜 autoGenerator.sh <br>
┣ 📂 temp<br>
┗ 📂 **프로젝트** <br>
&nbsp;&nbsp;┗ 📂 **Main 어플리케이션** <br>
&nbsp;&nbsp;┗ 📂 **IncludeOnly 어플리케이션**<br>

<br>
케이스 2) 두 개의 includeOnly 애플리케이션과 하나의 include 애플리케이션을 만들어 볼까요?

```bash
./autoGenerator.sh --main $Main_ProjectName --includeOnly $Include_Only_ProjectName_One --includeOnly $Include_Only_ProjectName_Two --include $Include_ProjectName

```


📦TuistAutoGenerator  
┗ 📜 autoGenerator.sh <br>
┣ 📂 temp<br>
┗ 📂 **프로젝트** <br>
&nbsp;&nbsp;┗ 📂 **Main 어플리케이션** <br> 
&nbsp;&nbsp;┗ 📂 **IncludeOnly 어플리케이션 1** <br>
&nbsp;&nbsp;┗ 📂 **IncludeOnly 어플리케이션 2** <br>

<br>

케이스 3) 프레임워크 생성은 어떨까요?

```bash
./autoGenerator.sh --main $Main_ProjectName --framework $Framework_ProjectName
```

📦TuistAutoGenerator  
┗ 📜 autoGenerator.sh <br>
┣ 📂 temp<br>
┗ 📂 **프로젝트** <br>
&nbsp;&nbsp;┗ 📂 **프레임워크** <br>
<br></br>

이제부터 이 옵션들이 무엇을 의미하는지 알아보고 이들의 구조와 왜 이것들이 필요한지에 대해서 설명하겠습니다


## "IncludeOnly" 프로젝트 구조
이 옵션을 사용하면 "includeOnly" 프로젝트에는 소스와 리소스가 없는 상태로 유지되지만 Main 프로젝트의 모든 폴더가 포함된 프로젝트 구조를 생성할 수 있습니다.
<p align="center" width="100%">
<img width="958" alt="includeOnlyProjectHiearchy" src="https://github.com/naldal/TuistAutoGen/assets/45508297/cc643f40-6d02-4bd9-9a20-32fcee5881e8">
</p>


### `--includeOnly` 옵션의 필요성
이 옵션은 "includeOnly" 프로젝트에 추가적인 리소스나 소스 파일을 포함하지 않으면서도 주 프로젝트에서 필요한 구성 요소를 포함하는 방법을 제공합니다. 이는 대규모 프로젝트에서 서로 다른 구성 요소가 공유 리소스를 참조해야 하는 경우나 간소화된 프로젝트 구조를 유지하는 것이 중요한 경우에 특히 유용합니다. --includeOnly 옵션은 내비게이션과 관리를 간소화하며, 보다 간결한 프로젝트 설정과 유지 관리 프로세스를 보장합니다.

예를 들어, 여러 가지 변형을 가진 애플리케이션을 개발하는 시나리오를 고려해봅시다. 예를 들어 "Dev" 버전과 "Prod" 버전이 있습니다. 두 버전은 동일한 기본 구조와 많은 리소스를 공유하지만, "Dev" 버전은 추가적인 디버깅 도구, 테스트 데이터 또는 구성 설정을 포함할 수 있습니다.

이 경우, `--includeOnly` 옵션은 강력한 도구가 될 수 있습니다. 아래는 작동 방식의 예시입니다:

주 프로젝트에는 "Dev"와 "Prod" 버전 모두에서 공유되는 모든 소스 코드와 리소스가 포함됩니다. 이 프로젝트는 애플리케이션의 기반이 됩니다.

다음으로, "Dev" 버전을 위한 "includeOnly" 프로젝트를 별도로 생성합니다. `--includeOnly` 옵션을 사용하여 이 프로젝트는 Main 프로젝트의 모든 폴더를 포함하지만 자체 소스나 리소스는 가지지 않습니다. 대신, 개발 환경에만 해당하는 디버깅 도구, 추가 구성 설정 또는 테스트 데이터 등을 포함할 수 있습니다.

이러한 설정을 통해 "Dev" 버전과 "Prod" 버전 사이를 쉽게 전환할 수 있으며, 프로젝트 구조를 깔끔하고 정리된 상태로 유지할 수 있습니다. 각 버전은 공통된 기본 구조와 리소스를 공유하면서도 버전별 사용자 정의를 가능하게 합니다.


## "Include" 프로젝트 구조
`--include` 옵션은 include 프로젝트가 Main 프로젝트의 모든 폴더를 포함하면서도 고유한 소스와 리소스를 유지하도록 합니다.
<p align="center" width="100%">
<img width="966" alt="includeProjectHiearchy" src="https://github.com/naldal/TuistAutoGen/assets/45508297/1992021f-958f-45ed-819a-aaaed7129d03">
</p>

### `--include` 옵션의 필요성
이 옵션을 사용하면 Main 프로젝트에서 필요한 구성 요소를 통합하는 과정을 용이하게 하면서도 include 프로젝트가 개별 리소스와 소스 파일을 유지할 수 있습니다. 이는 프로젝트의 다른 구성 요소가 공유 리소스를 참조해야 하지만 독립적인 파일을 유지해야 하는 상황에서 매우 유용합니다.

예를 들어, 공통된 구조와 리소스를 공유하지만 각각 고유한 기능을 필요로 하는 여러 모듈로 구성된 프로젝트에서 작업한다고 가정해 보겠습니다. `--include` 옵션을 사용하면 각 모듈이 고유한 기능을 유지하는 동시에 주 프로젝트로부터 공유 구조를 보존할 수 있습니다.

`--include` 옵션은 핵심 구조를 일관되게 유지하는 동시에 필요한 곳에서 개별성과 사용자 정의 가능성을 제공합니다. 이는 프로젝트 내비게이션과 관리를 간소화하고 개발자에게 더 효율적인 워크플로우를 제공합니다.

## "Framework" 프로젝트 구조
`--framework` 옵션은 프레임워크를 생성하는 프로젝트를 의미합니다. 이 프레임워크는 고유한 리소스와 소스를 유지하며, 샘플 앱도 자동으로 포함됩니다.

<p align="center" width="100%">
<img width="977" alt="FrameworkHiearchy" src="https://github.com/naldal/TuistAutoGen/assets/45508297/6bf25d0b-85d3-4be9-a0d8-dbe92699ab0d">
</p>

### `--framework` 옵션의 필요성
`--framework` 옵션을 사용하면 개발자는 코드를 재사용 가능하게 구성하여 복잡성을 줄이고 코드의 유지 보수성을 향상시킬 수 있습니다. `--framework` 옵션으로 생성된 프레임워크는 특정 리소스와 소스를 포함하며, 이는 여러 프로젝트나 애플리케이션 간에 쉽게 공유할 수 있는 기능의 완전한 패키지로 구성됩니다.

예를 들어, 다른 프로젝트에서 사용되는 네트워킹이나 데이터베이스 관리와 같은 일련의 기능이 있다고 가정해 보겠습니다. `--framework` 옵션을 사용하여 이러한 기능을 프레임워크로 묶음으로써 코드의 중복을 줄이고 개발 프로세스를 간소화하며 전체적인 코드 신뢰성을 높일 수 있습니다.

또한 프레임워크는 샘플 애플리케이션과 함께 제공됩니다. 이는 프레임워크의 기능을 테스트하는 데 도움을 주며, 개발자가 자신의 프로젝트에 프레임워크를 통합하고 사용하는 방법을 이해하는 데 실용적인 예시로 사용됩니다.

## 🗺️ 로드맵

 * [x] 📦 framework 단일 생성 가능화
 * [ ] 🫥 auto codesign 적용
 * [ ] 🖌️ tuist stencil 적용


## 마치며
이렇게 해서 강력한 도구인 TuistAutoGen을 사용하여 손쉽게 Tuist 프로젝트를 구축할 준비가 되었습니다.

TuistAutoGen을 통해 프로젝트 생성 과정을 간소화하고 생산성을 향상시키며 효율적인 개발 환경을 조성해 보세요.

Enjoy your journey!


## ⚖️  License
The MIT License (MIT)

Copyright (c) 2023 Hamin Song

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
