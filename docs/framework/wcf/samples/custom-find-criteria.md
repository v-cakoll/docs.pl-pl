---
title: Niestandardowe kryteria znajdowania
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 236cce194d89409ab19732c239459418cddd251b
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039943"
---
# <a name="custom-find-criteria"></a>Niestandardowe kryteria znajdowania
Ten przykład pokazuje, jak utworzyć niestandardowe dopasowanie zakresu przy użyciu logiki i jak wdrożyć niestandardową usługę odnajdywania. Klienci korzystają z funkcji dopasowywania zakresów niestandardowych w celu udoskonalenia i dalszej kompilacji na podstawie udostępnianej przez system funkcji odnajdowania usługi WCF. Ten przykład obejmuje następujące zagadnienia:  
  
1. Klient szuka usługi kalkulatora.  
  
2. Aby uściślić wyszukiwanie, klient musi używać niestandardowej reguły dopasowywania zakresu.  
  
3. Zgodnie z tą regułą usługa reaguje z powrotem do klienta, jeśli jego punkt końcowy jest zgodny z dowolnym z zakresów określonych przez klienta.  
  
## <a name="demonstrates"></a>Demonstracje  
  
- Tworzenie niestandardowej usługi odnajdywania.  
  
- Implementowanie niestandardowego dopasowania zakresu przez algorytm.  
  
## <a name="discussion"></a>Dyskusji  
 Klient szuka kryteriów dopasowania typu "lub". Usługa reaguje ponownie, jeśli zakresy w punktach końcowych pasują do dowolnego z zakresów dostarczonych przez klienta. W takim przypadku klient szuka usługi kalkulatora, która ma dowolne z zakresów na poniższej liście:  
  
1. `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2. `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3. `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 Aby to osiągnąć, klient kieruje usługi do użycia niestandardowej reguły dopasowywania zakresu przez przekazanie w niestandardowym zakresie według identyfikatora URI. Aby ułatwić dopasowanie zakresu niestandardowego, usługa musi używać niestandardowej usługi odnajdywania, która rozumie regułę niestandardowego dopasowania zakresu i implementuje skojarzoną logikę zgodną.  
  
 W projekcie klienta Otwórz plik Program.cs. Należy zauważyć, `ScopeMatchBy` że pole `FindCriteria` obiektu jest ustawione na określony identyfikator URI. Ten identyfikator jest wysyłany do usługi. Jeśli usługa nie rozpoznaje tej reguły, zignoruje żądanie wyszukiwania klienta.  
  
 Otwórz projekt usługi. Do zaimplementowania niestandardowej usługi odnajdywania są używane trzy pliki:  
  
1. **AsyncResult.cs**: Jest to implementacja `AsyncResult` , która jest wymagana przez metody odnajdywania.  
  
2. **CustomDiscoveryService.cs**: Ten plik implementuje niestandardową usługę odnajdywania. Implementacja rozszerza <xref:System.ServiceModel.Discovery.DiscoveryService> klasę i zastępuje wymagane metody. Zanotuj implementację <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> metody. Metoda sprawdza, czy niestandardowy dopasowanie zakresu według reguły został określony przez klienta. Jest to ten sam niestandardowy identyfikator URI, który został wcześniej określony przez klienta. Jeśli zostanie określona reguła niestandardowa, następuje ścieżka kodu implementująca logikę dopasowania "OR".  
  
     Ta niestandardowa logika przechodzi przez wszystkie zakresy w każdym punkcie końcowym, który ma usługa. Jeśli którykolwiek z zakresów punktu końcowego jest zgodny z dowolnym z zakresów dostarczonych przez klienta, usługa odnajdywania dodaje ten punkt końcowy do odpowiedzi wysyłanej do klienta.  
  
3. **CustomDiscoveryExtension.cs**: Ostatnim krokiem implementowania usługi odnajdywania jest połączenie tej implementacji niestandardowej usługi odnajdywania z hostem usługi. Użyta w tym miejscu Klasa pomocnika jest `CustomDiscoveryExtension` klasą. Ta Klasa rozszerza <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> klasę. Użytkownik musi zastąpić <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> metodę. W takim przypadku metoda zwraca wystąpienie niestandardowej usługi odnajdywania, która została utworzona wcześniej. `PublishedEndpoints`zawiera wszystkie punkty końcowe aplikacji, które są dodawane <xref:System.ServiceModel.ServiceHost>do. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Usługa odnajdywania niestandardowego używa tego do wypełniania listy wewnętrznej. Użytkownik może również dodać inne metadane punktu końcowego.  
  
 Na koniec Otwórz Program.cs. Należy zauważyć, że <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> oba `CustomDiscoveryExtension` elementy i są dodawane do hosta. Gdy to zrobisz, a host ma punkt końcowy, w którym będą odbierane komunikaty odnajdowania, aplikacja może używać niestandardowej usługi odnajdywania.  
  
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
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
