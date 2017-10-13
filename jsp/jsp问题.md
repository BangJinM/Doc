# jsp问题
1.$$_javassist_0 cannot be cast to javassist.util.proxy.Proxy
	导入的包中包含了两个javassist.jar，只需要将低版本的删除即可
2.Unknown entity: java.lang.Boolean; nested exception is org.hibernate.MappingException: Unknown entity: java.lang.Boolean
	类型不匹配