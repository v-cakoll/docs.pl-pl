---
title: Niestandardowe kryteria znajdowania
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 3bafe89f5c114106eece02c41599cf485591c1cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183861"
---
# <a name="custom-find-criteria"></a>Niestandardowe kryteria znajdowania
W tym przykładzie pokazano, jak utworzyć dopasowanie zakresu niestandardowego przy użyciu logiki i jak zaimplementować niestandardową usługę odnajdywania. Klienci używają funkcji dopasowywania zakresu niestandardowego, aby uściślić i dalej korzystać z funkcji znajdowania dostarczonych przez system w WCF Discovery. Scenariusz, który obejmuje ten przykład jest następujący:  
  
1. Klient szuka usługi kalkulatora.  
  
2. Aby zawęzić wyszukiwanie, klient musi użyć reguły dopasowywania zakresu niestandardowego.  
  
3. Zgodnie z tą regułą usługa odpowiada z powrotem do klienta, jeśli jego punkt końcowy pasuje do dowolnego zakresu określonego przez klienta.  
  
## <a name="demonstrates"></a>Demonstracje  
  
- Tworzenie niestandardowej usługi odnajdywania.  
  
- Implementowanie niestandardowego zakresu zgodnego według algorytmu.  
  
## <a name="discussion"></a>Dyskusji  
 Klient szuka kryteriów dopasowywania typu "OR". Usługa odpowiada z powrotem, jeśli zakresy w jego punktach końcowych odpowiadają dowolne z zakresów dostarczonych przez klienta. W takim przypadku klient szuka usługi kalkulatora, która ma którykolwiek z zakresów na następującej liście:  
  
1. `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2. `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3. `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 Aby to osiągnąć, klient kieruje usługi do używania reguły dopasowywania zakresu niestandardowego, przekazując w niestandardowym zakresie zgodne przez identyfikator URI. Aby ułatwić dopasowywanie zakresu niestandardowego, usługa musi używać niestandardowej usługi odnajdywania, która rozumie regułę dopasowania zakresu niestandardowego i implementuje skojarzoną logikę dopasowania.  
  
 W projekcie klienta otwórz plik Program.cs. Należy zauważyć, `ScopeMatchBy` że `FindCriteria` pole obiektu jest ustawiona na określony identyfikator URI. Ten identyfikator jest wysyłany do usługi. Jeśli usługa nie rozumie tej reguły, ignoruje żądanie znalezienia klienta.  
  
 Otwórz projekt usługi. Trzy pliki są używane do implementacji usługi odnajdowania niestandardowego:  
  
1. **AsyncResult.cs:** Jest to `AsyncResult` implementacja, która jest wymagana przez metody odnajdywania.  
  
2. **CustomDiscoveryService.cs:** Ten plik implementuje usługę odnajdowania niestandardowego. Implementacja rozszerza <xref:System.ServiceModel.Discovery.DiscoveryService> klasę i zastępuje niezbędne metody. Należy zwrócić uwagę <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> na implementację metody. Metoda sprawdza, czy niestandardowy zakres zgodny przez regułę został określony przez klienta. Jest to ten sam niestandardowy identyfikator URI, który klient określił wcześniej. Jeśli reguła niestandardowa jest określona, ścieżka kodu, która implementuje logikę dopasowania "OR".  
  
     Ta logika niestandardowa przechodzi przez wszystkie zakresy w każdym z punktów końcowych, które ma usługa. Jeśli którykolwiek z zakresów punktu końcowego są zgodne z dowolnym zakresem dostarczonym przez klienta, usługa odnajdywania dodaje ten punkt końcowy do odpowiedzi, która jest wysyłana z powrotem do klienta.  
  
3. **CustomDiscoveryExtension.cs:** Ostatnim krokiem w implementacji usługi odnajdywania jest połączenie tej implementacji usługi odnajdowania niestandardowego z hostem usługi. Klasa pomocnika używana w `CustomDiscoveryExtension` tym miejscu jest klasą. Ta klasa rozszerza <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> klasę. Użytkownik musi zastąpić <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> metodę. W takim przypadku metoda zwraca wystąpienie usługi odnajdywania niestandardowego, który został utworzony wcześniej. `PublishedEndpoints`jest <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> to, która zawiera wszystkie punkty końcowe <xref:System.ServiceModel.ServiceHost>aplikacji, które są dodawane do . Usługa odnajdywania niestandardowego używa tego do wypełniania swojej listy wewnętrznej. Użytkownik może również dodać inne metadane punktu końcowego.  
  
 Nareszcie otwórz Program.cs. Należy zauważyć, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> `CustomDiscoveryExtension` że zarówno i są dodawane do hosta. Po wykonaniu tej pracy i host ma punkt końcowy, za pomocą którego do odbierania komunikatów odnajdywania, aplikacja może korzystać z usługi odnajdywania niestandardowego.  
  
 Należy zauważyć, że klient jest w stanie znaleźć usługę bez znajomości jej adresu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Otwórz rozwiązanie, które zawiera projekt.  
  
2. Skompiluj projekt.  
  
3. Uruchom aplikację usługi.  
  
4. Uruchom aplikację kliencką.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
