# springboot 中使用websocket

### 1.创建WebSocketConfig类，代码如下：

```java
@Configuration
@EnableWebSocketMessageBroker//1
public class WebSocketConfig extends AbstractWebSocketMessageBrokerConfigurer{
    @Override
    public void registerStompEndpoints(StompEndpointRegistry registry) {
        registry.addEndpoint("/endpointWisely").withSockJS(); //2
    }
    @Override
    public void configureMessageBroker(MessageBrokerRegistry registry) {
        registry.enableSimpleBroker("/topic");//3
    }
}

```
(1),@EnableWebSocketMessageBroker注解用于开启使用STOMP协议来传输基于代理（MessageBroker）的消息，这时候控制器（controller）开始支持@MessageMapping,就像是使用@requestMapping一样。

(2),注册一个Stomp的节点（endpoint）,并指定使用SockJS协议。

(3),配置消息代理（MessageBroker）。

### 2.创建WiselyMessage类（浏览器向服务器传送消息，用该类进行接收），代码如下：

```java

public class WiselyMessage {
    private String name;
    public String getName(){
        return name;
    }
}

```

### 3.创建WiselyResponse类（服务器向浏览器传送消息，用该类进行传送），代码如下：

```java

public class WiselyResponse {
    private String responseMessage;
    public WiselyResponse(String responseMessage){
        this.responseMessage = responseMessage;
    }
    public String getResponseMessage(){
        return responseMessage;
    }
}

```

### 4.创建WsController类，代码如下：

```java
@Controller
public class WsController {
    @MessageMapping("/welcome")//1
    @SendTo("/topic/getResponse")//2
    public WiselyResponse say(WiselyMessage message) throws Exception {
        return new WiselyResponse("Welcome, " + message.getName() + "!");
    }
}
```
(1)@MessageMapping和@RequestMapping功能类似，用于设置URL映射地址，浏览器向服务器发起请求，需要通过该地址。

(2)如果服务器接受到了消息，就会对订阅了@SendTo括号中的地址传送消息。

### 5.前端使用

```javascript

var socket = new SockJS('/endpointWisely'); //1
        stompClient = Stomp.over(socket);//2
        stompClient.connect({}, function(frame) {//3
            setConnected(true);
            console.log('开始进行连接Connected: ' + frame);
            stompClient.subscribe('/topic/getResponse', function(respnose){ //4
                showResponse(JSON.parse(respnose.body).responseMessage);
            });
        });

```
（1）连接SockJS的endpoint是“endpointWisely”，与后台代码中注册的endpoint要一样。

（2）创建STOMP协议的webSocket客户端。

（3）连接webSocket的服务端。

（4）通过stompClient.subscribe（）订阅服务器的目标是'/topic/getResponse'发送过来的地址，与@SendTo中的地址对应。

（5）通过stompClient.send（）向地址为"/welcome"的服务器地址发起请求，与@MessageMapping里的地址对应。


