---
title: Federacja — przykład
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: bc2c28300d9bfc3c30388f8d13e05a23a9f37287
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051915"
---
# <a name="federation-sample"></a>Federacja — przykład
Niniejszy przykład pokazuje zabezpieczeń.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Windows Communication Foundation (WCF) obsługuje wdrażanie architektury zabezpieczeń za pomocą `wsFederationHttpBinding`. `wsFederationHttpBinding` Zapewnia bezpieczne, niezawodne i interoperacyjne powiązanie, które obejmuje korzystanie z protokołu HTTP jako podstawowy mechanizm transportu dla komunikacji żądanie/nietypizowana odpowiedź i Text/XML do kodowania w formacie o komunikacji sieciowej. Aby uzyskać więcej informacji na temat federacji w programie WCF zobacz [Federacji](../../../../docs/framework/wcf/feature-details/federation.md).  
  
 Scenariusz składa się z 4 elementów:  
  
- Usługa księgarni  
  
- Księgarni usługi STS  
  
- HomeRealm STS  
  
- Księgarni klienta  
  
 Usługa księgarni obsługuje dwie operacje `BrowseBooks` i `BuyBook`. Zezwala na dostęp anonimowy do `BrowseBooks` operacja, ale wymaga dostępu uwierzytelnionego do dostępu `BuyBooks` operacji. Uwierzytelnianie mają postać token wystawiony przez usługę STS księgarni. Wskazuje plik konfiguracyjny usługi księgarni klientów przy użyciu usługi STS księgarni `wsFederationHttpBinding`.  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 Usługa STS księgarni wymaga, że klienci uwierzytelniania przy użyciu tokenu wystawionego przez usługę STS HomeRealm. Ponownie plik konfiguracji dla usługi STS księgarni wskazuje klientów przy użyciu usługi STS HomeRealm `wsFederationHttpBinding`.  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 Kolejność zdarzeń przy uzyskiwaniu dostępu do `BuyBook` operacja jest w następujący sposób:  
  
1. Klient uwierzytelnia się do usługi STS HomeRealm przy użyciu poświadczeń Windows.  
  
2. HomeRealm usługi STS wystawia token, który może służyć do uwierzytelniania usługi STS księgarni.  
  
3. Klient jest uwierzytelniany przy użyciu tokenu wystawionego przez usługę STS HomeRealm usługi STS księgarni.  
  
4. Księgarni Usługa STS wystawia token, który może służyć do uwierzytelniania w usłudze księgarni.  
  
5. Klient uwierzytelnia się w usłudze księgarni przy użyciu tokenu wystawionego przez usługę STS księgarni.  
  
6. Klient uzyskuje dostęp do `BuyBook` operacji.  
  
 Zobacz następujące instrukcje dotyczące sposobu konfigurowania i przeprowadzania tego przykładu.  
  
> [!NOTE]
>  Musi mieć uprawnienia do zapisu **wwwroot** katalogu, aby uruchomić ten przykład.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Otwórz okno polecenia zestawu SDK. W ścieżce próbki należy uruchomić Setup.bat. Tworzy katalogi wirtualne wymagane dla przykładu i instaluje wymagane certyfikaty z odpowiednimi uprawnieniami.  
  
    > [!NOTE]
    >  Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z wierszem polecenia Windows SDK. Wymaga to, że zmienna środowiskowa MSSDK odwołują się do katalogu, w którym jest zainstalowany zestaw SDK. Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia Windows SDK. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], należy upewnić się, że zgodność z narzędziami zarządzania usług IIS 6.0 jest zainstalowany, ponieważ konfigurowania używa skrypty administratora usług IIS. Uruchamianie skryptu konfiguracji [!INCLUDE[wv](../../../../includes/wv-md.md)] wymaga uprawnień administratora.  
  
2. Otwórz FederationSample.sln w programie Visual Studio i wybierz **Kompiluj rozwiązanie** z **kompilacji** menu. Kompilacje wspólne pliki projektu, księgarni usługi STS księgarni, HomeRealm STS i ich wdrażania w usługach IIS. To również kompilacji aplikacji klienckiej księgarni i umieszcza BookStoreClient.exe wykonywalny w folderze FederationSample\BookStoreClient\bin\Debug.  
  
3. Double-click BookStoreClient.exe. Zostanie wyświetlone okno BookStoreClient.  
  
4. Możesz przeglądać dostępne w księgarni książki, klikając **Przeglądaj książki**.  
  
5. Aby dokonać zakupu wybranej książki, wybierz książkę na liście, a następnie kliknij przycisk **kupić książki**. Aplikacja uruchamia się i jest uwierzytelniany przy użyciu uwierzytelniania Windows za pomocą usługi tokenu zabezpieczającego HomeRealm.  
  
     Próbka jest skonfigurowane tak, aby umożliwić użytkownikom kupowanie książek, które koszt 15 USD lub mniej. Podjęto próbę kupowanie książek, które są droższe niż 15 USD wyniki w kliencie pobieranie komunikat Odmowa dostępu z usługi Store książek.  
  
    > [!NOTE]
    >  Przykład nie aktualizuje limit środków użytkownika po zakupie. Można wielokrotnie kupowanie książek w ramach limitu środków (stałe) użytkownika.  
  
#### <a name="to-clean-up"></a>Aby wyczyścić  
  
1. Uruchom Cleanup.bat. Usuwa katalogi wirtualne, które były tworzone podczas konfiguracji i usuwa również zainstalowane podczas instalacji certyfikaty.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
