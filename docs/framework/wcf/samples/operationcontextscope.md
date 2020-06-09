---
title: OperationContextScope
ms.date: 03/30/2017
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
ms.openlocfilehash: 0b2b4d9b22f654fa433c7473160444b41a5adfa4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575159"
---
# <a name="operationcontextscope"></a><span data-ttu-id="fdbd1-102">OperationContextScope</span><span class="sxs-lookup"><span data-stu-id="fdbd1-102">OperationContextScope</span></span>
<span data-ttu-id="fdbd1-103">Przykład OperationContextScope demonstruje sposób wysyłania dodatkowych informacji na temat wywołania Windows Communication Foundation (WCF) przy użyciu nagłówków.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-103">The OperationContextScope sample demonstrates how to send extra information on a Windows Communication Foundation (WCF) call using headers.</span></span> <span data-ttu-id="fdbd1-104">W tym przykładzie zarówno serwer, jak i klient są aplikacjami konsolowymi.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-104">In this sample, both the server and client are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fdbd1-105">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fdbd1-106">W przykładzie pokazano, jak klient może wysyłać dodatkowe informacje za <xref:System.ServiceModel.Channels.MessageHeader> pomocą <xref:System.ServiceModel.OperationContextScope> .</span><span class="sxs-lookup"><span data-stu-id="fdbd1-106">The sample demonstrates how a client can send additional information as a <xref:System.ServiceModel.Channels.MessageHeader> using <xref:System.ServiceModel.OperationContextScope>.</span></span> <span data-ttu-id="fdbd1-107"><xref:System.ServiceModel.OperationContextScope>Obiekt jest tworzony przez przeznaczanie go na kanał.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-107">An <xref:System.ServiceModel.OperationContextScope> object is created by scoping it to a channel.</span></span> <span data-ttu-id="fdbd1-108">Do kolekcji można dodawać nagłówki, które muszą być tłumaczone do usługi zdalnej <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> .</span><span class="sxs-lookup"><span data-stu-id="fdbd1-108">Headers that must be translated to the remote service can be added to the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="fdbd1-109">Nagłówki dodane do tej kolekcji można pobrać w usłudze, uzyskując dostęp do programu <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> .</span><span class="sxs-lookup"><span data-stu-id="fdbd1-109">Headers added to this collection can be retrieved on the service by accessing <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span></span> <span data-ttu-id="fdbd1-110">Wywołania są wykonywane w wielu kanałach, a następnie nagłówki dodane do klienta dotyczą tylko kanału, który został użyty do utworzenia <xref:System.ServiceModel.OperationContextScope> .</span><span class="sxs-lookup"><span data-stu-id="fdbd1-110">Its calls are made on multiple channels and then the headers added to the client only apply to the channel that was used to create the <xref:System.ServiceModel.OperationContextScope>.</span></span>  
  
## <a name="messageheaderreader"></a><span data-ttu-id="fdbd1-111">MessageHeaderReader</span><span class="sxs-lookup"><span data-stu-id="fdbd1-111">MessageHeaderReader</span></span>  
 <span data-ttu-id="fdbd1-112">Jest to przykładowa usługa, która odbiera komunikat od klienta i próbuje wyszukać nagłówek w <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-112">This is the sample service that receives a message from the client and tries to look up the header in the <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="fdbd1-113">Klient przekazuje identyfikator GUID, który został wysłany w nagłówku, a usługa pobiera niestandardowy nagłówek i, jeśli istnieje, porównuje go z identyfikatorem GUID przekazywanym jako argument przez klienta.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-113">The client passes the GUID that it sent in the header and the service retrieves the custom header and, if present, compares it with the GUID passed as the argument by the client.</span></span>  
  
```csharp
public bool RetrieveHeader(string guid)  
{  
     MessageHeaders messageHeaderCollection =
             OperationContext.Current.IncomingMessageHeaders;  
     String guidHeader = null;  
  
     Console.WriteLine("Trying to check if IncomingMessageHeader " +  
               " collection contains header with value {0}", guid);  
     if (messageHeaderCollection.FindHeader(  
                       CustomHeader.HeaderName,
                       CustomHeader.HeaderNamespace) != -1)  
     {  
          guidHeader = messageHeaderCollection.GetHeader<String>(  
           CustomHeader.HeaderName, CustomHeader.HeaderNamespace);  
     }  
     else  
     {  
          Console.WriteLine("No header was found");  
     }  
     if (guidHeader != null)  
     {  
          Console.WriteLine("Found header with value {0}. "+
         "Does it match with GUID sent as parameter: {1}",
          guidHeader, guidHeader.Equals(guid));  
      }  
  
      Console.WriteLine();  
      //Return true if header is present and equals the guid sent by  
      // client as argument  
      return (guidHeader != null && guidHeader.Equals(guid));  
}  
```  
  
## <a name="messageheaderclient"></a><span data-ttu-id="fdbd1-114">MessageHeaderClient</span><span class="sxs-lookup"><span data-stu-id="fdbd1-114">MessageHeaderClient</span></span>  
 <span data-ttu-id="fdbd1-115">Jest to implementacja klienta, która używa serwera proxy wygenerowanego przez narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) do komunikowania się z usługą zdalną.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-115">This is the client implementation that uses the proxy generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to communicate with the remote service.</span></span> <span data-ttu-id="fdbd1-116">Najpierw tworzy dwa obiekty proxy programu `MessageHeaderReaderClient` .</span><span class="sxs-lookup"><span data-stu-id="fdbd1-116">It first creates two proxy objects of `MessageHeaderReaderClient`.</span></span>  
  
```csharp
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 <span data-ttu-id="fdbd1-117">Następnie klient tworzy OperationContextScope i zakresy, do `client1` .</span><span class="sxs-lookup"><span data-stu-id="fdbd1-117">Client then creates an OperationContextScope and scopes it to `client1`.</span></span> <span data-ttu-id="fdbd1-118">Dodaje <xref:System.ServiceModel.Channels.MessageHeader> do <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> i wywołuje jedno wywołanie na obu klientach.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-118">It adds a <xref:System.ServiceModel.Channels.MessageHeader> to <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> and invokes one call on both clients.</span></span> <span data-ttu-id="fdbd1-119">Zapewnia, że nagłówek jest wysyłany tylko w przypadku, gdy `client1` nie jest on włączony, `client2` sprawdzając wartość zwracaną z `RetrieveHeader` wywołania.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-119">It ensures that the header is sent only on `client1` and not on `client2` by checking the return value from the `RetrieveHeader` call.</span></span>  
  
```csharp
using (new OperationContextScope(client1.InnerChannel))  
{  
    //Create a new GUID that is sent as the header.  
    String guid = Guid.NewGuid().ToString();  
  
    //Create a MessageHeader for the GUID we just created.  
    MessageHeader customHeader = MessageHeader.CreateHeader(CustomHeader.HeaderName, CustomHeader.HeaderNamespace, guid);  
  
    //Add the header to the OutgoingMessageHeader collection.  
    OperationContext.Current.OutgoingMessageHeaders.Add(customHeader);  
  
    //Now call RetrieveHeader on both the proxies. Since the OperationContextScope is tied to
    //client1's InnerChannel, the header should only be added to calls made on that client.  
    //Calls made on client2 should not be sending the header across even though the call  
    //is made in the same OperationContextScope.  
    Console.WriteLine("Using client1 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: True", client1.RetrieveHeader(guid));  
  
    Console.WriteLine();  
    Console.WriteLine("Using client2 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: False", client2.RetrieveHeader(guid));  
}  
```  
  
 <span data-ttu-id="fdbd1-120">Ten przykład jest samodzielny.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-120">This sample is self-hosted.</span></span> <span data-ttu-id="fdbd1-121">Dostępne są następujące przykładowe dane wyjściowe z uruchamiania przykładu:</span><span class="sxs-lookup"><span data-stu-id="fdbd1-121">The following sample output from running the sample is provided:</span></span>  
  
```console  
Prompt> Service.exe  
The service is ready.  
Press <ENTER> to terminate service.  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
Found header with value 2239da67-546f-42d4-89dc-8eb3c06215d8. Does it match with GUID sent as parameter: True  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
No header was found  
  
Prompt>Client.exe  
Using client1 to send message  
Did server retrieve the header? : Actual: True, Expected: True  
  
Using client2 to send message  
Did server retrieve the header? : Actual: False, Expected: False  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fdbd1-122">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="fdbd1-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fdbd1-123">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fdbd1-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fdbd1-124">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fdbd1-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="fdbd1-125">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fdbd1-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fdbd1-126">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fdbd1-127">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="fdbd1-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="fdbd1-128">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fdbd1-129">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
