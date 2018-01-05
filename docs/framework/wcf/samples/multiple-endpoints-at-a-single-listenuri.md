---
title: "Wiele punktów końcowych w pojedynczym identyfikatorze ListenUri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 909fb35f9b8e4628df06918f207c3c86770a2d4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a><span data-ttu-id="82e78-102">Wiele punktów końcowych w pojedynczym identyfikatorze ListenUri</span><span class="sxs-lookup"><span data-stu-id="82e78-102">Multiple Endpoints at a Single ListenUri</span></span>
<span data-ttu-id="82e78-103">W tym przykładzie pokazano, usługa, która obsługuje wiele punktów końcowych w pojedynczym `ListenUri`.</span><span class="sxs-lookup"><span data-stu-id="82e78-103">This sample demonstrates a service that hosts multiple endpoints at a single `ListenUri`.</span></span> <span data-ttu-id="82e78-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="82e78-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82e78-105">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="82e78-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="82e78-106">Jak pokazano w [wiele punktów końcowych](../../../../docs/framework/wcf/samples/multiple-endpoints.md) przykład usługa może obsługiwać wiele punktów końcowych, każde z nich różne adresy i prawdopodobnie również różnych powiązania.</span><span class="sxs-lookup"><span data-stu-id="82e78-106">As demonstrated in the [Multiple Endpoints](../../../../docs/framework/wcf/samples/multiple-endpoints.md) sample, a service can host multiple endpoints, each with different addresses and possibly also different bindings.</span></span> <span data-ttu-id="82e78-107">W tym przykładzie pokazano, czy jest możliwe do hostowania wiele punktów końcowych w ten sam adres.</span><span class="sxs-lookup"><span data-stu-id="82e78-107">This sample shows that it is possible to host multiple endpoints at the same address.</span></span> <span data-ttu-id="82e78-108">W tym przykładzie przedstawiono również różnice między dwa rodzaje adresów, które ma punkt końcowy usługi: `EndpointAddress` i `ListenUri`.</span><span class="sxs-lookup"><span data-stu-id="82e78-108">This sample also demonstrates the differences between the two kinds of addresses that a service endpoint has: `EndpointAddress` and `ListenUri`.</span></span>  
  
 <span data-ttu-id="82e78-109">`EndpointAddress` Jest adresów logicznych usługi.</span><span class="sxs-lookup"><span data-stu-id="82e78-109">The `EndpointAddress` is the logical address of a service.</span></span> <span data-ttu-id="82e78-110">Jest wiadomości SOAP są wysyłane na adres.</span><span class="sxs-lookup"><span data-stu-id="82e78-110">It is the address that SOAP messages are addressed to.</span></span> <span data-ttu-id="82e78-111">`ListenUri` To adres fizyczny usługi.</span><span class="sxs-lookup"><span data-stu-id="82e78-111">The `ListenUri` is the physical address of the service.</span></span> <span data-ttu-id="82e78-112">Z informacji adres i port której faktycznie nasłuchuje usługa punktu końcowego wiadomości na bieżącym komputerze.</span><span class="sxs-lookup"><span data-stu-id="82e78-112">It has the port and address information where the service endpoint actually listens for messages on the current machine.</span></span> <span data-ttu-id="82e78-113">W większości przypadków nie istnieje potrzeba dla tych adresów mogą się różnić; gdy `ListenUri` nie jest jawnie określona, domyślnie identyfikator URI `EndpointAddress` punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="82e78-113">In most cases, there is no need for these addresses to differ; when a `ListenUri` is not explicitly specified, it defaults to the URI of the `EndpointAddress` of the endpoint.</span></span> <span data-ttu-id="82e78-114">W niektórych przypadkach warto odróżnić je, np. podczas konfigurowania routera, który może akceptować komunikaty adresowane do szereg różnych usług.</span><span class="sxs-lookup"><span data-stu-id="82e78-114">In a few cases, it is useful to distinguish them, such as when configuring a router, which might accept messages addressed to a number of different services.</span></span>  
  
## <a name="service"></a><span data-ttu-id="82e78-115">Usługa</span><span class="sxs-lookup"><span data-stu-id="82e78-115">Service</span></span>  
 <span data-ttu-id="82e78-116">Usługi w tym przykładzie ma dwa kontrakty `ICalculator` i `IEcho`.</span><span class="sxs-lookup"><span data-stu-id="82e78-116">The service in this sample has two contracts, `ICalculator` and `IEcho`.</span></span> <span data-ttu-id="82e78-117">Oprócz zwyczajowe `IMetadataExchange` punktu końcowego, istnieją trzy punkty końcowe aplikacji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="82e78-117">In addition to the customary `IMetadataExchange` endpoint, there are three application endpoints, as shown in the following code.</span></span>  
  
```xml  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.ICalculator"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:OtherEcho"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
```  
  
 <span data-ttu-id="82e78-118">Wszystkie trzy punkty końcowe znajdują się w tym samym `ListenUri` i używać tego samego `binding` — punkty końcowe w tym samym `ListenUri` musi mieć tego samego powiązania, ponieważ są one udostępnianie stosu pojedynczego kanału, który wiadomości pod tym adresem fizycznym nasłuchuje maszyny.</span><span class="sxs-lookup"><span data-stu-id="82e78-118">All three endpoints are hosted at the same `ListenUri` and use the same `binding` - endpoints at the same `ListenUri` must have the same binding, because they are sharing a single channel stack that listens for messages at that physical address on the machine.</span></span> <span data-ttu-id="82e78-119">`address` Każdego punktu końcowego jest identyfikatorem URN; chociaż zazwyczaj adresy reprezentują lokalizacje fizyczne, w rzeczywistości adres może być dowolny rodzaj identyfikatora URI, ponieważ adres jest używany do dopasowywania i ich filtrowania, jak przedstawiono w przykładach w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="82e78-119">The `address` of each endpoint is a URN; though typically addresses represent physical locations, in fact the address can be any kind of URI, because the address is used for matching and filtering purposes as is demonstrated in this sample.</span></span>  
  
 <span data-ttu-id="82e78-120">Ponieważ wszystkie trzy punkty końcowe mają takie same `ListenUri`, po nadejściu wiadomości, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] należy zdecydować, który punkt końcowy komunikatu jest przeznaczony do.</span><span class="sxs-lookup"><span data-stu-id="82e78-120">Because all three endpoints share the same `ListenUri`, when a message arrives there, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] must decide which endpoint the message is destined for.</span></span> <span data-ttu-id="82e78-121">Każdy punkt końcowy ma filtr komunikatu, który składa się z dwóch części: filtr adresów i filtr umowy.</span><span class="sxs-lookup"><span data-stu-id="82e78-121">Each endpoint has a message filter that is comprised of two parts: the address filter and the contract filter.</span></span> <span data-ttu-id="82e78-122">Kryteria filtru adresu `To` wiadomości SOAP adres punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="82e78-122">The address filter matches the `To` of the SOAP message to the address of the service endpoint.</span></span> <span data-ttu-id="82e78-123">Na przykład tylko komunikaty adresowane `To "Urn:OtherEcho"` nadają się do trzeciego punktu końcowego tej usługi.</span><span class="sxs-lookup"><span data-stu-id="82e78-123">For example, only messages addressed `To "Urn:OtherEcho"` are candidates for the third endpoint of this service.</span></span> <span data-ttu-id="82e78-124">Akcje skojarzone z operacjami określonej umowy spełniają kryteria filtru kontraktu.</span><span class="sxs-lookup"><span data-stu-id="82e78-124">The contract filter matches the Actions associated with the operations of a particular contract.</span></span> <span data-ttu-id="82e78-125">Na przykład wiadomości z akcją `IEcho`.</span><span class="sxs-lookup"><span data-stu-id="82e78-125">For example, messages with the action of `IEcho`.</span></span> <span data-ttu-id="82e78-126">`Echo`Dopasowuje filtry kontraktu w drugim i innych punktów końcowych tej usługi, ponieważ oba te punkty końcowe hosta `IEcho` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="82e78-126">`Echo` matches the contract filters of both the second and third endpoints of this service, because both of those endpoints host the `IEcho` contract.</span></span>  
  
 <span data-ttu-id="82e78-127">W związku z tym kombinację adresu filtry i kontrakt umożliwia trasy każdy komunikat przychodzący w tej usłudze `ListenUri` do właściwego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="82e78-127">Thus the combination of address filter and contract filter makes it possible to route each message that arrives at this service's `ListenUri` to the correct endpoint.</span></span> <span data-ttu-id="82e78-128">Trzeci punktu końcowego jest zróżnicowana od dwóch innych, ponieważ akceptuje on komunikaty wysyłane do innego adresu z innych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="82e78-128">The third endpoint is differentiated from the other two because it accepts messages sent to a different address from the other endpoints.</span></span> <span data-ttu-id="82e78-129">Pierwszy i drugi punktów końcowych, które różnią się od siebie na podstawie ich umów (Akcja wiadomości przychodzącej).</span><span class="sxs-lookup"><span data-stu-id="82e78-129">The first and second endpoints are differentiated from each other based on their contracts (the Action of the incoming message).</span></span>  
  
## <a name="client"></a><span data-ttu-id="82e78-130">Klient</span><span class="sxs-lookup"><span data-stu-id="82e78-130">Client</span></span>  
 <span data-ttu-id="82e78-131">Tak samo, jak punkty końcowe na serwerze ma dwa różne adresy, punktów końcowych klienta również mieć dwa adresy.</span><span class="sxs-lookup"><span data-stu-id="82e78-131">Just as endpoints on the server have two different addresses, client endpoints also have two addresses.</span></span> <span data-ttu-id="82e78-132">Na serwerze i kliencie adresów logicznych jest nazywany `EndpointAddress`.</span><span class="sxs-lookup"><span data-stu-id="82e78-132">On both server and client, the logical address is called the `EndpointAddress`.</span></span> <span data-ttu-id="82e78-133">Jednakże adres fizyczny jest nazywany `ListenUri` na serwerze, na kliencie, jest nazywany adresu fizycznego `Via`.</span><span class="sxs-lookup"><span data-stu-id="82e78-133">But whereas the physical address is called the `ListenUri` on the server, on the client, the physical address is called the `Via`.</span></span>  
  
 <span data-ttu-id="82e78-134">Na serwerze, domyślnie obu tych adresów są takie same.</span><span class="sxs-lookup"><span data-stu-id="82e78-134">As on the server, by default, these two addresses are the same.</span></span> <span data-ttu-id="82e78-135">Aby określić `Via` na kliencie, który różni się od adresu punktu końcowego `ClientViaBehavior` jest używany:</span><span class="sxs-lookup"><span data-stu-id="82e78-135">To specify a `Via` on the client that is different from the endpoint's address, `ClientViaBehavior` is used:</span></span>  
  
```  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 <span data-ttu-id="82e78-136">Jak zwykle adres pochodzi z pliku konfiguracji klienta, który został wygenerowany przez Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="82e78-136">As usual, the address comes from the client configuration file, which was generated by Svcutil.exe.</span></span> <span data-ttu-id="82e78-137">`Via` (Które odpowiada `ListenUri` usługi) nie ma w metadanych usługi i dlatego te informacje muszą być przekazywane klienta poza pasmem (podobnie jak adres metadanych usługi).</span><span class="sxs-lookup"><span data-stu-id="82e78-137">The `Via` (which corresponds to the `ListenUri` of the service) does not appear in the service's metadata and so this information must be communicated to the client out-of-band (just like the service's metadata address).</span></span>  
  
 <span data-ttu-id="82e78-138">W tym przykładzie klient wysyła komunikaty do każdego z punktów końcowych aplikacji trzy serwera wykazać, że może komunikować się z (i odróżnienia) wszystkich trzech punktów końcowych, nawet jeśli wszystkie mają takie same `Via`.</span><span class="sxs-lookup"><span data-stu-id="82e78-138">The client in this sample sends messages to each of the server's three application endpoints, to demonstrate that it can communicate with (and differentiate) all three endpoints, even though they all have the same `Via`.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="82e78-139">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="82e78-139">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="82e78-140">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="82e78-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="82e78-141">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="82e78-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="82e78-142">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="82e78-142">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="82e78-143">Dla między komputerami należy zastąpić localhost w pliku Client.cs o nazwie maszyna usługi.</span><span class="sxs-lookup"><span data-stu-id="82e78-143">For cross-machine, you must replace localhost in the Client.cs file with the name of the service machine.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="82e78-144">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="82e78-144">The samples may already be installed on your machine.</span></span> <span data-ttu-id="82e78-145">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="82e78-145">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="82e78-146">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="82e78-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="82e78-147">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="82e78-147">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
  
## <a name="see-also"></a><span data-ttu-id="82e78-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82e78-148">See Also</span></span>
