# Liferay 7.4 DXP

Liferay DXP 7.4 running on docker compose.

## Requirements

* Docker and Docker Compose (CE edition) - version 24.0.2

## Start the environment

```
docker compose up --build -d
```

## Get logs:

```
docker compose logs -f liferay
```

## Access

Access http://localhost:8080/ and login with [USER] and [PASSWORD]

## Simulate the Error

Starts the portal:

```
docker compose up --build -d
```

Access gogo shell using `telnet localhost 11311` 

List the captcha modules from gogo shell: `scr:list | grep -i captcha`

The result should be something like bellow:
```
com.liferay.captcha.taglib.internal.struts.GetCaptchaImageStrutsAction in bundle 1,360 (com.liferay.captcha.taglib:5.1.11) enabled, 1 instance.
com.liferay.captcha.internal.upgrade.registry.CaptchaUpgradeStepRegistrator in bundle 338 (com.liferay.captcha.impl:4.0.16) enabled, 1 instance.
com.liferay.dynamic.data.mapping.form.field.type.internal.captcha.CaptchaDDMFormFieldType in bundle 1,130 (com.liferay.dynamic.data.mapping.form.field.type:6.0.186) enabled, 1 instance.
com.liferay.captcha.rest.internal.resource.v1_0.CaptchaResourceImpl in bundle 557 (com.liferay.captcha.rest.impl:1.0.13) enabled, 1 instance.
com.liferay.captcha.internal.configuration.persistence.listener.CaptchaConfigurationModelListener in bundle 338 (com.liferay.captcha.impl:4.0.16) enabled, 1 instance.
com.liferay.captcha.internal.provider.CaptchaProviderImpl in bundle 338 (com.liferay.captcha.impl:4.0.16) enabled, 1 instance.
com.liferay.captcha.recaptcha.ReCaptchaImpl in bundle 1,198 (com.liferay.captcha.api:7.0.0) enabled, 1 instance.
com.liferay.headless.admin.user.internal.jaxrs.exception.mapper.CaptchaExceptionMapper in bundle 423 (com.liferay.headless.admin.user.impl:5.0.133) enabled, 1 instance.
com.liferay.flags.web.internal.portlet.action.GetCaptchaMVCResourceCommand in bundle 754 (com.liferay.flags.web:6.0.23) enabled, 1 instance.
com.liferay.captcha.simplecaptcha.SimpleCaptchaImpl in bundle 1,198 (com.liferay.captcha.api:7.0.0) enabled, 1 instance.
com.liferay.captcha.rest.internal.jaxrs.exception.mapper.CaptchaTextExceptionMapper in bundle 557 (com.liferay.captcha.rest.impl:1.0.13) enabled, 1 instance.
com.liferay.captcha.rest.internal.resource.v1_0.factory.CaptchaResourceFactoryImpl in bundle 557 (com.liferay.captcha.rest.impl:1.0.13) enabled, 1 instance.
com.liferay.captcha.internal.configuration.settings.CaptchaSettingsImpl in bundle 338 (com.liferay.captcha.impl:4.0.16) enabled, 1 instance.
com.liferay.captcha.rest.internal.jaxrs.application.CaptchaRESTApplication in bundle 557 (com.liferay.captcha.rest.impl:1.0.13) enabled, 1 instance.
com.liferay.captcha.taglib.internal.auth.publicpath.AuthPublicPath in bundle 1,360 (com.liferay.captcha.taglib:5.1.11) enabled, 1 instance.
com.liferay.dynamic.data.mapping.form.field.type.internal.captcha.CaptchaDDMFormFieldTemplateContextContributor in bundle 1,130 (com.liferay.dynamic.data.mapping.form.field.type:6.0.186) enabled, 1 instance.
com.liferay.captcha.rest.internal.security.service.access.policy.CaptchaSAPEntryPortalInstanceLifecycleListener in bundle 557 (com.liferay.captcha.rest.impl:1.0.13) enabled, 1 instance.
com.liferay.configuration.admin.web.internal.category.CaptchaConfigurationCategory in bundle 451 (com.liferay.configuration.admin.web:5.0.91) enabled, 1 instance.
com.liferay.captcha.rest.internal.resource.v1_0.OpenAPIResourceImpl in bundle 557 (com.liferay.captcha.rest.impl:1.0.13) enabled, 1 instance.
```

Access http://localhost:8080/, and go to **Control Panel -> System Settings -> Security Tools -> CAPTCHA** and click in the "UPDATE" button at the end of the page.

Go back to gogo shell and execute `scr:list | grep -i captcha` again, the result should be something like:

```
com.liferay.captcha.taglib.internal.struts.GetCaptchaImageStrutsAction in bundle 1,360 (com.liferay.captcha.taglib:5.1.11) enabled, 1 instance.
com.liferay.captcha.internal.upgrade.registry.CaptchaUpgradeStepRegistrator in bundle 338 (com.liferay.captcha.impl:4.0.16) enabled, 1 instance.
com.liferay.dynamic.data.mapping.form.field.type.internal.captcha.CaptchaDDMFormFieldType in bundle 1,130 (com.liferay.dynamic.data.mapping.form.field.type:6.0.186) enabled, 1 instance.
com.liferay.captcha.rest.internal.resource.v1_0.CaptchaResourceImpl in bundle 557 (com.liferay.captcha.rest.impl:1.0.13) enabled, 1 instance.
com.liferay.captcha.internal.configuration.persistence.listener.CaptchaConfigurationModelListener in bundle 338 (com.liferay.captcha.impl:4.0.16) enabled, 1 instance.
com.liferay.captcha.internal.provider.CaptchaProviderImpl in bundle 338 (com.liferay.captcha.impl:4.0.16) enabled, 1 instance.
    Id: 1526, State:SATISFIED, PID(s): [com.liferay.captcha.configuration.CaptchaConfiguration]
com.liferay.captcha.recaptcha.ReCaptchaImpl in bundle 1,198 (com.liferay.captcha.api:7.0.0) enabled, 1 instance.
    Id: 5916, State:SATISFIED, PID(s): [com.liferay.captcha.configuration.CaptchaConfiguration]
com.liferay.headless.admin.user.internal.jaxrs.exception.mapper.CaptchaExceptionMapper in bundle 423 (com.liferay.headless.admin.user.impl:5.0.133) enabled, 1 instance.
com.liferay.flags.web.internal.portlet.action.GetCaptchaMVCResourceCommand in bundle 754 (com.liferay.flags.web:6.0.23) enabled, 1 instance.
com.liferay.captcha.simplecaptcha.SimpleCaptchaImpl in bundle 1,198 (com.liferay.captcha.api:7.0.0) enabled, 1 instance.
    Id: 5917, State:SATISFIED, PID(s): [com.liferay.captcha.configuration.CaptchaConfiguration]
com.liferay.captcha.rest.internal.jaxrs.exception.mapper.CaptchaTextExceptionMapper in bundle 557 (com.liferay.captcha.rest.impl:1.0.13) enabled, 1 instance.
com.liferay.captcha.rest.internal.resource.v1_0.factory.CaptchaResourceFactoryImpl in bundle 557 (com.liferay.captcha.rest.impl:1.0.13) enabled, 1 instance.
com.liferay.captcha.internal.configuration.settings.CaptchaSettingsImpl in bundle 338 (com.liferay.captcha.impl:4.0.16) enabled, 1 instance.
    Id: 1525, State:ACTIVE, PID(s): [com.liferay.captcha.configuration.CaptchaConfiguration]
com.liferay.captcha.rest.internal.jaxrs.application.CaptchaRESTApplication in bundle 557 (com.liferay.captcha.rest.impl:1.0.13) enabled, 1 instance.
com.liferay.captcha.taglib.internal.auth.publicpath.AuthPublicPath in bundle 1,360 (com.liferay.captcha.taglib:5.1.11) enabled, 1 instance.
com.liferay.dynamic.data.mapping.form.field.type.internal.captcha.CaptchaDDMFormFieldTemplateContextContributor in bundle 1,130 (com.liferay.dynamic.data.mapping.form.field.type:6.0.186) enabled, 1 instance.
com.liferay.captcha.rest.internal.security.service.access.policy.CaptchaSAPEntryPortalInstanceLifecycleListener in bundle 557 (com.liferay.captcha.rest.impl:1.0.13) enabled, 1 instance.
com.liferay.configuration.admin.web.internal.category.CaptchaConfigurationCategory in bundle 451 (com.liferay.configuration.admin.web:5.0.91) enabled, 1 instance.
com.liferay.captcha.rest.internal.resource.v1_0.OpenAPIResourceImpl in bundle 557 (com.liferay.captcha.rest.impl:1.0.13) enabled, 1 instance.
```

Notice new configuration were added:

```
Id: 1526, State:SATISFIED, PID(s): [com.liferay.captcha.configuration.CaptchaConfiguration]
Id: 5916, State:SATISFIED, PID(s): [com.liferay.captcha.configuration.CaptchaConfiguration]
Id: 5917, State:SATISFIED, PID(s): [com.liferay.captcha.configuration.CaptchaConfiguration]
Id: 1525, State:ACTIVE, PID(s): [com.liferay.captcha.configuration.CaptchaConfiguration]
```

Stops the Liferay service:

```
docker compose down liferay
```

Access the database service and show the configurations for captcha:

```
select * from configuration_ c where configurationId like '%captcha%';
```

It would return one record, check the value of the field dictionary, you will notice that there is a key like: `captchaEngine="com.liferay.captcha.simplecaptcha.SimpleCaptchaImpl"`, just change this value to something invalid, like: `captchaEngine="com.liferay.captcha.simplecaptcha.SimpleCaptchaImplNotExists"`, save the record.

Starts liferay again:

```
docker compose up -d
```

Access the portal again http://localhost:8080, go to **Control Panel -> Server Administration**, the page will not render, check the logs using `docker compose logs -f liferay` and you are going to see in the log:

```
2026-03-11 12:58:33.644 ERROR [http-nio-8080-exec-6][render_portlet_jsp:122] Cannot invoke "com.liferay.portal.kernel.captcha.Captcha.enforceCaptcha(javax.portlet.PortletRequest)" because the return value of "com.liferay.captcha.util.CaptchaUtil.getCaptcha()" is null
java.lang.NullPointerException: Cannot invoke "com.liferay.portal.kernel.captcha.Captcha.enforceCaptcha(javax.portlet.PortletRequest)" because the return value of "com.liferay.captcha.util.CaptchaUtil.getCaptcha()" is null
	at com.liferay.captcha.util.CaptchaUtil.enforceCaptcha(CaptchaUtil.java:43) ~[?:?]
	at org.apache.jsp.view_jsp._jspService(view_jsp.java:432) ~[?:?]
	at org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:67) ~[jasper.jar:9.0.112]
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:623) ~[servlet-api.jar:4.0.FR]
	at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:466) ~[jasper.jar:9.0.112]
	at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:376) ~[jasper.jar:9.0.112]
	at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:324) ~[jasper.jar:9.0.112]
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:623) ~[servlet-api.jar:4.0.FR]
	at com.liferay.portal.osgi.web.servlet.jsp.compiler.internal.JspServlet.service(JspServlet.java:323) ~[?:?]
	at com.liferay.portal.osgi.web.servlet.jsp.compiler.internal.JspServlet.service(JspServlet.java:332) ~[?:?]
	at org.eclipse.equinox.http.servlet.internal.registration.EndpointRegistration.service(EndpointRegistration.java:147) ~[?:?]
	at org.eclipse.equinox.http.servlet.internal.servlet.ResponseStateHandler.processRequest(ResponseStateHandler.java:63) ~[?:?]
	at org.eclipse.equinox.http.servlet.internal.context.DispatchTargets.doDispatch(DispatchTargets.java:120) ~[?:?]
	at org.eclipse.equinox.http.servlet.internal.servlet.RequestDispatcherAdaptor.include(RequestDispatcherAdaptor.java:48) ~[?:?]
	at com.liferay.portlet.internal.PortletRequestDispatcherImpl.dispatch(PortletRequestDispatcherImpl.java:282) ~[portal-impl.jar:?]
	at com.liferay.portlet.internal.PortletRequestDispatcherImpl.include(PortletRequestDispatcherImpl.java:114) ~[portal-impl.jar:?]
	at com.liferay.portal.kernel.portlet.bridges.mvc.MVCPortlet.include(MVCPortlet.java:611) ~[portal-kernel.jar:?]
	at com.liferay.portal.kernel.portlet.bridges.mvc.MVCPortlet.include(MVCPortlet.java:627) ~[portal-kernel.jar:?]
	at com.liferay.portal.kernel.portlet.bridges.mvc.MVCPortlet.doDispatch(MVCPortlet.java:497) ~[portal-kernel.jar:?]
	at javax.portlet.GenericPortlet.render(GenericPortlet.java:291) ~[portlet.jar:3.0.1]
```

### Fix the error

Stops the portal:

```
docker compose down liferay
```

Connect to the database and removes the captcha configuration:

```
delete from configuration_ c where configurationId like '%captcha%';
```

Starts the portal again:

```
docker compose up -d
```

Go to gogo shell and checks that the specific configurations doesn't exists anymore:

```
telnet localhost 11311
scr:list | grep -i captcha
```

Access http://localhost:8080 and go to **Control Panel -> Server Administation**, you will see that the page and captcha are rendering without errors.
