Useful stuff
============

- [Pre-Endeavour Publication](https://www.h2020-endeavour.eu/sites/www.h2020-endeavour.eu/files/u69/endeavour-UC.commmag.pdf)
    - Figure 1 shows the link between SDX controller, Route Server and Customers
        - This is the area I'm supposed to examine
    - Section 2 is dedicated to use-cases including traffic engineering, advanced blackholing, and IXP Operator's benefits.
        - Some of these usecases might be realizable through the route server. That's something I can write about.
- [On the Role of IXP Route Servers](https://conferences2.sigcomm.org/imc/2014/papers/p31.pdf)
    - Gives details on the usage of route servers 
        - Traffic ratio via public vs private is 1:2
    - Section 9.3 is on the role of the route server in inter-domain routing innovation
        - "This observation makes RS design and operations a prime candi-
date for Software Defined Networking (SDN) which, in turn, sug-
gests that IXPs are natural places for harnessing SDN’s power to
improve if not revolutionize inter-domain routing."
        - Definitely worth a read
- [Chris on SDX use case demonstrations](http://delivery.acm.org/10.1145/3070000/3060601/p181-Dietzel.pdf?ip=130.83.200.199&id=3060601&acc=ACTIVE%20SERVICE&key=2BA2C432AB83DA15%2E24DDBA2ADC8180AB%2E4D4702B0C3E38B35%2E4D4702B0C3E38B35&__acm__=1541512209_3c316d81ac5093d609ac57e27ae8880e)
    - With mininet demos on youtube
    - I should check these demos out for understanding, how a programmable route server could be used
    
- Open question: With do much research done on the control plane of sdn switches, does a sdx rs need the same amount of considerations? Which are those
    - In order to understand that, I'd need to know more about the problems, solutions and considerations of the sdn switch research area.
        - lecture and jeremias  

Route Selection Goals
=====================

Who has which route selection goals in the Internet?

- Which granularity is sensible/measurable?

    


