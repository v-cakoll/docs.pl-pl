---
title: "Przykład elementu powiązania odnajdywania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b658cc481d3ca5e87b5b9e2aab6b7561be2c65b1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="discovery-binding-element-sample"></a><span data-ttu-id="0fdcf-102">Przykład elementu powiązania odnajdywania</span><span class="sxs-lookup"><span data-stu-id="0fdcf-102">Discovery Binding Element Sample</span></span>
<span data-ttu-id="0fdcf-103">W tym przykładzie pokazano, jak element powiązania klienta odnajdywania umożliwia odnajdywanie usługi.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-103">This sample demonstrates how to use the discovery client binding element to discover a service.</span></span> <span data-ttu-id="0fdcf-104">Ta funkcja umożliwia deweloperom dodać kanałem klienta odnajdywania do ich istniejącego stosu kanału klienta, tworzenie bardzo intuicyjne modelu programowania.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-104">This feature enables developers to add a discovery client channel to their existing client channel stack, making the programming model very intuitive.</span></span> <span data-ttu-id="0fdcf-105">Po otwarciu kanału skojarzony adres usługi został rozwiązany za pomocą odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-105">When the associated channel is opened, the address of the service is resolved using discovery.</span></span> <span data-ttu-id="0fdcf-106">W tym przykładzie składa się z następujących projektów:</span><span class="sxs-lookup"><span data-stu-id="0fdcf-106">This sample consists of the following projects:</span></span>  
  
-   <span data-ttu-id="0fdcf-107">**CalculatorService**: wykrywalny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-107">**CalculatorService**: A discoverable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
-   <span data-ttu-id="0fdcf-108">**CalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji klienckiej, która korzysta z kanałem klienta odnajdywania do wyszukiwania i wywołać CalculatorService.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-108">**CalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery client channel to search for and call the CalculatorService.</span></span>  
  
-   <span data-ttu-id="0fdcf-109">**DynamicCalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji klienckiej, która używa do wyszukiwania i wywołać CalculatorService dynamiczne punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-109">**DynamicCalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses a dynamic endpoint to search for and call the CalculatorService.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0fdcf-110">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0fdcf-111">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="0fdcf-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0fdcf-112">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0fdcf-113">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a><span data-ttu-id="0fdcf-114">CalculatorService</span><span class="sxs-lookup"><span data-stu-id="0fdcf-114">CalculatorService</span></span>  
 <span data-ttu-id="0fdcf-115">Ten projekt zawiera usługi prosty kalkulator, który implementuje `ICalculatorService` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-115">This project contains a simple calculator service that implements the `ICalculatorService` contract.</span></span>  
  
 <span data-ttu-id="0fdcf-116">Następujący plik App.config służy do dodawania `<serviceDiscovery>` zachowanie zachowania usługi, jak również punkt końcowy odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-116">The following App.config file is used to add a `<serviceDiscovery>` behavior in the service behaviors as well as the discovery endpoint.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">  
        <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />  
      </service>  
    </services>  
    <behaviors>  
      <!--Enable discovery through configuration.-->  
      <serviceBehaviors>  
        <behavior name="CalculatorBehavior">  
          <serviceDiscovery>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="0fdcf-117">Dzięki temu usługa i jej punkty końcowe wykrywalny.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-117">This makes the service and its endpoints discoverable.</span></span> <span data-ttu-id="0fdcf-118">CalculatorService jest samodzielnie hostowana usługa, która dodaje jeden punkt końcowy, za pomocą tego powiązania NetTcpBinding.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-118">The CalculatorService is a self-hosted service that adds one endpoint using the NetTcpBinding binding.</span></span> <span data-ttu-id="0fdcf-119">Dodano również `EndpointDiscoveryBehavior` do punktu końcowego i określa zakres, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-119">It also adds an `EndpointDiscoveryBehavior` to the endpoint and specifies a scope as shown in the following code.</span></span>  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a><span data-ttu-id="0fdcf-120">CalculatorClient</span><span class="sxs-lookup"><span data-stu-id="0fdcf-120">CalculatorClient</span></span>  
 <span data-ttu-id="0fdcf-121">Ten projekt zawiera implementację klienta, który wysyła wiadomości do CalculatorService.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-121">This project contains a client implementation that sends messages to the CalculatorService.</span></span> <span data-ttu-id="0fdcf-122">Ten program używa `CreateCustomBindingWithDiscoveryElement()` metodę w celu utworzenia niestandardowego powiązania, które korzysta z kanałem klienta odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-122">This program uses the `CreateCustomBindingWithDiscoveryElement()` method to create a custom binding that uses the Discovery Client Channel.</span></span>  
  
```  
static CustomBinding CreateCustomBindingWithDiscoveryElement()  
 {  
      DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
            // Provide the search criteria and the endpoint over which the probe is sent  
            discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
            discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
            CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
            // Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
            // An exception is thrown if this binding element is not at the top  
            customBinding.Elements.Insert(0, discoveryBindingElement);  
  
            return customBinding; }  
```  
  
 <span data-ttu-id="0fdcf-123">Po <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> jest uruchomiony, deweloper określa kryteria służące do wyszukiwania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-123">After the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is instantiated, the developer specifies the criteria to use when searching for a service.</span></span> <span data-ttu-id="0fdcf-124">W takim przypadku kryterium wyszukiwania odnajdywania jest `ICalculatorService` typu.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-124">In this case, the discovery find criterion is the `ICalculatorService` type.</span></span> <span data-ttu-id="0fdcf-125">Ponadto określa dewelopera <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> co powoduje zwrócenie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> Określa, gdzie szukać usług.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-125">Additionally, the developer specifies a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> which returns a <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> that specifies where to look for the services.</span></span> <span data-ttu-id="0fdcf-126"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Zwraca nową <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-126">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> returns a new <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="0fdcf-127">[Używanie wiązania niestandardowego z kanałem klienta odnajdywania](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="0fdcf-127"> [Using a Custom Binding with the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span></span>  
  
```  
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
    // to the DiscoveryClientBindingElement. The Discovery ClientChannel   
    // uses this endpoint to send Probe message.  
    public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
    {  
        public override DiscoveryEndpoint GetDiscoveryEndpoint()  
        {  
            return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
        }  
    }  
```  
  
 <span data-ttu-id="0fdcf-128">W takim przypadku klient używa protokołu UDP multiemisji mechanizm zdefiniowany przez Protokół odnajdywania wyszukiwania usług w podsieci lokalnej.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-128">In this case, the client uses the UDP multicast mechanism defined by the Discovery protocol to search for services on the local subnet.</span></span> <span data-ttu-id="0fdcf-129">W pozostałej części metoda tworzy niestandardowego powiązania i wstawia elementu powiązania odnajdywania w górnej części stosu.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-129">The remainder of the method creates a custom binding and inserts the Discovery binding element at the top of the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fdcf-130"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Muszą znajdować się na wierzchołku stosu powiązania.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-130">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must be placed on the top of the binding stack.</span></span> <span data-ttu-id="0fdcf-131">Wszelkie <xref:System.ServiceModel.Channels.BindingElement> nad <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> należy się upewnić, że fabryki kanałów lub tworzy kanału nie używać `EndpointAddress` lub `Via` właściwości, ponieważ rzeczywista adres znajduje się tylko na kanałem klienta odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-131">Any <xref:System.ServiceModel.Channels.BindingElement> on top of <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must make sure that the channel factory or channel it creates does not use the `EndpointAddress` or `Via` properties, because the actual address is found only at the Discovery client channel.</span></span>  
  
 <span data-ttu-id="0fdcf-132">Następnie `CalculatorClient` mogą zostać utworzone przez przekazywanie w tym niestandardowego powiązania, a także adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-132">Next, the `CalculatorClient` can be instantiated by passing in this custom binding as well as an endpoint address.</span></span>  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 <span data-ttu-id="0fdcf-133">Korzystając z kanałem klienta odnajdywania, określony adres punktu końcowego stałej wcześniej jest przekazywana.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-133">When using the Discovery Client Channel, the constant endpoint address specified previously is passed in.</span></span> <span data-ttu-id="0fdcf-134">Teraz w czasie wykonywania, kanałem klienta odnajdywania umożliwia znalezienie usługi określone przez kryteria znajdowania i nawiązuje z nim połączenie.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-134">Now at runtime, the Discovery Client Channel finds the service specified by the find criteria and connects to it.</span></span> <span data-ttu-id="0fdcf-135">Dla usługi i klienta, aby nawiązać połączenie muszą mieć taki sam podstawowy stos powiązania.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-135">For the service and the client to establish a connection, they must also have the same underlying binding stack.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="0fdcf-136">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="0fdcf-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="0fdcf-137">Otwórz rozwiązanie w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0fdcf-137">Open the solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="0fdcf-138">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-138">Build the solution.</span></span>  
  
3.  <span data-ttu-id="0fdcf-139">Uruchamianie aplikacji usługi i każdego klienta aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-139">Run the service application and each of the client applications.</span></span>  
  
4.  <span data-ttu-id="0fdcf-140">Sprawdź, czy klient mógł znaleźć usługi bez uprzedniego uzyskania informacji o jego adres.</span><span class="sxs-lookup"><span data-stu-id="0fdcf-140">Observe that the client was able to find the service without knowing its address.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fdcf-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fdcf-141">See Also</span></span>
