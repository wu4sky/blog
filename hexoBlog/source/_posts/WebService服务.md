---
title: WebService服务
tags: WebService方案
categories: Java开发
description: 一个完整的基于JAX-WS的Web服务
indexing: true
hide: false
date: 2025-03-11 14:49:28
updated: 2025-03-11 14:49:28##
---



## WebService服务

### 本地的请求路径 ： http://localhost:8080/webservice

-------------------------------------------------- applicationContext.xml 配置 ---------------------------------------------

~~~xml
<jaxws:endpoint id="InspectionReportInfoByT100ServiceImpl" implementor="com.ambition.custom.webservice.service.impl.InspectionReportInfoByT100ServiceImpl"
					address="/saveInspectionReportInfo">
		<jaxws:inInterceptors>
			<bean class="org.apache.cxf.interceptor.LoggingInInterceptor"></bean>
			<bean class="com.ambition.webservice.logging.ErrorInterceptor"></bean>
		</jaxws:inInterceptors>
		<jaxws:outInterceptors>
			<bean class="org.apache.cxf.interceptor.LoggingInInterceptor"></bean>
			<bean class="com.ambition.webservice.logging.ErrorInterceptor"></bean>
		</jaxws:outInterceptors>
	</jaxws:endpoint>
~~~


InspectionReportInfoByT100ServiceImpl   Web服务端点，指定了它的实现类、访问地址以及入站和出站的拦截器

id="InspectionReportInfoByT100ServiceImpl": 这是该端点的唯一标识符。

implementor="com.ambition.custom.webservice.service.impl.InspectionReportInfoByT100ServiceImpl": 指定了实现该Web服务的Java类，即InspectionReportInfoByT100ServiceImpl类。

address="/saveInspectionReportInfo": 指定了该Web服务的访问地址。客户端可以通过这个地址来调用该服务

<jaxws:inInterceptors> 标签:这个标签用于定义在请求到达Web服务之前执行的拦截器。这是一个日志记录拦截器，用于记录进入的请求信息

<jaxws:outInterceptors> 标签:这个标签用于定义在响应发送给客户端之前执行的拦截器

------------------------------------------------ Java 代码实现 ---------------------------------------------------------------

#### 1.服务接口 (InspectionReportInfoByT100Service)

~~~java
package com.ambition.custom.webservice.service;

import javax.jws.WebService;

@WebService
public interface InspectionReportInfoByT100Service {
    String saveInspectionReportInfo(String reportInfo);
}
~~~

saveInspectionReportInfo 是服务方法，接收一个字符串参数并返回一个字符串。

#### 其他的版本方式

~~~java
@WebService
public interface InspectionReportInfoByT100Service {

    @WebResult(name="return", targetNamespace = "http://localhost:8080/")
    public abstract WebserviceResult saveInspectionReportInfo(@WebParam(name="inspectionReportInfo") InspectionReportInfoJk inspectionReportInfo);
}
~~~

#### **`@WebResult` 注解**

显式指定Web服务方法的返回值在SOAP消息中的名称和命名空间

区别：

- 如果不使用`@WebResult`，默认返回值在SOAP消息中的名称为`return`，命名空间为服务的默认命名空间。
- 使用`@WebResult`可以自定义返回值的名称和命名空间，使SOAP消息更符合特定需求或规范。



#### **`@WebParam` 注解**

显式指定Web服务方法的参数在SOAP消息中的名称

区别：

- 如果不使用`@WebParam`，默认参数在SOAP消息中的名称为`arg0`、`arg1`等。
- 使用`@WebParam`可以自定义参数的名称，使SOAP消息更易读和规范。



#### **`返回类型和参数类型` **

InspectionReportInfoJk  -- ----- 实体

public abstract WebserviceResult saveInspectionReportInfo(InspectionReportInfoJk inspectionReportInfo);

- **返回类型**：`WebserviceResult` 是一个自定义的复杂类型，而不是简单的`String`。
- **参数类型**：`InspectionReportInfoJk` 也是一个自定义的复杂类型，而不是简单的`String`。
- 区别：
  - 使用自定义的复杂类型可以使Web服务的接口更符合实际业务需求。
  - 复杂的返回类型和参数类型会在WSDL中生成更详细的结构定义，方便客户端理解和使用



#### **`targetNamespace`**

targetNamespace = "http://localhost:8080/"

- **作用**：指定Web服务方法的命名空间。
- 区别:
  - 如果不指定`targetNamespace`，默认使用服务接口的命名空间。
  - 显式指定命名空间可以避免潜在的命名冲突，并使WSDL更清晰

#### **与之前示例的区别**

| 特性       | 之前示例     | 当前示例                                   |
| ---------- | ------------ | ------------------------------------------ |
| 返回值类型 | `String`     | `WebserviceResult`（自定义复杂类型）       |
| 参数类型   | `String`     | `InspectionReportInfoJk`（自定义复杂类型） |
| 返回值命名 | 默认`return` | 自定义`return`                             |
| 参数命名   | 默认`arg0`   | 自定义`inspectionReportInfo`               |
| 命名空间   | 默认命名空间 | 显式指定`http://localhost:8080/`           |





#### 2.服务实现类 (InspectionReportInfoByT100ServiceImpl)

##### 一个基于Spring和JAX-WS的Web服务实现类

~~~java
package com.ambition.custom.webservice.service.impl;

import com.ambition.custom.webservice.service.InspectionReportInfoByT100Service;
import javax.jws.WebService;
//【 可以 】
/*@Service
@WebService(endpointInterface = "com.ambition.custom.webservice.service.InspectionReportInfoByT100Service", serviceName = "InspectionReportInfoByT100Service")*/

@WebService(endpointInterface = "com.ambition.custom.webservice.service.InspectionReportInfoByT100Service")
public class InspectionReportInfoByT100ServiceImpl implements InspectionReportInfoByT100Service {

    @Override
    public String saveInspectionReportInfo(String reportInfo) {
        // 具体的业务逻辑
        System.out.println("Received report info: " + reportInfo);
        // 假设这里将报告信息保存到数据库或其他操作
        return "Report info saved successfully!";
    }
}

~~~

####  其他的的版本方式

~~~Java
@Service
@WebService(endpointInterface = "com.ambition.custom.webservice.service.InspectionReportInfoByT100Service", serviceName = "InspectionReportInfoByT100Service")
public class InspectionReportInfoByT100ServiceImpl implements InspectionReportInfoByT100Service {
    @Override
    public synchronized WebserviceResult saveInspectionReportInfo(
            InspectionReportInfoJk inspectionReportInfo) {
        try {
            if (inspectionReportInfo != null) {

                String errorMsg = judgeRequired(inspectionReportInfo);
                WebserviceResult result = new WebserviceResult();
                if (StringUtils.isEmpty(errorMsg)) {
                    result.setMsg(errorMsg);
                    result.setStatus("false");
                    interfaceFileImportService.completTranslate(translateLog, "T100-QMS-saveInspectionReportInfo", TranslateLog.STATUS_失败, errorMsg, null);
                }
                return result;
            }
        } catch (Exception e) {
            logger.error("接收T100系统的报检任务信息失败：" + e.getMessage(), e);
            return WebserviceResult.createNgResult("接收T100系统的报检任务信息失败：" + e.getMessage());
        }
        
    }
    
}
~~~

实现`InspectionReportInfoByT100Service`接口，提供具体的业务逻辑，方法操作，记录保存

- `@Service`
  - 表明这是一个Spring管理的服务类，Spring会自动将其注册为Bean。
- `@WebService`
  - 表明这是一个JAX-WS Web服务实现类。
  - **`endpointInterface`**：指定Web服务的接口类。
  - **`serviceName`**：指定Web服务的名称。

- **`@Override`**：表明这是一个重写接口方法。
- **`synchronized`**：确保方法在多线程环境下是线程安全的





#### 3.自定义拦截器 (ErrorInterceptor)

```Java
package com.ambition.webservice.logging;

import org.apache.cxf.interceptor.Fault;
import org.apache.cxf.message.Message;
import org.apache.cxf.phase.AbstractPhaseInterceptor;
import org.apache.cxf.phase.Phase;

public class ErrorInterceptor extends AbstractPhaseInterceptor<Message> {

    public ErrorInterceptor() {
        super(Phase.PRE_INVOKE); // 在调用服务方法之前执行
    }

    @Override
    public void handleMessage(Message message) throws Fault {
        // 自定义错误处理逻辑
        System.out.println("ErrorInterceptor: Handling potential errors in the request...");
        // 可以在这里检查请求内容、记录日志或抛出异常
    }
}

```




#### 4.日志记录拦截器 (LoggingInInterceptor)

~~~java
package com.ambition.webservice.logging;

import org.apache.cxf.interceptor.LoggingInInterceptor;

public class CustomLoggingInterceptor extends LoggingInInterceptor {
    @Override
    public void handleMessage(Message message) throws Fault {
        // 自定义日志记录逻辑
        System.out.println("CustomLoggingInterceptor: Logging incoming request...");
        super.handleMessage(message); // 调用父类的日志记录逻辑
    }
}
~~~



#### 5.测试客户端 

~~~java
package com.ambition.client;

import com.ambition.custom.webservice.service.InspectionReportInfoByT100Service;
import org.apache.cxf.jaxws.JaxWsProxyFactoryBean;

public class WebServiceClient {
    public static void main(String[] args) {
        JaxWsProxyFactoryBean factory = new JaxWsProxyFactoryBean();
        factory.setServiceClass(InspectionReportInfoByT100Service.class);
      factory.setAddress("http://localhost:8080/services/saveInspectionReportInfo");

        InspectionReportInfoByT100Service client = (InspectionReportInfoByT100Service) factory.create();
        String response = client.saveInspectionReportInfo("Sample Report Info");
        System.out.println("Response from server: " + response);
    }
}
// http://localhost:8080/webservice/saveInspectionReportInfo?wsdl
~~~





#### WSDL（Web Services Description Language）文件，用于描述一个基于SOAP协议的Web服务

```xml
<?xml version="1.0" encoding="utf-8"?>
<wsdl:definitions xmlns:ns1="http://service.webservice.custom.ambition.com/" xmlns:ns2="http://schemas.xmlsoap.org/soap/http" xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/" xmlns:tns="http://impl.service.webservice.custom.ambition.com/" xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" name="InspectionReportInfoByT100Service" targetNamespace="http://impl.service.webservice.custom.ambition.com/">
  <wsdl:import location="http://localhost:8080/webservice/saveInspectionReportInfo?wsdl=InspectionReportInfoByT100Service.wsdl" namespace="http://service.webservice.custom.ambition.com/"> </wsdl:import>
  <wsdl:binding name="InspectionReportInfoByT100ServiceSoapBinding" type="ns1:InspectionReportInfoByT100Service">
    <soap:binding style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
    <wsdl:operation name="saveInspectionReportInfo">
      <soap:operation soapAction="" style="document"/>
      <wsdl:input name="saveInspectionReportInfo">
        <soap:body use="literal"/>
      </wsdl:input>
      <wsdl:output name="saveInspectionReportInfoResponse">
        <soap:body use="literal"/>
      </wsdl:output>
    </wsdl:operation>
  </wsdl:binding>
  <wsdl:service name="InspectionReportInfoByT100Service">
    <wsdl:port binding="tns:InspectionReportInfoByT100ServiceSoapBinding" name="InspectionReportInfoByT100ServiceImplPort">
      <soap:address location="http://localhost:8080/webservice/saveInspectionReportInfo"/>
    </wsdl:port>
  </wsdl:service>
</wsdl:definitions>

```
##### **操作定义**

~~~xml
<wsdl:operation name="saveInspectionReportInfo">
  <soap:operation soapAction="" style="document"/>
  <wsdl:input name="saveInspectionReportInfo">
    <soap:body use="literal"/>
  </wsdl:input>
  <wsdl:output name="saveInspectionReportInfoResponse">
    <soap:body use="literal"/>
  </wsdl:output>
</wsdl:operation>

~~~

- **作用**：定义服务操作及其输入输出消息格式。
- 主要属性
  - `name`：操作的名称（`saveInspectionReportInfo`）。
  - `soapAction`：SOAP操作的标识符（此处为空）。
  - `use="literal"`：表示消息体使用字面量格式



#### 示范的 发送 （未尝试）

~~~xml
<!-- 
假如 请求的url: http://localhost:8080/webservice/saveInspectionReportInfo
-->

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ser="http://service.webservice.custom.ambition.com/">
   <soapenv:Header/>
   <soapenv:Body>
      <ser:saveInspectionReportInfo>
      	<!-- 输入参数 -->
         <ser:reportData>
            <ser:reportId>12345</ser:reportId>
            <ser:reportName>Test Report</ser:reportName>
            <ser:reportDate>2023-10-01</ser:reportDate>
         </ser:reportData>
      </ser:saveInspectionReportInfo>
   </soapenv:Body>
</soapenv:Envelope>

~~~

