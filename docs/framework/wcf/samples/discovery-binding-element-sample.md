---
title: Przykład elementu powiązania odnajdywania
ms.date: 03/30/2017
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
ms.openlocfilehash: d906d9a389c50095f2af5d52e3874c3e43199e68
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964510"
---
# <a name="discovery-binding-element-sample"></a>Przykład elementu powiązania odnajdywania
W tym przykładzie pokazano, jak użyć elementu powiązania odnajdywania klienta do odnajdywania usługi. Ta funkcja umożliwia deweloperom Dodawanie kanału klienta odnajdywania do swojego istniejącego stosu kanału klienta, co bardzo intuicyjnego modelu programowania. Po otwarciu kanału skojarzony adres usługi zostanie rozwiązany, przy użyciu odnajdywania. W tym przykładzie składa się z następujących projektów:  
  
-   **CalculatorService**: odnajdywanej usługi WCF.  
  
-   **CalculatorClient**: aplikacja klienta WCF, korzystającą z kanałem klienta odnajdywania w celu wyszukiwania i wywołać CalculatorService.  
  
-   **DynamicCalculatorClient**: aplikacja kliencka WCF, która używa dynamicznego punkt końcowy do wyszukiwania i wywołać CalculatorService.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a>CalculatorService  
 Ten projekt zawiera usługę prosty kalkulator, który implementuje `ICalculatorService` kontraktu.  
  
 Następujący plik App.config służy do dodawania `<serviceDiscovery>` zachowanie w zachowania usług, jak również punkt końcowy odnajdowania.  
  
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
  
 Dzięki temu usługa i jej punkty końcowe wykrywalne. CalculatorService jest samodzielnie hostowana usługa, która dodaje jeden punkt końcowy, za pomocą powiązania NetTcpBinding. Dodaje także `EndpointDiscoveryBehavior` do punktu końcowego i określa zakres, jak pokazano w poniższym kodzie.  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a>CalculatorClient  
 Ten projekt zawiera implementacji klienta, która wysyła komunikaty do CalculatorService. Ten program używa `CreateCustomBindingWithDiscoveryElement()` metodę w celu utworzenia niestandardowego powiązania, które korzysta z kanałem klienta odnajdywania.  
  
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
  
 Po <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> jest tworzone, deweloper określa kryteria służące do wyszukiwania dla usługi. W tym przypadku jest kryterium wyszukiwania odnajdywania `ICalculatorService` typu. Ponadto określa Deweloper <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> co powoduje zwrócenie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> określający, gdzie należy spojrzeć na usługi. <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Zwraca nowy <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpienia. Aby uzyskać więcej informacji, zobacz [przy użyciu powiązania niestandardowego z kanałem klienta odnajdywania](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).  
  
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
  
 W takim przypadku klient używa protokołu UDP multiemisji mechanizm definicją protokołu odnajdowania, aby wyszukać usługi w podsieci lokalnej. Pozostała część metody tworzy powiązania niestandardowego i wstawia elementu powiązania odnajdywania na górze stosu.  
  
> [!NOTE]
>  <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Muszą być umieszczone na górze stosu powiązania. Wszelkie <xref:System.ServiceModel.Channels.BindingElement> w górnej części <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> musisz upewnić się, że fabryki kanałów lub tworzy kanał nie używa `EndpointAddress` lub `Via` właściwości, ponieważ rzeczywistego adresu znajduje się tylko na kanału klienta odnajdywania.  
  
 Następnie `CalculatorClient` mogą być utworzone przez przekazanie tego niestandardowego powiązania, a także adres punktu końcowego.  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 Korzystając z kanałem klienta odnajdywania, adres punktu końcowego stałej określony wcześniej jest przekazywany w. Teraz w czasie wykonywania, kanału klienta odnajdywania umożliwia znalezienie usługi określonych przez kryteria wyszukiwania i nawiązuje z nim połączenie. Dla usługi i klienta do nawiązania połączenia muszą mieć ten sam podstawowy stos powiązania.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz rozwiązanie w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Skompiluj rozwiązanie.  
  
3.  Uruchamianie aplikacji usługi, a każdy z klienta aplikacji.  
  
4.  Sprawdź, czy klient mógł znaleźć tę usługę, nie wiedząc o tym adresu.  
  
## <a name="see-also"></a>Zobacz też
