## Ricochet
**By [Alberto Passini](https://github.com/AlbertoPassini), [Amanda Fernandes](https://github.com/amandafer/) and [Tamiris Bastos](https://github.com/tatasb)**<br>
*Federal University of Minas Gerais, 2016.*

![Ricochet Logo](images/ricochet.png)

*Ricochet is an instant messenger tool that deals with the core problem of metadata.
The concept of this IM is to message without any servers in the middle. Ricochet accomplishes this by not trusting your data to any third party software, whenever your messages are forward to your contacts.*

### Table of Contents
1. [Introduction](#introduction-)
  1. [Main Features](#main_features-)
  2. [Benefits and warnings](#benefits_warnings-)
2. [Development Team and Contributions](#development-)
  1. [Stakeholders](#stakeholders-)
  2. [Competitors](#competitors-)
3. [Releases and Possibles Improvements](#releases-)
4. [Frameworks and Development Tools](#frameworks-)
  1. [TOR](#tor-)
  2. [Qt](#qt-)
  3. [OpenSSL](#openssl-)
  4. [Transifex](#transifex-)
5. [Architeture](#architecture-)
  1. [Components Diagram](#components-)
  2. [Use Case Diagram](#use_case-)
6. [Conclusion](#conclusion-)
7. [References](#references-)

### Introduction <a name="introduction"></a>
Created by John Brooks in 2010, Ricochet (previously Torsion) was a program for encrypted instant messaging that uses TOR hidden services for the protected transmission of communications. However, it only got users' attention in 2014, after Edward Snowden’s revelations about the government’s intrusive surveillance activities.

To achieve true peer-to-peer connectivity, the hard work is done by a hidden service architecture named TOR. The user’s Ricochet address (`ricochet:rs7ce36jsj24ogfw`) represents a public key and a hidden service, and through TOR peers can ask to connect to you. Both sides make an anonymous connection to a rendezvous relay, and messages are sent through that connection. The address identifies a public key, which encrypts all of that communication.

The project was developed using C++ and Qt, a cross platform software. The interface was built with QML, a declarative UI language derived from javascript.

In this chapter, we will provide insights into the Ricochet project's architectural perspectives, and give background on the different stakeholders.

#### Main Features <a name="main_features"></a>
Ricochet is an experimental type of instant messaging that does not trust anyone with your identity, your contact list, or your communications.

* You can chat without exposing your identity (or IP address) to anyone.
* Nobody can discover who your contacts are or when you talk (metadata-free).
* There are no servers or operators that could be compromised, exposing your information.
* It is cross-platform and easy for non-technical users.

Similar to any instant messaging application, Ricochet has on the right a list of your contacts and their statuses. As for the left, the majority part of the window, the conversation with a particular contact is shown. The connection between the application and TOR is displayed at the beginning, when the user opens Ricochet.

The figure below illustrates the software working, plus the windows "Add Contact" and "Settings" opened for visualization.

![Features of Ricochet application](images/app_features.png)
Figure 01: Features of Ricochet application


By clicking the `+` button, other Ricochet users can be added. For that, a new window will appear: (1) "Add Contacts", as shown in Figure 01. The user’s Ricochet ID appears at the top of the window; this allow others to add you as a contact. In the ID field, the Ricochet ID of the contact you wish to add must be entered. The name field is the name you choose for your contact and the message field is optional. However, it is useful to let the contact to know who is the person requesting to connect, since the app will only show the Ricochet ID.

When your contact comes online, they will see a new window with your Ricochet ID and your message, if you chose to give one. They will not know who you are unless you have told them using a different medium. The added contact will have the option to accept or refuse your request to connect. If they reject the message, you will not be able to see their status nor be able to communicate with them using Ricochet. Once your contact accepts your message, and if they are online, you will be able see them as online, and will be able to start a new conversation with them.

In the case that the IM window is closed, the conversation history will be gone. When a contact closes Ricochet, the client window will show them as offline.

The "Settings" window can be used to change the application configuration, along with managing contacts.


#### Benefits and Warnings <a name="benefits_warnings"></a>
Some of the benefits of the privacy provided by Ricochet:
* Because of TOR, users are not personally identifiable; neither has IP addresses or physical locations revealed.
* Message content is cryptographically authenticated and private.
* There is no need to register anywhere in order to use Ricochet, particularly not with a fixed server.
* Contact list information is stored locally, and it would be very difficult for passive surveillance techniques to determine whom you are chatting with.
* Ricochet does not save chat history. When a conversation is closed, the chat log is not recoverable.
* The use of TOR hidden services prevents network traffic from ever leaving the Tor network, thereby preserving anonymity and complicating passive network surveillance.
* Ricochet is a portable application; users do not need to install any software to use Ricochet. Ricochet connects to the TOR network automatically.

Even though Ricochet presents a secure connection and cryptographed chat, the following warnings must be taken into consideration:

* An already-compromised computer system will typically defeat the privacy protections that Ricochet offers, such as a keystroke logging malware.
* Even though Ricochet uses TOR, other applications will not be using TOR unless you have independently set up additional TOR services on your computer.
* Active and passive surveillance techniques can still tell if you are using the Internet, and when, but not necessarily what you are doing on the Internet.
* Since a Ricochet user does not register or log in anywhere to use the application, it is important to implement layered physical security, including disk encryption, to protect Ricochet.
* Tails Linux users, and other live operating systems users, can optionally back up Ricochet to zero-knowledge cloud services such as SpiderOak, or on a personally owned USB drive (ideally encrypted).

John Brooks, main creator of Ricochet, once made a statement about the risks of anonymity [7]:
> “Ricochet is an experiment. Security and anonymity are difficult topics, and you should carefully evaluate your risks and exposure with any software.”

### Development Team and Contributions <a name="development"></a>
Most development and contributions are made through the GitHub platform. The open source project counts on numerous users that help with its growth. Below, the main contributors and competitors are identified [2].

#### Stakeholders <a name="stakeholders"></a>
* Development
  - John Brooks (@special) <john.brooks@dereferenced.net>


* Sponsors
    - Blueprint for Free Speech https://blueprintforfreespeech.net/
    - invisible.im group


* Translations
  - Bulgarian - ivopetkovcz
  - Czech - Einfach
  - Danish - Mikkel Kroman
  - Dutch - mijnheer, Meternalf
  - Finnish - reviewjolla
  - French - rike, Creaprog, CrumpyGat, Jordi, franck99
  - German - djsmith85, rike
  - Italian - HostFat, GIANNAT
  - Polish - Kacper Kołodziej
  - Portuguese (Brazil) - swperman
  - Russian - vla8752, qualte
  - Spanish - strel
  - Swedish - rawtaz
  - Tagalog - taskmaster
  - Turkish - cbolat, basarancaner
  - Ukrainian - l3rixon, nergal


* Thanks
  - Helder Ribeiro (@obvio171) - "Ricochet"
  - Robin Burchell (@rburchell)
  - prof7bit (TorChat) - Inspiration
  - Patrick Gray - invisible.im
  - Suelette Dreyfus
  - HD Moore
  - The Grugq
  - Lawrence Eastland - "R" icon


* Cryptographic Software
  - Eric Young - (eay@cryptsoft.com)
  - Tim Hudson - (tjh@cryptsoft.com)

An overview of what has contributed to the creation of Ricochet is shown below:

![Ricochet Structure](images/ricochet_diagram.png)

#### Competitors <a name="competitors"></a>
Many online chats use end-to-end encrypted messages. However, only a few of them focus on a proper, secure way of maintaining anonymity. Ricochet is one of those projects that deals with the core problem of metadata, but there are also a few others to be considered.

* **Tox:** this messenger is the main competitor of the application Ricochet. It is a peer-to-peer instant messaging and video calling protocol that offers end-to-end encryption.  Contrary to Ricochet, Tox relies on a *Distributed Hash Table* for peer discovery and has voice/video calls as a priority.

* **Ring:** another serverless application, Ring is an open-source SIP-compatible softphone and instant messenger that does not require any central servers. Ring is based on a MVC model, with a daemon and a client communication. The daemon handles all the processing, including communication layer (SIP/IAX), audio capture and playback.

* **Whatsapp, Facebook Messenger and Line:** these applications use end-to-end encrypted messages, although they do not focus on anonymity. Line is a proprietary application for instant communications on electronic devices and conducts free VoIP conversations and video conferences. It was heavily used by countries where censorship exists, like China. The major advantage of Line is the possibility to create "Hidden Chats," giving the user the ability to set a timer after which messages disappear from both involved devices and Line servers.

It is possible to analyse the comparisons between the applications with the image below. The complete version can be found on the website referenced by [5].

**TODO put table**

### Releases and Possibles Improvements <a name="releases"></a>
The program has eight available versions as of the present date (October 2016). The main and new features of each release will be discussed shortly in this section. In the next figure [15], the additions and deletions per week are shown. The gap between the old project and the beginning of what would become Ricochet represents the difficulty of retaining and gaining users prior to 2014. After that, between all releases, a lot of features were added, which is also reflected by the increased size of the project.

![Ricochet Structure](images/releases.png)

The peaks of the above figure correspond to the releases of the Ricochet project. The numbered peaks are explained one by one below.

1. **Torsion 1.0.0**:
This was the very first version of the system and implemented a “real-world,” decentralized and anonymous messaging client for TOR. The last release was on 23 March 2014.

2. **Torsion 1.0.1**:
On the website they express gratitude to some contributors like HostFat and delineate the fixes and features of the program.
The following additions were made: a static Linux build running without dependencies, an Italian translation, a security update to OpenSSL 1.0.1g, possibility to open or copy an URL's from the chat and compatibility with older OS X versions. Additionally, the display of hidden service state was fixed and it became possible to use the system on Linux, OS X and Windows.

3. **Ricochet 1.0.2**:
This was the first version of the program with the final name Ricochet, which was suggested by the contributor `@obvio171`. The changes were minimal in this version, but some did occur: characters were displayed correctly in the chat, a Spanish translation was added and packages were updated.
*************
NOT REVISED
4. **Ricochet 1.0.3**
In this version, an excellent improvement on the security was achieved with the update of TOR. This new version prevented the anonymous attack on users of hidden services. Also, more translations was added like Danish and Brazilian Portuguese and the configuration was changed to make the program more flexible, useful, robust and reliable.

5. **Ricochet 1.0.4**
This release focused on bugs corrections to fix common errors in the system. To exemplify, a error where the program rebooted unexpectedly and the error “Configuration is already in use” would appear. As well as the previous versions, some additions in the documentation and translations were made.

6. **Ricochet 1.1.0**
This as a major release switching the environment to a safer and more extensible protocol,  brand new icons were added and 11 new language translations included. It also includes many UI fixes, as well as security updates for TOR and OpenSSL. The most differential change made in this release was the incompatibility with the new version and older ones. This update forced users to migrate to the newer version in other to maintain their chats and contacts. The migration could be done through the system itself, in time to use it.

7. **Ricochet 1.1.1**
This version included bugs corrections, updates and features. Some new features were: choosing the language after the installation, be able to visualize the number of unread messages and the system to play sounds when messages were received.

8. **Ricochet 1.1.2**
This is the latest version and it is possible to consider that big improvements are made. For instance, the reliability and stability of connections were improved. This can be proven, as now contact users with suspicious names are blocked and it does not allow attempts to connect or disconnected users.
***************

As we see, the design described is close to the simplest implementation possible. For future improvements, the protocol has the potential to be extended to enable features such as file transfer or even voice/video streaming. A more advanced use of hidden services could also be implemented and would mitigate the risks of publishing a publicly connectable service. Separate services or more elaborate designs could be used to prevent attacks by non-contacts. Also, future development in TOR could improve the cryptography and principles behind hidden services.

### Frameworks and Development Tools <a name="frameworks"></a>
The main tools used to make the Ricochet system are TOR, Qt, OpenSSL and Transifex. The backend system is primarily written in C++ and the interface in QML. In this section, we will discuss more each one of the used tools and their importance to the project.

#### TOR <a name="tor"></a>
TOR uses Onion Router as an Internet networking protocol designed to anonymize the data relayed across it. The software makes it possible for users to hide their locations (and their IP addresses), as well as making it difficult for any snoops to see the user’s online activity.

The Ricochet system uses TOR hidden services to create a connection between users. The TOR network runs through the computer servers of thousands of volunteers spread throughout the world. The data is bundled into an encrypted packet when it enters the network, and unlike normal internet connections, part of the packet's header is removed. The removed part, which contains the addressing information, can be used to gather information about the sender, hence why its removal is important. Finally, TOR encrypts the rest of the addressing information. The modified and encrypted data packet is then routed through many of these servers to its final destination.

A hidden service needs to advertise its existence in the Tor network before clients will be able to contact it. Therefore the service randomly picks some relays, builds circuits to them, and asks them to act as *introduction points* by telling them its public key. By using a full TOR circuit, it is hard for anyone to associate an introduction point with the hidden server's IP address. While the introduction points are told the hidden service's identity (public key), we do not want them to learn about the hidden server's location (IP address).

The picture below exemplify the use of a working Transifex system[16]:

![TOR hidden service](images/tor.png)

#### Qt <a name="qt"></a>
Qt is a cross-platform application development framework for desktop, embedded and mobile; it is written in C++ and used for creation of an application’s frontend. Qt is not a programming language on its own, therefore QML (Qt Meta Language) was used on Ricochet to design the user interface.

QML is a user interface markup language. It is a JSON-like declarative language for designing user interface–centric applications. Inline JavaScript code handles imperative aspects. QML is mainly used for mobile applications where touch input, fluid animations and user experience are crucial. Elements of this language, shipped with Qt, are a sophisticated set of building blocks, graphical and behavioral. These elements can be combined to build components ranging in complexity from simple buttons and sliders to complete internet-enabled programs.

QML elements can also be seamlessly integrated and extended by C++ components using the Qt framework.

#### OpenSSL <a name="openssl"></a>

#### Transifex <a name="transifex"></a>
Transifex is a proprietary, web-based translation platform. It is accessible from any browser and also a globalization management system (GMS). Prior to 2013, this was an open source project. However, that version was discontinued.

This translation tool targets technical projects with frequently updated content, such as software, documentation and websites and encourages the automation of the localization workflow by integrating with the tools used by developers. Transifex has powerful tools to help the quality of the translations offered. An example is the option “Concordance Search”, it searches for a specific term and check how it was previously translated to ensure consistency, automating the process.

In Ricochet this tool is used to help the translators to add their collaborations into the project. With the help of this platform the developers can centralize their translations in only one place, which makes  it easier to locate apps and content from start to finish.

### Architecture <a name="architecture"></a>
In this section, the architecture of Ricochet is going to be addressed. The source code is separated in modules that contains interfaces with the headers of the functions and classes needed for the right behavior of Ricochet. Below, the structure of the project is analyzed and also the way that the software works.

In the Utils package, there are the classes and the interfaces for this classes that specify and set up  structures and functions to deal with the cryptography, manipulation of strings and configuration of permissions. Firstly, some of them deal with the generation and the manipulation of the secure key used for communication. Secondly, there are the ones that deal with the verification and the storage of the status of secure check operations (like if an operation has finished correctly, if an operation has finished with an error, if an operation has finished abruptly and if it has an error, the error message). Also, there are classes to manage configuration objects and files, that deal with the user's permissions and the accessibility. And finally, classes that deal with bugs and errors that may appear during the use. So, this module is for more general utilities, that are needed in the software.

Now, the UI (user interface) package is a module that specifies and determines the properties of the graphical user interface (GUI) of the software. It has files that define classes that deal with the presentation of graphical components like icons, buttons, labels, menus, lists and others. The models of the user interface, which are present in this module, contains the classes with functions, for example, to render the list of contacts, the options of languages and the chat presentation. The interface of this module that cover all of its functionalities, is the MainWindow.h. This one, includes all other classes that are needed to the chat interface. In other words, it contains the features to set up the main frame of Ricochet.

The protocol package, has the files to configure a connection. Being more specific, it is responsible to set up the connection. It defines the process of establishing a communication channel, the parameters of the communication channel and the packages containing the messages exchanged between the users. Furthermore, this module, also determine how the request and the response are treated in the Ricochet chat. The protocol used for the communication, like it has already been said before, is the TCP.

While protocol package has the functions for the communication channel, the TOR package, deals with the communication through the TOR network. It sets up the properties of the socket and the properties of the authentication process. Moreover, the classes defined in this module are responsible for the management and the control of the process of trading encrypted messages, using sockets, through TOR network.

The core module has the classes and the interfaces used to manage the local identification of the user and set up the properties of the users, of the conversation and of the list of contacts, while using the chat. It provides some features to add contacts, delete contacts, send messages, change status, validate users and others. Besides that, it includes interfaces from protocol module which take care of incoming requests (providing functions to set up the hostname, the contact ID, the nickname, the message and the active communication).

Those modules provide the interfaces needed to put Ricochet chat to work correctly. The next figure shows a tree of the interfaces relationship.

After the approach of each module and the interfaces, the way that the program works and the most important aspects of the architecture are going to be explored in the next lines.
One of the problems that hidden services can solve is to contact someone without anybody in the middle knowing who you are or who you're contacting. With a hidden service, a user's traffic never leaves the TOR network, making it much harder for an attacker to see where traffic is going or coming from. Ricochet client hosts a hidden service, since Ricochet ID it is literally an .onion address. Anyone that posses the address can contact the user. Ricochet also encrypts the contents of messages by default.

Ricochet does not communicate with central servers and neither does allow direct connections. Instead, each desktop client operates as a TOR hidden service and uses the TOR network to transmit encrypted and anonymous communication. The client generates a random 16-character public key or ID to authenticate the user and establish the channel for secure communication in a simple way that does not require users to install TOR separately. Generating the public key occurs with a single click, and the key is stored on the user’s machine, or any other device. In this way, the user can communicate with Ricochet from different machines.

To communicate with another Ricochet user, the client of the user making the request reaches out through the TOR network to arrange a rendezvous point. The client first connects anonymously via three hops to a TOR relay, which it is not aware of the origin of the connection. That relay searches for the other user’s Ricochet client ID and obtains a list of other TOR relays that can be used to reach out to the other party’s Ricochet client. It is important to highlight that the list of TOR relays changes every 24 hours. When the message reaches the other Ricochet client indicating a neutral relay for the rendezvous, the two clients meet there to exchange communication. However, at any time, there are at least six relays between the two users, three on each side.

The first relay is the only one that is aware of the user’s IP address, but it does not know the ID of your Ricochet client nor can match your IP address to that ID. It also does not know the Ricochet ID of the person the user is trying to contact. Those informations are only revealed to the relay three hops down the line from you, which peels off a layer of the TOR encryption to reveal the ID.
For instance, if two users are communicating and someone is passively monitoring one or the other party, this will protect them. Unless someone is directly monitoring both users at the same time, it would be very hard to identify the communication.
Ricochet does not require registration nor have an IM account anywhere. It does not need personal information of any kind. The generated Ricochet ID is sufficient for people to be identified and connect to start a communication. At the same time, Ricochet tries to maintain privacy by encrypting chat traffic and routing it through TOR.

The protocol has three layers:
* **Connection:** that “describes the use of an anonymized TCP-style connection for peer-to-peer communication”;

* **Packet:** makes possible do “multiplexing different operations on the same connection”.

* **Channel:** this layer treats and analyse the packets according to your state and channel.

The system is composed of template, components, modules and plugins where:

* **Template:** controls how the system is presented to the user.

* **Components:** basically are the main functional units of the system and can be seen as mini-applications.

* **Modules:** “usually contain information presented by components, but can also show static HTML code or plain text. An example of a commonly used module is” [8] the preferences module.

* **Plugins:** provide the most basic of functions such as “add contacts” functionality.


#### Components Diagram <a name="components"></a>

#### Use Case Diagram <a name="use_case"></a>
The Use Case Diagram is a useful way to represent what the final user can do with the system and it is also convenient to understand the behavior of the application while running. One of the most important part is that use cases diagram are easily understandable by both developers and customers, since the language is simple and objective.

Below we have examples and the explanations of the scenarios of the main functionalities. The steps below are considering a user on Windows OS and are shown in the order that the actions happen to the user.

| Scenario 1       |
|------------------|--------|
| Scenario Name    | A - Install the system |
| Actor            | Users                  |
| Precondition     | Have the necessary file |
| Normal Flow      | 1. Execute the file .exe <br> 2. Choose  the normal installation <br> 3. Mark the option “Execute Ricochet” |
| Alternative Flow | 1. Execute the file .exe <br> 2. Run it in a portable way|
| Postcondition    | Open to configure and use the program|


| Scenario 2       |
|------------------|--------|
| Scenario Name    | B - Configure the system |
| Actor            | Users  |
| Precondition     | Have the system installed |
| Normal Flow      | 1. Open the system <br> 2. Choose the type of the connection - (free internet connection) |
| Alternative Flow | 1. Open the system <br> 2. Choose the type of the connection - (censored internet connection) |
| Postcondition    | Start to use the program |


| Scenario 3       |
|------------------|--------|
| Scenario Name    | C - Add contacts |
| Actor            | Users  |
| Precondition     | Have the system running |
| Normal Flow      | 1. Click in the bottom “Add contacts” <br> 2. Write the ID of another user on the option “ID” <br> 3. Choose a nickname for this user and write on the option “Name” <br> 4. Write some message to this person to help her decide if she want to add you or not on the option “Message” <br> 5. Mark “Add” |
| Alternative Flow | 1. Click in the bottom “Add contacts” <br> 2. Write the ID of another user on the option “ID” <br> 3. Choose a nickname for this user and write on the option “Name” - (optional step) <br> 4. Mark “Add” |
| Postcondition    | Start chatting |


| Scenario 4       |
|------------------|--------|
| Scenario Name    | D - Exchange messages |
| Actor            | Users  |
| Precondition     | Have at least one contact in the system |
| Normal Flow      | 1. Choose the user in your list that you want to talk <br> 2. Send messages <br> 3. Read messages |
| Alternative Flow | 1. Accept some user <br> 2. Send messages <br> 3. Read messages |
| Postcondition    |   -    |

The final diagram is presented below, where it is possible to understand how system perform when it is operated by one or more users and their possible participation and actions.

![Use Case Diagram](images/use_case.png)

### Conclusion <a name="conclusion"></a>

### References <a name="references"></a>
1. Ricochet repository https://github.com/ricochet-im/ricochet/
2. Ricochet authors  https://github.com/ricochet-im/ricochet/blob/master/AUTHORS.md
3. Tox protocol https://en.wikipedia.org/wiki/Tox_%28protocol%29
4. Line application https://en.wikipedia.org/wiki/Line_%28application%29
5. Comparison between instant messengers https://en.wikipedia.org/wiki/Comparison_of_instant_messaging_clients
6. Ricochet software https://en.wikipedia.org/wiki/Ricochet_%28software%29
7. COX, Joseph. *'Ricochet', the Messenger That Beats Metadata, Passes Security Audit*. February, 2016. Available online at http://motherboard.vice.com/read/ricochet-encrypted-messenger-tackles-metadata-problem-head-on
8. https://delftswa.github.io/chapters/joomla/
9. Ring https://en.wikipedia.org/wiki/Ring_%28software%29
10. TOR project website https://www.torproject.org/docs/hidden-services.html.en
<br>https://www.torproject.org/about/overview
11. Yawnbox. *How to: Use Ricochet for Windows*. November, 2015. Available online at https://yawnbox.com/index.php/category/ricochet/
12. NANDI, Sunit. *Chat anonymously and serverlessly with Torsion (Ricochet)*. June, 2014. Available online at http://technofaq.org/posts/2014/06/chat-anonymously-and-serverlessly-with-torsion/
13. ZETTER, Kim. *Middle-School Dropout Codes Clever Chat Program That Foils NSA Spying*. September, 2014. Available online at https://www.wired.com/2014/09/new-encrypted-chat-program-thwarts-nsa-eliminating-metadata/
14. Transifex website https://www.transifex.com/how-it-works/
15. Graph and code frequency of Ricochet https://github.com/ricochet-im/ricochet/graphs/code-frequency
16. Anonabox. *What is TOR*. https://www.anonabox.com/what-is-tor.html
