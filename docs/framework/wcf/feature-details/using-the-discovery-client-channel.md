---
title: Używanie kanału klienta odnajdywania
ms.date: 03/30/2017
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
ms.openlocfilehash: 298cafe34b20a3644f967acf15f831be5b0b90ac
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329938"
---
# <a name="using-the-discovery-client-channel"></a>Używanie kanału klienta odnajdywania
Podczas pisania aplikacji klienta WCF, musisz znać adres punktu końcowego usługi, którą wywołujesz. W wielu sytuacjach adres punktu końcowego usługi nie jest znana z wyprzedzeniem lub adres usługi zmienia się wraz z upływem czasu. Kanału klienta odnajdywania umożliwia pisanie aplikacji klienta WCF, opisano usługi, którą chcesz się połączyć, a kanału klienta automatycznie wysyła żądania sondowania. Gdy usługa odpowie, kanału klienta odnajdywania pobiera adres punktu końcowego usługi z odpowiedzi na sondę i używa go do wywołania tej usługi.  
  
## <a name="using-the-discovery-client-channel"></a>Używanie kanału klienta odnajdywania  
 Aby korzystać z kanałem klienta odnajdywania, dodaje wystąpienie <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> do stosu kanału klienta. Możesz też użyć <xref:System.ServiceModel.Discovery.DynamicEndpoint> i <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> jest automatycznie dodawany do wiązania, jeśli nie jeszcze nie istnieje.  
  
> [!CAUTION]
>  Zalecane jest, <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> jest elementem najważniejsze na stosie kanału klienta. Dowolny element powiązania, który jest dodawany w górnej części <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> musi upewnij się, że <xref:System.ServiceModel.ChannelFactory> lub tworzy kanał nie używa adresu punktu końcowego lub `Via` adresu (przekazany do `CreateChannel` metoda), ponieważ nie może zawierać poprawny adres.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Klasa zawiera dwie właściwości publiczne:  
  
1. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, który jest używany do opisu usługi ma zostać wywołana.  
  
2. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> który określa punkt końcowy odnajdowania do wysyłania wiadomości odnajdywania.  
  
 <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> Właściwość umożliwia określenie kontraktu usługi, którego szukasz, wszystkie wymagane zakres identyfikatorów URI, a maksymalna liczba czas na próby otwarcia kanału. Typ kontraktu jest określony przez wywołanie konstruktora <xref:System.ServiceModel.Discovery.FindCriteria>. Zakres identyfikatorów URI mogą być dodawane do <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> właściwości. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> Właściwości można określić maksymalną liczbę wyników, w którym klient próbuje nawiązać połączenie. Po otrzymaniu odpowiedzi sondy klient spróbuje otworzyć kanału przy użyciu adresu punktu końcowego z odpowiedzi na sondę. Jeśli wystąpi wyjątek Klient przechodzi do następnego odpowiedzi sondowania, oczekiwania na odpowiedzi więcej do odbioru, jeśli to konieczne. Kontynuuje to zrobić, dopóki kanał zostanie pomyślnie otwarty lub osiągnięto maksymalną liczbę wyników. Aby uzyskać więcej informacji o tych ustawieniach, zobacz <xref:System.ServiceModel.Discovery.FindCriteria>.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> Właściwość pozwala określić punkt końcowy odnajdywania do użycia. Zazwyczaj jest to <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, ale może być dowolnym prawidłowego punktu końcowego.  
  
 Podczas tworzenia powiązania na potrzeby komunikacji z usługą, należy uważać, aby użyć dokładnie tego samego powiązania jako usługa. Jedyną różnicą jest to klient powiązania ma <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> górze stosu. Jeśli usługa używa jednego z powiązań dostarczanych przez system, Utwórz nowe <xref:System.ServiceModel.Channels.CustomBinding> i przekazać powiązania dostarczane przez system do <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> konstruktora. Następnie można dodać <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> przez wywołanie metody `Insert` na <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> właściwości.  
  
 Po dodaniu <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> do wiązania i skonfigurować go, można utworzyć wystąpienia klasy klienta WCF, otwórz go, a wywołać jego metody. W poniższym przykładzie użyto kanału klienta odnajdywania w celu odnalezienia usługi WCF, która implementuje `ICalculator` klasy (używane w ramach samouczka Wprowadzenie usługi WCF) i wywołuje jego `Add` metody.  
  
```  
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
  
## <a name="security-and-the-discovery-client-channel"></a>Zabezpieczenia i kanału klienta odnajdywania  
 Korzystając z kanałem klienta odnajdywania, określania dwa punkty końcowe. Jeden służy do odnajdywania wiadomości, zwykle <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, a drugi to punkt końcowy aplikacji. Podczas implementowania bezpiecznej usłudze, należy uważać, aby zabezpieczyć zarówno punkty końcowe. Aby uzyskać więcej informacji na temat zabezpieczeń, zobacz [zabezpieczania usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).
