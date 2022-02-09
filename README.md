# gradle-javadoc-sourcepath

This repository demonstrates an issue with the default `javadoc` task when the javadoc classpath contains jars that
include .java files. If not explicitly specified, `-sourcepath` uses the same values from `-classpath`.

To see the error, run:

```shell
./gradlew clean javadoc
```

It will produce an error message similar to

```
> Task :javadoc FAILED
/home/devin/.gradle/caches/modules-2/files-2.1/com.google.jsinterop/base/1.0.0/5d2a5cda3092004832cb67cfe7a100a2ef8411f8/base-1.0.0.jar(/jsinterop/base/Js.java):21: error: package javaemul.internal.annotations does not exist
import javaemul.internal.annotations.DoNotAutobox;
...
```

To workaround the issue, run:

```shell
./gradlew clean javadoc -PexplicitSourcepath
```

See [build.gradle](build.gradle) for more information.

## Issue

[gradle#19869](https://github.com/gradle/gradle/issues/19869)
