---
title: try catch finally
date:  2021-04-11
toc: true
categories: java
tags: java
---



1. finally块的语句在try或catch中的return语句执行之后,返回之前执行

2. finally里的修改语句可能影响也可能不影响try或catch中 return已经确定的返回值

   若try/catch中 return 基础类型变量a,finally中修改a,对最终return值不影响

   若try/catch中 return 引用类型变量b,finally中修改b,最终return修改后的b

   (原因: Java只有值传递)

3. 若finally里也有return语句则覆盖try或catch中的return语句直接返回

4. 当发生异常后，catch中的return执行情况与未发生异常时try中return的执行情况完全一样

```java
public class FinallyTest1 {

 public static void main(String[] args) {

	System.out.println(test3());
 }

 public static int test3() {
 	int b = 20;

 	try {
        
        System.out.println("try block");
 		return b += 80;
        
    } catch (Exception e) {
        
        System.out.println("catch block");
        
    } finally {

        System.out.println("finally block");

        if (b > 25) {
            System.out.println("b>25, b = " + b);
        }
        b += 150;
    }

    return 2000;

}
//==================
try block
finally block
b>25, b = 100
100
```

```java
public class FinallyTest2 {
 	public static void main(String[] args) {
        System.out.println(getMap().get("KEY").toString());
    }

    public static Map getMap() {
        Map map = new HashMap();
        map.put("KEY", "INIT");

        try {
            map.put("KEY", "TRY");
            return map;
        }
        catch (Exception e) {
            map.put("KEY", "CATCH");
        }
        finally {
            map.put("KEY", "FINALLY");
            map = null;  //Java中只有值传递,通过引用可改变内容,引用指向变更对旧引用无影响
        }

        return map;
    }

}
//========
FINALLY
```

```java
public class FinallyTest3 {

 public static void main(String[] args) {

	System.out.println(test3());
 }

 public static int test3() {
 	int b = 20;

 	try {
        
        System.out.println("try block");
 		b += 80;
        
    } catch (Exception e) {
        
        System.out.println("catch block");
        
    } finally {

        System.out.println("finally block");

        if (b > 25) {
            System.out.println("b>25, b = " + b);
        }
        b += 150;
    }

    return b;

}
//==================
try block
finally block
b>25, b = 100
250
```

