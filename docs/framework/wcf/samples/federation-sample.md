---
title: Federacja — przykład
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 9ec462f88c0e3a039b7f288554be3e28f13ece08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144672"
---
# <a name="federation-sample"></a>Federacja — przykład
Ten przykład pokazuje zabezpieczenia federacyjne.  
  
## <a name="sample-details"></a>Przykładowe szczegóły  
 Windows Communication Foundation (WCF) zapewnia obsługę wdrażania architektur zabezpieczeń `wsFederationHttpBinding`federacyjnego za pośrednictwem . Zapewnia `wsFederationHttpBinding` bezpieczne, niezawodne i interoperacyjne powiązanie, które obejmuje użycie protokołu HTTP jako podstawowy mechanizm transportu dla komunikacji żądania/odpowiedzi i Text/XML jako formatu przewodowego do kodowania. Aby uzyskać więcej informacji na temat federacji w WCF, zobacz [Federacja](../../../../docs/framework/wcf/feature-details/federation.md).  
  
 Scenariusz składa się z 4 sztuk:  
  
- Usługa Księgarnia  
  
- Księgarnia STS  
  
- Strona głównaRealm STS  
  
- Klient księgarni  
  
 Usługa Księgarnia obsługuje dwie `BrowseBooks` `BuyBook`operacje i . Umożliwia anonimowy `BrowseBooks` dostęp do operacji, ale wymaga `BuyBooks` uwierzytelnionego dostępu do operacji. Uwierzytelnianie ma formę tokenu wystawionego przez sts księgarni. Plik konfiguracyjny usługi Księgarni wskazuje klientom usługę `wsFederationHttpBinding`BOOKStore STS przy użyciu pliku .  
  
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
  
 BookStore STS następnie wymaga, aby klienci uwierzytelnić przy użyciu tokenu wystawionego przez HomeRealm STS. Ponownie, plik konfiguracyjny dla BookStore STS wskazuje klientom `wsFederationHttpBinding`HomeRealm STS za pomocą .  
  
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
  
 Kolejność zdarzeń podczas uzyskiwania `BuyBook` dostępu do operacji jest następująca:  
  
1. Klient uwierzytelnia się w homerealm STS przy użyciu poświadczeń systemu Windows.  
  
2. HomeRealm STS wystawia token, który może służyć do uwierzytelniania w sts księgarni.  
  
3. Klient uwierzytelnia się w sts księgarni przy użyciu tokenu wydanego przez HomeRealm STS.  
  
4. BookStore STS wystawia token, który może służyć do uwierzytelniania w usłudze Księgarni.  
  
5. Klient uwierzytelnia się w usłudze Księgarni przy użyciu tokenu wystawionego przez sts księgarni.  
  
6. Klient uzyskuje dostęp `BuyBook` do operacji.  
  
 Zobacz poniższe instrukcje dotyczące konfigurowania i uruchamiania tego przykładu.  
  
> [!NOTE]
> Aby uruchomić ten przykład, musisz mieć uprawnienia do zapisu w katalogu **wwwroot.**  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Otwórz okno polecenia SDK. W przykładowej ścieżce uruchom plik Setup.bat. Spowoduje to utworzenie katalogów wirtualnych wymaganych dla próbki i zainstalowanie wymaganych certyfikatów z odpowiednimi uprawnieniami.  
  
    > [!NOTE]
    > Plik wsadowy setup.bat jest przeznaczony do uruchamiania z wiersza polecenia SDK systemu Windows. Wymaga to, aby zmienna środowiskowa MSSDK wskazywała katalog, w którym jest zainstalowany pakiet SDK. Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia zestawu Windows SDK. W systemie Windows Vista należy upewnić się, że zgodność zarządzania usługami IIS 6.0 jest zainstalowana, ponieważ konfiguracja używa skryptów administratora usług IIS. Uruchamianie skryptu konfiguracji w systemie Windows Vista wymaga uprawnień administratora.  
  
2. Otwórz FederationSample.sln w programie Visual Studio i wybierz **pozycję Zbudować rozwiązanie** z menu **Kompilacja.** Spowoduje to zbudowanie typowych plików projektu, usługi Księgarnia, StS księgarni, HomeRealm STS i wdraża je w usługach IIS. Spowoduje to również kompilację aplikacji klienta księgarni i umieszcza plik wykonywalny BookStoreClient.exe w folderze FederationSample\BookStoreClient\bin\Debug.  
  
3. Kliknij dwukrotnie pozycję BookStoreClient.exe. Zostanie wyświetlone okno BookStoreClient.  
  
4. Książki dostępne w księgarni można przeglądać, klikając pozycję **Przeglądaj książki**.  
  
5. Aby kupić konkretną książkę, wybierz książkę na liście i kliknij pozycję **Kup książkę**. Aplikacja uruchamia się i uwierzytelnia przy użyciu uwierzytelniania systemu Windows za pomocą usługi tokenu zabezpieczającego HomeRealm.  
  
     Próbka jest skonfigurowana tak, aby umożliwić użytkownikom zakup książek, które kosztują 15 USD lub mniej. Próba zakupu książek, które kosztują więcej niż 15 USD powoduje, że klient otrzymuje komunikat Odmowa dostępu z usługi Księgarnia.  
  
    > [!NOTE]
    > Przykład nie aktualizuje limitu kredytowego użytkownika po zakupie. Książki można wielokrotnie kupować w ramach (stałego) limitu kredytowego użytkownika.  
  
#### <a name="to-clean-up"></a>Aby oczyścić  
  
1. Uruchom Cleanup.bat. Spowoduje to usunięcie katalogów wirtualnych utworzonych podczas konfigurowania, a także usunięcie certyfikatów zainstalowanych podczas instalacji.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
