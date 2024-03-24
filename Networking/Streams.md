- Writing to files is not different to writing Bytes. 
- Streams are Synchronous (waits for Data to be read or written first)
- Input streams read data; output streams write data
```java
InputStreamReader isr = new InputStreameader(c.getInputStream());
OutputStream clOutputStream = client.getOutputStream();
```

 - Always flush before closing Stream to ensure data is sent even if the Buffer isn't full.
 - A single write of many bytes is almost always much faster than many small writes that add up to the same thing