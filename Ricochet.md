## Ricochet
By [Alberto Passini](https://github.com/AlbertoPassini), [Amanda Fernandes](https://github.com/amandafer/) and [Tamiris Bastos](https://github.com/tatasb)

![Ricochet Logo](images/ricochet.png)

*Ricochet is an instant messenger tool that deals with the core problem of metadata.
The concept of this IM is to message without any servers in the middle. Meaning, without trusting your data to anything so it can forward your messages to your contacts.*

### Table of Contents


### Introduction
Created by John Brooks in 2010, Ricochet (previously Torsion) was a program for encrypted instant messaging that uses TOR hidden services for the protected transmission of communications. However, it only got user's attention in 2014, after Edward Snowden’s revelations about the government’s intrusive surveillance activities.

To achieve true peer-to-peer connectivity, the hard work is done by a hidden service architecture named TOR. The user’s Ricochet address (i.e. `ricochet:rs7ce36jsj24ogfw`) represents a public key and a hidden service, and through TOR peers can ask to connect to you. Both sides make an anonymous connection to a rendezvous relay, and messages are sent through that connection. The address identifies a public key, which encrypts all of that communication.

The project was developed using C++ and Qt, a cross platform software. The interface was built with QML, a declarative UI language derived from javascript.
In this chapter, the insights of the Ricochet project are given. We will give some background on the different stakeholders and architectural view and perspectives.

#### Main Features
Ricochet is an experimental kind of instant messaging that doesn't trust anyone with your identity, your contact list, or your communications.
* You can chat without exposing your identity (or IP address) to anyone
* Nobody can discover who your contacts are or when you talk (metadata-free)
* There are no servers or operators that could be compromised, exposing your information.
* It's cross-platform and easy for non-technical users.

Similar to any instant messaging application, Ricochet has on the right a list of your contacts and their status. As for the left, and majority part of the window, the conversation with a particular contact is shown. the connection between the application and TOR is given at the beginning, when the user opens Ricochet.

The figure below illustrates the software working, plus the windows Add Contact and Settings opened for visualization.

![Features of Ricochet application](images/app_features.png)
Figure 01: Features of Ricochet application


By clicking at the `+` button, other Ricochet users can be added. With that, a new window will appear (1) Add Contacts, as shown in Figure 01. The user’s Ricochet ID appears at the top of the window, this allow others to add you as a contact. In the ID field, the contact’s Ricochet ID, whom you wish to add, must be entered. The name field is the name you choose for your contact and the message field is optional. However, it is useful to let the contact to know who is the person requesting to connect, since the app will only show the Ricochet ID.

When your contact comes online, they will see a new window with your Ricochet ID and your message, if you chose to give one. They will not know who you are unless you have told them using a different medium. The added contact will have the option to accept or refuse your request to connect. If they reject the message, you will not be able to see that their status nor be able to communicate with them using Ricochet. Once your contact accepts your message, and if they are online, you will be able see them as online, and will be able to start a new conversation with them.

In case the IM window is closed, the conversation history will be gone. When a contact closes Ricochet, the client window will show them as offline.

The settings window can be used to change the application configuration, besides managing contacts.


#### Benefits and warnings
Some of the benefits about the privacy provided by Ricochet:
* Users are not personally identifiable, neither has IP addresses or physical locations revealed because of TOR.
* Message content is cryptographically authenticated and private.
* There is no need to register anywhere in order to use Ricochet, particularly with a fixed server.
* Contact list information is stored locally, and it would be very difficult for passive surveillance techniques to determine whom you’re chatting with.
* Ricochet does not save chat history. When a conversation is closed, the chat log is not recoverable.
* The use of Tor hidden services prevents network traffic from ever leaving the Tor network, thereby preserving anonymity and complicating passive network surveillance.
* Ricochet is a portable application, users do not need to install any software to use Ricochet. Ricochet connects to the Tor network automatically.

Even though Ricochet presents a secure connection and cryptographed chat, the following warnings must be take into consideration:
* An already-compromised computer system will typically defeat the privacy protections that Ricochet offers, such as a keystroke logging malware.
* Even though Ricochet uses TOR, other applications will not be using Tor unless you’ve independently set up additional TOR services on your computer.
* Active and passive surveillance techniques can still tell if you’re using the Internet, and when, but not necessarily what you’re doing on the Internet.
* Since a Ricochet user does not register or log in anywhere to use the application, it is important to implement layered physical security, including disk encryption, to protect Ricochet.
* Tails Linux users, and other live operating systems users, can optionally backup Ricochet to zero-knowledge cloud services such as SpiderOak, or on a personally owned USB drive (ideally encrypted).

John Brooks, main creator of Ricochet, once made a statement about the risks of anonymity [7]:
> “Ricochet is an experiment. Security and anonymity are difficult topics, and you should carefully evaluate your risks and exposure with any software.”

### Development team and contributions
Most of development and contributions are made through github platform. The open source project counts with numerous users that help on its growth. Below, the main contributors and competitors were identified [2].

#### Stakeholders
Development
John Brooks (@special) <john.brooks@dereferenced.net>

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

An overview of what is around Ricochet is shown below:

![Ricochet Structure](images/ricochet_diagram.png)

#### Competitors
Many online chats use end-to-end encrypted messages. However, only a few of them focus on a proper secure way to maintain anonymity. Ricochet is one of those projects that deals with the core problem of metadata, but there are also few others to be consider.

* **Tox:** this messenger is the main competitor of the application Ricochet. It is a peer-to-peer instant messaging and video calling protocol that offers end-to-end encryption.  Contrary to Ricochet, Tox relies on a Distributed Hash Table for peer discovery and has voice/video calls as a priority.
* **Ring** - another serverless application, Ring is an open-source SIP-compatible softphone and instant messenger that does not require any central servers. Based on a MVC model, with a daemon and a client communication. The daemon handles all the processing including communication layer (SIP/IAX), audio capture and playback.
* **Whatsapp, Facebook Messenger and Line** - those applications use a end-to-end to encrypt messages, although they do not focus on anonymity. Line is a proprietary application for instant communications on electronic devices and conduct free VoIP conversations and video conferences, and is was heavily used by countries where censorship exists, like China. The differential of Line is the possibility to create "Hidden Chats", giving the user the ability to set a timer after which messages disappear from both involved devices and Line servers.

It is possible to analyse the comparisons between the applications on the image below. The complete version can be found on the website referenced by [5].

**TODO put table**

### Releases and possibles improvements
The program has eight available versions until the present date, October 2016. The main features and new of each release will be discussed shortly in this topic. In the next figure, the additions and deletions per week are shown. The gap between the old project and the beginning of what would became Ricochet, represents the difficulty of retaining and gaining users prior to 2014. After that, between all releases, a lot of features has been added, as is also reflected by the increased size of the project.

![Ricochet Structure](images/releases.png)

The additions and deletions of the numerous peaks, are shown in this figure. These peaks correspond to the releases of the Ricochet project. The numbered peaks are explained one by one below.
1. **Torsion 1.0.0**:
This was the very first version of the system and implements a “real-world” of a decentralized and anonymous messaging client for Tor. The last release was on 23 Mar 2014.
2. **Torsion 1.0.1**:
On the website they are grateful to some contributors like HostFat and we found the fixes and features of the program. Same examples are that the security was updated to OpenSSL 1.0.1g, was added an Italian translation, a static Linux build, became possible opened or copied an URL from the chat, the compatibility with older versions of OS X and the display of hidden service state was fixed. Became possible use the system on Linux, OS X and Windows.
3. **Ricochet 1.0.2**:
This was the first version of the program with the final name ricochet, and the name was suggested for the contributor `@obvio171`. The changes was minimal on this version and some examples of the changes was: some characters pass to be displayed on the correct way in the chat and wass added Spanish translation and some updates on the installations.
4. **Ricochet 1.0.3**:
On this version, we have an excellent improvement on the security with the new version of Tor, that prevent an anonymous attack on users of hidden services. Also, more translations was added like Danish and Brazilian Portuguese and some configurations was change to make the program more flexible, useful, robust and reliable.
5. **Ricochet 1.0.4**:
On this release we have only bugs corrections to fix some things that are commons or not on the system, for an example the error that appears when the program reboots unexpected (“Configuration is already in use”) and some addition in documentation and translations.
6. **Ricochet 1.1.0**:
The website resume this version saying that “This major release switches to a safer and more extensible protocol, adds a brand new icon and 11 new language translations, and includes many UI fixes as well as security updates for Tor and OpenSSL.” The most important information is that this version is not compatible with the olders versions and to continuous changing messages, every contact have to update theirs own version and this migration can be done through the system itself, in time to use it.
7. **Ricochet 1.1.1**:
This version includes bugs corrections, some updates and features like choose the language after the installation, see the number of unread messages and put the system to play sounds when receive messages.
8. **Ricochet 1.1.2**:
This is the latest version and we can consider that big improvements are made here, like in reliability and stability connections. This can be seen as now that contact users with suspicious names are blocked and it does not allow attempts to connect or disconnected users.

As seen, the design described is close to the simplest implementation possible. For future improvements, the protocol has the potential to be extended to enable features as, for instance, file transfer or even voice/video streaming. A more advanced use of hidden services can also be implemented and mitigate the risks of publishing a publicly connectable service. Separate services or more elaborated designs can be used to prevent attacks by non-contacts. Also, future development in Tor can improve the cryptography and principles behind hidden services.

### Used frameworks and development tools
The main tools used to make the Ricochet system are Tor, Qt, OpenSSL and Transifex. The backend system is basically written in C++ and the interface in QML. In this section, we will discuss more about each one of the used tools and their importance to the project.

#### TOR
Tor uses Onion Router as an Internet networking protocol designed to anonymize the data relayed across it. The software makes it possible for users to hide their locations (and IP address), as well as making difficult for any snoops to see the user’s online activity.

Ricochet system uses Tor hidden services to create a connection between users. Tor network runs through the computer servers of thousands of volunteers spread throughout the world. The data is bundled into an encrypted packet when it enters the network, and unlike normal Internet connections, part of the packet's header is removed. The removed part, which contains the addressing information, can be used to gather information about the sender, hence why it is important its removal. Finally, Tor encrypts the rest of the addressing information. The modified and encrypted data packet is then routed through many of these servers to its final destination.

A hidden service needs to advertise its existence in the Tor network before clients will be able to contact it. Therefore, the service randomly picks some relays, builds circuits to them, and asks them to act as *introduction points* by telling them its public key. By using a full Tor circuit, it's hard for anyone to associate an introduction point with the hidden server's IP address. While the introduction points and others are told the hidden service's identity (public key), we don't want them to learn about the hidden server's location (IP address).

#### Qt
QT is a cross-platform application development framework for desktop, embedded and mobile written in C++ and used for creation of an application’s frontend. Qt is not a programming language by its own, therefore QML, Qt Meta Language, was used on Ricochet to design the user interface.

QML is a user interface markup language. It is a JSON-like declarative language for designing user interface–centric applications. Inline JavaScript code handles imperative aspects. QML is mainly used for mobile applications where touch input, fluid animations and user experience are crucial. Elements of this language, shipped with Qt, are a sophisticated set of building blocks, graphical and behavioral. These elements can be combined to build components ranging in complexity from simple buttons and sliders, to complete internet-enabled programs.

QML elements can also be seamlessly integrated and extended by C++ components using the Qt framework.



### Architecture

### Conclusion

### References
1. https://github.com/ricochet-im/ricochet
2. https://www.torproject.org/docs/hidden-services.html.en
3. https://yawnbox.com/index.php/category/ricochet/
4. http://technofaq.org/posts/2014/06/chat-anonymously-and-serverlessly-with-torsion/
5. https://www.wired.com/2014/09/new-encrypted-chat-program-thwarts-nsa-eliminating-metadata/
6. http://motherboard.vice.com/read/ricochet-encrypted-messenger-tackles-metadata-problem-head-on
