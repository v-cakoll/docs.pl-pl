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
ms.workload: dotnet
ms.openlocfilehash: dbbaefbd32048924434342dc3f902c99a3c2448c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="discovery-binding-element-sample"></a>Przykład elementu powiązania odnajdywania
W tym przykładzie pokazano, jak element powiązania klienta odnajdywania umożliwia odnajdywanie usługi. Ta funkcja umożliwia deweloperom dodać kanałem klienta odnajdywania do ich istniejącego stosu kanału klienta, tworzenie bardzo intuicyjne modelu programowania. Po otwarciu kanału skojarzony adres usługi został rozwiązany za pomocą odnajdywania. W tym przykładzie składa się z następujących projektów:  
  
-   **CalculatorService**: wykrywalny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.  
  
-   **CalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji klienckiej, która korzysta z kanałem klienta odnajdywania do wyszukiwania i wywołać CalculatorService.  
  
-   **DynamicCalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji klienckiej, która używa do wyszukiwania i wywołać CalculatorService dynamiczne punktu końcowego.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a>CalculatorService  
 Ten projekt zawiera usługi prosty kalkulator, który implementuje `ICalculatorService` kontraktu.  
  
 Następujący plik App.config służy do dodawania `<serviceDiscovery>` zachowanie zachowania usługi, jak również punkt końcowy odnajdowania.  
  
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
  
 Dzięki temu usługa i jej punkty końcowe wykrywalny. CalculatorService jest samodzielnie hostowana usługa, która dodaje jeden punkt końcowy, za pomocą tego powiązania NetTcpBinding. Dodano również `EndpointDiscoveryBehavior` do punktu końcowego i określa zakres, jak pokazano w poniższym kodzie.  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a>CalculatorClient  
 Ten projekt zawiera implementację klienta, który wysyła wiadomości do CalculatorService. Ten program używa `CreateCustomBindingWithDiscoveryElement()` metodę w celu utworzenia niestandardowego powiązania, które korzysta z kanałem klienta odnajdywania.  
  
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
  
 Po <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> jest uruchomiony, deweloper określa kryteria służące do wyszukiwania dla usługi. W takim przypadku kryterium wyszukiwania odnajdywania jest `ICalculatorService` typu. Ponadto określa dewelopera <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> co powoduje zwrócenie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> Określa, gdzie szukać usług. <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Zwraca nową <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpienia. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Używanie wiązania niestandardowego z kanałem klienta odnajdywania](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).  
  
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
  
 W takim przypadku klient używa protokołu UDP multiemisji mechanizm zdefiniowany przez Protokół odnajdywania wyszukiwania usług w podsieci lokalnej. W pozostałej części metoda tworzy niestandardowego powiązania i wstawia elementu powiązania odnajdywania w górnej części stosu.  
  
> [!NOTE]
>  <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Muszą znajdować się na wierzchołku stosu powiązania. Wszelkie <xref:System.ServiceModel.Channels.BindingElement> nad <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> należy się upewnić, że fabryki kanałów lub tworzy kanału nie używać `EndpointAddress` lub `Via` właściwości, ponieważ rzeczywista adres znajduje się tylko na kanałem klienta odnajdywania.  
  
 Następnie `CalculatorClient` mogą zostać utworzone przez przekazywanie w tym niestandardowego powiązania, a także adres punktu końcowego.  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 Korzystając z kanałem klienta odnajdywania, określony adres punktu końcowego stałej wcześniej jest przekazywana. Teraz w czasie wykonywania, kanałem klienta odnajdywania umożliwia znalezienie usługi określone przez kryteria znajdowania i nawiązuje z nim połączenie. Dla usługi i klienta, aby nawiązać połączenie muszą mieć taki sam podstawowy stos powiązania.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz rozwiązanie w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Skompiluj rozwiązanie.  
  
3.  Uruchamianie aplikacji usługi i każdego klienta aplikacji.  
  
4.  Sprawdź, czy klient mógł znaleźć usługi bez uprzedniego uzyskania informacji o jego adres.  
  
## <a name="see-also"></a>Zobacz też
