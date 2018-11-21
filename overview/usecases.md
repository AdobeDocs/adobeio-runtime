# Use Cases for Adobe I/O Runtime

There are many possible uses for Adobe I/O Runtime&rsquo;s serverless, event-driven, on-demand computing model. In addition to the typical serverless use cases, there are a few that are ideal for Runtime:

* Microservices
* Extending Adobe's Cloud Platform
* Internet of Things (IoT)
* API back-end
* Mobile back-end
* Data processing
* Adobe Sensei
* Event processing with Adobe I/O Events

## Microservices
Microservices offer many benefits, but provisioning server-side support for them can be daunting, whether you&rsquo;re using a traditional server approach or a cloud-based solution. Development teams often find they spend as much or more time configuring the server or cloud solution for fault tolerance, load balancing, logging, and auto-scaling. This expertise is often outside the bounds of the development team, which implies the need for a server admin or admin team to do this work, thus adding to the resource demands of the microservice.

Adobe I/O Runtime is a perfect solution for this problem. By abstracting the server side of the equation and offering automatic scaling and load balancing, Runtime relieves developers of the need to maintain their own server infrastructure, either locally or in the cloud. Runtime&rsquo;s architecture is perfect for building modular solutions, because each function you place in Runtime&rsquo;s serverless cloud is independently deployed and managed and scales independently as well, so wherever the demand for computing from your microservie hits, Runtime can respond at scale. Runtime supports interconnectivity among your functions, so they can call each other, run in sequence, etc. Thus, instead of architecting and maintaining a server-side backend for your microservice, you merely deploy a set of functions that can respond at scale as they&rsquo;re needed.

[//]: <> (Took out web apps and wanted to make it more Adobe-specific.)

## Extending Adobe's Cloud Platform
Adobe I/O Runtime allows you to extend Adobe's Cloud Platform by deploying your own microservices on top of Adobe's infrastructure. With those microservices you can interact directly with your content and data and build out services that modify, transform, or automate processes based on your specific business needs. Those services can be invoked with events from Adobe I/O Events or via REST APIs.

## Internet of Things (IoT)
Connecting intelligent devices to the Internet has enabled incredibly useful innovations in home automation, navigation, and many other areas. Adobe I/O Runtime is an excellent choice for hosting functions to support IoT applications:

* IoT applications are often sensor-driven: devices are programmed to respond to external stimuli, such as a change in location or orientation. Under the right circumstances, sensor-driven events can spike from the low level of normal conditions to a flood of sensor events under extreme conditions. This makes designing and maintaining a scalable backend with traditional approaches can be particularly challenging and costly: either you build a system to handle normal use, which can&rsquo;t scale for peak use, or you build a system to handle peak use, most of the capacity of which sits idle the vast majority of the time.  The auto-scaling capabilities of Adobe I/O Runtime solve this problem, not only enabling your IoT application to continue to function in response to peak sensor events, but eliminating the need for you to design and provision that backend yourself.
* Given the lack of standardization with respect to data formats used in IoT devices, and their need to connect and report to myriad backend services and related applications, data transformation can be a major challenge: to provide functionality in real time, a device may need to transform data in both directions and depend on transformations among collaborating applications and platforms on the backend. The on-demand, scalable computing resources offered by Adobe I/O Runtime make it much easier to develop and deploy data transformation functions that operate in real time to and from your IoT device.

## API back-end
Imagine creating an API for your application without having a server to run it! Adobe I/O Runtime enables just that. Your functions hosted in Runtime&rsquo;s cloud can expose REST APIs to other applications. This makes it possible for you to offer customers a way to program against your Runtime application; it&rsquo;s also a great way to implement a backend for microservices or to customize Adobe's existing APIs to meet your needs. You can also connect your Runtime functions to any API management tool you choose.

## Mobile back-end
Mobile backend is an optimal use for Adobe I/O Runtime. Mobile applications often need extensive server-side functionality; however, mobile developers generally don&rsquo;t have much server-side development expertise. With Adobe I/O Runtime, you can build your mobile app and support it dynamically with Runtime functions written in JavaScript and Node.js, inheriting the server-side automation and management of Runtime and gaining the scalability to respond to mobile applications&rsquo; often unpredictable spikes in usage.

## Data processing
Adobe I/O Runtime functions can access any data stored in the Adobe Cloud Platform and can be designed to transform and process data in response to events or conditions, send and receive messages, invoke other functions, and access ACP or other data stores. You can build complete data processing pipelines in Runtime, and even make changes through simple configurations without having to reprogram. Combined with the scalability and flexibility of Runtime, this enables Runtime data processing solutions to be highly agile and responsive to changing requirements.

## Adobe Sensei
Adobe I/O Runtime functions can connect to Adobe Sensei intelligent services through the Adobe API Gateway or as native Runtime functions. This offers you incredible potential to apply machine learning and artificial intelligence algorithms to solutions you build on Adobe Runtime and to orchestrate custom workflows that bring together Sensei services. Imagine building your own custom digital asset processing and management functionality by leveraging Adobe Sensei functions and combining them with your own algorithms to create new applications. 

## Event processing with Adobe I/O Events
As you might imagine, Adobe I/O Runtime is ideally situated to work with Adobe I/O Events. When you combine a platform for hosting event-driven code with a service that fires events you can consume, the implications are obvious: build and deploy your event-driven logic on Adobe I/O Runtime to consume events from Adobe I/O Events. The possibilities are endless.
