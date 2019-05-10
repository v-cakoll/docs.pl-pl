---
title: CustomChannelsTester
ms.date: 03/30/2017
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
ms.openlocfilehash: dbd10d1bd08529d11e86c3d9296e68264564a21d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650151"
---
# <a name="customchannelstester"></a>CustomChannelsTester
`CustomChannelsTester` To narzędzie, które można użyć do testowania implementacji usługi niestandardowym kanale z zestawem kontraktów predefiniowaną usługę. Można wybrać zestaw kontraktów usług i przekazać go do narzędzia, za pomocą pliku XML. Narzędzie generuje następnie usługi i klienta, który korzysta z implementacjami niestandardowym kanale podczas wymiany komunikatów.  
  
### <a name="to-build-the-tool"></a>Aby utworzyć narzędzie  
  
1. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Skompilować rozwiązanie generuje trzy pliki: CustomChannelsTester.exe, TestSpec.xml and SampleRun.cmd. Plik SampleRun.cmd zawiera przykładowy wiersz polecenia, który pokazuje, jak używać tego narzędzia do testowania [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.  
  
### <a name="to-run-the-tool"></a>Aby uruchomić narzędzie  
  
- W wierszu polecenia wpisz następujące polecenie:  
  
    ```  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     Za pomocą `/binding` opcja jest wymagana.  
  
     `/dll` jest wymagany, jeśli "powiązanie" nie jest dostarczane przez system powiązania dostarczane przez Windows Communication Foundation (WCF).  
  
     `/testspec` jest opcjonalne.  
  
     Spowoduje to utworzenie serwera i klientów na podstawie specyfikacji testowego i wiązania.  
  
     Uruchamia klienta i serwera i zwraca wyniki.  
  
     Poniżej przedstawiono przykładowy kod XML do opisu testu specyfikacje (testspec.xml):  
  
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
    <!--URI for the callBack address for the CLient. The client will receive the messages from the server on this address in case of a CallBack Contract-->  
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
