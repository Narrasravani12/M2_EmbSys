# Password Based Protection System
Password Based Circuit System is designed to protect a circuit from damage which is caused by over load or short circuit. Many fatal electrical accidents are happen due to miscommunication between the maintenance staff and the electric substation staff. To avoid accidents, the project is designed in which only authorized person can operate it with the help of a password.
      
The password based circuit system is a system that access only specified password to control the circuit system by authorized person only. Here there is also a provision of changing the password.The entered password is compared with the stored password which is stored in the microcontroller. If the entered password is right, then the line can be switched ON/OFF.The system is also integrated with buzzer . For every three successive incorrect password entries ,the buzzer will on. After the system making its function ,it will be switched off only if we re-enter the correct password. If the person entering again three successive wrong passwords after getting the output ,the buzzer will be  on again. The system is fully controlled by 8-bit microcontroller from 8051 family which has an 8KB for program memory . LCD is used as an interface between the user and the system. The matrix keypad is used to enter the password and relay driver  IC is used to switch ON/OFF the loads (ex: bulb,led,buzzer, motor etc..,) through relays.

This system can be futherly interfaced with a GSM modem for remotely controlling the electronic circuit system through the SMS.

( Software tool (keil u vision) is used to write a code to dump in microcontroller and hardware tool (Proteus) is used to gather all required components for the system to perform an operation)

