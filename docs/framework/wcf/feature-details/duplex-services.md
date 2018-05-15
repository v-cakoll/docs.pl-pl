---
title: Usługi dwukierunkowe
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: da92b8f2d1223f582677a93a8ff6fd697512d297
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="duplex-services"></a><span data-ttu-id="25fa9-102">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="25fa9-102">Duplex Services</span></span>
<span data-ttu-id="25fa9-103">Kontrakt usługi dwustronnej jest wymiany komunikatów w których oba punkty końcowe można wysyłać wiadomości do innych niezależnie.</span><span class="sxs-lookup"><span data-stu-id="25fa9-103">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="25fa9-104">Usługi duplex, w związku z tym wiadomości można wysyłać do punktu końcowego klienta, zapewniając zdarzenia podobne zachowania.</span><span class="sxs-lookup"><span data-stu-id="25fa9-104">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="25fa9-105">Komunikację dupleksową występuje, gdy klient nawiąże połączenie z usługą i zapewnia usługę, z kanałem, na którym usługa można wysłać wiadomości zwrotnie do klienta.</span><span class="sxs-lookup"><span data-stu-id="25fa9-105">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="25fa9-106">Należy pamiętać, że zachowanie podobnych zdarzeń usługi dwukierunkowe działa tylko w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="25fa9-106">Note that the event-like behavior of duplex services only works within a session.</span></span>  
  
 <span data-ttu-id="25fa9-107">Aby utworzyć kontrakt dupleksowy, należy utworzyć dwa interfejsy.</span><span class="sxs-lookup"><span data-stu-id="25fa9-107">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="25fa9-108">Pierwszy jest interfejsem kontraktu usługi, który zawiera opis czynności, które klient może wywołać.</span><span class="sxs-lookup"><span data-stu-id="25fa9-108">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="25fa9-109">Ten kontrakt usługi musi określać *kontrakt wywołania zwrotnego* w <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="25fa9-109">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="25fa9-110">Kontrakt wywołania zwrotnego to interfejs, który definiuje operacje, które usługa może wywoływać klienta w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="25fa9-110">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="25fa9-111">Kontrakt dupleksowy nie wymaga sesji, mimo że dwukierunkowego powiązania dostarczane przez system, należy korzystać z nich.</span><span class="sxs-lookup"><span data-stu-id="25fa9-111">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>  
  
 <span data-ttu-id="25fa9-112">Oto przykład kontraktu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="25fa9-112">The following is an example of a duplex contract.</span></span>  
  
 [!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
 [!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]  
  
 <span data-ttu-id="25fa9-113">`CalculatorService` Klasa implementuje podstawową `ICalculatorDuplex` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="25fa9-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="25fa9-114">Używane przez usługę <xref:System.ServiceModel.InstanceContextMode.PerSession> tryb wystąpienia przechowywać wynik dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="25fa9-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="25fa9-115">Właściwość prywatna o nazwie `Callback` uzyskuje dostęp do kanału wywołania zwrotnego do klienta.</span><span class="sxs-lookup"><span data-stu-id="25fa9-115">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="25fa9-116">Usługa używa wywołania zwrotnego do wysyłania wiadomości do klienta za pośrednictwem interfejsu wywołania zwrotnego, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="25fa9-116">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>  
  
 [!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
 [!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]  
  
 <span data-ttu-id="25fa9-117">Klient musi dostarczyć klasy, która implementuje interfejs wywołania zwrotnego kontrakt dupleksu do odbierania wiadomości z usługi.</span><span class="sxs-lookup"><span data-stu-id="25fa9-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="25fa9-118">Poniższy przykładowy kod przedstawia `CallbackHandler` klasa implementująca `ICalculatorDuplexCallback` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="25fa9-118">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>  
  
 [!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
 [!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]  
  
 <span data-ttu-id="25fa9-119">Klient WCF, generowany dla kontraktu dwukierunkowego wymaga <xref:System.ServiceModel.InstanceContext> klasę, aby podać po konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="25fa9-119">The WCF client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="25fa9-120">To <xref:System.ServiceModel.InstanceContext> klasa jest używana jako witryna dla obiekt, który implementuje interfejs wywołania zwrotnego i obsługi wiadomości, które są wysyłane z usługi.</span><span class="sxs-lookup"><span data-stu-id="25fa9-120">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="25fa9-121"><xref:System.ServiceModel.InstanceContext> Klasy jest tworzony przy użyciu wystąpienia `CallbackHandler` klasy.</span><span class="sxs-lookup"><span data-stu-id="25fa9-121">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="25fa9-122">Ten obiekt obsługi komunikatów wysyłanych z usługi do klienta w interfejsie wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="25fa9-122">This object handles messages sent from the service to the client on the callback interface.</span></span>  
  
 [!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
 [!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]  
  
 <span data-ttu-id="25fa9-123">Konfiguracji usługi musi skonfigurować ma zostać udostępnione wiązanie, która obsługuje zarówno sesji komunikacji i komunikację dupleksową.</span><span class="sxs-lookup"><span data-stu-id="25fa9-123">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="25fa9-124">`wsDualHttpBinding` Elementu obsługuje komunikację sesji i umożliwia komunikację dupleksową zapewniając dwa połączenia HTTP, po jednej dla każdego kierunku.</span><span class="sxs-lookup"><span data-stu-id="25fa9-124">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>  
  
 <span data-ttu-id="25fa9-125">Na komputerze klienckim należy skonfigurować adres serwera można użyć do nawiązania połączenia klienta, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="25fa9-125">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>  
  
  
  
> [!NOTE]
>  <span data-ttu-id="25fa9-126">Throw non-duplex klientów, którzy nie mogą się uwierzytelnić, zwykle za pomocą bezpiecznej konwersacji <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="25fa9-126">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="25fa9-127">Jednak jeśli dupleksu klienta, który używa bezpiecznej konwersacji uwierzytelnianie zakończy się niepowodzeniem, klient odbierze <xref:System.TimeoutException> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="25fa9-127">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>  
  
 <span data-ttu-id="25fa9-128">W przypadku utworzenia przy użyciu klienta/usługa `WSHttpBinding` elemencie i użytkownik nie ma punktu końcowego wywołania zwrotnego klienta, zostanie wyświetlony następujący błąd.</span><span class="sxs-lookup"><span data-stu-id="25fa9-128">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>  
  
```  
HTTP could not register URL  
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.  
```  
  
 <span data-ttu-id="25fa9-129">Następujący przykładowy kod przedstawia sposób określania klienta adres punktu końcowego programowo.</span><span class="sxs-lookup"><span data-stu-id="25fa9-129">The following sample code shows how to specify the client endpoint address programmatically.</span></span>
  
```csharp  
WSDualHttpBinding binding = new WSDualHttpBinding();  
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");  
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");  
```  
```vb
Dim binding As New WSDualHttpBinding()
Dim endptadr As New EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server")
binding.ClientBaseAddress = New Uri("http://localhost:8000/DuplexTestUsingCode/Client/")  
```

 <span data-ttu-id="25fa9-130">Następujący przykładowy kod przedstawia sposób określić klienta adres punktu końcowego w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="25fa9-130">The following sample code shows how to specify the client endpoint address in configuration.</span></span>  
  
```xml  
<client>  
    <endpoint name ="ServerEndpoint"   
          address="http://localhost:12000/DuplexTestUsingConfig/Server"  
          bindingConfiguration="WSDualHttpBinding_IDuplexTest"   
            binding="wsDualHttpBinding"  
           contract="IDuplexTest" />  
</client>  
<bindings>  
    <wsDualHttpBinding>  
        <binding name="WSDualHttpBinding_IDuplexTest"    
          clientBaseAddress="http://localhost:8000/myClient/" >  
            <security mode="None"/>  
         </binding>  
    </wsDualHttpBinding>  
</bindings>  
```  
  
> [!WARNING]
>  <span data-ttu-id="25fa9-131">Automatycznie dupleksu modelu nie wykrywa usługi lub klienta powoduje zamknięcie kanału.</span><span class="sxs-lookup"><span data-stu-id="25fa9-131">The duplex model does not automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="25fa9-132">Dlatego jeśli klienta zakończy się nieoczekiwanie, domyślnie Usługa nie zostanie poinformowany lub jeśli klienta zakończy się nieoczekiwanie, usługa nie będzie powiadamiany.</span><span class="sxs-lookup"><span data-stu-id="25fa9-132">So if a client unexpectedly terminates, by default the service will not be notified, or if a client unexpectedly terminates, the service will not be notified.</span></span> <span data-ttu-id="25fa9-133">Klienci i usługi można zaimplementować własnych protokołu do siebie powiadomienia, gdy wybiera on.</span><span class="sxs-lookup"><span data-stu-id="25fa9-133">Clients and services can implement their own protocol to notify each other if they so choose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25fa9-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25fa9-134">See Also</span></span>  
 [<span data-ttu-id="25fa9-135">Dupleks</span><span class="sxs-lookup"><span data-stu-id="25fa9-135">Duplex</span></span>](../../../../docs/framework/wcf/samples/duplex.md)  
 [<span data-ttu-id="25fa9-136">Określanie zachowania klienta w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="25fa9-136">Specifying Client Run-Time Behavior</span></span>](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [<span data-ttu-id="25fa9-137">Instrukcje: tworzenie fabryki kanałów i używanie jej do tworzenia kanałów oraz zarządzania nimi</span><span class="sxs-lookup"><span data-stu-id="25fa9-137">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
