# Android Interview Topic Review

Please review the questions below in each section, research the answers on our CodePath guides and any other sources (StackOverflow, official docs) and then write up a complete answer (between a few sentences and a few paragraphs) for each of the questions below.

## 2. Core Android
Research and answer the following core Android questions:

1.
>Explain Activity lifecycle including most notable events and
the order they run.

The Activity lifecycle is a set of hooks or callbacks the Android system/framework provide to describe the state of the Activity. The lifecycle goes through the order of onCreate(), onStart(), and onResume() when the Activity is starting up. The lifecycle goes through complementary/mirror events in the order of onPause(), onStop(), onDestroy() when the Activity is finishing up.

onCreate() - is when the Activity is first created and provides a place to insert startup logic that happens only once in the Activity's lifetime.

onStart() - is when the Activity is visible to the user and a place to insert initialize code that maintains the UI i.e. BroadcastReceiver

onResume() - is when the Activity is in the foreground and the app interacts with the user. Code that should be executed every time the Activity enters the foreground should be placed here.

onPause() - is when the user is leaving the Activity, but can be expected to be resumed shortly. It is called when the Activity's not in focus but may be partially visible. It is meant to be brief and long running operations should not be performed here.

onStop() - is when the Activity is no longer visible to the user. It's common to release all resources that aren't needed while the user is not using it and perform CPU-intensive shutdown operations.

onDestroy() - is when the Activity is about to be destroyed. The callback releases all resources that have not been released by earlier callbacks.

2.
>Explain Fragment lifecycle including most notable events and the order they run.

The Fragment lifecycle is a set of hooks/callbacks that the Android framework/system provide to describe the state of the fragment. The fragment goes through the lifecycle of onAttach(), onCreate(), onCreateView(), onActivityCreated() onViewCreated(), onStart(), onResume() when starting up and go through the steps onPause(), onStop(), onDestroyView(), onDestroy(), onDetach() when finishing up.

The events that mirror the Activity lifecycle callbacks provide the same functionality in a Fragment's lifecycle.

onAttach() - is when the fragment becomes associated with its Activity

onCreateView() - is when you instantiate the layout and view hierarchy of the fragment.

onActivityCreated() - is when the Activity associated with the fragment has completed it's own Activity.onCreate();

onViewCreated() - is when the fragment's view has been created and UI referencing and initialization can be performed.

onDestroyView() - is when the fragment's view is being destroyed and cleaning up resources related to its View can be handled here.

onDetach() - is when the fragment is no longer associated with its Activity.

3.
>How would you preserve Activity state during a screen rotation?

You would preserve Activity state during screen rotation by saving state information during the onSaveInstaceState() callback in the Bundle object and read from that state information during the onCreate() callback.

4.
>What are Intents and what are the major types? When would you use one over another?

Intents provide a mechanism in Android to communicate between applications to request an action from another application. The major types are Implicit and Explicit.

Explicit Intents - when you want to invoke a specific Activity to perform an action, and used for targeting specific components within your application.

Implicit Intents = when you want to see which Activities can "handle" said intent and thus allowing an external application to handle the event.

5.
>What is the difference between ListView and RecyclerView?

ListView is view widget to implement a list type UI while RecyclerView is a the newer implementation to accomplish this. ListView is less flexible and can perform slower compared to a RecyclerView if the ViewHolder pattern is not used (RecyclerView requires the ViewHolder inheritenly in its implementation)

6.
>What is the ViewHolder pattern? Why should we use it?

The ViewHolder pattern is a view optimization, so that if a view has already been inflated/created it's reused to bind the view data, saving the expensive call for layout creation.

7.
>Explain all the major Android components (e.g activities, services, broadcast receivers, content providers) and how they each are used in apps.

Activities - is the main place in an app to present UI to the user. Logic related to creating and rendering UI is done here.

Services - is where long running operations reside and are performed in the background. Logic that does not have UI live would likely live in a service such playing music.

BrodcastReceiver - is a place to receive messages from the Android system and other Android apps. You would subscribe/ register for specific system events the app may be interested in such system boot or device starts charging

ContentProvider - is the mechanism to use when you want to share data with other applications. For example the contacts data can be used across multiple applications.

8.
>Explain the difference between Service, IntentService, and AsyncTask? When would you use one over another?

Service - is long living and used to perform operations that require no direct interaction with UI, by default operations are executed on the main thread.

IntentService - is used to perform operation in the backround, it is short-lived and will last as long as needed to complete the operation.

AsyncTask - is used to perform an operation in the background that is short-lived, but also provides hooks to update the UI on the state of the background operation.

9.
>Explain what Looper, Handler and HandlerThread are and how they are used.

Looper - is a mechanism to run a message loop for a thread and is used to process messages.

Handler - is used to send and process Message and Runnable objects associated with a thread's MessageQueue. Typically handlers are used to schedule messages and runnables and to queue actions to perform on different threads

HandlerThread - a convenience class that creates a new thread with a looper, typically used when handling multiple jobs in a background thread

10.
>Explain the difference between services and threads in Android? How and why are they used?

Services provide a way for you to perform logic when no UI is needed to be presented. Threads are used to keep computation heavy tasks in a separate thread from the main UI thread.

11.
>Why should you avoid running non-ui code on the main thread?

You avoid running non-ui code from the main thread to avoid Application Not Responding (ANR) errors that are thrown by the system. Offloading non-ui code to separate threads make sure application to render, perform smoothly.

12.
>What are the options for persisting data in an Android app?
When would you use the various different options available?

| Option        | Description     |
| ------------- |-------------:|
| Shared Preferences      | simple key value pair storage that stores the key-value pairs in a file on disk.   |
| SQLite Database      | store data in a relational database using SQLite with tables and rows.     |
| Content Provider | underlying stores data in SQLite, provides an abstraction layer, used when want to share data across applications.     |
|File storage   | simply store data in a file on disk, can store in the internal app package directory.|


| Option        | Use When     |
| ------------- |-------------:|
| Shared Preferences      | Need to store simple unstructured data, don't need to perform queries, or store one-off flags  |
| SQLite Database      | Need to store structured, query-able data i.e. get me a list of all data with userId   |
| Content Provider | Store data that will be shared across different applications.     |
|File storage   | Need to store data in a specific format csv, JSON, xml |

13.
>What is the difference between a fragment and an activity?
Explain the relationship between the two.

A Fragment is a part/portion or subset of UI in an Activity. The relationship is an Activity contains Fragments and can compose multiple fragments in a single Activity. Fragments are modular sections of an Activity.

14.
>How would you communicate between two Fragments? Describe the best practices for communication.

You could communicate between two Fragments, by having the Activity be the intermediary. Have each Fragment interact with the activity through an interface and have the Activity relay the messages between the two fragments. THe Activity could also interact with the Fragments through an interface.

15.
>What are "launch modes"? What are some common ways you might use launch modes.

Launch modes are the different modes of behavior when launching an Activity.

| Mode        | Description     |
| ------------- |-------------:|
| standard      | default behavior of Activity, creates a new instance of an Activity, can be multiple instances within a task stack
| singleTop     | If launching an Activity that already exists in the task stack use that instance to handle launching activity will receive onNewIntent() callback. You could use this for example with a SearchResultActivity, re-populating different data for different search results  |
| singleTask   |  launches a new instance of an activity in it's own new task stack and will reroute launching to an existing instance if exists via onNewIntent(). You would use this mode for an entry point activity like social network timeline or email client inbox page.  |
| singleInstance   | used with applications with only one Activity, with similar behavior as singleTask except no other activites will be created in the same task. Can be used for is an Activity for Launcher.  |

16.
>What is a BroadcastReceiver? What is a LocalBroadcastManager? What situations might you commonly use these?

A broadcast receiver is a mechanism to subscribe to receive notification of system events. You would use these to listen in to certain interested system events such as when system boots. A LocalBroadcastManager used to register and send events to local objects within your process. You might use a LocalBroadcastManager to provide a way to communicate between Activities or Fragments.

17.
>What is a ContentProvider and what is it typically used for? Would you commonly use them in an app, and if not, why not?

A content provider one method to persist data. You would commonly used them if you want share data with other applications.

18.
>How do you handle Bitmaps in Android and what are common issues associated with them? How do you address these issues?

Using an image downloading, loading library such as Glide or Picasso. Common issues with Bitmaps is managing their memory usage and performance in loading and cleaning up resources.

19.
>What is the function of an intent filter? When would you use them in an app?

The function of an intent filter is to define the specific attributes an Activity can handle. You would use them in an
app for instance to define the Activity that would be used for app's launcher.
