# Components used 
* Microcontroller 8051

* 16 * 2 LCD Display

* 4 * 4 Matrix keypad

* Relay drivers

* Load (Bulb,LED)

* Buzzer

# SWOT Analysis
## Strengths:
#### User Friendly:   
Large population of the computer technology is familiar with username/ password scheme. It is obvious that users feels and understands the concept of using this technique. It has quite different but simple appearances for the user interface to enter the login and password and the main theme of information processing for authentication lies below the normal user understanding.
#### Diverse Usage :   
This technique is adopted by major portion of the user community due to its simplicity in understanding and working and is a pioneer approach for authentication.
#### User Define Password :   
The password can be merely created by user at an individual basis. So, it makes easy for the user to remember and change password according. It provides increase flexibility in choosing a password instead of system define passwords. 
#### User Trust and Experience :   
It is the foremost advantage of the technique that generally users are well known to this technique and as maximum number of the users are unaware of the problems in this technique that why they to use it. They believe that the password they hold is quite secure from the external world. As a pioneer technique by the business market, users hold experience in using it. 
#### Complexity/ Low Response Time :   
Since time is very critical factor when administering the user behavior, so lower the complexity, lower will be the time required by the user to authenticate with the system. Since the scheme does not hold significant complexity in algorithm in implementing higher degree of encryption in the basic and digest, so the performance at user and server end is assumed to be high.
#### User access During Mobility :   
User is totally free to move around only requiring username/ password to remember to use the service. No need to carry some sort of hardware or specialized software to access the service. 

## Weakness:
#### Password Security :   
Easy passwords are easy to guess, the possibility for user define password could be harmful in a sense, if the password level is low. Most of the users are not expert users to the technology so they cannot keep hard password as they are difficult to memorize. Even with possibility to build higher and dynamic user define passwords, it’s important to notice that “basic” send the password in the plain text format, so it’s highly vulnerable. If “digest” method is used, the encryption holds significant importance at the either end but if the data during transmission is monitored through spoofing, password can be decoded with small efforts because MD5 algorithm is freely available. Also when we enter the username/password, it remains in the browsers cache until we exit the browser completely.
#### Less Efficient :   
It requires double processing time and data transmission because when the access is requested, browser receive the reply from authenticating server to enter the username and password and then browser sends the data again i.e. second time for authentication. Also without having and intelligent server, it is likely that for access each secure page double authentication is required. Whereas new explores utilizes the stored username/ password in cache and reduces the number of login attempts.
## Opportunities:
#### Password Definition Level Guidelines :   
Users are free to choose username and password but it’s crucial to notify the users about the level of secure password selection. This can be implemented by the IMS system in a sense that alpha numeric passwords in concatenation with suitable password length size should be defined. Also to keep the password security, common policy to change the password with the same level of security will be provided in limited number of day.
## Threats:
#### User Dependent Password :   
Higher risk and uncertainty is associated with the user perceptions in choosing the password. It’s difficult for the user to remember hard passwords containing alpha numeric values/digits. An attempt to access the service from unauthorized user could result in access due to weak security protection of the user itself. It could be because the user have chosen password like its name, telephone number, date of birth, city and country name, which are very easy to guess. Also a problem is associated with the standard password chosen by the user but unable to protect it i.e. write on piece of a paper, in mobile, some text file that are vulnerable to security attacks (physically and remotely).
#### Login Attempts :   
High security requires improvement in the software as well as an extra work load on the server and personnel UE side. Wrong login attempt could grew higher processing tasks, causing network traffic increase and low response time, and could also results in denial of service. 
#### Security Attacks


# 4W's & 1H :
* WHAT : Password based protection system.
* WHERE : At all the subsystems in our localities.
* WHEN : When any accidents occur.
* WHY : To save the lives near electric poles.
* HOW : By alerting a lineman with the help of password.
# Requirements :

## High level requirements :
|ID|Description|Status|
|--|-----------|------|
|HLR01|Microcontoller-8051|It shall control all the actions|
|HLR02|Key pad (4* 4)|It shall acess the keys|
|HLR03|LCD Display 16* 2|It shall display all the operations|
|HLR04|Relay driver(ULN2003)|It shall drives to give output|
|HLR05|Buzzer|It shall ring for certain parameters as mentioned in Mc|
|HLR06|Relays|It shall gives the output|


## Low level requirements :
