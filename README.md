# SAPUI5 Tutorial

**※ Chrome 설치 필요**

---
### 1. SCP(SAP Cloud Platform) TRIAL 접속 및 가입
* https://account.hanatrial.ondemand.com/
* 네오(NEO) 평가판으로 접속

---
### 2. SAP WEB IDE 실행
* 서비스 → SAP Web IDE 전체 스택(Full Stack) → 서비스로 이동

---
### 3. 프로젝트 생성 ([Ex01](https://github.com/knotting/sapui5-tutorial/raw/master/Ex01.zip))
* Workspace 우클릭 → New → Project from Template
* SAPUI5 Application 선택 → Next
* Project Name: Ex01, Namespace: ns 입력 → Next → Finish

---
### 4. Hello, World! ([Ex01](https://github.com/knotting/sapui5-tutorial/raw/master/Ex01.zip))
* View1.view.xml 파일의 <content></content> 안에 라벨 작성
    ```xml
    <content><Label text="Hello, World!"/></content>
    ```

---
### 5. App Overview
![App Overview](https://sapui5.hana.ondemand.com/docs/topics/loioeeae30fe7983476a9777e809a8820147_LowRes.png)

---
### 6. Model View Controller (MVC) Concept
![MVC](https://sapui5.hana.ondemand.com/docs/topics/loio1eb216151b1b41f1979b7b6c969670df_LowRes.png)
* Models
    * Client-Side
        * JSON
        * XML
        * Resource
    * Server-Side
        * OData V2
        * OData V4 (limited feature scope)
* Views
    * XML View
    * JSON View
    * JavaScript View
    * HTML View
* Controllers
    * JavaScript

---
### 7. SAPUI5 UI Control ([Ex01](https://github.com/knotting/sapui5-tutorial/raw/master/Ex01.zip))
* Label, Input, Button 생성 (View1.view.xml)
    ```xml
    <Page id="page" title="Ex01 - XML View">
        <content>
        <Label id="lblFirstName" text="First Name:"/>
        <Input id="inpFirstName"/>
        <Label id="lblLastName" text="Last Name:"/>
        <Input id="inpLastName"/>
        <Button id="btnSubmit" text="Submit" press="onBtnClick"/>
        </content>
    </Page>
    ```
* Controller 연동
    * "sap/m/MessageBox" define 추가
    * MessageBox Function Parameter 추가
    * onBtnClick 이벤트 추가
        ```javascript
        onBtnClick: function () {
            var firstName = this.byId("inpFirstName").getValue();
            var lastName = this.byId("inpLastName").getValue();
            var message = "First Name: " + firstName + "\n" + "Last Name: " + lastName;
            MessageBox.show(message, {
            icon: MessageBox.Icon.SUCCESS,
            title: "Button Pressed",
            actions: MessageBox.Action.CLOSE
            });
        }
        ```
* Code Assist
    * Code Completion: Ctrl + Space
    * Beautifier: Ctrl + Alt + B
    * Commented: Ctrl + /, Ctrl + Shift + /

---
### 8. Different View Types
* 예제 프로젝트 ([Ex02](https://github.com/knotting/sapui5-tutorial/raw/master/Ex02.zip)) Import
    * Workspace 우클릭 → Import → File or Project
    * Browse... → Ex02.zip 선택 → OK
* index.html 의 설정 변경 (viewName, type)
    ```html
    <script>
        sap.ui.getCore().attachInit(function() {
        new sap.m.Shell({
            app: new sap.ui.view({id:"idView1", viewName:"ns.Ex02.view.View1", 
                                height:"100%",
                                type:sap.ui.core.mvc.ViewType.XML})
        }).placeAt("content");
        });
    </script>
    ```

---
### 9. Debugging
* Chrome Developer Tools
    * Ctrl + Shift + I (in Chrome)
    * F12 (in Chrome)
* UI5 Inspector
    * Chrome 웹 스토어
        * https://chrome.google.com/webstore/category/extensions?hl=ko

---
### 10. Documentation
* SAPUI5
    * https://sapui5.hana.ondemand.com
* OPENUI5
    * https://openui5.hana.ondemand.com

---
### 11. Using Layouts
* 예제 프로젝트 ([Ex03](https://github.com/knotting/sapui5-tutorial/raw/master/Ex03.zip)) Import
    * Workspace 우클릭 → Import → File or Project
    * Browse... → Ex03.zip 선택 → OK
* Commented Source 확인
    * View1.view.xml
    * View1.controller.js

---
### 12. Data Handling
1. Property Binding
    * 예제 프로젝트 ([Ex04](https://github.com/knotting/sapui5-tutorial/raw/master/Ex04.zip)) Import
        * Workspace 우클릭 → Import → File or Project
        * Browse... → Ex04.zip 선택 → OK
    * Commented Source 확인
        * View1.view.xml
        * View1.controller.js
2. Aggregation Binding
    * 예제 프로젝트 ([Ex05](https://github.com/knotting/sapui5-tutorial/raw/master/Ex05.zip)) Import
        * Workspace 우클릭 → Import → File or Project
        * Browse... → Ex05.zip 선택 → OK
    * Commented Source 확인
        * View1.view.xml
        * View1.controller.js
3. Using OData
    * 예제 프로젝트 ([Ex06](https://github.com/knotting/sapui5-tutorial/raw/master/Ex06.zip)) Import
        * Workspace 우클릭 → Import → File or Project
        * Browse... → Ex06.zip 선택 → OK
    * Destination 설정
        * SCP Cockpit → 연결 → 대상
        * 신규 대상 생성
            * 이름: Northwinds
            * 내역: Northwinds OData Service
            * URL: http://services.odata.org
            * 추가 속성
                * WebIDEEnabled: true
                * WebIDESystem: Northwinds
                * WebIDEUsage: odata_gen
        * neo-app.json 설정 확인
    * Commented Source 확인
        * View1.view.xml
        * View1.controller.js

---
