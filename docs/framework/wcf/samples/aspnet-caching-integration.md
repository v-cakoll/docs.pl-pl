---
title: Integracja buforowania platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 56f686b83deb576f1245a9d4b9df2df433ea1e2f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045780"
---
# <a name="aspnet-caching-integration"></a>Integracja buforowania platformy ASP.NET

Ten przykład pokazuje, jak korzystać z pamięci podręcznej ASP.NET Output z modelem programowania HTTP sieci WEB w programie WCF. Ten temat koncentruje się na funkcji integracji wyjściowej pamięci podręcznej ASP.NET.

## <a name="demonstrates"></a>Demonstracje

Integracja z wyjściową pamięcią podręczną ASP.NET

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`

## <a name="discussion"></a>Dyskusji

W przykładzie użyto programu <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> do wykorzystania ASP.NET wyjściowego buforowanie z usługą Windows Communication Foundation (WCF). Program <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> jest stosowany do operacji usługi i udostępnia nazwę profilu pamięci podręcznej w pliku konfiguracji, który powinien zostać zastosowany do odpowiedzi z danej operacji.

W pliku Service.cs przykładowego projektu `GetCustomer` usługi <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>operacje i `GetCustomers` są oznaczone przy użyciu, która zawiera nazwę profilu pamięci podręcznej "CacheFor60Seconds". W pliku Web. config projektu usługi profil pamięci podręcznej "CacheFor60Seconds" znajduje się w obszarze <`caching`> elementu <`system.web`>. Dla tego profilu pamięci podręcznej wartość `duration` atrybutu to "60", więc odpowiedzi skojarzone z tym profilem są buforowane w pamięci podręcznej ASP.NET wyjściowe przez 60 sekund. Ponadto dla tego profilu `varmByParam` pamięci podręcznej atrybut ma wartość "format", więc żądania o różnych wartościach `format` dla parametru ciągu zapytania są buforowane osobno. Na koniec `varyByHeader` atrybut profilu pamięci podręcznej jest ustawiony na wartość "Akceptuj", więc żądania o różnych wartościach nagłówka Accept są buforowane osobno.

Program.cs w projekcie klienta pokazuje, w jaki sposób ten klient może zostać utworzony za <xref:System.Net.HttpWebRequest>pomocą programu. Należy pamiętać, że jest to tylko jeden sposób na dostęp do usługi WCF. Istnieje również możliwość uzyskiwania dostępu do usługi przy użyciu innych klas .NET Framework, takich jak fabryka kanałów WCF <xref:System.Net.WebClient>i. Inne przykłady w zestawie SDK (na przykład [podstawowa usługa http](../../../../docs/framework/wcf/samples/basic-http-service.md) ) ilustrują sposób korzystania z tych klas do komunikowania się z usługą WCF.

## <a name="to-run-the-sample"></a>Aby uruchomić przykład

Przykład składa się z trzech projektów:

- **Usługa**: Projekt aplikacji sieci Web, który obejmuje usługę HTTP WCF hostowaną w ASP.NET.

- **Klient**: Projekt aplikacji konsolowej, który tworzy wywołania do usługi.

- **Wspólny**: Biblioteka udostępniona, która zawiera typ klienta używany przez klienta i usługę.

Gdy aplikacja konsoli klienta zostanie uruchomiona, klient wysyła żądania do usługi i zapisuje odpowiednie informacje z odpowiedzi do okna konsoli.

#### <a name="to-run-the-sample"></a>Aby uruchomić przykład

1. Otwórz rozwiązanie dla przykładu integracji pamięci podręcznej ASP.NET.

2. Naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować rozwiązanie.

3. Jeśli okno **Eksplorator rozwiązań** nie jest jeszcze otwarte, naciśnij klawisze Ctrl + W + S.

4. W oknie **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **usługi** i wybierz polecenie **Uruchom nowe wystąpienie**. Spowoduje to uruchomienie serwera deweloperskiego ASP.NET, który jest hostem usługi.

5. W oknie **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **klienta** i wybierz polecenie **Uruchom nowe wystąpienie**.

6. Zostanie wyświetlone okno konsoli klienta z identyfikatorem URI uruchomionej usługi oraz identyfikatorem URI strony pomocy HTML dla działającej usługi. W dowolnym momencie możesz wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce.

7. W miarę uruchamiania przykładu klient zapisuje stan bieżącego działania.

8. Naciśnij dowolny klawisz, aby zakończyć aplikację konsolową klienta.

9. Naciśnij klawisze SHIFT + F5, aby zatrzymać debugowanie usługi.

10. W obszarze powiadomień systemu Windows kliknij prawym przyciskiem myszy ikonę serwera deweloperskiego ASP.NET i wybierz polecenie **Zatrzymaj**.
