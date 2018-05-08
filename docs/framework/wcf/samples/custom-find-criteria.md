---
title: Niestandardowe kryteria znajdowania
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 6c9363add13e38ded75685e4115a5084629d6505
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="custom-find-criteria"></a>Niestandardowe kryteria znajdowania
Przykładzie pokazano, jak utworzyć niestandardowy zakres dopasowania przy użyciu logiki i sposobu implementacji usługi odnajdywania niestandardowych. Klienci używają niestandardowy zakres funkcji dopasowywania uściślić i dalsze bazując funkcje Znajdź dostarczane przez system odnajdywania WCF. Scenariusz, które obejmuje ten przykład jest następujący:  
  
1.  Klient szuka usługi Kalkulator.  
  
2.  Aby uściślić wyszukiwanie, klient musi używać niestandardowego zakresu regułę dopasowania.  
  
3.  Zgodnie z regułą usługa odpowiada klientowi Jeśli punktu końcowego pasuje do żadnego z zakresów określonych przez klienta.  
  
## <a name="demonstrates"></a>Demonstracje  
  
-   Tworzenie niestandardowych odnajdywania usługi.  
  
-   Implementowanie dopasowanie niestandardowy zakres przez algorytm.  
  
## <a name="discussion"></a>Omówienie  
 Dla typu "Lub" spełniających kryteria wyszukiwania klienta. Usługa odpowiada ponownie, jeśli zakresy na jego punkty końcowe pasuje do żadnej z zakresów określonych przez klienta. W takim przypadku klient jest szuka usługi Kalkulator, które ma jakiekolwiek z zakresów na poniższej liście:  
  
1.  `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2.  `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3.  `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 W tym celu klienta określa, że usługi do użycia niestandardowego zakresu regułę dopasowania przez przekazywanie dopasowanie niestandardowy zakres przez identyfikator URI. W celu ułatwienia dopasowywania niestandardowy zakres, usługa musi używać usługi odnajdywania niestandardowych rozumie reguły dopasowania niestandardowy zakres, który implementuje skojarzonej logiki zgodnego.  
  
 W projekcie klienta Otwórz plik Program.cs. Należy pamiętać, że `ScopeMatchBy` pole `FindCriteria` obiektu ma ustawioną wartość określonego identyfikatora URI. Ten identyfikator jest wysyłane do usługi. Jeśli usługa nie rozpoznaje tej reguły, ignoruje żądanie Znajdź klienta.  
  
 Otwórz projekt usługi. Trzy pliki są używane do implementowania usługi odnajdywania niestandardowe:  
  
1.  **AsyncResult.cs**: jest to implementacja `AsyncResult` , co jest wymagane przez metody odnajdywania.  
  
2.  **CustomDiscoveryService.cs**: ten plik implementuje usługę odnajdywania niestandardowych. Implementacja rozszerza <xref:System.ServiceModel.Discovery.DiscoveryService> klasy i zastępuje metody niezbędne. Należy pamiętać, implementacja <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> metody. Metoda sprawdza, czy dopasowanie niestandardowy zakres przez regułę został określony przez klienta. To jest tej samej niestandardowy identyfikator URI, który poprzednio określono klienta. Jeśli określono niestandardową regułę, implementujący logiki dopasowania "Lub" ścieżkę kodu jest zakończony.  
  
     Tej niestandardowej logiki przechodzi przez wszystkie zakresy na każdym z punktów końcowych, które w usłudze. Jeśli żadnego punktu końcowego zakresy zgodny z żadną z zakresów dostarczonych przez klienta usługi odnajdywania dodaje tego punktu końcowego do odpowiedzi, który jest wysyłany do klienta.  
  
3.  **CustomDiscoveryExtension.cs**: ostatni krok w przypadku implementowania usługi odnajdywania jest podłączenie tej implementacji niestandardowego odnajdywanie usługi hosta usługi. Klasa pomocnika używany w tym miejscu jest `CustomDiscoveryExtension` klasy. Ta klasa rozszerza <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> klasy. Użytkownik musi przesłonić <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> metody. W tym przypadku metoda zwraca wystąpienie usługi odnajdywania niestandardowego, który został utworzony przed. `PublishedEndpoints` jest <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> zawierający wszystkie punkty końcowe aplikacji, które są dodawane do <xref:System.ServiceModel.ServiceHost>. Usługi odnajdywania niestandardowe używa go do wypełnienia listy wewnętrznej. Użytkownik może dodać inne metadane punktu końcowego.  
  
 Na koniec Otwórz plik Program.cs. Należy pamiętać, że zarówno <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> i `CustomDiscoveryExtension` zostaną dodane do hosta. Gdy odbywa się i host ma punkt końcowy służącym do odbierania wiadomości odnajdywania, aplikacja może korzystać z usługi odnajdywania niestandardowych.  
  
 Sprawdź, czy klient jest w stanie znaleźć usługi bez uprzedniego uzyskania informacji o jego adres.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Otwórz rozwiązanie, które zawiera projekt.  
  
2.  Skompiluj projekt.  
  
3.  Uruchom aplikację usługi.  
  
4.  Uruchom aplikację klienta.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
