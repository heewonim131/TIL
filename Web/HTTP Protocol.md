## HTTP (HyperText Transfer Protocol)
HTTP는 메시지를 주고(Request) 받는(Response) 형태의 통신 방법이다.<br>
TCP를 기반으로 한 REST의 특징을 모두 구현하고 있는 Web 기반의 프로토콜이다.<br>
HTML, SML, JSON, IMAGE, PDF 등 컴퓨터에서 다룰 수 있는 것은 모두 전송할 수 있다.

![image](https://user-images.githubusercontent.com/92259017/150667697-f9d5df1b-c4e0-41f6-9874-c4a970da5be0.png)

## HTTP Method
HTTP의 요청을 특정하는 8가지 Method가 존재한다.<br>
REST를 구현하기 위한 인터페이스 이니 알아둬야 한다.

![image](https://user-images.githubusercontent.com/92259017/150667760-91f1f729-2ad7-463d-b88f-b933ac34e4ac.png)

## GET
- **RestController** : REST API 설정<br>
**RequestMapping** : 리소스 설정<br>
![image](https://user-images.githubusercontent.com/92259017/150681370-19271968-1466-47cc-8c05-ec42eb3d59fd.png)

- **GetMapping** : Get 리소스 설정<br>
**RequestMapping** : method = Get 리소스 설정<br>
![image](https://user-images.githubusercontent.com/92259017/150681388-1101c2cc-8c49-40e3-8701-91a60d1e7211.png)

- **PathVariable** : URL Path Variable Parsing<br>
![image](https://user-images.githubusercontent.com/92259017/150680745-5012806a-01b3-485c-b2ce-443ceea3db61.png)

- **RequestParam** : URL Query Parameter Parsing<br>
![image](https://user-images.githubusercontent.com/92259017/150680979-03b9e4a8-f86d-41d2-9c71-3be92c31658c.png)

  dto를 생성하여 필드를 정의하고 dto 객체를 받는 방법을 많이 사용한다.<br>
  (@RequestParam 어노테이션은 붙이지 않는다.)<br>
  ![image](https://user-images.githubusercontent.com/92259017/150681209-f9ddf851-6b9a-4428-87bf-f06832f6bb43.png)

## POST
- **RestController** : REST API 설정<br>
**RequestMapping** : 리소스 설정<br>
![image](https://user-images.githubusercontent.com/92259017/150681834-30a6e72b-e8ab-4015-a6f1-cdac250b67bb.png)

- **PostMapping** : POST 리소스 설정<br>
![image](https://user-images.githubusercontent.com/92259017/150681889-6fd5c71c-9fe9-45e9-be4d-1d15a084a8e3.png)

- **RequestBody** : Request Body 부분 Parsing<br>
dto를 생성하여 필드를 정의하고 dto 객체를 받는다.<br>
![image](https://user-images.githubusercontent.com/92259017/150682001-63a187c7-7fc1-4692-b453-815955b571b8.png)

- **JsonProperty** : json naming<br>
![image](https://user-images.githubusercontent.com/92259017/150682217-125929cf-63b2-4b43-a14e-b5c344101fac.png)

- **JsonNaming** : class json naming
- **PathVariable** : URL Path Variable Parsing

## PUT
- **RestController** : REST API 설정<br>
**RequestMapping** : 리소스 설정<br>
![image](https://user-images.githubusercontent.com/92259017/150683667-02673ecf-9ce8-48b6-a8f7-0ad36470e28c.png)

- **PutMapping** : PUT 리소스 설정<br>
**RequestBody** : Request Body 부분 Parsing<br>
**PathVariable** : URL Path Variable Parsing<br>
![image](https://user-images.githubusercontent.com/92259017/150683802-fcb2c237-82ec-4ebe-b73a-81bde913371a.png)

  JsonNaming : dto에 class json naming<br>
  ![image](https://user-images.githubusercontent.com/92259017/150683734-5ff88d00-2748-4840-ab6b-009533f8646f.png)

## DELETE
- **RestController** : REST API 설정<br>
**RequestMapping** : 리소스 설정<br>
![image](https://user-images.githubusercontent.com/92259017/150683876-4e18cb1b-7e2b-4763-a4d6-254f2d4fdbdf.png)

- **DeleteMapping** : DELETE 리소스 설정<br>
**RequestParam** : URL Query Parameter Parsing<br>
**PathVariable** : URL Path Variable Parsing<br>
![image](https://user-images.githubusercontent.com/92259017/150683990-68348b8c-766d-4ea9-b233-5f13d645cbd9.png)

## HTTP Status Code
응답의 상태를 나타내는 코드

![image](https://user-images.githubusercontent.com/92259017/150667781-a092f429-41cf-4b21-90fe-ed1327202d40.png)

자주 사용되는 코드

![image](https://user-images.githubusercontent.com/92259017/150667785-da99a48c-c45c-4961-b3ba-697f8b2b62fd.png)

## Response 내려주기
![image](https://user-images.githubusercontent.com/92259017/150680654-e36b74cb-345b-4ce3-bfcf-6b3b6560b912.png)
