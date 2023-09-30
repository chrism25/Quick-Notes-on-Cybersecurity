# <p align="center"> Sentry Exploited in the Wild

# <p align="center"> New macOS Variant

* Xloader has been around in some form or another since 2015. In 2021 its 1st macOS variant was spotted as it was being distributed as a Java program. Luckily, Java was never set as default so the targets were limited. However, the new version is written natively in the C and Objective C programming languages and signed with an Apple developer signature, the new disguise is an office productivity app “OfficeNote”.
* This new version is bundled inside a standard Apple disk image “OfficeNote.dmg”. The application contained within is signed with the developer signature MAIT JAKHU (54YDV8NU9C). Since then Apple revoked the signature, but it seems like  Apple’s malware blocking tool “XProtect” doesn’t have a signature to prevent execution of this malware at the time of writing.
* What is worrying, is that the malware seems to have been widely distributed in the wild. VirusTotal has numerous records and in some forums like “Crimeware” advertisements offer the Mac version for rental as well as the Windows one.   

*  The way that XLoader works is that when executed, an error appears indicating some malfunction. However, this is when the payload is delivered and installs a persistence agent.
At this point, the malware creates a hidden directory and constructs a barebones minimal app within it, it uses a copy of itself for the main executable. The malware cleverly randomizes the names of the hidden directory, app and executable on each execution. Additionally, a launch agent is also dropped in the library folder, to provide a start value for the executable, so the binary can distinguish between the 1st and subsequent runs.
