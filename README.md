The very well known Observer pattern found its way to enterprise development frameworks such as Spring or CDI through application events.
Although the pattern itself is simple and well-understood, applying it in the transactional and multithreaded context of enterprise application might sometimes turn out to be more difficult than initially thought. The goal of this blog series is to explain in details what are the characteristics of application events.

The main advantage of events is that they allow to decouple event emitters (observables) from event consumers (observers). By decoupling I mean removing any compile-time dependency on both ends of the event. Observers do not know anything about the interface or implementation of observables and vice versa. 

However, there are other types of dependencies that you need to take into consideration while designing your application:
<ul>
<li> <b>time</b>: is the event handled at the same time as it is produced, in other words are the events synchronous or asynchronous?</li>
<li> <b>transactions</b>: if an event was emitted within a transaction, will the transaction span over the event handling?</li>
<li> <b>threads</b>: do the emitter and consumers have to be in the same thread?</li>
<li> <b>scope</b>: should the emitters and consumers be in the same scope? What if the event emitter is in application (singleton) scope and the event consumer is in session scope, or the other way around?</li>
</ul>
