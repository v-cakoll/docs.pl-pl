---
title: Federacja — przykład
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 00cb9a13a01687fb41f1d5c09f277d582f706e3b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594689"
---
# <a name="federation-sample"></a>Federacja — przykład
Ten przykład pokazuje zabezpieczenia federacyjne.  
  
## <a name="sample-details"></a>Przykładowe szczegóły  
 Windows Communication Foundation (WCF) zapewnia obsługę wdrażania federacyjnych architektur zabezpieczeń za pomocą programu `wsFederationHttpBinding` . `wsFederationHttpBinding`Zapewnia bezpieczne, niezawodne i interoperacyjne powiązanie, które polega na użyciu protokołu HTTP jako podstawowego mechanizmu transportowego do komunikacji żądania/odpowiedzi oraz text/xml jako formatu sieci do kodowania. Aby uzyskać więcej informacji na temat Federacji w programie WCF, zobacz [Federacja](../feature-details/federation.md).  
  
 Scenariusz składa się z 4 sztuk:  
  
- Usługa księgarni  
  
- Księgarni STS  
  
- HomeRealm STS  
  
- Klient księgarni  
  
 Usługa księgarni obsługuje dwie operacje `BrowseBooks` i `BuyBook` . Umożliwia anonimowy dostęp do `BrowseBooks` operacji, ale wymaga dostępu uwierzytelnionego, aby uzyskać dostęp do `BuyBooks` operacji. Uwierzytelnianie przyjmuje postać tokenu wystawionego przez usługę STS księgarni. Plik konfiguracji dla klientów punktów usługi księgarni w usłudze STS księgarni przy użyciu `wsFederationHttpBinding` .  
  
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
  
 Usługa STS księgarni wymaga, aby klienci uwierzytelniali się przy użyciu tokenu wystawionego przez usługę HomeRealm STS. Ponownie plik konfiguracji dla klientów punktów usługi STS księgarni do usługi STS HomeRealm przy użyciu `wsFederationHttpBinding` .  
  
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
  
 Sekwencja zdarzeń podczas uzyskiwania dostępu do `BuyBook` operacji jest następująca:  
  
1. Klient jest uwierzytelniany w usłudze STS HomeRealm przy użyciu poświadczeń systemu Windows.  
  
2. Usługa STS HomeRealm wystawia token, którego można użyć do uwierzytelniania w usłudze księgarni STS.  
  
3. Klient jest uwierzytelniany w usłudze STS księgarni przy użyciu tokenu wystawionego przez usługę HomeRealm STS.  
  
4. Usługa STS księgarni wystawia token, którego można użyć do uwierzytelnienia w usłudze księgarni.  
  
5. Klient jest uwierzytelniany w usłudze księgarni przy użyciu tokenu wystawionego przez usługę księgarni STS.  
  
6. Klient uzyskuje dostęp do `BuyBook` operacji.  
  
 Zapoznaj się z poniższymi instrukcjami dotyczącymi sposobu konfigurowania i uruchamiania tego przykładu.  
  
> [!NOTE]
> Aby uruchomić ten przykład, musisz mieć uprawnienia do zapisu w katalogu **wwwroot** .  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Otwórz okno polecenia zestawu SDK. W przykładowej ścieżce uruchom setup. bat. Spowoduje to utworzenie katalogów wirtualnych wymaganych dla przykładu i zainstalowanie wymaganych certyfikatów z odpowiednimi uprawnieniami.  
  
    > [!NOTE]
    > Plik wsadowy Setup. bat został zaprojektowany tak, aby można go było uruchomić z poziomu wiersza polecenia Windows SDK. Wymaga, aby zmienna środowiskowa MSSDK wskazywała katalog, w którym zainstalowano zestaw SDK. Ta zmienna środowiskowa jest ustawiana automatycznie w wierszu polecenia Windows SDK. W systemie Windows Vista należy upewnić się, że zgodność z zarządzaniem usługami IIS 6,0 jest zainstalowana, ponieważ konfiguracja używa skryptów administratora usług IIS. Uruchomienie skryptu konfiguracji w systemie Windows Vista wymaga uprawnień administratora.  
  
2. Otwórz FederationSample. sln w programie Visual Studio i wybierz opcję **Kompiluj rozwiązanie** z menu **kompilacja** . Powoduje to utworzenie wspólnych plików projektu, usług księgarni, księgarni STS, HomeRealm STS i wdrożenie ich w usługach IIS. Powoduje to również kompilację aplikacji klienckiej księgarni i umieszczenie pliku wykonywalnego BookStoreClient. exe w folderze FederationSample\BookStoreClient\bin\Debug.  
  
3. Kliknij dwukrotnie plik BookStoreClient. exe. Zostanie wyświetlone okno BookStoreClient.  
  
4. Książki dostępne w księgarni można przeglądać, klikając pozycję **Przeglądaj książki**.  
  
5. Aby zakupić określoną książkę, wybierz ją z listy, a następnie kliknij pozycję **Kup książkę**. Aplikacja uruchamia się i uwierzytelnia przy użyciu uwierzytelniania systemu Windows za pomocą usługi tokenu zabezpieczającego HomeRealm.  
  
     Przykład jest skonfigurowany tak, aby zezwalał użytkownikom na kupowanie książek o kosztach $15 lub mniejszych. Podjęto próbę zakupu książek, które są droższe niż $15 wyniki w przypadku otrzymania przez klienta komunikatu o odmowie dostępu od usługi książki.  
  
    > [!NOTE]
    > Przykład nie aktualizuje limitu kredytowego użytkownika po zakupie. Można wielokrotnie kupować książki w ramach limitu kredytu użytkownika (ustalonego).  
  
#### <a name="to-clean-up"></a>Aby oczyścić  
  
1. Uruchom Oczyść. bat. Spowoduje to usunięcie katalogów wirtualnych, które zostały utworzone podczas konfiguracji, a także spowoduje usunięcie certyfikatów zainstalowanych podczas instalacji.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
