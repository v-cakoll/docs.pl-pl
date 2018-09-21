---
title: Niestandardowe kryteria znajdowania
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 699260fcef7680710f721d213dbf1126ebf7a896
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46471700"
---
# <a name="custom-find-criteria"></a>Niestandardowe kryteria znajdowania
Niniejszy przykład pokazuje, jak utworzyć niestandardowy zakres dopasowanie przy użyciu logiki i jak wdrożyć usługę odnajdywania niestandardowych. Klienci używają niestandardowy zakres funkcji dopasowywania, aby dostosować i dalszych są oparte na funkcji Znajdź dostarczane przez system odnajdowania usługi WCF. Scenariusz, który opisano w tym przykładzie jest następująca:  
  
1.  Klient szuka usługi kalkulatora.  
  
2.  Aby zawęzić wyszukiwanie, klient musi używać niestandardowego zakresu regułę dopasowania.  
  
3.  Zgodnie z regułą usługa odpowiada klient jeśli jej punkt końcowy zgodny z dowolnym z zakresów określonych przez klienta.  
  
## <a name="demonstrates"></a>Demonstracje  
  
-   Tworzenie usługi odnajdywanie niestandardowe.  
  
-   Implementowanie dopasowanie niestandardowy zakres przez algorytm.  
  
## <a name="discussion"></a>Dyskusja  
 Klient jest wyszukiwanie typu "Lub" spełniające kryteria. Usługa odpowiada ponownie, jeśli zakresy na jego punkty końcowe pasuje do żadnego z zakresów określonych przez klienta. W takim przypadku klient szuka usługi Kalkulator, które ma jakiekolwiek z zakresów na poniższej liście:  
  
1.  `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2.  `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3.  `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 Aby to osiągnąć, klient określa, że usługi do użycia niestandardowego zakresu reguły dopasowania, przekazując dopasowanie niestandardowy zakres według identyfikatora URI. W celu ułatwienia dopasowywania niestandardowy zakres, usługi, należy użyć usługę odnajdywania niestandardowych, która rozumie reguły dopasowania niestandardowy zakres i skojarzonej logiki pasującego implementuje.  
  
 W projekcie klienta Otwórz plik Program.cs. Należy pamiętać, że `ScopeMatchBy` pole `FindCriteria` obiekt jest ustawiony do określonego identyfikatora URI. Ten identyfikator jest wysyłane do usługi. Jeśli usługa nie rozpoznaje tej reguły, ignoruje żądanie Znajdź klienta.  
  
 Otwórz projekt usługi. Trzy pliki są używane do implementowania usługi odnajdywania niestandardowe:  
  
1.  **AsyncResult.cs**: jest to implementacja `AsyncResult` metod odnajdywania jest to wymagane.  
  
2.  **CustomDiscoveryService.cs**: ten plik implementuje usługę odnajdywanie niestandardowe. Rozszerza implementację <xref:System.ServiceModel.Discovery.DiscoveryService> klasy i zastępuje niezbędne metody. Należy pamiętać, implementacja <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> metody. Metoda sprawdza, czy dopasowanie niestandardowy zakres przez regułę został określony przez klienta. Jest to ten sam niestandardowy identyfikator URI, który klient określony wcześniej. Jeśli określono niestandardową regułę, ścieżka kodu, która implementuje logikę dopasowania "Lub" jest zakończony.  
  
     Tę logikę niestandardowego przechodzi przez wszystkie zakresy na każdym z punktów końcowych, które usługa ma. Jeśli żadnego z zakresów punktu końcowego pasuje do żadnego z zakresów określonych przez klienta, Usługa odnajdywania dodaje punkt końcowy do odpowiedzi, który jest wysyłany do klienta.  
  
3.  **CustomDiscoveryExtension.cs**: ostatni krok, przy wdrażaniu usługi odnajdywania polega na połączeniu tej implementacji niestandardowego odnajdywały usługę host usługi. Klasa pomocnika używana w tym miejscu jest `CustomDiscoveryExtension` klasy. Ta klasa rozszerza <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> klasy. Użytkownik musi przesłonić metodę <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> metody. W tym przypadku metoda zwraca wystąpienie usługę odnajdywania niestandardowej, która została utworzona wcześniej. `PublishedEndpoints` jest <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> zawierający wszystkie punkty końcowe aplikacji, które są dodawane do <xref:System.ServiceModel.ServiceHost>. Usługa odnajdywania niestandardowy używa tej wartości do wypełniania listy wewnętrznej. Użytkownik może dodać inne metadane punktu końcowego.  
  
 Wreszcie Otwórz plik Program.cs. Należy pamiętać, że zarówno <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> i `CustomDiscoveryExtension` są dodawane do hosta. Gdy odbywa się i host ma punkt końcowy, względem którego ma zostać odbierać komunikaty odnajdywania, aplikacja może użyć usługi odnajdywania niestandardowych.  
  
 Sprawdź, czy klient jest w stanie znaleźć tę usługę, nie wiedząc o tym adresu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Otwórz rozwiązanie, które zawiera projekt.  
  
2.  Skompiluj projekt.  
  
3.  Uruchom aplikację usługi.  
  
4.  Uruchom aplikację klienta.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
