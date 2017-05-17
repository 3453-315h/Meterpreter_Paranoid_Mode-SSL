[![Version](https://img.shields.io/badge/Meterpreter_Paranoid_Mode-1.3-brightgreen.svg?maxAge=259200)]()
[![Stage](https://img.shields.io/badge/Release-Stable-brightgreen.svg)]()
[![Build](https://img.shields.io/badge/Supported_OS-kali,Mint,Ubuntu,Parrot-blue.svg)]()


![Meterpreter_Paranoid_Mode v1.3](http://1.1m.yt/4xyGfw.png)


## Meterpreter_Paranoid_Mode v1.3 - SSL/TLS connections
    Version release: v1.3 (Beta)
    Author: pedro ubuntu [ r00t-3xp10it ]
    Distros Supported : Linux Kali, Mint, Ubuntu,Parrot
    Suspicious-Shell-Activity (SSA) RedTeam develop @2017

<br /><br />

## Description:
     Meterpreter_Paranoid_Mode.sh allows users to secure your staged/stageless
     connection for Meterpreter by having it check the certificate of the
     handler it is connecting to.

     We start by generating a certificate in PEM format, once the certs have
     been created we can create a HTTP or HTTPS or EXE payload for it and give
     it the path of PEM format certificate to be used to validate the connection.

     To have the connection validated we need to tell the payload what certificate
     the handler will be using by setting the path to the PEM certificate in the
     HANDLERSSLCERT option then we enable the checking of this certificate by
     setting stagerverifysslcert to true.

     Once that payload is created we need to create a handler to receive the
     connection and again we use the PEM certificate so the handler can use the
     SHA1 hash for validation. Just like with the Payload we set the parameters
     HANDLERSSLCERT with the path to the PEM file and stagerverifysslcert to true. 


    When we get payload execution (target), we can see the stage doing the validation
![Meterpreter_Paranoid_Mode v1.3](http://4.1m.yt/culWay.png)
![Meterpreter_Paranoid_Mode v1.3](http://4.1m.yt/jq464O0.png)

 
## Exploitation:
    Meterpreter_Paranoid_Mode tool starts posgresql service, builds the PEM certificate,
    builds payload (staged OR stageless), and starts the comrespondent handler associated
    to the PEM certificate created (manual) OR impersonated (msf auxliary module) ..
![Meterpreter_Paranoid_Mode v1.3](http://3.1m.yt/quzn56A.png)

## Payloads available:
    Staged (payload.bat|ps1|txt):
    windows/meterpreter/reverse_winhttps
    windows/meterpreter/reverse_https
    windows/x64/meterpreter/reverse_https

    Stageless (binary.exe):
    windows/meterpreter_reverse_https
    windows/x64/meterpreter_reverse_https

<br /><br />

## Dependencies/Limitations:
    xterm, zenity, metasploit, postgresql


    WARNING: This tool will NOT evade AV detection, its made to prevent the data
    beeing transmited from client (payload) to server beeing captured (Eavesdropping)

    WARNING: If you decided to use a 64bit payload, then edit settings file and change
    'MSF_ENCODER=x86/shikata_ga_nai' to one payload arch compatible encoder(64bit)

    WARNING: Only in 'staged' builds, Users are allowed to chose the extension (bat|ps1|txt)
    WARNING: 'Staged' payloads in this tool will not use the .exe extension
![Meterpreter_Paranoid_Mode v1.3](http://1.1m.yt/wzgG0m.png)

<br /><br />

## Config Settings file
msf postgresql database connection check? (msfdb reinit)
![Meterpreter_Paranoid_Mode v1.3](http://1.1m.yt/tLKSkOQ.png)
Default payload extension (output) to use in staged builds
![Meterpreter_Paranoid_Mode v1.3](http://1.1m.yt/UuJ7dTt.png)
Metasploit encoder to use in obfuscating payload sourcecode
![Meterpreter_Paranoid_Mode v1.3](http://4.1m.yt/klS2vq.png)
Default msf post module to run at session creation
![Meterpreter_Paranoid_Mode v1.3](http://3.1m.yt/JWulri.png)

<br /><br />

## Download/Install/Config:
    1º - Download framework from github
         git clone https://github.com/r00t-3xp10it/Meterpreter_Paranoid_Mode-SSL.git

    2º - Set files execution permitions
         cd Meterpreter_Paranoid_Mode-SSL
         sudo chmod +x *.sh

    3º - Config tool settings
         nano settings

    4º - Run main tool
         sudo ./Meterpreter_Paranoid_Mode.sh

<br /><br />

## Tool screenshots
![Meterpreter_Paranoid_Mode v1.3](http://1.1m.yt/em7t0J6.png)
![Meterpreter_Paranoid_Mode v1.3](http://2.1m.yt/ws0tkJU.png)
![Meterpreter_Paranoid_Mode v1.3](http://2.1m.yt/5dgO89S.png)

<br />

## Video tutorials:
Meterpreter_Paranoid_Mode [ Stageless payload - exe ]: https://www.youtube.com/watch?v=czbpD_4Mcdw

Meterpreter_Paranoid_Mode [ Staged payload - ps1 ]: ---

<br />

### Special thanks (POCs):
**@hdmoore** | **@OJ** | **@darkoperator**

http://buffered.io/posts/staged-vs-stageless-handlers/

https://github.com/rapid7/metasploit-framework/wiki/Meterpreter-Paranoid-Mode

https://www.darkoperator.com/blog/2015/6/14/tip-meterpreter-ssl-certificate-validation

**Suspicious-Shell-Activity (SSA) RedTeam develop @2017**
