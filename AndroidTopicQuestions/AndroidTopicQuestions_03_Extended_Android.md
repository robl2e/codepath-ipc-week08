# Android Interview Topic Review

Please review the questions below in each section, research the answers on our CodePath guides and any other sources (StackOverflow, official docs) and then write up a complete answer (between a few sentences and a few paragraphs) for each of the questions below.

## 3. Extended Android
Research and answer the following extended Android questions:

1.
>What is the difference JVM, DVM and ART?

The are the different runtime environments used to convert high level code in Java to machine code that is understood by low level CPU/Processor.

| Runtime        | Description     |
| ------------- |-------------:|
| JVM      | Environment used in traditional java apps.
| DVM     | Dalvik used in Android converts to DEX bytecode. Dalvik is a just-in-time JIT compilation based engine--as app is run code is dynamically translates bytecode to machine code. JIT compiles part of the code and uses less memory and disk space.
| ART   | ART uses Ahead-of-time AOT compilation, code executes faster because ART statically translates DEX bytecode one time during installation and stores it in device storage. ART runs machine code directly and uses less CPU but uses more disk space to store compiled code.  |

2.
>Have you used ConstraintLayout and what do you think of it?

Yes, it's great layout and provides a more precise way to define how the UI elements are aligned in a layout. It has a slightly harder learning curve at first compared to other layouts, but once learned it's easier to arrange elements as desired.

3.
>What is the architecture you used for your last app? Describe how the files and components were organized and what worked well or could be improved.

The architecture for my last app used MVP (Model View Presenter) for UI separation from business logic, data storage was a SqLite database abstracted using the Repository Pattern. Files and components are organized/packaged at the top level data from ui and subpackages are organized by feature. Example organization:

```
ui (ui related screens, with subpackages with features)
|_home
|_detail

data (data contains domain, business logic)
|_model (domain models, subpackage features)
  |_home
  |_detail
|_local (store data locally)
  |_home  
|_remote (retrieve data from server)
  |_response
  |_request

util (infrastructure, cross-functional, helper classes)
```
MVP and package structure worked well for modularizing and separating different kinds of logic. What could be improved is reusing common logic from Presenters and adding an dependency injection framework.

4.
>What is Dependency Injection? Why is it useful? Can you name few libraries?

Dependency Injection is the idea of injecting needed dependencies for a class instead of instantiating the dependencies directly in the class. It is useful since it separates out the logic to create a class from the class that needs to use it--thus making it more flexible to change the dependency. Popular dependency injection libraries are Dagger, Dagger2, Toothpick.

5.
> What do you think of RxJava? What are the benefits of using it? Are there any cons.

RxJava is a library to help perform functional programming type operations in code. The benefits of functional programming is more concise, shorter code and ability to listen/receive callbacks on operations. The cons are it has a difficult learning curve to understand and may be difficult to debug.

6.
>What is Android Data Binding? Do you like using this in your apps, why or why not?

Android Data Binding is a library to help implement the MVVM (Model-View-ViewModel) UI Architecture pattern. Android Data Binding allows you to bind a object view model specified in the xml layout. I have not used it before, but can see the benefit of reducing a lot of boiler plate code.

7.
>What is an ORM? What ORM do you use? What is Room and how do you think this compares with other ORMs?  

An ORM is an Object-relational mapping tool used to help persist objects to the database. ORMs create DAOs (Data Access Object) which works with Database Entity Objects to help perform CRUD operations. I've used OrmLite and GreenDAO before. Room is persistence library as part of the official Android Architecture components and provides an abstraction to a SQLite database. I have not used Room before, but appears to provide similar features to other ORMs.

8.
>What is a SurfaceView? Why would you use one?

A SurfaceView is an Android view that provides a drawing surface embedded inside a view hierarchy. You would use one typically for rendering video content in a view.

9.
>What is overdraw? Why is this important and how do you fix this?

Overdraw is when the same pixel is drawn more than once in a single frame. It's important because overdrawing can lead to unnecessary calls by the GPU for pixels that are not needed. The problem can be found by using the Debug GPU Overdraw or Profile GPU rendering tool. The problem can be fixed by:
  - Removing unneeded backgrounds in layouts
  - Flattening the view hierarchy
  - Reducing transparency

10.
>Have you used Kotlin and what do you think of it?

No, but the language seems to be more concise with less boilerplate code.

11.
>How to avoid memory leaks in Android? How to discover them?

You can avoid memory leaks by avoiding holding strong references to the Activity context in worker threads. You can discover memory leaks by using libraries such as LeakCanary or using Android Studio's Memory profiler to monitor abnormal memory usage.

12.
>Name 3 libraries that you like to use in apps and why?

* Glide - image downloading and loading library. I like it because it helps simplify the logic to render remote images--handling downloading and caching

* GSON - library to serialize and deserialize objects to JSON. I like it because the library has an easy to use API and an effective way to support handling serialization of interfaces and generics type objects.

* mosby(MVP) - library to help implement the MVP pattern. I like it because it helps handle the boilerplate code to implement the MVP pattern and is designed well so that existing classes don't need to extend from the libraries to use it.

13.
>What’s a new Android SDK feature or API that was released recently that looked interesting or are playing with?

The new Notifications feature in Android Oreo looks interesting with idea of "channels" to segment different types of notifications.

14.
>What is a JobScheduler? How does this differ from other alternatives?

JobScheduler is a feature help manage running multiple tasks or jobs. It differs from alternatives in that the Android OS optimizes and intelligently decides when it should execute the requests to balance battery and performance.

15.
>How do you play sounds in Android?

You play sounds using Android's MediaPlayer library. The MediaPlayer is used to play local media stored on the phone.

16.
>Describe any experience or knowledge high level of unit testing. What is Espresso used for? What is Mockito used for? What is the difference between unit and instrumented tests?

Unit testing is a way to test small chunks of code in isolation and usually independently from other parts of the app. Espresso is a form of UI test automation to help test UI code and logic. Mockito is a library for testing to mock/fake object dependencies with controlled test-friendly versions i.e. replacing actual database dependency with a fake one. Instrumented tests usually compose of testing larger chunk of code and akin more to "android" tests (testing involving the Android framework). Unit tests normally tests pure Java classes and is associated more with JUnit.

17.
>What is obfuscation? What is it used for? What common tools enables this?

Obfuscation is a method to obscure or hide the compiled code of an app by changing class, method, and variable names to a less human-readable format. It is used as a method to help secure and protect the source code from external parties. Proguard is the common tool to enable this.
