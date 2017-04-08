---
title: "Use polymorphism!"
tags: [java]
---

A while ago, I wrote code with long `if else` statements due to an user interaction on a web modeller that created some new objects on the backend. Like this you were able to model some IT infrastructure with its componets such as _swiches_, _routers_, _firewalls_, ect. 

On the server side, we got a request with a parameter of which device should be created, therefore certain attributs had to be set. We ended up with below solution: 

{% highlight java %}
DeviceEntity device;

if ("server".equals(request.getParam("device"))) {
  device = new ServerEntity();
} else if ("switch".equals(request.getParam("device"))) {
  device = new SwitchEntity();
} else if ("router".equals(request.getParam("device"))) {
  device = new RouterEntity();
} else if ("firewall".equals(request.getParam("device"))) {
  device = new FirewallEntity();
} else if ("pc".equals(request.getParam("device"))) {
  device = new PcEntity();
} else {
  device = null;
}
{% endhighlight %}

This had to be improved! So I refactored this by using a map that held objects with all the necessary information:

{% highlight java %}
Map<String, DeviceUi> devices = new HashMap<String, DeviceUi>();
devices.put("firewall", new FirewallUi());
devices.put("router", new RouterUi());
devices.put("switch", new SwitchUi());
devices.put("server", new ServerUi());
devices.put("pc", new PcUi());

... 

String requestedDevice = request.getParam("device");
DeviceEntity device = devices.get(requestedDevice).createEntity();
{% endhighlight %}

But this version was still too static. If you created a new device, you also had to add it to the map manually. So we came up with the solution of using the spring `@Component`. 

{% highlight java %}
@Configuration
@ComponentScan(basePackages = {"polymorphism.uiobject"})
public class UiDevicesConfig {
	
  @Autowired
  private Map<String, DeviceUi> devices;
	
  @Bean("uidevices")
  public Map<String, DeviceUi> getAllUiDevices() {
    return devices;
  }
}
{% endhighlight %}

Spring injects dynamically all the `DeviceUi` objects into the map so you can use it as follows:

{% highlight java %}
ApplicationContext context = new AnnotationConfigApplicationContext(UiDevicesConfig.class);

...

Map<String, DeviceUi> devices = context.getBean("uidevices", HashMap.class);
DeviceEntity device = devices.get(request.getParam("device")).createEntity();
{% endhighlight %}

