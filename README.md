# Guava: Google Core Libraries for Java

[![Latest release](https://img.shields.io/github/release/google/guava.svg)](https://github.com/google/guava/releases/latest)
[![Build Status](https://travis-ci.org/google/guava.svg?branch=master)](https://travis-ci.org/google/guava)

Guava is a set of core libraries that includes new collection types (such as
multimap and multiset), immutable collections, a graph library, and utilities
for concurrency, I/O, hashing, primitives, strings, and more!

Guava comes in two flavors.

*   The JRE flavor requires JDK 1.8 or higher.
*   If you need support for JDK 1.7 or Android, use the Android flavor. You can
    find the Android Guava source in the [`android` directory].

[`android` directory]: https://github.com/google/guava/tree/master/android

## Adding Guava to your build

Guava's Maven group ID is `com.google.guava` and its artifact ID is `guava`.
Guava provides two different "flavors": one for use on a (Java 8+) JRE and one
for use on Android or Java 7 or by any library that wants to be compatible with
either of those. These flavors are specified in the Maven version field as
either `28.1-jre` or `28.1-android`. For more about depending on Guava, see
[using Guava in your build].

To add a dependency on Guava using Maven, use the following:

```xml
<dependency>
  <groupId>com.google.guava</groupId>
  <artifactId>guava</artifactId>
  <version>28.1-jre</version>
  <!-- or, for Android: -->
  <version>28.1-android</version>
</dependency>
```

To add a dependency using Gradle:

```gradle
dependencies {
  // Pick one:

  // 1. Use Guava in your implementation only:
  implementation("com.google.guava:guava:28.1-jre")

  // 2. Use Guava types in your public API:
  api("com.google.guava:guava:28.1-jre")

  // 3. Android - Use Guava in your implementation only:
  implementation("com.google.guava:guava:28.1-android")

  // 4. Android - Use Guava types in your public API:
  api("com.google.guava:guava:28.1-android")
}
```

For more information on when to use `api` and when to use `implementation`,
consult the
[Gradle documentation on API and implementation separation](https://docs.gradle.org/current/userguide/java_library_plugin.html#sec:java_library_separation).

## Snapshots

Snapshots of Guava built from the `master` branch are available through Maven
using version `HEAD-jre-SNAPSHOT`, or `HEAD-android-SNAPSHOT` for the Android
flavor.

-   Snapshot API Docs: [guava][guava-snapshot-api-docs]
-   Snapshot API Diffs: [guava][guava-snapshot-api-diffs]

## Learn about Guava

-   Our users' guide, [Guava Explained]
-   [A nice collection](http://www.tfnico.com/presentations/google-guava) of
    other helpful links

## Links

-   [GitHub project](https://github.com/google/guava)
-   [Issue tracker: Report a defect or feature request](https://github.com/google/guava/issues/new)
-   [StackOverflow: Ask "how-to" and "why-didn't-it-work" questions](https://stackoverflow.com/questions/ask?tags=guava+java)
-   [guava-announce: Announcements of releases and upcoming significant changes](http://groups.google.com/group/guava-announce)
-   [guava-discuss: For open-ended questions and discussion](http://groups.google.com/group/guava-discuss)

## IMPORTANT WARNINGS

1.  APIs marked with the `@Beta` annotation at the class or method level are
    subject to change. They can be modified in any way, or even removed, at any
    time. If your code is a library itself (i.e. it is used on the CLASSPATH of
    users outside your own control), you should not use beta APIs, unless you
    [repackage] them. **If your code is a library, we strongly recommend using
    the [Guava Beta Checker] to ensure that you do not use any `@Beta` APIs!**

2.  APIs without `@Beta` will remain binary-compatible for the indefinite
    future. (Previously, we sometimes removed such APIs after a deprecation
    period. The last release to remove non-`@Beta` APIs was Guava 21.0.) Even
    `@Deprecated` APIs will remain (again, unless they are `@Beta`). We have no
    plans to start removing things again, but officially, we're leaving our
    options open in case of surprises (like, say, a serious security problem).

3.  Guava has one dependency that is needed at runtime:
    `com.google.guava:failureaccess:1.0.1`

4.  Serialized forms of ALL objects are subject to change unless noted
    otherwise. Do not persist these and assume they can be read by a future
    version of the library.

5.  Our classes are not designed to protect against a malicious caller. You
    should not use them for communication between trusted and untrusted code.

6.  For the mainline flavor, we unit-test the libraries using only OpenJDK 1.8
    on Linux. Some features, especially in `com.google.common.io`, may not work
    correctly in other environments. For the Android flavor, our unit tests run
    on API level 15 (Ice Cream Sandwich).

[guava-snapshot-api-docs]: https://google.github.io/guava/releases/snapshot-jre/api/docs/
[guava-snapshot-api-diffs]: https://google.github.io/guava/releases/snapshot-jre/api/diffs/
[Guava Explained]: https://github.com/google/guava/wiki/Home
[Guava Beta Checker]: https://github.com/google/guava-beta-checker

<!-- References -->

[using Guava in your build]: https://github.com/google/guava/wiki/UseGuavaInYourBuild
[repackage]: https://github.com/google/guava/wiki/UseGuavaInYourBuild#what-if-i-want-to-use-beta-apis-from-a-library-that-people-use-as-a-dependency


1：Guava是个啥玩意？

   Guava是一个工具库，由Google公司的程序员们使用Java语言开发

2：Guava有啥用？

   提供一个内容丰富的工具箱，供Java程序员们使用
   
3：Guava有啥优势？

   背靠大公司，久经考验，提供的工具类丰富、简洁、实用

4：Guava咋用？

   引入对应的jar，不管使用什么方式，然后熟悉一下API，就能直接使用了

5：Guava带给了我什么？

   5-1：工具类基本都是使用了 final 关键字来修饰，表示类是不可被继承的，防止子类复写对应的方法
   
   5-2：工具类基本都提供了一个私有的无参构造方法，防止此类在外部被实例化
   
   5-3：工具类内的方法基本都是静态的方法，提供对外使用就用 public 来修饰，对内使用的就用 private 来修饰
   
   5-4：工具箱中的工具主要有基本数据类型相关、集合相关、并发相关、IO相关、反射相关、缓存相关、数学计算相关、网络相关、图表相关、事件直通车相关、注解相关
   
   5-5：Google的程序员们代码注释写的比较丰富
   
   5-6：每一个工具类都有对应的单元测试类，这是一种非常棒的习惯
   
   5-7：顺藤摸瓜，通过一个优秀的开源项目看到了一大片优秀的开源项目
   
   



