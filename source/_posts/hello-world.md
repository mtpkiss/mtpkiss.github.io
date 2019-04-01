---
title: Hello World
date: 2017-12-05 09:30:55
categories: java
tags:
  - java
---

```java
import java.util.*;

public class HelloWorld{

  public static String randomString(int i)
  {
      Random ran = new Random(i);
      StringBuilder sb = new StringBuilder();
      for (int n = 0; ; n++)
      {
          int k = ran.nextInt(27);
          if (k == 0)
              break;

          sb.append((char)('`' + k));
      }

      return sb.toString();
  }

  public static void main(String[] args){
      System.out.println(randomString(-229985452)+" "+randomString(-147909649));
  }

}
```
