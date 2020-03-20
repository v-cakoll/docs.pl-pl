---
title: CustomChannelsTester
ms.date: 03/30/2017
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
ms.openlocfilehash: c23bd3eddd49972b7083347fed88d4e70707ae58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183810"
---
# <a name="customchannelstester"></a>CustomChannelsTester
Jest `CustomChannelsTester` to narzędzie, którego można użyć do testowania implementacji kanału niestandardowego względem zestawu wstępnie zdefiniowanych umów serwisowych. Można wybrać zestaw umów serwisowych i przekazać go do narzędzia za pomocą pliku XML. Narzędzie następnie generuje usługę i klienta, który wykonuje implementacje kanału niestandardowego podczas wymiany wiadomości.  
  
### <a name="to-build-the-tool"></a>Aby zbudować narzędzie  
  
1. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Tworzenie rozwiązania generuje trzy pliki: CustomChannelsTester.exe, TestSpec.xml i SampleRun.cmd. Plik SampleRun.cmd ma przykładowy wiersz polecenia, który pokazuje, jak użyć tego narzędzia do [testowania przykładu Transport: UDP.](../../../../docs/framework/wcf/samples/transport-udp.md)  
  
### <a name="to-run-the-tool"></a>Aby uruchomić narzędzie  
  
- W wierszu polecenia wpisz następujące polecenie:  
  
    ```console  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     Użycie `/binding` tej opcji jest wymagane.  
  
     `/dll`jest wymagane, jeśli "powiązanie" nie jest powiązanie dostarczone przez system dostarczone przez Windows Communication Foundation (WCF).  
  
     Parametr `/testspec` jest opcjonalny.  
  
     Spowoduje to utworzenie serwera i klientów na podstawie specyfikacji testu i powiązania.  
  
     Wykonuje klienta i serwera i zwraca wyniki.  
  
     Poniżej znajduje się przykładowy kod XML opis specyfikacji badań (testspec.xml):  
  
    ```xml  
    <TestSpec xmlns="http://WCF/TestSpec" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" >  
    <ServiceContract>  
    <!-- Test a contract which has oneway / twoway operations. If you set ExpandAll = true, both types of contracts are tested -->    <IsOneWay ExpandAll="true">true</IsOneWay>  
    <!-- Test a contract with Asynchronous / Synchronous Operations-->  
        <IsAsync>false</IsAsync>
    <!-- Test a sessionful / sessionless contract-->
        <IsSession ExpandAll="true">true</IsSession>  
    <!-- If the Service Contract includes a CallBack Contract-->
        <IsCallBack ExpandAll="true">true</IsCallBack>  
    </ServiceContract>  
    <TestDetails>  
    <!-- Name of the machine that runs the server - required if you want to run the test crossmachine-->  
        <ServerName>ReplaceThisWithTheServerMachineName</ServerName>  
    <!-- Port Number - Optional-->  
        <Port>8000</Port>  
    <!--URI for the callBack address for the client. The client will receive the messages from the server on this address in case of a CallBack Contract-->  
        <ClientCallBackAddress/>
    <!-- Duration (in sec) after the server has started, it times out - optional(default = 300sec) -->  
        <ServerTimeout>300</ServerTimeout>  
    <!-- Duration (in sec) before the Client initializes -optional(default = 60sec) -->  
        <ClientTimeout>60</ClientTimeout>  
    <!-- Number of clients for each service - optional(default = 1) -->  
        <NumberOfClients>1</NumberOfClients>  
    <!-- Number of messages each client sends to the service - optional(default = 1) -->  
        <MessagesPerClient>1</MessagesPerClient>  
    </TestDetails>  
    </TestSpec>  
    ```  
