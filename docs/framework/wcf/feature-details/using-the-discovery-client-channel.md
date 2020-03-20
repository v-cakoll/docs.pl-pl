---
title: Używanie kanału klienta odnajdywania
ms.date: 03/30/2017
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
ms.openlocfilehash: 2d9dd68d233541f4d8cb3185adc1023cd5a19de1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184265"
---
# <a name="using-the-discovery-client-channel"></a>Używanie kanału klienta odnajdywania
Podczas pisania aplikacji klienckiej WCF należy znać adres punktu końcowego usługi, którą wywołujesz. W wielu sytuacjach adres końcowy usługi nie jest znany z wyprzedzeniem lub adres usługi zmienia się wraz z upływem czasu. Discovery Client Channel umożliwia pisanie aplikacji klienckiej WCF, opisać usługę, którą chcesz wywołać, a kanał klienta automatycznie wysyła żądanie sondy. Gdy usługa odpowiada, kanał klienta odnajdywania pobiera adres punktu końcowego dla usługi z odpowiedzi sondy i używa go do wywołania usługi.  
  
## <a name="using-the-discovery-client-channel"></a>Używanie kanału klienta odnajdywania  
 Aby użyć kanału klienta odnajdywania, dodaj wystąpienie stosu <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> kanału klienta. Alternatywnie można użyć <xref:System.ServiceModel.Discovery.DynamicEndpoint> i <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> a jest automatycznie dodawany do powiązania, jeśli nie jest już obecny.  
  
> [!CAUTION]
> Zaleca się, <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> że jest najwyższej elementu na stosie kanału klienta. Każdy element wiązania, który jest <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> dodawany na <xref:System.ServiceModel.ChannelFactory> górze musi upewnić się, że `Via` lub kanał, `CreateChannel` który tworzy nie używa adresu lub adresu punktu końcowego (przekazywane do metody), ponieważ mogą nie zawierać poprawny adres.  
  
 Klasa <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> zawiera dwie właściwości publiczne:  
  
1. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, który jest używany do opisywania usługi, którą chcesz wywołać.  
  
2. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A>który określa punkt końcowy odnajdywania, do którego mają być wysyłane komunikaty odnajdywania.  
  
 Właściwość <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> umożliwia określenie umowy serwisowej, której szukasz, wszelkie wymagane identyfikatory URI zakresu i maksymalną liczbę czasu, aby spróbować otworzyć kanał. Typ kontraktu jest określony przez <xref:System.ServiceModel.Discovery.FindCriteria>wywołanie konstruktora . Identyfikatory identyfikatorów URI <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> zakresu można dodać do właściwości. Właściwość <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> umożliwia określenie maksymalnej liczby wyników, z którymi klient próbuje się połączyć. Po odebraniu odpowiedzi sondy klient próbuje otworzyć kanał przy użyciu adresu punktu końcowego z odpowiedzi sondy. Jeśli wystąpi wyjątek klient przechodzi do następnej odpowiedzi sondy, oczekiwanie na więcej odpowiedzi, które mają zostać odebrane, jeśli to konieczne. Kontynuuje to do momentu pomyślnego otwarcia kanału lub osiągnięcia maksymalnej liczby wyników. Aby uzyskać więcej informacji <xref:System.ServiceModel.Discovery.FindCriteria>na temat tych ustawień, zobacz .  
  
 Właściwość <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> umożliwia określenie punktu końcowego odnajdywania do użycia. Zwykle jest to <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, ale może to być dowolny prawidłowy punkt końcowy.  
  
 Podczas tworzenia powiązania do komunikowania się z usługą, należy uważać, aby użyć dokładnie tego samego powiązania jako usługi. Jedyną różnicą jest powiązanie klienta ma <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> na górze stosu. Jeśli usługa jest przy użyciu jednego z powiązań <xref:System.ServiceModel.Channels.CustomBinding> dostarczonych przez system, utworzyć <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> nowy i przekazać w systemie powiązania do konstruktora. Następnie można dodać, <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> `Insert` dzwoniąc <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> do obiektu.  
  
 Po dodaniu <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> do powiązania i skonfigurowaniu go, można utworzyć wystąpienie klasy klienta WCF, otworzyć go i wywołać jego metody. W poniższym przykładzie użyto odnajdywania kanału `ICalculator` klienta do odnajdowania usługi WCF, która implementuje klasę (używane w samouczku Wprowadzenie WCF) i wywołuje jego `Add` metodę.  
  
```csharp
// Create the DiscoveryClientBindingElement  
DiscoveryClientBindingElement bindingElement = new DiscoveryClientBindingElement();  
// Search for a service that implements the ICalculator interface, attempting to open  
// the channel a maximum of 2 times  
bindingElement.FindCriteria = new FindCriteria(typeof(ICalculator)) { MaxResults = 2 };  
// Use the UdpDiscoveryEndpoint  
bindingElement.DiscoveryEndpoint = new UdpDiscoveryEndpoint();  
  
// The service uses the BasicHttpBinding, so use that and insert the DiscoveryClientBindingElement at the
// top of the stack  
CustomBinding binding = new CustomBinding(new BasicHttpBinding());  
binding.Elements.Insert(0,bindingElement);  
  
try  
{  
    // Create the WCF client and call a method  
    CalculatorClient client = new CalculatorClient(binding, new EndpointAddress("http://schemas.microsoft.com/dynamic"));  
    client.Open();  
    client.Add(1, 1);  
}  
catch (EndpointNotFoundException ex)  
{  
    Console.WriteLine("An exception occurred: " + ex.Message);  
}  
```  
  
## <a name="security-and-the-discovery-client-channel"></a>Zabezpieczenia i kanał klienta odnajdywania  
 Podczas korzystania z kanału klienta odnajdywania, dwa punkty końcowe są określane. Jeden jest używany do <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>komunikatów odnajdywania, zwykle , a drugi jest punktem końcowym aplikacji. Podczas wdrażania bezpiecznej usługi, należy zwrócić uwagę na zabezpieczenie obu punktów końcowych. Aby uzyskać więcej informacji na temat zabezpieczeń, zobacz [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).
