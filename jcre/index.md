# Runtime Environment Specification for the Java Card Platform  
# Java 卡运行时规范

### Version 2.2.2 3-8-06
### 版本 2.2.2 06年8月3日

## Contents
## 目录

### Figures
### Preface 
### 1. Introduction 
### 1. 简介
### 2. Lifetime of the Java Card Virtual Machine 
### 3. Java Card Applet Lifetime 
#### 3.1 install Method 
#### 3.2 select Method 
#### 3.3 process Method 
#### 3.4 deselect Method(s) 
#### 3.5 uninstall Method 
#### 3.6 Power Loss and Reset 
#### 3.6.1 Concurrent Operations Over Multiple Interfaces 
### 4. Logical Channels and Applet Selection 
#### 4.1 Default Applets 
#### 4.1.1 Card Reset Behavior 
#### 4.1.2 Proximity Card (PICC) Activation Behavior 
#### 4.1.3 Default Applet Selection Behavior on Opening a New Channel 
#### 4.2 Multiselectable Applets 
#### 4.3 Forwarding APDU Commands To a Logical Channel 
#### 4.4 Opening and Closing Logical Channels 
#### 4.4.1 MANAGE CHANNEL Command Processing 
#### 4.5 Applet Selection 
#### 4.5.1 Applet Selection with MANAGE CHANNEL OPEN 
#### 4.5.2 Applet Selection with SELECT FILE 
#### 4.6 Applet Deselection 
#### 4.6.1 MANAGE CHANNEL CLOSE Command 
#### 4.7 Other Command Processing 
### 5. Transient Objects 
#### 5.1 Events That Clear Transient Objects 
### 6. Applet Isolation and Object Sharing 
#### 6.1 Applet Firewall 
#### 6.1.1 Firewall Protection 
#### 6.1.2 Contexts and Context Switching 
#### 6.1.2.1 Active Contexts in the VM 
#### 6.1.2.2 Context Switching in the VM 
#### 6.1.3 Object Ownership 
#### 6.1.4 Object Access 
#### 6.1.5 Transient Objects and Contexts 
#### 6.1.6 Static Fields and Methods 
#### 6.1.6.1 Optional Static Access Checks 
#### 6.2 Object Access Across Contexts 
#### 6.2.1 Java Card RE Entry Point Objects 
#### 6.2.2 Global Arrays 
#### 6.2.3 Java Card RE Privileges 
#### 6.2.4 Shareable Interfaces 
#### 6.2.4.1 Server Applet A Builds a Shareable Interface Object 
#### 6.2.4.2 Client Applet B Obtains the Shareable Interface Object 
#### 6.2.4.3 Client Applet B Requests Services from Applet A 
#### 6.2.5 Determining the Previous Context 
#### 6.2.5.1 Java Card RE Context 
#### 6.2.6 Shareable Interface Details 
#### 6.2.6.1 Java Card API Shareable Interface 
#### 6.2.7 Obtaining Shareable Interface Objects 
#### 6.2.7.1 Applet.getShareableInterfaceObject(AID, byte) Method 
#### 6.2.7.2 JCSystem.getAppletShareableInterfaceObject Method 
#### 6.2.8 Class and Object Access Behavior 
#### 6.2.8.1 Accessing Static Class Fields 
#### 6.2.8.2 Accessing Array Objects 
#### 6.2.8.3 Accessing Class Instance Object Fields 
#### 6.2.8.4 Accessing Class Instance Object Methods 
#### 6.2.8.5 Accessing Standard Interface Methods 
#### 6.2.8.6 Accessing Shareable Interface Methods 
#### 6.2.8.7 Throwing Exception Objects 
#### 6.2.8.8 Accessing Classes 
#### 6.2.8.9 Accessing Standard Interfaces 
#### 6.2.8.10 Accessing Shareable Interfaces 
#### 6.2.8.11 Accessing Array Object Methods 
###  7. Transactions and Atomicity 
#### 7.1 Atomicity 
#### 7.2 Transactions 
#### 7.3 Transaction Duration 
#### 7.4 Nested Transactions 
#### 7.5 Tear or Reset Transaction Failure 
#### 7.6 Aborting a Transaction 
#### 7.6.1 Programmatic Abortion 
#### 7.6.2 Abortion by the Java Card RE 
#### 7.6.3 Cleanup Responsibilities of the Java Card RE 
#### 7.7 Transient Objects and Global Arrays 
#### 7.8 Commit Capacity 
#### 7.9 Context Switching 
### 8. Remote Method Invocation Service 
#### 8.1 Java Card Platform RMI 
#### 8.1.1 Remote Objects 
#### 8.1.1.1 Parameters and Return Values 
#### 8.1.1.2 Exceptions 
#### 8.1.1.3 Functional Limitations 
#### 8.2 RMI Messages 
#### 8.2.1 Applet Selection 
#### 8.2.2 Method Invocation 
#### 8.3 Data Formats 
#### 8.3.1 Remote Object Identifier 
#### 8.3.2 Remote Object Reference Descriptor 
#### 8.3.3 Method Identifier 
#### 8.3.4 Parameter Encoding 
#### 8.3.4.1 Primitive Data Type Parameter Encoding 
#### 8.3.4.2 Array Parameter Encoding 
#### 8.3.5 Return Value Encoding 
#### 8.3.5.1 Normal Response Encoding 
#### 8.3.5.2 Exception Response Encoding 
#### 8.3.5.3 Error Response Encoding 
#### 8.4 APDU Command Formats 
#### 8.4.1 SELECT FILE Command 
#### 8.4.2 INVOKE Command 
#### 8.5 RMIService Class 
#### 8.5.1 setInvokeInstructionByte Method 
#### 8.5.2 processCommand Method 
### 9. API Topics 
#### 9.1 Resource Use Within the API 
#### 9.2 Exceptions Thrown by API Classes 
#### 9.3 Transactions Within the API 
#### 9.4 APDU Class 
#### 9.4.1 T=0 Specifics for Outgoing Data Transfers 
#### 9.4.1.1 Constrained Transfers With No Chaining 
#### 9.4.1.2 Regular Output Transfers 
#### 9.4.1.3 Additional T=0 Requirements 
#### 9.4.2 T=1 Specifics for Outgoing Data Transfers 
#### 9.4.2.1 Constrained Transfers With No Chaining 
#### 9.4.2.2 Regular Output Transfers 
#### 9.4.3 T=1 Specifics for Incoming Data Transfers 
#### 9.4.3.1 Incoming Transfers Using Chaining 
#### 9.4.4 Extended Length APDU Specifics 
#### 9.4.4.1 Extended Length API Semantics 
#### 9.5 Security and Crypto Packages 
#### 9.6 JCSystem Class 
#### 9.7 Optional Extension Packages 
### 10. Virtual Machine Topics 
#### 10.1 Resource Failures 
#### 10.2 Security Violations 
### 11. Applet Installation and Deletion 
#### 11.1 The Installer 
#### 11.1.1 Installer Implementation 
#### 11.1.2 Installer AID 
#### 11.1.3 Installer APDUs 
#### 11.1.4 CAP File Versions 
#### 11.1.5 Installer Behavior 
#### 11.1.6 Installer Privileges 
#### 11.2 The Newly Installed Applet 
#### 11.2.1 Installation Parameters 
#### 11.3 The Applet Deletion Manager 
#### 11.3.1 Applet Deletion Manager Implementation 
#### 11.3.2 Applet Deletion Manager AID 
#### 11.3.3 Applet Deletion Manager APDUs 
#### 11.3.4 Applet Deletion Manager Behavior 
#### 11.3.4.1 Applet Instance Deletion 
#### 11.3.4.2 Applet/Library Package Deletion 
#### 11.3.4.3 Applet Package and Contained Instances Deletion 
#### 11.3.5 Applet Deletion Manager Privileges 
### 12. API Constants 
#### 12.1 Class javacard.framework.APDU  
#### 12.2 Class javacard.framework.APDUException  
#### 12.3 Interface javacard.framework.ISO7816  
#### 12.4 Class javacard.framework.JCSystem  
#### 12.5 Class javacard.framework.PINException  
#### 12.6 Class javacard.framework.SystemException  
#### 12.7 Class javacard.framework.TransactionException  
#### 12.8 Class javacard.framework.service.Dispatcher  
#### 12.9 Class javacard.framework.service.RMIService  
#### 12.10 Class javacard.framework.service.ServiceException  
#### 12.11 Class javacard.security.Checksum  
#### 12.12 Class javacard.security.CryptoException  
#### 12.13 Class javacard.security.KeyAgreement  
#### 12.14 Class javacard.security.KeyBuilder  
#### 12.15 Class javacard.security.KeyPair  
#### 12.16 Class javacard.security.MessageDigest  
#### 12.17 Class javacard.security.RandomData  
#### 12.18 Class javacard.security.Signature  
#### 12.19 Class javacardx.biometry.BioBuilder  
#### 12.20 Class javacardx.biometry.BioException  
#### 12.21 Class javacardx.biometry.BioTemplate  
#### 12.22 Class javacardx.crypto.Cipher  
#### 12.23 Class javacardx.external.ExternalExeption  
#### 12.24 Class javacardx.external.Memory  
#### 12.25 Class javacardx.framework.math.BigNumber  
#### 12.26 Class javacardx.framework.tlv.BERTag  
#### 12.27 Class javacardx.framework.tlv.TLVException  
#### 12.28 Class javacardx.framework.util.UtilException  
Glossary 
Index 
