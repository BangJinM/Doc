### ssh框架上传文件问题
1.Write operations are not allowed in read-only mode (FlushMode.NEVER) turn your Session into FlushMode.AUTO or remove 'readOnly' marker from transaction definition
	解决方案：
``` java
//在方法前加入注释
@Transactional
	@Override
	public void saveVideo(Video video) {
		// TODO Auto-generated method stub
		
		getHibernateTemplate().getSessionFactory().getCurrentSession().setFlushMode(FlushMode.AUTO);
		this.getHibernateTemplate().save(video);
	}
</filter>
<filter-mapping>
     <filter-name>OpenSessionInViewFilter</filter-name>
     <url-pattern>/*</url-pattern>
</filter-mapping>
```
2.但之后又出现了Unable to find ‘struts.multipart.saveDir’
``` java
	//在struts中配置
    <constant name="struts.multipart.saveDir" value="/temp"></constant>
```
3.之后又出现 Could not obtain transaction-synchronized Session for current thread
```JAVA
https://wenku.baidu.com/view/912d9a370b4c2e3f57276336.html
```