---
title: Integracja buforowania platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 55e6213bf0c4c212ebcf4e68882d16532c0e4229
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061445"
---
# <a name="aspnet-caching-integration"></a>Integracja buforowania platformy ASP.NET
Niniejszy przykład pokazuje sposób wykorzystywania wyjściowej pamięci podręcznej platformy ASP.NET przy użyciu modelu programowania protokołu HTTP sieci WEB WCF. Zobacz [podstawowej usługi do zasobu](../../../../docs/framework/wcf/samples/basic-resource-service.md) próbki Self-Hosted wersję tego scenariusza, który w tym artykule omówiono szczegółowo implementacji usługi. Ten temat koncentruje się na funkcji Integracja z pamięci podręcznej danych wyjściowych platformy ASP.NET.  
  
## <a name="demonstrates"></a>Demonstracje  
 Integracja z pamięci podręcznej danych wyjściowych platformy ASP.NET  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a>Dyskusja  
 W przykładzie użyto <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> korzystanie z platformy ASP.NET buforowania danych wyjściowych za pomocą usługi Windows Communication Foundation (WCF). <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Jest stosowany do operacji usługi i zawiera nazwę profilu pamięci podręcznej w pliku konfiguracji, który ma zostać zastosowany do odpowiedzi od danej operacji.  
  
 W pliku Service.cs przykładowego projektu usługi zarówno `GetCustomer` i `GetCustomers` operacje są oznaczone <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, który zapewnia nazwa profilu pamięci podręcznej "CacheFor60Seconds". W pliku Web.config projektu usługi profilu pamięci podręcznej "CacheFor60Seconds" znajduje się w obszarze <`caching`> elementu <`system.web`>. Dla tego profilu pamięci podręcznej wartości `duration` atrybut jest "60", więc odpowiedzi skojarzony z tym profilem są buforowane w pamięci podręcznej danych wyjściowych platformy ASP.NET w 60 sekund. Ponadto w przypadku tego profilu pamięci podręcznej `varmByParam` ma ustawioną wartość atrybutu "format" tego zażąda z różnymi wartościami dla `format` zapytania parametr ciągu ma ich odpowiedzi na buforowane osobno. Na koniec pamięci podręcznej profilu `varyByHeader` ma ustawioną wartość atrybutu "Akceptuj", więc ich odpowiedzi na buforowane osobno żądania z różnych wartości nagłówka Accept.  
  
 Plik program.CS w projekcie klienta pokazuje, jak takiego klienta mogą być tworzone za pomocą <xref:System.Net.HttpWebRequest>. Należy pamiętać, że jest to tylko jeden sposób uzyskiwania dostępu do usługi WCF. Istnieje również możliwość uzyskania dostępu do usługi przy użyciu innych klas .NET Framework, takich jak WCF fabryki kanałów i <xref:System.Net.WebClient>. Inne przykłady w zestawie SDK (takie jak [podstawowa usługa HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) próbki i [automatyczne wybieranie formatu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) przykładowy) ilustrują sposób korzystania z tych klas do komunikowania się z usługą WCF.  
  
## <a name="to-run-the-sample"></a>Aby uruchomić przykład  
 Przykład obejmuje trzy projekty:  
  
-   **Usługa**: projekt aplikacji sieci Web, która obejmuje usługi HTTP programu WCF hostowanych w programie ASP.NET.  
  
-   **Klient**: projekt aplikacji konsoli, która sprawia, że wywołań do usługi.  
  
-   **Typowe**: biblioteki udostępnionej, który zawiera typ klienta używany przez klienta i usługi.  
  
 Po uruchomieniu aplikacji konsolowej klienta klient wysyła żądania do usługi i zapisuje odpowiednie informacje z odpowiedzi w oknie konsoli.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Otwórz rozwiązanie dla przykładu integracja buforowania platformy ASP.NET.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
3.  Jeśli **Eksploratora rozwiązań** okno nie jest jeszcze otwarty, naciśnij klawisze CTRL + W + S.  
  
4.  Z **Eksploratora rozwiązań** okna, kliknij prawym przyciskiem myszy **usługi** projektu, a następnie wybierz **Uruchom nowe wystąpienie**. Spowoduje to uruchomienie oprogramowania ASP.NET development server, który hostuje usługę.  
  
5.  Z **Eksploratora rozwiązań** okna, kliknij prawym przyciskiem myszy **klienta** projektu, a następnie wybierz **Uruchom nowe wystąpienie**.  
  
6.  Okna konsoli klienta pojawia się i zawiera identyfikator URI uruchomioną usługę i identyfikator URI elementu HTML pomocy strony dla uruchomionej usługi. W dowolnym momencie możesz wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce.  
  
7.  Po uruchomieniu przykładu klienta zapisuje stan bieżącego działania.  
  
8.  Naciśnij dowolny klawisz, aby zakończyć aplikację konsoli klienta.  
  
9. Naciśnij klawisze SHIFT + F5, aby zatrzymać debugowanie usługi.  
  
10. W obszarze powiadomień Windows kliknij prawym przyciskiem myszy ikonę serwera rozwoju platformy ASP.NET, a następnie wybierz **zatrzymać**.
