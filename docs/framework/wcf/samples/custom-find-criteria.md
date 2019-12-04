---
title: Niestandardowe kryteria znajdowania
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: a7f1b5996f3aefe1ccd77d3ddc117bc7c53ed2aa
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715463"
---
# <a name="custom-find-criteria"></a>Niestandardowe kryteria znajdowania
Ten przykład pokazuje, jak utworzyć niestandardowe dopasowanie zakresu przy użyciu logiki i jak wdrożyć niestandardową usługę odnajdywania. Klienci korzystają z funkcji dopasowywania zakresów niestandardowych w celu udoskonalenia i dalszej kompilacji na podstawie udostępnianej przez system funkcji odnajdowania usługi WCF. Ten przykład obejmuje następujące zagadnienia:  
  
1. Klient szuka usługi kalkulatora.  
  
2. Aby uściślić wyszukiwanie, klient musi używać niestandardowej reguły dopasowywania zakresu.  
  
3. Zgodnie z tą regułą usługa reaguje z powrotem do klienta, jeśli jego punkt końcowy jest zgodny z dowolnym z zakresów określonych przez klienta.  
  
## <a name="demonstrates"></a>Przedstawia  
  
- Tworzenie niestandardowej usługi odnajdywania.  
  
- Implementowanie niestandardowego dopasowania zakresu przez algorytm.  
  
## <a name="discussion"></a>Dyskusji  
 Klient szuka kryteriów dopasowania typu "lub". Usługa reaguje ponownie, jeśli zakresy w punktach końcowych pasują do dowolnego z zakresów dostarczonych przez klienta. W takim przypadku klient szuka usługi kalkulatora, która ma dowolne z zakresów na poniższej liście:  
  
1. `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2. `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3. `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 Aby to osiągnąć, klient kieruje usługi do użycia niestandardowej reguły dopasowywania zakresu przez przekazanie w niestandardowym zakresie według identyfikatora URI. Aby ułatwić dopasowanie zakresu niestandardowego, usługa musi używać niestandardowej usługi odnajdywania, która rozumie regułę niestandardowego dopasowania zakresu i implementuje skojarzoną logikę zgodną.  
  
 W projekcie klienta Otwórz plik Program.cs. Należy zauważyć, że pole `ScopeMatchBy` obiektu `FindCriteria` jest ustawione na określony identyfikator URI. Ten identyfikator jest wysyłany do usługi. Jeśli usługa nie rozpoznaje tej reguły, zignoruje żądanie wyszukiwania klienta.  
  
 Otwórz projekt usługi. Do zaimplementowania niestandardowej usługi odnajdywania są używane trzy pliki:  
  
1. **AsyncResult.cs**: to jest implementacja `AsyncResult`, która jest wymagana przez metody odnajdywania.  
  
2. **CustomDiscoveryService.cs**: ten plik implementuje niestandardową usługę odnajdywania. Implementacja rozszerza klasę <xref:System.ServiceModel.Discovery.DiscoveryService> i zastępuje wymagane metody. Zanotuj implementację metody <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A>. Metoda sprawdza, czy niestandardowy dopasowanie zakresu według reguły został określony przez klienta. Jest to ten sam niestandardowy identyfikator URI, który został wcześniej określony przez klienta. Jeśli zostanie określona reguła niestandardowa, następuje ścieżka kodu implementująca logikę dopasowania "OR".  
  
     Ta niestandardowa logika przechodzi przez wszystkie zakresy w każdym punkcie końcowym, który ma usługa. Jeśli którykolwiek z zakresów punktu końcowego jest zgodny z dowolnym z zakresów dostarczonych przez klienta, usługa odnajdywania dodaje ten punkt końcowy do odpowiedzi wysyłanej do klienta.  
  
3. **CustomDiscoveryExtension.cs**: ostatni krok implementacji usługi odnajdywania polega na połączeniu tej implementacji niestandardowej usługi odnajdywania z hostem usługi. Użyta w tym miejscu Klasa pomocnika jest klasą `CustomDiscoveryExtension`. Ta Klasa rozszerza klasę <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension>. Użytkownik musi zastąpić metodę <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A>. W takim przypadku metoda zwraca wystąpienie niestandardowej usługi odnajdywania, która została utworzona wcześniej. `PublishedEndpoints` to <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, która zawiera wszystkie punkty końcowe aplikacji, które są dodawane do <xref:System.ServiceModel.ServiceHost>. Usługa odnajdywania niestandardowego używa tego do wypełniania listy wewnętrznej. Użytkownik może również dodać inne metadane punktu końcowego.  
  
 Na koniec Otwórz Program.cs. Należy zauważyć, że zarówno <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>, jak i `CustomDiscoveryExtension` są dodawane do hosta. Gdy to zrobisz, a host ma punkt końcowy, w którym będą odbierane komunikaty odnajdowania, aplikacja może używać niestandardowej usługi odnajdywania.  
  
 Zwróć uwagę, że klient może znaleźć usługę bez znajomości jej adresu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Otwórz rozwiązanie, które zawiera projekt.  
  
2. Skompiluj projekt.  
  
3. Uruchom aplikację usługi.  
  
4. Uruchom aplikację kliencką.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
