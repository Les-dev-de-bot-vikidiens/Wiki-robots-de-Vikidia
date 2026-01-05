# Multitier architecture - Wikipedia

![Overview of a three-tier application](https://upload.wikimedia.org/wikipedia/commons/thumb/5/51/Overview_of_a_three-tier_application_vectorVersion.svg/500px-Overview_of_a_three-tier_application_vectorVersion.svg.png)

In software engineering, **multitier architecture** (often referred to as **n‑tier architecture**) is a client–server architecture in which various levels of software architecture are physically separated. The most common use of multitier architecture is the **three‑tier architecture**, which separates presentation, application processing and data management functions, such as in the case of Cisco's [hierarchical internetworking model](/broken/pages/79e2c650640b7690de09024fd91830707b65d4b3). Other tiers of separation may include the [service layer](/broken/pages/a016adcd17d84e483be536704c95b3938a2733e8), [business layer](/broken/pages/f2f621e7c2cc7f33d992f0e87125a3fd47af8a71), [data access layer](/broken/pages/14a7b2e698945f4b834f4ddb097bf8ab23b5cf8f), and [persistence layer](/broken/pages/7617c48b2d760cfd98bc43376d193aafbbc5b833).

N‑tier application architecture provides a model by which developers can modify or add to a specific tier in the software development process instead of reworking the entire application. It is commonly used for small and simple applications because of its simplicity and low cost.\[1]\[2] In web development, three‑tier architecture is often used to describe websites that comprise a front‑end web server serving static content and some cached dynamic content, a middle dynamic content processing and generation application server, and a back‑end database or data store.

In a strict layered system, each layer depends on the layer below it and can exist without the layers above it. In a relaxed layered system, a layer can also depend on all of the layers below it, creating additional couplings between layers.\[3] Some multitier architectures use a hybrid approach so that some layers are strict while other layers are relaxed.\[4]\[5] N‑tier architecture may also be implemented with the [model–view–presenter](/broken/pages/0739f18a3bd529c5db9c51ce8e83c481582c9ec8) pattern.

The terms layer and tier are often used interchangeably, although layer is sometimes used to refer to a conceptual software logic structuring mechanism, while tier is used to refer to the physical hardware structuring mechanism for system infrastructure.\[6]\[7] In this usage, a three‑layer solution could be deployed on a single tier, as in some database‑centric architectures called RDBMS‑only architecture or in personal workstations.\[8]\[9]

### Layers

#### Common layers

In a logical multilayer architecture for an information system with an object‑oriented design, the following four are the most common:\[3]

* Presentation layer (a.k.a. UI layer, view layer, presentation tier in multitier architecture)
* Application layer (a.k.a. [service layer](/broken/pages/a016adcd17d84e483be536704c95b3938a2733e8) or GRASP Controller Layer)
* Business layer (a.k.a. business logic layer (BLL), domain logic layer)
* Data access layer (a.k.a. persistence layer, logging, networking, and other services required to support a particular business layer)

The more usual convention is that the application layer (or service layer) is considered a sublayer of the business layer, typically encapsulating the API definition surfacing the supported business functionality. The application/business layers can be further subdivided to emphasize additional sublayers of distinct responsibility. For example, if the [model–view–presenter](/broken/pages/0739f18a3bd529c5db9c51ce8e83c481582c9ec8) pattern is used, the presenter sublayer might be used as an additional layer between the user interface layer and the business/application layer (as represented by the model sublayer). If the application architecture has no explicit distinction between the business layer and the presentation layer (i.e., the presentation layer is considered part of the business layer), then a traditional client‑server (two‑tier) model has been implemented.

Some also identify a separate layer called the business infrastructure layer (BI), located between the business layer(s) and the infrastructure layer(s). It is also sometimes called the "low‑level business layer" or the "business services layer". This layer is very general and can be used in several application tiers (e.g. a CurrencyConverter).\[13]

The infrastructure layer can be partitioned into different levels (high‑level or low‑level technical services).\[13] Developers often focus on the persistence (data access) capabilities of the infrastructure layer and therefore only talk about the persistence layer or the data access layer (instead of an infrastructure layer or technical services layer). The Data Access layer normally contains an object known as the [Data Access Object (DAO)](/broken/pages/ec1aee78f42054cd0c5ce9829b22a8d450559f5c).

In a strict layered system, each layer depends on the layer below it and can exist without the layers above it. In a relaxed layered system, a layer can also depend on all of the layers below it and not merely the layer directly below it.\[3] The relaxed layered system has more couplings and is more difficult to change. Some multitier architectures use a hybrid approach so that some layers are strict while other layers are relaxed.\[4]\[5]

#### Three‑tier architecture

Three‑tier architecture is a client‑server software architecture pattern in which the user interface (presentation), functional process logic ("business rules"), computer data storage and data access are developed and maintained as independent modules, most often on separate platforms.\[14] It was developed by John J. Donovan in Open Environment Corporation (OEC), a tools company he founded in Cambridge, Massachusetts.

Apart from the usual advantages of modular software with well‑defined interfaces, the three‑tier architecture is intended to allow any of the three tiers to be upgraded or replaced independently in response to changes in requirements or technology. For example, a change of operating system in the presentation tier would only affect the user interface code. Typically, the user interface runs on a desktop PC or workstation and uses a standard graphical user interface, functional process logic that may consist of one or more separate modules running on a workstation or application server, and an RDBMS on a database server or mainframe that contains the computer data storage logic. The middle tier may be multitiered itself (in which case the overall architecture is called an "n‑tier architecture").\[15]

* Presentation tier
  * The topmost level of the application. The presentation tier displays information related to services such as browsing merchandise, purchasing and shopping cart contents. It communicates with other tiers by which it puts out results to the browser/client tier and all other tiers in the network. It is a layer that users can access directly (such as a web page or an operating system's GUI).
* Application tier (business logic, logic tier, or middle tier)
  * The logical tier is pulled out from the presentation tier and controls an application's functionality by performing detailed processing.
* Data tier
  * The data tier includes the data persistence mechanisms (database servers, file shares, etc.) and the data access layer that encapsulates the persistence mechanisms and exposes the data. The data access layer should provide an API to the application tier that exposes methods of managing the stored data without exposing or creating dependencies on the data storage mechanisms. Avoiding dependencies on the storage mechanisms allows for updates or changes without the application tier clients being affected by or even aware of the change. As with the separation of any tier, there are costs for implementation and often costs to performance in exchange for improved scalability and maintainability.

**Web development**

In the web development field, three‑tier is often used to refer to websites, commonly electronic commerce websites, which are built using three tiers:

{% stepper %}
{% step %}
### Front-end web server

A front‑end web server serving static content, and potentially some cached dynamic content. In web‑based applications, front end is the content rendered by the browser. The content may be static or generated dynamically.
{% endstep %}

{% step %}
### Application server (middle tier)

A middle dynamic content processing and generation level application server (e.g., Symfony, Spring, ASP.NET, Django, Rails, Node.js).
{% endstep %}

{% step %}
### Back-end data store

A back‑end database or data store, comprising both data sets and the database management system software that manages and provides access to the data.
{% endstep %}
{% endstepper %}

#### Other considerations

Data transfer between tiers is part of the architecture. Protocols involved may include one or more of [SNMP](/broken/pages/5447202dec3b6f9de91726f62945136341ece77a), [CORBA](/broken/pages/1259ef6517d15a90e69626ad64d458350de4bc73), [Java RMI](/broken/pages/8099671e1275cd01e957b0aecb39e1deedfc3a08), [.NET Remoting](/broken/pages/f61125689fad3f139008898e9b7d622ebab1afc4), [Windows Communication Foundation](/broken/pages/ed83e2a149794d745bc40235bc1a8405e139ce85), [sockets](/broken/pages/bb63e79fb341236b291d02c2b2b5c9c23ae6e896), [UDP](/broken/pages/097d821f5bb01951f7ff4f0401fec9c49badd5ed), web services or other standard or proprietary protocols. Often [middleware](/broken/pages/e36d99f8c8f752aea16b0d3b21bb8582b210f094) is used to connect the separate tiers. Separate tiers often (but not necessarily) run on separate physical servers, and each tier may itself run on a [cluster](/broken/pages/986ffd171d17e2072cbecb7591fb71e27f50d156).

### Traceability

The [Application Response Measurement](/broken/pages/4d368844fd6b8f2c49c454c202ca95d18136eaf8) defines concepts and APIs for measuring performance and correlating transactions between tiers.

Generally, the term "tiers" is used to describe physical distribution of components of a system on separate servers, computers, or networks (processing nodes). A three‑tier architecture then will have three processing nodes. The term "layers" refers to a logical grouping of components which may or may not be physically located on one processing node.

### See also

* [Abstraction layer](/broken/pages/199baab5ef626803de45c0d227041fa6b808d924)
* [Database-centric architecture](/broken/pages/b06ad404ba86f834c4e48faca0f268ea773f4f2a)
* [Front-end and back-end](/broken/pages/8c84ffe99c248f5a1d63eb1ba6fec68e8cba2d69)
* [Load balancing (computing)](/broken/pages/4bb5f9a104c226f69ee9e0ae066a677edbc85d36)
* [Monolithic application](/broken/pages/22ef35c12e8400e2f5b66b822af1f8c431efe5ba)
* [Open Services Architecture](/broken/pages/201ffe0cd22d5c97712a68c9cee938db2765fd7d)
* [Rich web application](/broken/pages/a3c4196824934826b6c661a106c93c63fcf4968b)
* [Web application](/broken/pages/70521b63c918c09f4a54208ae7ccd61de2317baf)

### References

1. Richards, Mark (2020). Fundamentals of Software Architecture: An Engineering Approach (1st ed.). O'Reilly Media. ISBN 978-1492043454.
2. Richards, Mark (2022). Software Architecture Patterns. O'Reilly Media, Inc. ISBN 9781098134273.
3. Buschmann, Frank; Meunier, Regine; Rohnert, Hans; Sommerlad, Peter; Stal, Michael (1996‑08). Pattern‑Oriented Software Architecture, Volume 1, A System of Patterns. Wiley. ISBN 978-0-471-95869-7. Retrieved from http://www.wiley.com/WileyCDA/WileyTitle/productCd-0471958697.html.
4. Richards, Mark (March 3, 2020). Fundamentals of Software Architecture: An Engineering Approach (1st ed.). O'Reilly Media. ISBN 978-1492043454.
5. Richards, Mark. Software Architecture Patterns. O'Reilly Media, Inc.
6. Deployment Patterns (Microsoft Enterprise Architecture, Patterns, and Practices) — http://msdn.microsoft.com/en-us/library/ms998478.aspx
7. Fowler, Martin "Patterns of Enterprise Application Architecture" (2002). Addison Wesley.
8. Deployment Patterns (Microsoft Enterprise Architecture, Patterns, and Practices) — http://msdn.microsoft.com/en-us/library/ms998478.aspx
9. Vicente, Alfonso; Etcheverry, Lorena; Sabiguero, Ariel (2021). "An RDBMS-only architecture for web applications". 2021 XLVII Latin American Computing Conference (CLEI). pp. 1–9. doi:10.1109/CLEI53233.2021.9640017. ISBN 978-1-6654-9503-5. S2CID 245387844.
10. Martin Fowler's Service Layer — http://martinfowler.com/eaaCatalog/serviceLayer.html
11. Martin Fowler explains that Service Layer is the same as Application Layer — http://martinfowler.com/bliki/AnemicDomainModel.html
12. Comparison/discussion of the GRASP Controller Layer vs. Application/Service Layer — https://archive.today/20120715125904/http://tech.groups.yahoo.com/group/domaindrivendesign/message/7582
13. Applying UML and Patterns, 3rd edition, page 203 — http://www.craiglarman.com/wiki/index.php?title=Books#Applying\_UML\_and\_Patterns

### External links

* Linux Journal, _Three Tier Architecture_ — http://www.linuxjournal.com/article/3508
* Microsoft Application Architecture Guide — http://msdn.microsoft.com/en-us/library/ee658109.aspx

(Image and all links retained as in the source.)
