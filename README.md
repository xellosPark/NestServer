1. npm install -g @nestjs/cli

2. nest new project-name (2. nest new ./ ) <- 해당 폴더

3. 모듈 추가  (모듈 생성)
 - nest g module boards

   nest: using nestcli
   g: generate
   module:schematic that i want to create
   boards: name of the (schematic) 개요의 윤곽

4. Controller 추가 (Controller 란)
 컨트롤러는 들어오는 요청을 처리하고 클라이언트에 응답을 반환합니다.
 - nest g controller boards --no-spec

   nest: using nestcli
   g: generate
   conroller: controller schematic
   boards: name of the schematic
   --no-spec:테스트를 위한 소스 코드 생성
   

5. Service 추가
 - nest g service boards --no-spec

   nest: using nestcli
   g: generate
   conroller: service schematic
   boards: name of the schematic
   --no-spec:테스트를 위한 소스 코드 생성

5_1. Borad Service를 Board Controller에서 이용할 수 있게 해주기
     (Dependency injection)
     Nest Js에서 Dependency injection은 클래스의 Constructor 이루어 집니다.
    Service 주입

********
Board Controller ts에 BoardsService를 BoardsController service 등록
    constructor(private boardsService: BoardsService) {}


  5_2. boardsService 파라미터에 BoardsService 객체를 타입으로 지정해줍니다.
  5_3. 이 boardsService 파라미터를 BoardsController 클래스 안에서 사용하기 위해
     서 this.boardsService 프로퍼티에 boardsService 파라미터를 할당해줍니다.
  5_4. 하지만 타입스크립트에서는 선언한 값만 객체의 프로퍼티로 사용가능하기 때 문에
     위에 boardsService: BoardsService로 선언해줍니다.
  5_5. 이렇게 갖게된 boardsService 프로퍼티를 이용해서 BoardsController 클래스       안에서   활용을 할수가 있습니다.

  5_6 접근 제한자를 이용해서 소스 간단하게 하기
접근 제한자(public, protected, private)을 생성자(constructor) 파라미터에 선언 하면 접근 제한자가 사용된 생성자 파라미터는 암묵적으로 클래스 프로퍼티로 선언됩니다

6.Providers 
 - 프로바이더는 Nest의 기본 개념입니다. 대부분의 기본 Nest 클래스는 서비스, 리포지토리, 팩토리, 헬퍼등 프로바이더로 취급될 수 있습니다. 프로바이더의 주요 아이디어는 종속성으로 주입할 수 있다는 것입니다. 즉, 객체는 서로 다양한 관계를 만들 수 있으며 객체의 인스턴스를 "연결"하는 기능은
 대부분 Nest 런타임 스스템에 위임될 수 있습니다.

6. uuid 모듈 사용하기  
   유니크 값 사용시 사용 대부분 ID 아이디에 사용
 - npm install uuid --save

7. 파이프 필요한 모듈
   파이프를 이용해서 게시물을 생성할 때 유효성 체크
- npm install class-validator class-transformer --save
참조
- https://github.com/typestack/class-validator#manual-validation

8. TypeORM을 사용하기 위해서 설치해야하는 모듈
@nestjs/typeorm
 -Nest.js에서 TypeOrm을 사용하기 위해 연동
npm install pg typeorm @nestjs/typeorm --save

typeorm
 - TypeORM 모듈

 pg
  -pgstgres 모듈


npm & yarn명령어 복습
npm 명령어	                     yarn 명령어	                       설명
npm init	                       yarn init	                프로젝트 초기화
npm install 	                   yarn 또는 yarn install	    package.json의 패키지 설치
npm install --save 패키지명	     yarn add                   패키지명	패키지를 프로젝트 의존성 수준으로 추가
npm install --save-dev 패키지명	 yarn add --dev 패키지명	  패키지를 프로젝트 개발 의존성 수준으로 추가
npm install --global 패키지명	   yarn global add 패키지명	  패키지를 전역 수준으로 추가
npm update --save	               yarn upgrade	              프로젝트 패키지 업데이트
npm run 스크립트명	             yarn 스크립트명	          package.json의 스크립트 명령 실행
npm uninstall --save 패키지명	  yarn remove 패키지명	      패키지 삭제
npm cache clean	                yarn cache clean	          캐쉬 삭제

npm으로 nodemon설치
실시간으로 스크립트 파일을 디버깅 할 수 있는 패키지입니다.
npm install --global nodemon


📢 DTO란 무엇인가요?  
DTO(Data Transfer Object, 데이터 전송 객체)란 프로세스 간에 데이터를 전달하는 객체를 의미합니다. 말 그대로 데이터를 전송하기 위해 사용하는 객체라서 그 안에 비즈니스 로직 같은 복잡한 코드는 없고 순수하게 전달하고 싶은 데이터만 담겨있습니다.  아래의 그림을 통해 DTO는 주로 클라이언트와 서버가 데이터를 주고받을 때 사용하는 객체임을 알 수 있습니다
interface나 class를 이용해서 정의 될 수 있습니다.
하지만 클래스를 이용하는것을 NestJs에서는 추천하고 있습니다.


DTO는 데이터 전송 객체(Data Transfer Object)의 약자로,
클라이언트에서 서버로 전달되는 데이터의 형식을 지정하는 역할을 합니다.
서버 측에서 요청을 처리하기 전에 데이터의 유효성을 검사하고, 해당 데이터를 가공하고,
DB와 통신하기 전에 데이터를 변환하는 등의 역할을 수행합니다.
Nest.js에서는 이러한 DTO를 쉽게 작성할 수 있는 클래스 형태로 제공하며,
class-validator와 같은 라이브러리를 사용하여 데이터 유효성 검사를 지원합니다.


파이프 정리


Typeorm의 repository 패턴을 적용 (repository 저장소)
 
 리포지토리란 무엇인가요?
리포지토리 또는 리포는 개발자가 애플리케이션 소스 코드에 대한 변경을 수행 및 관리하는 데 사용하는 중앙화된 디지털 스토리지입니다. 개발자는 소프트웨어를 개발할 때 폴더, 텍스트 파일 밑 기타 유형의 문서를 저장 및 공유해야 합니다. 리포는 개발자가 쉽게 코드 변경 사항을 추적하고, 파일을 동시에 편집하고 어디에서든 동일한 프로젝트에서 효율적인 협업을 수행할 수 있게 해 주는 기능을 갖추고 있습니다. 