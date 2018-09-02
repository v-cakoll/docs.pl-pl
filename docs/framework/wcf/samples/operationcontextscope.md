---
title: OperationContextScope
ms.date: 03/30/2017
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
ms.openlocfilehash: 09ead071c5d8320452724edbb1c7f7f5e0124421
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395007"
---
# <a name="operationcontextscope"></a><span data-ttu-id="55ca7-102">OperationContextScope</span><span class="sxs-lookup"><span data-stu-id="55ca7-102">OperationContextScope</span></span>
<span data-ttu-id="55ca7-103">Przykładowy element OperationContextScope pokazano sposób wysyłania dodatkowych informacji na temat wywołania usług Windows Communication Foundation (WCF) przy użyciu nagłówków.</span><span class="sxs-lookup"><span data-stu-id="55ca7-103">The OperationContextScope sample demonstrates how to send extra information on a Windows Communication Foundation (WCF) call using headers.</span></span> <span data-ttu-id="55ca7-104">W tym przykładzie serwera i klienta są aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="55ca7-104">In this sample, both the server and client are console applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55ca7-105">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="55ca7-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="55ca7-106">W przykładzie pokazano, jak klient może wysłać dodatkowe informacje jako <xref:System.ServiceModel.Channels.MessageHeader> przy użyciu <xref:System.ServiceModel.OperationContextScope>.</span><span class="sxs-lookup"><span data-stu-id="55ca7-106">The sample demonstrates how a client can send additional information as a <xref:System.ServiceModel.Channels.MessageHeader> using <xref:System.ServiceModel.OperationContextScope>.</span></span> <span data-ttu-id="55ca7-107"><xref:System.ServiceModel.OperationContextScope> Obiekt jest tworzony przez zakresu go do kanału.</span><span class="sxs-lookup"><span data-stu-id="55ca7-107">An <xref:System.ServiceModel.OperationContextScope> object is created by scoping it to a channel.</span></span> <span data-ttu-id="55ca7-108">Nagłówki, które muszą być przetłumaczone do zdalnej usługi mogą być dodawane do <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="55ca7-108">Headers that must be translated to the remote service can be added to the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="55ca7-109">Nagłówki dodane do tej kolekcji mogą być pobierane, uzyskując dostęp do usługi <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span><span class="sxs-lookup"><span data-stu-id="55ca7-109">Headers added to this collection can be retrieved on the service by accessing <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span></span> <span data-ttu-id="55ca7-110">Jego wywołań za pośrednictwem różnych kanałów i następnie nagłówki dodane do klienta mają zastosowanie tylko do kanału, który został użyty do utworzenia <xref:System.ServiceModel.OperationContextScope>.</span><span class="sxs-lookup"><span data-stu-id="55ca7-110">Its calls are made on multiple channels and then the headers added to the client only apply to the channel that was used to create the <xref:System.ServiceModel.OperationContextScope>.</span></span>  
  
## <a name="messageheaderreader"></a><span data-ttu-id="55ca7-111">MessageHeaderReader</span><span class="sxs-lookup"><span data-stu-id="55ca7-111">MessageHeaderReader</span></span>  
 <span data-ttu-id="55ca7-112">To jest usługa próbki, która otrzymuje komunikat z klienta i podejmuje próbę wyszukiwania nagłówka w <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="55ca7-112">This is the sample service that receives a message from the client and tries to look up the header in the <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="55ca7-113">Klient przekazuje identyfikator GUID, który on wysyłany w nagłówku i pobiera niestandardowych nagłówków i, jeśli jest obecny, porównuje go z identyfikatorem GUID przekazany jako argument przez klienta.</span><span class="sxs-lookup"><span data-stu-id="55ca7-113">The client passes the GUID that it sent in the header and the service retrieves the custom header and, if present, compares it with the GUID passed as the argument by the client.</span></span>  
  
```  
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
  
## <a name="messageheaderclient"></a><span data-ttu-id="55ca7-114">MessageHeaderClient</span><span class="sxs-lookup"><span data-stu-id="55ca7-114">MessageHeaderClient</span></span>  
 <span data-ttu-id="55ca7-115">Jest to implementacji klienta, który używa serwera proxy generowany przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do komunikowania się z usługi zdalnej.</span><span class="sxs-lookup"><span data-stu-id="55ca7-115">This is the client implementation that uses the proxy generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to communicate with the remote service.</span></span> <span data-ttu-id="55ca7-116">Najpierw tworzy dwa obiekty proxy `MessageHeaderReaderClient`.</span><span class="sxs-lookup"><span data-stu-id="55ca7-116">It first creates two proxy objects of `MessageHeaderReaderClient`.</span></span>  
  
```  
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 <span data-ttu-id="55ca7-117">Klient następnie tworzy element OperationContextScope i jego zakresów `client1`.</span><span class="sxs-lookup"><span data-stu-id="55ca7-117">Client then creates an OperationContextScope and scopes it to `client1`.</span></span> <span data-ttu-id="55ca7-118">Dodaje <xref:System.ServiceModel.Channels.MessageHeader> do <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> i wywołuje jedno wywołanie na obu komputerach klienckich.</span><span class="sxs-lookup"><span data-stu-id="55ca7-118">It adds a <xref:System.ServiceModel.Channels.MessageHeader> to <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> and invokes one call on both clients.</span></span> <span data-ttu-id="55ca7-119">Gwarantuje to, że nagłówek jest wysyłany tylko na `client1` a nie w systemie `client2` , sprawdzając wartość zwrotną z elementu `RetrieveHeader` wywołania.</span><span class="sxs-lookup"><span data-stu-id="55ca7-119">It ensures that the header is sent only on `client1` and not on `client2` by checking the return value from the `RetrieveHeader` call.</span></span>  
  
```  
using (new OperationContextScope(client1.InnerChannel))  
{  
    //Create a new GUID that is sent as the header.  
    String guid = Guid.NewGuid().ToString();  
  
    //Create a MessageHeader for the GUID we just created.  
    MessageHeader customHeader = MessageHeader.CreateHeader(CustomHeader.HeaderName, CustomHeader.HeaderNamespace, guid);  
  
    //Add the header to the OutgoingMessageHeader collection.  
    OperationContext.Current.OutgoingMessageHeaders.Add(customHeader);  
  
    //Now call RetreieveHeader on both the proxies. Since the OperationContextScope is tied to   
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
  
 <span data-ttu-id="55ca7-120">W tym przykładzie jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="55ca7-120">This sample is self-hosted.</span></span> <span data-ttu-id="55ca7-121">Następujące przykładowe dane wyjściowe z działa aplikacja przykładowa została zapewniona:</span><span class="sxs-lookup"><span data-stu-id="55ca7-121">The following sample output from running the sample is provided:</span></span>  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="55ca7-122">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="55ca7-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="55ca7-123">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="55ca7-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="55ca7-124">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="55ca7-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="55ca7-125">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="55ca7-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="55ca7-126">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="55ca7-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="55ca7-127">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="55ca7-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="55ca7-128">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="55ca7-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="55ca7-129">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="55ca7-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
  
## <a name="see-also"></a><span data-ttu-id="55ca7-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55ca7-130">See Also</span></span>
