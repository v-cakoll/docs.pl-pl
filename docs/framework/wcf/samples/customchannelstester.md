---
title: CustomChannelsTester
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 802d501dabbf14d30a26cd682afb366f0a83a17a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="customchannelstester"></a><span data-ttu-id="2b979-102">CustomChannelsTester</span><span class="sxs-lookup"><span data-stu-id="2b979-102">CustomChannelsTester</span></span>
<span data-ttu-id="2b979-103">`CustomChannelsTester` To narzędzie, które służy do testowania implementacjach użytkownika niestandardowym kanale z zestawem kontraktów usług wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="2b979-103">The `CustomChannelsTester` is a tool that you can use to test your custom channel implementations against a set of predefined service contracts.</span></span> <span data-ttu-id="2b979-104">Możesz wybrać zestaw kontraktów usług i przekaż go za pomocą pliku XML.</span><span class="sxs-lookup"><span data-stu-id="2b979-104">You can select the set of service contracts and pass it to the tool using an XML file.</span></span> <span data-ttu-id="2b979-105">Narzędzie generuje następnie usługi i klienta, który korzysta z implementacji niestandardowego kanału podczas wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2b979-105">The tool then generates the service and client that exercises your custom channel implementations during message exchange.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="2b979-106">Aby utworzyć narzędzie</span><span class="sxs-lookup"><span data-stu-id="2b979-106">To build the tool</span></span>  
  
1.  <span data-ttu-id="2b979-107">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2b979-107">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="2b979-108">Tworzenie rozwiązania generuje trzy pliki: CustomChannelsTester.exe, TestSpec.xml i SampleRun.cmd.</span><span class="sxs-lookup"><span data-stu-id="2b979-108">Building the solution generates three files: CustomChannelsTester.exe, TestSpec.xml and SampleRun.cmd.</span></span> <span data-ttu-id="2b979-109">Plik SampleRun.cmd zawiera przykładowy wiersz polecenia, który przedstawia sposób użycia tego narzędzia do testowania [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="2b979-109">The file SampleRun.cmd has a sample command line that shows how to use this tool to test the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="2b979-110">Aby uruchomić narzędzie</span><span class="sxs-lookup"><span data-stu-id="2b979-110">To run the tool</span></span>  
  
-   <span data-ttu-id="2b979-111">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="2b979-111">At the command prompt type the following command:</span></span>  
  
    ```  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     <span data-ttu-id="2b979-112">Przy użyciu `/binding` opcja jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="2b979-112">Using the `/binding` option is required.</span></span>  
  
     <span data-ttu-id="2b979-113">`/dll`jest wymagany, jeśli "powiązanie" nie jest udostępniane przez powiązania dostarczane przez system [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2b979-113">`/dll` is required if "binding" is not a system-provided binding provided by [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
     <span data-ttu-id="2b979-114">`/testspec`jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="2b979-114">`/testspec` is optional.</span></span>  
  
     <span data-ttu-id="2b979-115">Spowoduje to utworzenie serwer i klienci na podstawie specyfikacji testu i powiązania.</span><span class="sxs-lookup"><span data-stu-id="2b979-115">This creates server and clients based on the test specifications and the binding.</span></span>  
  
     <span data-ttu-id="2b979-116">Wykonuje klienta i serwera i zwraca wyniki.</span><span class="sxs-lookup"><span data-stu-id="2b979-116">Executes the client and server and returns the results.</span></span>  
  
     <span data-ttu-id="2b979-117">Poniżej przedstawiono przykładowe XML opisu specyfikacji testu (testspec.xml):</span><span class="sxs-lookup"><span data-stu-id="2b979-117">The following is the sample XML for the description of the test specifications (testspec.xml):</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2b979-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b979-118">See Also</span></span>
