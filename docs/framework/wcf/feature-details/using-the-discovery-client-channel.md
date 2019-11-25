---
title: Używanie kanału klienta odnajdywania
ms.date: 03/30/2017
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
ms.openlocfilehash: 05ca54d62179d024e619bc5c9c70a4e08b9dd62f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975938"
---
# <a name="using-the-discovery-client-channel"></a>Używanie kanału klienta odnajdywania
Podczas pisania aplikacji klienckiej WCF należy znać adres punktu końcowego wywoływanej usługi. W wielu sytuacjach adres punktu końcowego usługi nie jest znany z góry lub adres usługi zmienia się w miarę upływu czasu. Kanał klienta odnajdywania umożliwia napisanie aplikacji klienckiej WCF, określenie usługi, która ma zostać wywołana, a kanał klienta automatycznie wysyła żądanie sondowania. Gdy usługa odpowiada, kanał klienta odnajdowania Pobiera adres punktu końcowego dla usługi z odpowiedzi sondy i używa jej do wywoływania usługi.  
  
## <a name="using-the-discovery-client-channel"></a>Używanie kanału klienta odnajdywania  
 Aby użyć kanału klienta odnajdywania, Dodaj wystąpienie <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> do stosu kanału klienta. Alternatywnie możesz użyć <xref:System.ServiceModel.Discovery.DynamicEndpoint>, a <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> jest automatycznie dodawany do powiązania, jeśli jeszcze nie istnieje.  
  
> [!CAUTION]
> Zaleca się, aby <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> jest najwyższego poziomu elementu na stosie kanału klienta. Każdy element powiązania, który jest dodawany do <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> musi mieć pewność, że <xref:System.ServiceModel.ChannelFactory> lub kanał tworzony przez niego nie używa adresu punktu końcowego lub adresu `Via` (przekazaną do metody `CreateChannel`), ponieważ mogą nie zawierać poprawnego adresu.  
  
 Klasa <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> zawiera dwie właściwości publiczne:  
  
1. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, który jest używany do opisywania usługi, która ma zostać wywołana.  
  
2. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A>, która określa punkt końcowy odnajdywania, do którego mają być wysyłane komunikaty wykrywania.  
  
 Właściwość <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> umożliwia określenie kontraktu usługi, którego szukasz, wymaganych identyfikatorów URI zakresu oraz maksymalną liczbę prób otwarcia kanału. Typ kontraktu jest określony przez wywołanie konstruktora <xref:System.ServiceModel.Discovery.FindCriteria>. Identyfikatory URI zakresu można dodać do właściwości <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A>. Właściwość <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> pozwala określić maksymalną liczbę wyników, z którymi klient próbuje nawiązać połączenie. Po otrzymaniu odpowiedzi sondy klient próbuje otworzyć kanał przy użyciu adresu punktu końcowego z odpowiedzi na sondę. Jeśli wystąpi wyjątek, klient przechodzi do następnej odpowiedzi sondy, czekając na odebranie większej liczby odpowiedzi w razie potrzeby. Kontynuuje to działanie do momentu pomyślnego otwarcia kanału lub osiągnięcia maksymalnej liczby wyników. Aby uzyskać więcej informacji na temat tych ustawień, zobacz <xref:System.ServiceModel.Discovery.FindCriteria>.  
  
 Właściwość <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> umożliwia określenie punktu końcowego odnajdywania, który ma być używany. Zwykle jest to <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, ale może być dowolnym prawidłowym punktem końcowym.  
  
 Podczas tworzenia powiązania, które ma być używane do komunikacji z usługą, należy zachować ostrożność, aby użyć dokładnie tego samego powiązania co usługa. Jedyną różnicą jest to, że powiązanie klienta ma <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> w górnej części stosu. Jeśli usługa używa jednego z powiązań dostarczonych przez system, Utwórz nowe <xref:System.ServiceModel.Channels.CustomBinding> i przekaż powiązanie dostarczone przez system do konstruktora <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A>. Następnie można dodać <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, wywołując `Insert` właściwości <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A>.  
  
 Po dodaniu <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> do powiązania i skonfigurowaniu go można utworzyć wystąpienie klasy klienta WCF, otworzyć ją i wywołać jej metody. W poniższym przykładzie użyto kanału klienta odnajdywania w celu odnalezienia usługi WCF implementującej klasę `ICalculator` (używane w samouczku Wprowadzenie WCF) i wywołanie jej `Add` metody.  
  
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
 W przypadku korzystania z kanału klienta odnajdywania są określane dwa punkty końcowe. Jest on używany w przypadku komunikatów odnajdywania, zwykle <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, a drugi jest punktem końcowym aplikacji. Podczas implementowania bezpiecznej usługi należy zachować ostrożność, aby zabezpieczyć oba punkty końcowe. Aby uzyskać więcej informacji na temat zabezpieczeń, zobacz [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).
