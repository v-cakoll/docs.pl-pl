---
title: Integracja buforowania platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 420ff192caf41a37b6229bf36e32124f3646d69c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="aspnet-caching-integration"></a>Integracja buforowania platformy ASP.NET
W tym przykładzie pokazano, jak korzystać z pamięci podręcznej danych wyjściowych programu ASP.NET z modelem programowania protokołu HTTP sieci WEB WCF. Zobacz [podstawowej usługi zasobów](../../../../docs/framework/wcf/samples/basic-resource-service.md) próbkowania dla siebie wersji tego scenariusza, który opisano szczegółowo implementacji usługi. Ten temat koncentruje się na funkcji Integracja z pamięci podręcznej danych wyjściowych programu ASP.NET.  
  
## <a name="demonstrates"></a>Demonstracje  
 Integracja z pamięci podręcznej danych wyjściowych programu ASP.NET  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a>Omówienie  
 W przykładzie użyto <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> mogą korzystać z ASP.NET dane wyjściowe pamięci podręcznej z usługą Windows Communication Foundation (WCF). <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Jest stosowany do operacji usługi, a także nazwę profilu pamięci podręcznej w pliku konfiguracji, który ma zostać zastosowany do odpowiedzi od danej operacji.  
  
 W pliku Service.cs przykładowy projekt usługi zarówno `GetCustomer` i `GetCustomers` operacji są oznaczone ikoną z <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, która zawiera nazwę profilu pamięci podręcznej "CacheFor60Seconds". W pliku Web.config projektu usługi, profil pamięci podręcznej "CacheFor60Seconds" znajduje się w obszarze <`caching`> elementu <`system.web`>. Dla tego profilu pamięci podręcznej, wartość `duration` atrybutu jest "60", dlatego skojarzone z tym profilem odpowiedzi są buforowane w pamięci podręcznej danych wyjściowych programu ASP.NET przez 60 sekund. Ponadto dla tego profilu pamięci podręcznej `varmByParam` atrybut jest ustawiony na "format" wniosek o różnych wartościach dla `format` zapytania parametr ciągu ma odpowiedzi w pamięci podręcznej oddzielnie. Ponadto pamięć podręczna profilu `varyByHeader` atrybut jest ustawiony na "Akceptuj", więc żądania za pomocą innej wartości nagłówka Accept oddzielnie buforowane odpowiedzi.  
  
 Program.CS w projekcie klienta pokazano, jak takiego klienta mogą być tworzone za pomocą <xref:System.Net.HttpWebRequest>. Należy pamiętać, że jest tylko jeden sposób uzyskiwania dostępu do usługi WCF. Istnieje również możliwość uzyskania dostępu do usługi przy użyciu innych klas .NET Framework, takich jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fabryki kanałów i <xref:System.Net.WebClient>. Inne przykłady w zestawie SDK (takich jak [podstawowa usługa HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) próbki i [automatycznego wyboru formatu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) przykładowe) ilustrują sposób używania tych klas do komunikowania się z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.  
  
## <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
 Przykład obejmuje trzy projekty:  
  
-   **Usługa**: projekt aplikacji sieci Web A, która obejmuje usługi HTTP usług WCF hostowanych w programie ASP.NET.  
  
-   **Klient**: projekt aplikacji konsoli wykonywania wywołań do usługi.  
  
-   **Typowe**: biblioteki udostępnionej, którą zawiera typ klienta używany przez klienta i usługi.  
  
 Podczas działania aplikacji konsoli klienta, klient wysyła żądania do usługi i zapisuje istotnych informacji z odpowiedzi w oknie konsoli.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Otwórz rozwiązanie przykładowej integracja buforowania platformy ASP.NET.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
3.  Jeśli **Eksploratora rozwiązań** okno nie jest jeszcze otwarty, naciśnij kombinację klawiszy CTRL + P + S.  
  
4.  Z **Eksploratora rozwiązań** okna, kliknij prawym przyciskiem myszy **usługi** projekt i wybierz **uruchomić nowe wystąpienie**. Spowoduje to uruchomienie ASP.NET development server, który obsługuje usługę.  
  
5.  Z **Eksploratora rozwiązań** okna, kliknij prawym przyciskiem myszy **klienta** projekt i wybierz **uruchomić nowe wystąpienie**.  
  
6.  Okno konsoli klienta pojawia się i zawiera identyfikator URI uruchomionej usługi i identyfikator URI elementu HTML pomocy strony uruchomionej usługi. W dowolnym momencie można wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce.  
  
7.  Jak działa próbki, klient zapisuje stan bieżącego działania.  
  
8.  Naciśnij dowolny klawisz, aby zakończyć działanie aplikacji konsoli klienta.  
  
9. Naciśnij klawisz SHIFT + F5, aby zatrzymać debugowanie usługi.  
  
10. W obszarze powiadomień systemu Windows kliknij prawym przyciskiem myszy ikonę ASP.NET development serwera i wybierz **zatrzymać**.
