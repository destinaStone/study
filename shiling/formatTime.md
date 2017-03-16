# Java时间格式转换

```java
   <1> private static final String COMMON_DATE_TIME = "yyyy-MM-dd HH:mm:ss:SSS";
   <2> SimpleDateFormat m_oSimpleDateFormat = new SimpleDateFormat(COMMON_DATE_TIME);
   <3> String strCurrentTime = m_oSimpleDateFormat.format(System.currentTimeMillis());
```
