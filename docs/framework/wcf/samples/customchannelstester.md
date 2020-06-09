---
title: CustomChannelsTester
ms.date: 03/30/2017
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
ms.openlocfilehash: 9123167e0f97592592765f7b4a4aa768064fc173
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596607"
---
# <a name="customchannelstester"></a>CustomChannelsTester
`CustomChannelsTester`To narzędzie, którego można użyć do testowania niestandardowych implementacji kanałów w oparciu o zestaw wstępnie zdefiniowanych kontraktów usługi. Można wybrać zestaw umów usługi i przekazać go do narzędzia przy użyciu pliku XML. Narzędzie generuje następnie usługę i klienta, który wykonuje niestandardowe implementacje kanałów podczas wymiany komunikatów.  
  
### <a name="to-build-the-tool"></a>Aby skompilować narzędzie  
  
1. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
2. Kompilowanie rozwiązania generuje trzy pliki: CustomChannelsTester. exe, TestSpec. XML i SampleRun. cmd. Plik SampleRun. cmd zawiera przykładowy wiersz polecenia, który pokazuje, jak używać tego narzędzia do testowania [transportu: przykład protokołu UDP](transport-udp.md) .  
  
### <a name="to-run-the-tool"></a>Aby uruchomić narzędzie  
  
- W wierszu polecenia wpisz następujące polecenie:  
  
    ```console  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     Korzystanie z tej `/binding` opcji jest wymagane.  
  
     `/dll`jest wymagana, jeśli "Binding" nie jest powiązaniem dostarczonym przez system Windows Communication Foundation (WCF).  
  
     Parametr `/testspec` jest opcjonalny.  
  
     Spowoduje to utworzenie serwera i klientów na podstawie specyfikacji testów i powiązania.  
  
     Wykonuje klienta i serwer i zwraca wyniki.  
  
     Poniżej znajduje się przykładowy kod XML opisujący specyfikacje testu (TestSpec. xml):  
  
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
