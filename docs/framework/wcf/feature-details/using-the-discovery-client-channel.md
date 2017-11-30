---
title: "Używanie kanału klienta odnajdywania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9d0aede489c6b5db029a9df37f84d0a067bbf836
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-discovery-client-channel"></a>Używanie kanału klienta odnajdywania
Podczas pisania aplikacji klienta WCF musisz znać adres punktu końcowego usługi jest wywoływany. W wielu sytuacjach adres punktu końcowego usługi nie jest znany wcześniej lub adresu usługi zmienia się wraz z upływem czasu. Kanałem klienta odnajdywania służy do tworzenia aplikacji klienta WCF, opisu usługi, którą chcesz się połączyć, i kanału klienta automatycznie wysyła żądanie sondowania. Gdy usługa odpowiada, kanałem klienta odnajdywania pobiera adres punktu końcowego usługi z odpowiedzi sondowania i używa go do wywołania tej usługi.  
  
## <a name="using-the-discovery-client-channel"></a>Używanie kanału klienta odnajdywania  
 Aby korzystać z kanałem klienta odnajdywania, dodać wystąpienia <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> do stosu kanału klienta. Możesz też użyć <xref:System.ServiceModel.Discovery.DynamicEndpoint> i <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> jest automatycznie dodawany do wiązania, jeśli nie znajduje się już.  
  
> [!CAUTION]
>  Zalecane jest <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> to najwyższy element na stosie kanału klienta. Dowolny element powiązania jest dodawany nad <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> musi upewnij się, że <xref:System.ServiceModel.ChannelFactory> lub tworzy kanału nie używa adres punktu końcowego lub `Via` adresu (przekazany do `CreateChannel` — metoda), ponieważ nie może zawierać poprawny adres.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Klasa zawiera dwie właściwości publicznej:  
  
1.  <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, który jest używany do opisu usługi ma zostać wywołana.  
  
2.  <!--zz <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpoint%2A>  --> `DiscoveryEndpoint`, which specifies the discovery endpoint to send discovery messages to.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A> Właściwość umożliwia określenie kontraktu usługi, którego szukasz, wszelkie niezbędne zakres identyfikatorów URI, a maksymalna liczba czasu, aby otworzyć kanału. Typ kontraktu jest określany przez wywołanie konstruktora <<!--zz <xref:System.ServiceModel.Discovery.FindCriteria%2A>  --> `FindCriteria`>. Zakres identyfikatorów URI mogą być dodawane do <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> właściwości. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> Właściwości można określić maksymalną liczbę wyników, do których klient próbuje nawiązać połączenie. Po odebraniu odpowiedzi sondowania klient spróbuje otworzyć kanału przy użyciu adresu punktu końcowego z odpowiedzi sondowania. Jeśli wystąpi wyjątek Klient przechodzi do następnego odpowiedzi sondowania, oczekiwanie na więcej odpowiedzi do odebrania w razie potrzeby. Nadal czasu pomyślnie otwarciu kanału lub osiągnięto maksymalną liczbę wyników. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]te ustawienia, zobacz <<!--zz <xref:System.ServiceModel.Discovery.FindCriteria%2A>  --> `FindCriteria`>.  
  
 <!--zz <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpoint%2A>  --> `DiscoveryEndpoint%2A>` Właściwość umożliwia określenie odnajdowania punktu końcowego. Zazwyczaj jest to <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, ale może być dowolnym prawidłowy punkt końcowy.  
  
 Podczas tworzenia powiązania w celu użycia do komunikowania się z usługą, należy pamiętać, aby użyć dokładnie tego samego powiązania jako usługa. Jedyną różnicą jest to klient powiązania ma <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> wierzchołku stosu. Jeśli usługa używa jednego powiązania dostarczane przez system, Utwórz nową <xref:System.ServiceModel.Channels.CustomBinding> i podaj powiązania dostarczane przez system <!--zz <xref:System.ServiceModel.CustomBinding.CustomBinding%2A> `CustomBinding` --> konstruktora. Następnie można dodać <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> przez wywołanie metody `Insert` na <!--zz <xref:System.ServiceModel.Channels.Binding.Elements%2A> --> `Elements` właściwości.  
  
 Po dodaniu <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> do wiązania i skonfigurowaniu go, można tworzyć wystąpienia klasy klienta WCF, otwórz go i wywołania metody. W poniższym przykładzie użyto kanałem klienta odnajdywania, aby dowiedzieć się, usługa WCF, która implementuje `ICalculator` klasy (używane w samouczku pobierania programu WCF) i wywołania jego `Add` metody.  
  
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
  
## <a name="security-and-the-discovery-client-channel"></a>Bezpieczeństwo i kanałem klienta odnajdywania  
 Korzystając z kanałem klienta odnajdywania, jest określany dwa punkty końcowe. Jeden służy do odnajdywania wiadomości, zwykle <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, a drugi to punkt końcowy aplikacji. Podczas implementowania bezpiecznej usługi, należy uważać, aby zabezpieczyć oba punkty końcowe. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]zabezpieczenia, zobacz [zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).
