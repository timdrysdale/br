# br

![alt text][logo]

![alt text][status]

business rules (software-architecturally-speaking) for a distributed, democratised, open-source infrastructure supporting non-traditional practical work experiments from remote, virtual and simulated laboratories

## Introduction
```br``` is the core "business rules" of an open-source infrastructure project that is to non-traditional practical work (remote, virtual, simulated laboratories) what Uber is to taxis (without the human rights issues). Reducing the minimum buy-in to make a world class remote laboratory  down to a single experiment hosted on a single board computer, on any old internet-surfing network you've got access to. Federate with others to offer your users frictionless, faultless, emotionally engaging experiences. With it, if you can afford a raspberry pi with a camera, and you have a network connection, then you can join a give your users a world class experience, with access to a wealth of experiments (shared from others within the same ecosystem) - no need to wait for a big government cheque to get started building your lab.

## Business rules

This is an software architectural term for the rules that apply in an organisation whether they relate to the computer or not, that speak to the opportunity to make or save money. It's the stuff that matters to humans and beancounters alike, but it doesn't care about computing implementation details. All the same we aim to get the abstract concepts expressed in computing terms so we can turn a lot of hot air made from nice human thoughts into practical value obtained by wisely marshalling the actions of our computing resources now and in the future (without having to rewrite everything everytime we get a new idea).  

## Background
Non-traditional practical work refers to a collection of activities that are distinguished by being "other" than traditional proximal practical work. Starting with remote laboratories: they comprise hardware and users that are geographically separated, relying on digital communications to exchange video, data, and commands. Hardware converts commands into actions, generating data and video, which is transmitted to the user. The user receives, displays, and interprets the data and video, then decides on new command(s) to issue, with the cycle repeating until the experiment is complete. Sometimes, the hardware and user are separated in time as well, with experiments running to their own schedule, without interactive oversight from the user. The geographical separation may not be absolute - for example the user may have previously been physically present in the same location as the hardware to set up a long running experiment, or may expect to be physically co-located at a future date. In cases where hardware is expensive, or rare, large data sets may have been pre-collected but then replayed to users over following years as if being obtained live (virtual microscopes are an example of this). Due to the high value of some data sets, access requirements may become indistinguishable from experiments with actual hardware. In the case that actual, or virtual hardware is not available due to unexpected conditions, such as extremely high demand, damage to equipment, network issues, or student location (e.g. offshore, underground or away from network coverage), then simulations may be substituted for hardware (with appropriate allowances made for communicating this to users who have a right to expect transparency in these matters). Accommodating all of these use cases just mentioned will require considerable flexibility in the system, not to mention what is required to support as yet unenvisaged use cases. 

While individual remote connections are relatively straightforward, managing large fleets of experiments and large cohorts of users is not. In a large distributed remote laboratory, there is likely to be an almost infinite need for flexibility to accommodate local preferences, policies, regulations and resources. However, the basic problem boils down to an experiment and a user (or user group) need to reach some common ground on how they will exchange video, data and commands, as well as how they will interact with any other services that may apply (booking, payment, authorisation, evaluation, etc). Following the open-closed principle (OCP is the O in SOLID), we can fix in place procedures that cover each new case that we know about. Those procedures (once developed) become closed to modification, so that we can rely on them, but we do not restrict the number of new procedures that are added, i.e. the system remains open for extension. In this way, the system can be made to accommodate almost anything, for example new forms of video transmission, new experimental interfaces, new institutional policies, new pricing schemes from suppliers etc.

It is impossible to anticipate all eventualities so there will be evolution in the procedures. Hence, it is intended to defer decisions about connections (network diagrams) and policies (decision making) as ong as possible to avoid the situation that we create something that might cover a great number of the anticipated cases we can think of now, but be difficult to extend later. One way of pursuing this aim is to consider creating elemental building blocks that can be assembled into complex networks that make multivariate and nuanced decisions. To complement this, we can identify boundaries, particularly aiming to highlight boundaries that we'd be reasonably tempted to overlook in the architecture of a single site, or closed site-group remote laboratory. First we consider some other factors that are likely to strongly influence the business rules we wish to develop, so that we can be alerted to some of the boundaries that have otherwise slipped by unnoticed.

## Factors to consider

In any system that promises to be all things to all people, you're going to find your mileage varies considerably based on how many other people share a similar view to you. Here are some factors that have been on my mind, that are influencing my thoughts about what to support. 


### Diverse capabilities encouraged, preferred approaches emerging democratically

A guiding principle is that any participant should be able to "do it their way" whilst still accessing the maximum theoretical potential benefits of federation that would apply to their way of doing things, without the rest of us trying to pre-guess or constrain what "doing their way" might need or entail. For example, someone might want to add string-telephone comms links to their experiments. Ok, fine, it'd be great click-bait and fun student project. It'll need an acoustic modem, which will have a low data rate, so the video will have to be low resolution, and with a low frame rate. That means a bunch of people probably won't want to use it for their experimental pools because it won't perform as well as their other experiments that stick to optical and electrical transmissions. There won't be the redundancy that you might get in another experiment if you choose to go down this route, because there will be fewer experiments like it due to its divergence from the norm. But what the federation might lose in redundancy, it gains in diversity. A pretty cool, albeit gimmicky, capability has been introduced into the network for others to access as users, or to re-use in their own experiments. 

Considering a more realistic case, existing laboratories use video communications methods across a wide range: Wowser media relays, custom LabVIEW websocket jpeg update, webRTC, RTSP. Each of these capabilities is mirrored in the associated user interfaces (e.g. in a browser), or client applications (e.g. a native operating system application). Some video connections are straightforward to establish, others less so. Latency suffers if you transcode, so there are disadvantages to having different expectations about how you send and receive video. But technically, there is nothing to stop you implementing some transcoding anyway, or adding additional video display capabilities to existing interfaces. Over time, what is more likely to happen is that a few fairly good, convenient ways of doing video will emerge, and the majority of experiments and interfaces are likely to try supporting them, and thus grow the redundancy and interoperability in the system. Anyone developing a new remote laboratory system is likely to choose something that suits their particular circumstances. There's a good chance that will be jsmpeg with external data relay. Also fine (in fact, encouraged, because of the benefits to users with restrictive network permissions in their home, or place of work/study). All methods are welcome. 

### Commercial ed-tech vendors have different goals to you

The non-returnable engineering costs of developing practical work experiments, and the diversity required to support highly localised contexts, coupled with the relatively small size of the STEM market mean that edtech companies are focusing on the larger, more generic opportunities for now (such as lecture recording). However, do we really want a world in which edtech hands us black boxes, and in which we are subject to vendor lock-in, and policy decisions that are driven by keeping the lights on today, making new sales, looking sharp in public, and maximising shareholder value? Nope. Your time and expertise is valuable, so invest instead in a system that you can organically increase your involvement in, change anything you need to,  and ultimately run entirely yourself should circumstances ever dictate. Remote laboratories offer a great opportunity for student co-creation, with senior years learning as they make activities for use by junior students in their own or other disciplines, so it is a virtuous cycle. 

### Benefits of federation

Federation allows a multitude ofindvidually-deployed experiments to offer a high level of overall reliability (via redundancy), throughput (through aggregration into pools), and diversity (through accessing experiments you do not own yourself). Therefore, systems that facilitate multiple experiment owners to federate are highly desirable. 

### Reducing barriers to entry

Existing university-based remote laboratories tend to have built centralised installations in dedicated spaces, with customised network permissions, facilitated with major capital funding, and often requiring the continued investment of staff time to oversee management and maintenance. In these instances, economy of scale has been applied in a single time and place. It is desirable to find a way to exploit the economy of scale such that other Universities can benefit from remote laboratories (by using and hosting), with the full benefit of local customisation, but without the constraints of needing dedicated space, special network permissions, extensive digital skillsets, or signficant capital and staff funding. These existing facilities can be complemented by many individually-owned, inexpensive experiments that be organically developed and grown as local conditions allow. Federated together such labs will achieve an overall throughput, reliability and diversity that will eventually be the envy of existing single-site, or site-group remote laboratories. It is explicitly intended to support the mutually beneficial integration of such

### Managing privacy 

Universities in Europe have the General Data Protection Regulations to contend with, which have the effect of encouraging organisations to carefully manage employee and student data sharing provisions. This does not directly prevent the sharing of equipment per se, but it does skew interest toward keeping data streams in-house. Hence one obvious supporting feature in a distributed remote laboratory would be to encourage approaches that allow individual institutions to own the data path from end-to-end between experiments (not belonging to them) and their students (who may or may not be on campus at the time). Organisations would swap in their data path to use a particular experiment, then swap it back out again to allow the next organisation to put in theirs. Such approaches will also better support organisations in applying local policies regarding data transport, monitoring and storage provisions, such as may apply to automated generation of formative feedback, summative assessment, detection of unexpected activity or misuse.

### Quality of experience

Students should be confident of having privacy during their sessions, and be protected from inadvertent access by other parties (e.g. previous users), which can sometimes happen with inadequate access and authorisation systems such as shared basic authentication managed at specific items of equipment.

System usage should be frictionless, with computers performing obviously-automatable tasks, and performant systems.

### Sustainability

It costs money to serve hardware, maintain the software infrastructure, and transfer data between experiments and users. However, Universities typically favour site-license approaches that mitigate the risk of cost overuns, yet wish to be aware of fine-grained usage information, so accounting and business analytics systems need to be decoupled from each other. 


### Service granularity

In a highly distributed system, second-resolution nano-contracts for sub-minute duration services are forseeable in the short term (e.g. for 15 second access to an asynchronous experiment such as the wobbling beam at RELOAD). Similarly, spot-priced data and video relay services will require contract durations shorter than the termination notice period (currently two minutes for AWS).  

### Payments

Nano-payments require real-time latency with the option of pre-purchasing, and an transation overhead that is significantly lower than the work per nano-contract. Hence, bitcoin-based transactions are unlikely to offer acceptable performance. Accounting also needs to be able to be performed with RPC calls, i.e. without requiring subsequent callbacks in reverse directions. 


## Boundaries

### data path


It is anticipated that the following constituencies will exist:
0. experiment constructors (hardware and software - remember to minimise firmware says Uncle Bob!)
1. experiment constructors


### payments



## Objects

capabilites represented with dr
mmmm ... or category is your namespace, and id is just that ...
hash, catalogue search (elastic search, not on hash)
(n.b. can save results of previous searches as list of hashes to look for next time ...so do we include version and network permissions etc?)
or accept fast results for known hashes, plus "slower" lookup through other entries... which won't be that slow.



[logo]: ./img/logo.png "ua logo, person in square"
[uses]: ./img/uses.png "browser and native uses are envisages"
[status]: https://img.shields.io/badge/concept-development-red "Concept development" 






