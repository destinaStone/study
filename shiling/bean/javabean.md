### spring声明bean的注解

> @Component组件，没有明确的角色
> @Service在业务逻辑层service层使用
> @Controller在mvc控制层使用
> @Repository在Dao层使用

  添加以上的注解的类，是spring的一个bean，在启动时被加载；
 
 ### spring 依赖注入
 
 spring IOC容器ApplicationContext负责bean的创建；
 
 例如：
 
 ```java
@Component
public class IppsWebScoketUtils
{
    private SimpMessagingTemplate simpMessagingTemplate;

    @Autowired
    public IppsWebScoketUtils(SimpMessagingTemplate oSimpMessagingTemplate)
    {
        this.simpMessagingTemplate = oSimpMessagingTemplate;
    }

    public void sendWs(String strTopic, String strDestinationPath,
                       WsMessageVo wsMessageVo)
    {

        this.simpMessagingTemplate.convertAndSend("/topic/bbit", wsMessageVo);

    }

    public void sendWs4User(String topic, String destinalpath,
                            WsMessageVo wsMessageVo)
    {
        this.simpMessagingTemplate.convertAndSendToUser(topic, destinalpath,
            wsMessageVo);
    }

}
 
 ```
 
 (1)通过注解@Component来声明IppsWebScoketUtils是spring的一个bean;
 (2)通过 @Autowired注解将SimpMessagingTemplate的一个实例给注入到了IppsWebScoketUtils中，这样就可以使用SimpMessagingTemplate的功能
 
 ### 配置类
 
 （1）@Configuration声明当前类是配置类；
 （2）@ComponentScan（“xx”）,自动扫描“xx”目录下的所有的的java文件添加了@Component,@Service,@Controller,@Repository的类为spring的bean;
