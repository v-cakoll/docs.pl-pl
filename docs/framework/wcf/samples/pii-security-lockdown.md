---
title: Blokada zabezpieczeń PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: 13ed280e9b7de2b205e0878761dbf97e168f06d3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326648"
---
# <a name="pii-security-lockdown"></a>Blokada zabezpieczeń PII
W tym przykładzie pokazano, jak kontrolować kilka funkcji związanych z zabezpieczeniami usługi Windows Communication Foundation (WCF) przez:  
  
-   Szyfrowanie poufnych informacji w pliku konfiguracji usługi.  
  
-   Blokowanie elementów w pliku konfiguracji, tak, aby zagnieżdżone podkatalogów usługi nie może przesłonić ustawienia.  
  
-   Kontrolowanie logowania z osobiście identyfikowalne dane osobowe w dziennikach śledzenia i wiadomości.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Dyskusja  
 Każda z tych funkcji może być używane razem lub osobno do sterowania aspektami zabezpieczeń usługi. Nie jest wyczerpujący zabezpieczaniem usługi WCF.  
  
 Pliki konfiguracji .NET Framework mogą zawierać poufne informacje, takie jak parametry połączenia z bazami danych. W scenariuszach hostowanych w sieci Web, współdzielonych może być pożądane, aby zaszyfrować te informacje w pliku konfiguracji dla usługi tak, aby dane zawarte w pliku konfiguracji jest odporna na zwykłych wyświetlania. .NET framework 2.0 i nowszych ma możliwość szyfrowania części pliku konfiguracji, za pomocą aplikacji Windows Data Protection programowania interfejsu (DPAPI) lub dostawcy usług kryptograficznych RSA. Umożliwia ona szyfrowanie aspnet_regiis.exe przy użyciu interfejsu DPAPI lub RSA wybierz części pliku konfiguracji.  
  
 W scenariuszach hostowanych w sieci Web jest możliwość usługi w podkatalogach innych usług. Semantyczne podczas określania wartości konfiguracji domyślnej umożliwia pliki konfiguracyjne w katalogach zagnieżdżone, aby zastąpić wartości konfiguracji w katalogu nadrzędnym. W niektórych sytuacjach może to być niepożądane różnych powodów. Konfiguracja obsługuje usługi WCF, blokowanie wartości konfiguracji, tak, aby zagnieżdżone konfiguracji generuje wyjątki, gdy zagnieżdżony usługa jest uruchomiona, przy użyciu przesłonić wartości konfiguracji.  
  
 W tym przykładzie pokazano, jak do sterowania rejestrowaniem z znanych osobiście identyfikowalne dane osobowe w dziennikach śledzenia i wiadomości, takich jak nazwa użytkownika i hasło. Domyślnie rejestrowanie znane też danych osobowych jest wyłączone, jednak w niektórych sytuacjach rejestrowania danych osobowych może być istotne w debugowaniu aplikacji. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Ponadto w tym przykładzie użyto śledzenie i rejestrowanie komunikatów. Aby uzyskać więcej informacji, zobacz [śledzenia i rejestrowania komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) próbki.  
  
## <a name="encrypting-configuration-file-elements"></a>Szyfrowanie elementy pliku konfiguracji  
 Ze względów bezpieczeństwa we współużytkowanym środowisku hostingu w sieci Web może być pożądane, aby zaszyfrować niektórych elementów konfiguracji, takich jak parametry połączenia bazy danych, które mogą zawierać poufne informacje. Element konfiguracji, może być zaszyfrowany za pomocą narzędzia aspnet_regiis.exe znaleziony w folderze .NET Framework, na przykład % WINDIR%\Micrsoft.NET\Framework\v4.0.20728.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>Aby zaszyfrować wartości w sekcji appSettings w pliku Web.config dla przykładu  
  
1. Otwórz wiersz polecenia przy użyciu Start -> Uruchom... Wpisz `cmd` i kliknij przycisk **OK**.  
  
2. Przejdź do bieżącego katalogu .NET Framework, wydając polecenie: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.  
  
3. Szyfrowanie ustawienia konfiguracji appSettings w folderze Web.config przy wykonaniu poniższego polecenia: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.  
  
 Więcej informacji o szyfrowaniu sekcje pliki konfiguracji można znaleźć, przeczytaj instrukcje na interfejsie DPAPI w konfiguracji platformy ASP.NET ([tworzenie zabezpieczanie aplikacji ASP.NET: Uwierzytelniania, autoryzacji i bezpieczna komunikacja](https://go.microsoft.com/fwlink/?LinkId=95137)) i porad na RSA w konfiguracji platformy ASP.NET ([How to: Szyfrowanie sekcji konfiguracyjnych w programie ASP.NET 2.0 przy użyciu RSA](https://go.microsoft.com/fwlink/?LinkId=95138)).  
  
## <a name="locking-configuration-file-elements"></a>Blokujące elementy pliku konfiguracji  
 W scenariuszach hostowanych w sieci Web jest możliwość usługi w podkatalogach usług. W takich przypadkach wartości konfiguracji dla usługi w podkatalogu są obliczane, sprawdzając wartości w pliku Machine.config i kolejno scalanie z wszelkich plikach Web.config w katalogi nadrzędne przenoszenia w dół drzewa katalogów i na koniec scalania Plik Web.config w katalogu, który zawiera usługi. Domyślne zachowanie dla większości elementów konfiguracji jest umożliwienie plików konfiguracji w podkatalogach do zastąpienie wartości ustawionych w katalogi nadrzędne. W niektórych sytuacjach może być pożądane, aby uniemożliwić pliki konfiguracyjne w podkatalogach zastąpienie wartości ustawionych w konfiguracji katalogu nadrzędnego.  
  
 .NET Framework umożliwia zablokowanie elementy pliku konfiguracji, tak, aby konfiguracje, które zastępują elementy konfiguracji zablokowane zgłaszają wyjątki czasu wykonywania.  
  
 Element konfiguracji można zablokować, określając `lockItem` atrybutu dla węzła w pliku konfiguracji, na przykład, aby zablokować węzła CalculatorServiceBehavior w pliku konfiguracji usługi Kalkulator w zagnieżdżone pliki konfiguracji Nie można można użyć zmiany zachowania następującą konfigurację.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>   
          <serviceBehaviors>   
             <behavior name="CalculatorServiceBehavior" lockItem="true">   
               <serviceMetadata httpGetEnabled="True"/>   
               <serviceDebug includeExceptionDetailInFaults="False" />   
             </behavior>   
          </serviceBehaviors>   
       </behaviors>   
    </system.serviceModel>  
</configuration>  
```  
  
 Blokowanie elementów konfiguracji, może być bardziej szczegółowe. Lista elementów, które można określić jako wartość `lockElements` zablokować zestaw elementów w obrębie kolekcji elementów podrzędnych. Lista atrybutów, można określić jako wartość `lockAttributes` zablokować zestaw atrybutów w obrębie elementu. Można zablokować cały zbiór elementów lub atrybutów z wyjątkiem określonej listy, określając `lockAllElementsExcept` lub `lockAllAttributesExcept` atrybutów w węźle.  
  
## <a name="pii-logging-configuration"></a>Konfiguracja rejestrowania danych osobowych  
 Rejestrowanie danych osobowych jest kontrolowane przez dwa przełączniki: ustawienie komputera znajduje się w pliku Machine.config, który umożliwia akceptowanie lub odrzucanie rejestrowanie dane osobowe i ustawienia aplikacji, umożliwiający administrator aplikacji włączyć rejestrowanie danych osobowych dla każdego administratora komputera Źródło w pliku Web.config lub App.config.  
  
 Ustawienia komputera jest kontrolowany przez ustawienie `enableLoggingKnownPii` do `true` lub `false`w `machineSettings` elementu w pliku Machine.config. Na przykład poniżej umożliwia aplikacji włączyć rejestrowanie danych osobowych.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  Plik Machine.config zawiera domyślna lokalizacja: % WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 Jeśli `enableLoggingKnownPii` atrybut nie jest obecny w pliku Machine.config, rejestrowanie danych osobowych jest niedozwolone.  
  
 Włączanie rejestrowania dla aplikacji odbywa się przez ustawienie właściwości PII `logKnownPii` atrybut elementu źródłowego do `true` lub `false` w pliku Web.config lub App.config. Na przykład poniżej umożliwia rejestrowanie danych osobowych dotyczących rejestrowania śledzenia i rejestrowania komunikatów.  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel.MessageLogging" logKnownPii="true">  
                <listeners>   
                ...   
                </listeners>  
            </source>  
            <source name="System.ServiceModel" switchValue="Verbose, ActivityTracing">  
            <listeners>  
        ...   
            </listeners>  
            </source>  
        </sources>  
    </system.diagnostics>  
</configuration>  
```  
  
 Jeśli `logKnownPii` atrybut nie jest określony, a następnie dane osobowe nie jest zalogowany.  
  
 Dane osobowe tylko jest rejestrowane, jeśli obie `enableLoggingKnownPii` ustawiono `true`, i `logKnownPii` ustawiono `true`.  
  
> [!NOTE]
>  System.Diagnostics ignoruje wszystkie atrybuty wszystkich źródeł, z wyjątkiem pierwszej wymienione w pliku konfiguracji. Dodawanie `logKnownPii` atrybut do drugiego źródła w pliku konfiguracji nie ma znaczenia.  
  
> [!IMPORTANT]
>  Aby uruchomić ten przykład obejmuje ręcznej modyfikacji pliku Machine.config. Należy uważać podczas modyfikujących Machine.config niepoprawne wartości lub nieprawidłowa składnia może uniemożliwiać uruchomienia wszystkich aplikacji .NET Framework.  
  
 Istnieje również możliwość szyfrowania przy użyciu interfejsu DPAPI i RSA elementy pliku konfiguracji. Aby uzyskać więcej informacji zobacz następujące linki:  
  
-   [Tworzenie aplikacji ASP.NET bezpiecznego: Uwierzytelniania, autoryzacji i bezpiecznej komunikacji](https://go.microsoft.com/fwlink/?LinkId=95137)  
  
-   [Instrukcje: Szyfrowanie sekcji konfiguracyjnych w programie ASP.NET 2.0 przy użyciu RSA](https://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Edytowanie pliku Machine.config można ustawić `enableLoggingKnownPii` atrybutu `true`, dodając węzły nadrzędne, jeśli to konieczne.  
  
3. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
#### <a name="to-clean-up-the-sample"></a>Aby wyczyścić próbki  
  
1. Edytowanie pliku Machine.config można ustawić `enableLoggingKnownPii` atrybutu `false`.  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady monitorowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
