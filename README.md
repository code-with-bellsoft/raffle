# Raffle-fx: an application choosing a random name/number from a list

A JavaFX application for shuffling a list of Strings to choose a winner participant.
If the participant in present, they are congratulated.
If not, the name is removed from the list, which gets shuffled again to choose another name.

There's an option of masking emails: in this case, only the part before the at sign will be displayed on the screen.
Example:
john.doe*****


## Building

This project assumes you are using a graalvm JDK. Such a JDK can be downloaded via http://www.graalvm.org/ or via SDK man (https://www.sdkman.io)

    sdk install java 24.0.1-graalce

To get the native executable, compile the app with following command:

    mvn clean package

You will get a native executable in `./target/native/` called `raffle`.

The app will need various javafx libraries, which are copied from the SDK. This prevents errors like

    Error initializing QuantumRenderer: no suitable pipeline found
    java.lang.RuntimeException: java.lang.RuntimeException: Error initializing QuantumRenderer: no suitable pipeline found
    at com.sun.javafx.tk.quantum.QuantumRenderer.getInstance(QuantumRenderer.java:283)
    at com.sun.javafx.tk.quantum.QuantumToolkit.init(QuantumToolkit.java:253)
    at com.sun.javafx.tk.Toolkit.getToolkit(Toolkit.java:268)
    at com.sun.javafx.application.PlatformImpl.startup(PlatformImpl.java:291)
    at com.sun.javafx.application.PlatformImpl.startup(PlatformImpl.java:163)
    at com.sun.javafx.application.LauncherImpl.startToolkit(LauncherImpl.java:659)
    at com.sun.javafx.application.LauncherImpl.launchApplication1(LauncherImpl.java:679)
    at com.sun.javafx.application.LauncherImpl.lambda$launchApplication$2(LauncherImpl.java:196)
    at java.base@24.0.1/java.lang.Thread.runWith(Thread.java:1460)
    at java.base@24.0.1/java.lang.Thread.run(Thread.java:1447)
    at org.graalvm.nativeimage.builder/com.oracle.svm.core.thread.PlatformThreads.threadStartRoutine(PlatformThreads.java:832)
    at org.graalvm.nativeimage.builder/com.oracle.svm.core.thread.PlatformThreads.threadStartRoutine(PlatformThreads.java:808)
    Caused by: java.lang.RuntimeException: Error initializing QuantumRenderer: no suitable pipeline found
    at com.sun.javafx.tk.quantum.QuantumRenderer$PipelineRunnable.init(QuantumRenderer.java:95)
    at com.sun.javafx.tk.quantum.QuantumRenderer$PipelineRunnable.run(QuantumRenderer.java:125)
    ... 4 more
    Exception in thread "main" java.lang.RuntimeException: No toolkit found
    at com.sun.javafx.tk.Toolkit.getToolkit(Toolkit.java:280)
    at com.sun.javafx.application.PlatformImpl.startup(PlatformImpl.java:291)
    at com.sun.javafx.application.PlatformImpl.startup(PlatformImpl.java:163)
    at com.sun.javafx.application.LauncherImpl.startToolkit(LauncherImpl.java:659)
    at com.sun.javafx.application.LauncherImpl.launchApplication1(LauncherImpl.java:679)
    at com.sun.javafx.application.LauncherImpl.lambda$launchApplication$2(LauncherImpl.java:196)
    at java.base@24.0.1/java.lang.Thread.runWith(Thread.java:1460)
    at java.base@24.0.1/java.lang.Thread.run(Thread.java:1447)
    at org.graalvm.nativeimage.builder/com.oracle.svm.core.thread.PlatformThreads.threadStartRoutine(PlatformThreads.java:832)
    at org.graalvm.nativeimage.builder/com.oracle.svm.core.thread.PlatformThreads.threadStartRoutine(PlatformThreads.java:808)
    
Currently the app only works on Linux! On Mac the app won't show the User Interface.