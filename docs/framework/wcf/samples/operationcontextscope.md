---
title: OperationContextScope
ms.date: 03/30/2017
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
ms.openlocfilehash: ce21d9d099d893015ea828bdc3b136ab83f6d8e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183435"
---
# <a name="operationcontextscope"></a><span data-ttu-id="00833-102">OperationContextScope</span><span class="sxs-lookup"><span data-stu-id="00833-102">OperationContextScope</span></span>
<span data-ttu-id="00833-103">Przykład OperationContextScope pokazuje, jak wysyłać dodatkowe informacje na wywołanie Programu Windows Communication Foundation (WCF) przy użyciu nagłówków.</span><span class="sxs-lookup"><span data-stu-id="00833-103">The OperationContextScope sample demonstrates how to send extra information on a Windows Communication Foundation (WCF) call using headers.</span></span> <span data-ttu-id="00833-104">W tym przykładzie serwer i klient są aplikacjami konsoli.</span><span class="sxs-lookup"><span data-stu-id="00833-104">In this sample, both the server and client are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00833-105">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="00833-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="00833-106">W przykładzie pokazano, jak klient może <xref:System.ServiceModel.Channels.MessageHeader> <xref:System.ServiceModel.OperationContextScope>wysyłać dodatkowe informacje jako za pomocą .</span><span class="sxs-lookup"><span data-stu-id="00833-106">The sample demonstrates how a client can send additional information as a <xref:System.ServiceModel.Channels.MessageHeader> using <xref:System.ServiceModel.OperationContextScope>.</span></span> <span data-ttu-id="00833-107">Obiekt <xref:System.ServiceModel.OperationContextScope> jest tworzony przez jego zakres do kanału.</span><span class="sxs-lookup"><span data-stu-id="00833-107">An <xref:System.ServiceModel.OperationContextScope> object is created by scoping it to a channel.</span></span> <span data-ttu-id="00833-108">Nagłówki, które muszą być przetłumaczone na usługę <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> zdalną można dodać do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="00833-108">Headers that must be translated to the remote service can be added to the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="00833-109">Nagłówki dodane do tej kolekcji można pobrać w <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>usłudze, uzyskując dostęp .</span><span class="sxs-lookup"><span data-stu-id="00833-109">Headers added to this collection can be retrieved on the service by accessing <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span></span> <span data-ttu-id="00833-110">Jego wywołania są dokonywane na wielu kanałach, a następnie nagłówki dodane do <xref:System.ServiceModel.OperationContextScope>klienta dotyczą tylko kanału, który został użyty do utworzenia pliku .</span><span class="sxs-lookup"><span data-stu-id="00833-110">Its calls are made on multiple channels and then the headers added to the client only apply to the channel that was used to create the <xref:System.ServiceModel.OperationContextScope>.</span></span>  
  
## <a name="messageheaderreader"></a><span data-ttu-id="00833-111">Czytnik nagłówków komunikatów</span><span class="sxs-lookup"><span data-stu-id="00833-111">MessageHeaderReader</span></span>  
 <span data-ttu-id="00833-112">Jest to przykładowa usługa, która odbiera komunikat od klienta i <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> próbuje wyszukać nagłówek w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="00833-112">This is the sample service that receives a message from the client and tries to look up the header in the <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="00833-113">Klient przekazuje identyfikator GUID, który został wysłany w nagłówku, a usługa pobiera niestandardowy nagłówek i, jeśli jest obecny, porównuje go z identyfikatorem GUID przekazanym jako argument przez klienta.</span><span class="sxs-lookup"><span data-stu-id="00833-113">The client passes the GUID that it sent in the header and the service retrieves the custom header and, if present, compares it with the GUID passed as the argument by the client.</span></span>  
  
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
  
## <a name="messageheaderclient"></a><span data-ttu-id="00833-114">MessageHeaderClient (Adres nagłówka wiadomości)</span><span class="sxs-lookup"><span data-stu-id="00833-114">MessageHeaderClient</span></span>  
 <span data-ttu-id="00833-115">Jest to implementacja klienta, która używa serwera proxy generowanego przez [narzędzie narzędzia Metadane ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do komunikowania się z usługą zdalną.</span><span class="sxs-lookup"><span data-stu-id="00833-115">This is the client implementation that uses the proxy generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to communicate with the remote service.</span></span> <span data-ttu-id="00833-116">Najpierw tworzy dwa obiekty `MessageHeaderReaderClient`proxy .</span><span class="sxs-lookup"><span data-stu-id="00833-116">It first creates two proxy objects of `MessageHeaderReaderClient`.</span></span>  
  
```csharp
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 <span data-ttu-id="00833-117">Klient następnie tworzy OperationContextScope i `client1`zakresy go do .</span><span class="sxs-lookup"><span data-stu-id="00833-117">Client then creates an OperationContextScope and scopes it to `client1`.</span></span> <span data-ttu-id="00833-118">Dodaje <xref:System.ServiceModel.Channels.MessageHeader> do <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> i wywołuje jedno wywołanie na obu klientach.</span><span class="sxs-lookup"><span data-stu-id="00833-118">It adds a <xref:System.ServiceModel.Channels.MessageHeader> to <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> and invokes one call on both clients.</span></span> <span data-ttu-id="00833-119">Zapewnia, że nagłówek jest wysyłany tylko na, `client1` a nie na, `client2` sprawdzając wartość zwracaną z `RetrieveHeader` wywołania.</span><span class="sxs-lookup"><span data-stu-id="00833-119">It ensures that the header is sent only on `client1` and not on `client2` by checking the return value from the `RetrieveHeader` call.</span></span>  
  
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
  
 <span data-ttu-id="00833-120">Ten przykład jest hostowany samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="00833-120">This sample is self-hosted.</span></span> <span data-ttu-id="00833-121">Dostarczane są następujące przykładowe dane wyjściowe z uruchomienia próbki:</span><span class="sxs-lookup"><span data-stu-id="00833-121">The following sample output from running the sample is provided:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="00833-122">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="00833-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="00833-123">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="00833-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="00833-124">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="00833-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="00833-125">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="00833-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="00833-126">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="00833-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="00833-127">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="00833-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="00833-128">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="00833-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="00833-129">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="00833-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
