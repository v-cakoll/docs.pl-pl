---
title: Usługi dwukierunkowe
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: 9adbb4166d713cea0344c9fa58ce85e5afce086d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717926"
---
# <a name="duplex-services"></a><span data-ttu-id="2a40f-102">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="2a40f-102">Duplex Services</span></span>
<span data-ttu-id="2a40f-103">Kontrakt usługi dwustronnej jest wymiany komunikatów, w którym obu punktów końcowych może wysyłać komunikaty do innych niezależnie.</span><span class="sxs-lookup"><span data-stu-id="2a40f-103">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="2a40f-104">Usługi duplex, dlatego wiadomości można wysyłać do punktu końcowego klienta, zapewniając zachowanie podobne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2a40f-104">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="2a40f-105">Komunikację dupleksową występuje, gdy klient łączy się z usługą i udostępnia usługi za pomocą kanału, na którym usługa może wysłać wiadomości zwrotnie do klienta.</span><span class="sxs-lookup"><span data-stu-id="2a40f-105">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="2a40f-106">Należy pamiętać, że zachowanie podobne zdarzenia usługi dwukierunkowe działa tylko w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="2a40f-106">Note that the event-like behavior of duplex services only works within a session.</span></span>  
  
 <span data-ttu-id="2a40f-107">Aby utworzyć kontrakt dupleksowy należy utworzyć dwa interfejsy.</span><span class="sxs-lookup"><span data-stu-id="2a40f-107">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="2a40f-108">Pierwsza to interfejsu kontraktu usługi, który opisuje operacje, które mogą być wywoływane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="2a40f-108">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="2a40f-109">Należy określić ten kontrakt usługi *kontrakt wywołania zwrotnego* w <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2a40f-109">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="2a40f-110">Kontrakt wywołania zwrotnego jest interfejsem, który definiuje operacje, które usługa może wywołać w punkcie końcowym klienta.</span><span class="sxs-lookup"><span data-stu-id="2a40f-110">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="2a40f-111">Kontraktu dwukierunkowego nie wymaga sesję, mimo że dwukierunkowego powiązania dostarczane przez system, należy korzystać z nich.</span><span class="sxs-lookup"><span data-stu-id="2a40f-111">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>  
  
 <span data-ttu-id="2a40f-112">Oto przykład kontraktu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="2a40f-112">The following is an example of a duplex contract.</span></span>  
  
 [!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
 [!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]  
  
 <span data-ttu-id="2a40f-113">`CalculatorService` Klasa implementuje podstawowy `ICalculatorDuplex` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2a40f-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="2a40f-114">Używa usługi <xref:System.ServiceModel.InstanceContextMode.PerSession> tryb wystąpienia do obsługi wyników dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="2a40f-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="2a40f-115">Właściwość prywatna o nazwie `Callback` uzyskuje dostęp do kanału wywołania zwrotnego do klienta.</span><span class="sxs-lookup"><span data-stu-id="2a40f-115">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="2a40f-116">Usługa używa wywołania zwrotnego do wysyłania wiadomości do klienta za pośrednictwem interfejs wywołania zwrotnego, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2a40f-116">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>  
  
 [!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
 [!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]  
  
 <span data-ttu-id="2a40f-117">Klient musi podać klasę, która implementuje interfejs wywołania zwrotnego kontraktu dwukierunkowego, do odbierania wiadomości z usługi.</span><span class="sxs-lookup"><span data-stu-id="2a40f-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="2a40f-118">Poniższy przykładowy kod przedstawia `CallbackHandler` klasę, która implementuje `ICalculatorDuplexCallback` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2a40f-118">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>  
  
 [!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
 [!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]  
  
 <span data-ttu-id="2a40f-119">Klient WCF, który jest generowany dla kontraktu dwukierunkowego wymaga <xref:System.ServiceModel.InstanceContext> klasy, należy podać podczas konstruowania.</span><span class="sxs-lookup"><span data-stu-id="2a40f-119">The WCF client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="2a40f-120">To <xref:System.ServiceModel.InstanceContext> klasa jest używana jako witryna dla obiektu, który implementuje interfejs wywołania zwrotnego i obsługuje wiadomości wysyłanych na odpowiedź od usługi.</span><span class="sxs-lookup"><span data-stu-id="2a40f-120">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="2a40f-121"><xref:System.ServiceModel.InstanceContext> Klasy składa się z wystąpieniem `CallbackHandler` klasy.</span><span class="sxs-lookup"><span data-stu-id="2a40f-121">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="2a40f-122">Ten obiekt obsługi komunikatów wysyłanych z usługi na kliencie, na interfejs wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="2a40f-122">This object handles messages sent from the service to the client on the callback interface.</span></span>  
  
 [!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
 [!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]  
  
 <span data-ttu-id="2a40f-123">Konfiguracji usługi należy skonfigurować umożliwia powiązanie, które obsługuje zarówno sesji komunikacji, jak i komunikację dupleksową.</span><span class="sxs-lookup"><span data-stu-id="2a40f-123">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="2a40f-124">`wsDualHttpBinding` Element obsługuje komunikację sesji i umożliwia komunikację dupleksową, zapewniając dwa połączenia HTTP, jedno dla każdego kierunku.</span><span class="sxs-lookup"><span data-stu-id="2a40f-124">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>  
  
 <span data-ttu-id="2a40f-125">Na komputerze klienckim należy skonfigurować adres serwera służy do połączenia z klientem, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="2a40f-125">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>  
  
  
  
> [!NOTE]
>  <span data-ttu-id="2a40f-126">Throw klientów non-duplex, którzy nie próbę uwierzytelnienia przy użyciu bezpiecznej konwersacji zazwyczaj <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="2a40f-126">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="2a40f-127">Jednak jeśli dwukierunkowego klienta, który używa bezpiecznej konwersacji uwierzytelnianie zakończy się niepowodzeniem, klient odbierze <xref:System.TimeoutException> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="2a40f-127">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>  
  
 <span data-ttu-id="2a40f-128">Jeśli utworzysz klienta/usługi przy użyciu `WSHttpBinding` elementu i nie mają punkt końcowy wywołania zwrotnego klienta, zostanie wyświetlony następujący błąd.</span><span class="sxs-lookup"><span data-stu-id="2a40f-128">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>  
  
```  
HTTP could not register URL  
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.  
```  
  
 <span data-ttu-id="2a40f-129">Następujący przykładowy kod przedstawia sposób określania klienta adres punktu końcowego programowo.</span><span class="sxs-lookup"><span data-stu-id="2a40f-129">The following sample code shows how to specify the client endpoint address programmatically.</span></span>
  
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

 <span data-ttu-id="2a40f-130">Poniższy przykład kodu pokazuje, jak określić klienta adres punktu końcowego w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2a40f-130">The following sample code shows how to specify the client endpoint address in configuration.</span></span>  
  
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
>  <span data-ttu-id="2a40f-131">Automatycznie dwukierunkowego modelu nie wykrywa usługi lub klienta powoduje zamknięcie kanału.</span><span class="sxs-lookup"><span data-stu-id="2a40f-131">The duplex model does not automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="2a40f-132">Dlatego jeśli klient zakończy się nieoczekiwanie, domyślnie Usługa nie będzie powiadamiany lub jeśli klient zakończy się nieoczekiwanie, usługa nie będzie powiadamiany.</span><span class="sxs-lookup"><span data-stu-id="2a40f-132">So if a client unexpectedly terminates, by default the service will not be notified, or if a client unexpectedly terminates, the service will not be notified.</span></span> <span data-ttu-id="2a40f-133">Klienci i usługi mogą implementować własne protokół do siebie powiadomienie, jeśli dokonają takiego wyboru.</span><span class="sxs-lookup"><span data-stu-id="2a40f-133">Clients and services can implement their own protocol to notify each other if they so choose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a40f-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a40f-134">See also</span></span>
- [<span data-ttu-id="2a40f-135">Dupleks</span><span class="sxs-lookup"><span data-stu-id="2a40f-135">Duplex</span></span>](../../../../docs/framework/wcf/samples/duplex.md)
- [<span data-ttu-id="2a40f-136">Określanie zachowania klienta w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="2a40f-136">Specifying Client Run-Time Behavior</span></span>](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="2a40f-137">Instrukcje: Tworzenie fabryki kanałów i używanie jej do tworzenia kanałów oraz zarządzania nimi</span><span class="sxs-lookup"><span data-stu-id="2a40f-137">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
