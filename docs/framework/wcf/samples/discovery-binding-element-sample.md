---
title: Przykład elementu powiązania odnajdywania
ms.date: 03/30/2017
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
ms.openlocfilehash: d906d9a389c50095f2af5d52e3874c3e43199e68
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44177539"
---
# <a name="discovery-binding-element-sample"></a><span data-ttu-id="cf481-102">Przykład elementu powiązania odnajdywania</span><span class="sxs-lookup"><span data-stu-id="cf481-102">Discovery Binding Element Sample</span></span>
<span data-ttu-id="cf481-103">W tym przykładzie pokazano, jak użyć elementu powiązania odnajdywania klienta do odnajdywania usługi.</span><span class="sxs-lookup"><span data-stu-id="cf481-103">This sample demonstrates how to use the discovery client binding element to discover a service.</span></span> <span data-ttu-id="cf481-104">Ta funkcja umożliwia deweloperom Dodawanie kanału klienta odnajdywania do swojego istniejącego stosu kanału klienta, co bardzo intuicyjnego modelu programowania.</span><span class="sxs-lookup"><span data-stu-id="cf481-104">This feature enables developers to add a discovery client channel to their existing client channel stack, making the programming model very intuitive.</span></span> <span data-ttu-id="cf481-105">Po otwarciu kanału skojarzony adres usługi zostanie rozwiązany, przy użyciu odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="cf481-105">When the associated channel is opened, the address of the service is resolved using discovery.</span></span> <span data-ttu-id="cf481-106">W tym przykładzie składa się z następujących projektów:</span><span class="sxs-lookup"><span data-stu-id="cf481-106">This sample consists of the following projects:</span></span>  
  
-   <span data-ttu-id="cf481-107">**CalculatorService**: odnajdywanej usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="cf481-107">**CalculatorService**: A discoverable WCF service.</span></span>  
  
-   <span data-ttu-id="cf481-108">**CalculatorClient**: aplikacja klienta WCF, korzystającą z kanałem klienta odnajdywania w celu wyszukiwania i wywołać CalculatorService.</span><span class="sxs-lookup"><span data-stu-id="cf481-108">**CalculatorClient**: A WCF client application that uses the discovery client channel to search for and call the CalculatorService.</span></span>  
  
-   <span data-ttu-id="cf481-109">**DynamicCalculatorClient**: aplikacja kliencka WCF, która używa dynamicznego punkt końcowy do wyszukiwania i wywołać CalculatorService.</span><span class="sxs-lookup"><span data-stu-id="cf481-109">**DynamicCalculatorClient**: A WCF client application that uses a dynamic endpoint to search for and call the CalculatorService.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cf481-110">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="cf481-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cf481-111">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="cf481-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cf481-112">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="cf481-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cf481-113">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cf481-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a><span data-ttu-id="cf481-114">CalculatorService</span><span class="sxs-lookup"><span data-stu-id="cf481-114">CalculatorService</span></span>  
 <span data-ttu-id="cf481-115">Ten projekt zawiera usługę prosty kalkulator, który implementuje `ICalculatorService` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="cf481-115">This project contains a simple calculator service that implements the `ICalculatorService` contract.</span></span>  
  
 <span data-ttu-id="cf481-116">Następujący plik App.config służy do dodawania `<serviceDiscovery>` zachowanie w zachowania usług, jak również punkt końcowy odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="cf481-116">The following App.config file is used to add a `<serviceDiscovery>` behavior in the service behaviors as well as the discovery endpoint.</span></span>  
  
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
  
 <span data-ttu-id="cf481-117">Dzięki temu usługa i jej punkty końcowe wykrywalne.</span><span class="sxs-lookup"><span data-stu-id="cf481-117">This makes the service and its endpoints discoverable.</span></span> <span data-ttu-id="cf481-118">CalculatorService jest samodzielnie hostowana usługa, która dodaje jeden punkt końcowy, za pomocą powiązania NetTcpBinding.</span><span class="sxs-lookup"><span data-stu-id="cf481-118">The CalculatorService is a self-hosted service that adds one endpoint using the NetTcpBinding binding.</span></span> <span data-ttu-id="cf481-119">Dodaje także `EndpointDiscoveryBehavior` do punktu końcowego i określa zakres, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="cf481-119">It also adds an `EndpointDiscoveryBehavior` to the endpoint and specifies a scope as shown in the following code.</span></span>  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a><span data-ttu-id="cf481-120">CalculatorClient</span><span class="sxs-lookup"><span data-stu-id="cf481-120">CalculatorClient</span></span>  
 <span data-ttu-id="cf481-121">Ten projekt zawiera implementacji klienta, która wysyła komunikaty do CalculatorService.</span><span class="sxs-lookup"><span data-stu-id="cf481-121">This project contains a client implementation that sends messages to the CalculatorService.</span></span> <span data-ttu-id="cf481-122">Ten program używa `CreateCustomBindingWithDiscoveryElement()` metodę w celu utworzenia niestandardowego powiązania, które korzysta z kanałem klienta odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="cf481-122">This program uses the `CreateCustomBindingWithDiscoveryElement()` method to create a custom binding that uses the Discovery Client Channel.</span></span>  
  
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
  
 <span data-ttu-id="cf481-123">Po <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> jest tworzone, deweloper określa kryteria służące do wyszukiwania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="cf481-123">After the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is instantiated, the developer specifies the criteria to use when searching for a service.</span></span> <span data-ttu-id="cf481-124">W tym przypadku jest kryterium wyszukiwania odnajdywania `ICalculatorService` typu.</span><span class="sxs-lookup"><span data-stu-id="cf481-124">In this case, the discovery find criterion is the `ICalculatorService` type.</span></span> <span data-ttu-id="cf481-125">Ponadto określa Deweloper <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> co powoduje zwrócenie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> określający, gdzie należy spojrzeć na usługi.</span><span class="sxs-lookup"><span data-stu-id="cf481-125">Additionally, the developer specifies a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> which returns a <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> that specifies where to look for the services.</span></span> <span data-ttu-id="cf481-126"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Zwraca nowy <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cf481-126">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> returns a new <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance.</span></span> <span data-ttu-id="cf481-127">Aby uzyskać więcej informacji, zobacz [przy użyciu powiązania niestandardowego z kanałem klienta odnajdywania](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="cf481-127">For more information, see [Using a Custom Binding with the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span></span>  
  
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
  
 <span data-ttu-id="cf481-128">W takim przypadku klient używa protokołu UDP multiemisji mechanizm definicją protokołu odnajdowania, aby wyszukać usługi w podsieci lokalnej.</span><span class="sxs-lookup"><span data-stu-id="cf481-128">In this case, the client uses the UDP multicast mechanism defined by the Discovery protocol to search for services on the local subnet.</span></span> <span data-ttu-id="cf481-129">Pozostała część metody tworzy powiązania niestandardowego i wstawia elementu powiązania odnajdywania na górze stosu.</span><span class="sxs-lookup"><span data-stu-id="cf481-129">The remainder of the method creates a custom binding and inserts the Discovery binding element at the top of the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf481-130"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Muszą być umieszczone na górze stosu powiązania.</span><span class="sxs-lookup"><span data-stu-id="cf481-130">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must be placed on the top of the binding stack.</span></span> <span data-ttu-id="cf481-131">Wszelkie <xref:System.ServiceModel.Channels.BindingElement> w górnej części <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> musisz upewnić się, że fabryki kanałów lub tworzy kanał nie używa `EndpointAddress` lub `Via` właściwości, ponieważ rzeczywistego adresu znajduje się tylko na kanału klienta odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="cf481-131">Any <xref:System.ServiceModel.Channels.BindingElement> on top of <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must make sure that the channel factory or channel it creates does not use the `EndpointAddress` or `Via` properties, because the actual address is found only at the Discovery client channel.</span></span>  
  
 <span data-ttu-id="cf481-132">Następnie `CalculatorClient` mogą być utworzone przez przekazanie tego niestandardowego powiązania, a także adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="cf481-132">Next, the `CalculatorClient` can be instantiated by passing in this custom binding as well as an endpoint address.</span></span>  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 <span data-ttu-id="cf481-133">Korzystając z kanałem klienta odnajdywania, adres punktu końcowego stałej określony wcześniej jest przekazywany w.</span><span class="sxs-lookup"><span data-stu-id="cf481-133">When using the Discovery Client Channel, the constant endpoint address specified previously is passed in.</span></span> <span data-ttu-id="cf481-134">Teraz w czasie wykonywania, kanału klienta odnajdywania umożliwia znalezienie usługi określonych przez kryteria wyszukiwania i nawiązuje z nim połączenie.</span><span class="sxs-lookup"><span data-stu-id="cf481-134">Now at runtime, the Discovery Client Channel finds the service specified by the find criteria and connects to it.</span></span> <span data-ttu-id="cf481-135">Dla usługi i klienta do nawiązania połączenia muszą mieć ten sam podstawowy stos powiązania.</span><span class="sxs-lookup"><span data-stu-id="cf481-135">For the service and the client to establish a connection, they must also have the same underlying binding stack.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="cf481-136">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="cf481-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="cf481-137">Otwórz rozwiązanie w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf481-137">Open the solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="cf481-138">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="cf481-138">Build the solution.</span></span>  
  
3.  <span data-ttu-id="cf481-139">Uruchamianie aplikacji usługi, a każdy z klienta aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf481-139">Run the service application and each of the client applications.</span></span>  
  
4.  <span data-ttu-id="cf481-140">Sprawdź, czy klient mógł znaleźć tę usługę, nie wiedząc o tym adresu.</span><span class="sxs-lookup"><span data-stu-id="cf481-140">Observe that the client was able to find the service without knowing its address.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf481-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf481-141">See Also</span></span>
