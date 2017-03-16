# 学习下载文件,推送文件回前台

```java
public static ResponseEntity<byte[]> responseFile(String strFilePath)
        throws IOException
    {
        if (null == strFilePath || strFilePath.isEmpty())
        {
            return null;
        }

        File oFile = new File(strFilePath);
        if (!oFile.exists())
        {
            return null;
        }

        HttpHeaders headers = new HttpHeaders();
        headers.setContentType(MediaType.APPLICATION_OCTET_STREAM);

        // 回复的文件名支持中文
        headers.setContentDispositionFormData("attachment",
            new String(oFile.getName().getBytes("utf-8"), "ISO8859-1"));
        return new ResponseEntity<byte[]>(FileUtils.readFileToByteArray(oFile),
            headers, HttpStatus.OK);
    }
    
    ```
