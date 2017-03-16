#Java时间格式转换
```
private static final String COMMON_DATE_TIME = "yyyy-MM-dd HH:mm:ss:SSS";
SimpleDateFormat m_oSimpleDateFormat = new SimpleDateFormat(COMMON_DATE_TIME);
String strCurrentTime = m_oSimpleDateFormat.format(System.currentTimeMillis());
```
