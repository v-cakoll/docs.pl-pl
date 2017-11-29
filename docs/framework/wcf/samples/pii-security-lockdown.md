---
title: "Blokada zabezpieczeń PII"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
caps.latest.revision: "25"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 93849fc315409b769a06cdd216bbc86e83cf6155
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="pii-security-lockdown"></a>Blokada zabezpieczeń PII
W tym przykładzie pokazano sposób kontrolowania kilka funkcji związanych z zabezpieczeniami programu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] przez:  
  
-   Szyfrowanie poufnych informacji w pliku konfiguracji usługi.  
  
-   Blokowanie elementów w pliku konfiguracji, aby zagnieździć podkatalogów usługi nie może zastąpić ustawienia.  
  
-   Kontrolowanie logowania z osobiście informacji osobowych w dziennikach śledzenia i wiadomości.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Omówienie  
 Każda z tych funkcji może być używane razem lub osobno aspektów kontroli zabezpieczeń usługi. To nie jest wyczerpujący do zabezpieczania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.  
  
 Pliki konfiguracji .NET Framework mogą zawierać poufne informacje, takie jak parametry połączenia z bazami danych. W scenariuszach udostępnionego, hostowanych w sieci Web może być pożądane, aby zaszyfrować te informacje w pliku konfiguracji dla usługi tak, aby dane zawarte w pliku konfiguracji jest odporna na wyświetlanie zwykłych. .NET framework 2.0 lub nowszy ma możliwość szyfrowania części pliku konfiguracji za pomocą programowania interfejsu (DPAPI) lub dostawcy usług kryptograficznych RSA aplikacji ochrony danych systemu Windows. Aspnet_regiis.exe przy użyciu DPAPI lub RSA można zaszyfrować wybierz części pliku konfiguracji.  
  
 W scenariuszach hostowanych w sieci Web jest możliwe usług w podkatalogach innych usług. Domyślne semantycznego określania wartości konfiguracji umożliwia pliki konfiguracyjne w katalogach zagnieżdżone, aby zastąpić wartości konfiguracji w katalogu nadrzędnym. W niektórych sytuacjach może to być niepożądane z różnych przyczyn. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Usługa konfiguracji obsługuje blokowania wartości konfiguracji, dzięki czemu zagnieżdżone konfiguracji generuje wyjątki, gdy jest uruchamiana usługa zagnieżdżonych przy użyciu przesłonięcia wartości konfiguracji.  
  
 W tym przykładzie pokazano, jak sterujące rejestrowaniem z znane osobiście informacji osobowych w dziennikach śledzenia i wiadomości, takie jak nazwa użytkownika i hasło. Domyślnie rejestrowanie znanych danych jest wyłączona, jednak w niektórych sytuacjach może być ważne dla debugowania aplikacji rejestrowanie danych osobowych. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Ponadto w tym przykładzie użyto śledzenie i rejestrowanie komunikatów. Aby uzyskać więcej informacji, zobacz [śledzenie i rejestrowanie komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) próbki.  
  
## <a name="encrypting-configuration-file-elements"></a>Elementy konfiguracji szyfrowania w pliku  
 Ze względów bezpieczeństwa w udostępnionym środowisku hostingu sieci Web może być pożądane, aby zaszyfrować niektórych elementów konfiguracji, takich jak parametry połączenia bazy danych, które mogą zawierać poufne informacje. Element konfiguracji może być szyfrowana przy użyciu narzędzia aspnet_regiis.exe w folderze na przykład % WINDIR%\Micrsoft.NET\Framework\v4.0.20728 .NET Framework.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>Aby zaszyfrować wartości w sekcji appSettings w pliku Web.config dla próbki  
  
1.  Otwórz wiersz polecenia przy użyciu Start -> Uruchom... Wpisz w `cmd` i kliknij przycisk **OK**.  
  
2.  Przejdź do bieżącego katalogu .NET Framework, wydając polecenie: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.  
  
3.  Szyfrowanie ustawienia konfiguracji appSettings w pliku Web.config folderu wydając polecenie: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.  
  
 Przeczytaj instrukcje na interfejsie DPAPI w konfiguracji platformy ASP.NET można znaleźć więcej informacji na temat szyfrowania plików konfiguracji ([tworzenie zabezpieczanie aplikacji ASP.NET: uwierzytelnianie, autoryzację i bezpieczna komunikacja](http://go.microsoft.com/fwlink/?LinkId=95137)) i opisy na RSA w konfiguracji platformy ASP.NET ([jak: szyfrowanie sekcji konfiguracyjnych w programie ASP.NET 2.0 przy użyciu RSA](http://go.microsoft.com/fwlink/?LinkId=95138)).  
  
## <a name="locking-configuration-file-elements"></a>Blokowanie elementów pliku konfiguracji  
 W scenariuszach hostowanych w sieci Web prawdopodobnie zostały usługi podkatalogi usług. W takich przypadkach wartości konfiguracji dla usługi w podkatalogu mają być obliczane, sprawdzając wartości w pliku Machine.config i kolejno scalanie z żadnych plików Web.config w katalogach nadrzędnych przeniesienie w dół drzewa katalogów i na koniec scalania Plik Web.config w katalogu, który zawiera tę usługę. Domyślne zachowanie dla większości elementów konfiguracji jest umożliwienie pliki konfiguracyjne w podkatalogach, aby zastąpić wartości w katalogach nadrzędnych. W niektórych sytuacjach może być pożądane, aby zapobiec pliki konfiguracyjne w podkatalogach zastępowanie wartości w konfiguracji katalogu nadrzędnego.  
  
 .NET Framework zapewnia sposób blokowania elementy pliku konfiguracji, tak aby konfiguracje, które zastępują elementy konfiguracji zablokowanym zgłaszają wyjątki czasu wykonywania.  
  
 Element konfiguracji można zablokować, określając `lockItem` atrybutu dla węzła w pliku konfiguracji, na przykład w celu blokowania węzła CalculatorServiceBehavior w pliku konfiguracji, tak aby usługi Kalkulator w zagnieżdżone pliki konfiguracji nie zmiany zachowania następującej konfiguracji można użyć.  
  
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
  
 Blokowanie elementów konfiguracji mogą być bardziej szczegółowych. Lista elementów może być określona jako wartość `lockElements` zablokować zestaw elementów w kolekcji elementów podrzędnych. Lista atrybutów, można określić jako wartość `lockAttributes` zablokować zestaw atrybutów w obrębie elementu. Z wyjątkiem określonej listy można zablokować cały zbiór elementów lub atrybutów, określając `lockAllElementsExcept` lub `lockAllAttributesExcept` atrybutów w węźle.  
  
## <a name="pii-logging-configuration"></a>Konfiguracja rejestrowania danych osobowych  
 Rejestrowanie danych osobowych jest kontrolowany przez dwa przełączniki: ustawienie komputera znaleziono w pliku Machine.config, umożliwiający administratora komputera zezwolić lub odmówić rejestrowanie danych osobowych i ustawienie aplikacji, który umożliwia administratorowi aplikacji Włącz rejestrowanie danych osobowych dla każdego Źródło w pliku Web.config lub App.config.  
  
 Ustawienia komputera jest kontrolowany przez ustawienie `enableLoggingKnownPii` do `true` lub `false`w `machineSettings` elementu w pliku Machine.config. Na przykład poniżej umożliwia aplikacji włączyć rejestrowanie danych osobowych.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  Plik Machine.config ma domyślnej lokalizacji: % WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 Jeśli `enableLoggingKnownPii` atrybut nie jest obecny w pliku Machine.config, rejestrowanie danych osobowych jest niedozwolone.  
  
 Włączanie rejestrowania danych osobowych dla aplikacji odbywa się przez ustawienie `logKnownPii` atrybut elementu źródłowego do `true` lub `false` w pliku Web.config lub App.config. Na przykład poniżej umożliwia rejestrowanie danych osobowych dotyczących rejestrowania komunikatów, jak i rejestrowania śledzenia.  
  
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
  
 Dane osobowe jest rejestrowane tylko, jeśli obie `enableLoggingKnownPii` ustawiono `true`, i `logKnownPii` ma ustawioną wartość `true`.  
  
> [!NOTE]
>  System.Diagnostics ignoruje wszystkie atrybuty wszystkich źródeł z wyjątkiem pierwszej wymienione w pliku konfiguracji. Dodawanie `logKnownPii` atrybut do drugiego źródła w pliku konfiguracji nie ma znaczenia.  
  
> [!IMPORTANT]
>  Aby uruchomić ten przykład obejmuje zmodyfikowania pliku Machine.config. Należy zachować ostrożność podczas modyfikacji pliku Machine.config lub niepoprawne wartości składni spowodować, że wszystkie działania aplikacji .NET Framework.  
  
 Istnieje również możliwość szyfrowania przy użyciu DPAPI i RSA elementy pliku konfiguracji. Aby uzyskać więcej informacji zobacz następujące linki:  
  
-   [Tworzenie aplikacji ASP.NET bezpiecznego: Uwierzytelniania, autoryzacji i zapewnienia bezpiecznej komunikacji](http://go.microsoft.com/fwlink/?LinkId=95137)  
  
-   [Porady: Szyfrowanie sekcji konfiguracyjnych w programie ASP.NET 2.0 przy użyciu RSA](http://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Edytuj Machine.config, aby ustawić `enableLoggingKnownPii` atrybutu `true`, dodawanie węzłów nadrzędnych, jeśli to konieczne.  
  
3.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
#### <a name="to-clean-up-the-sample"></a>Aby wyczyścić próbki  
  
1.  Edytuj Machine.config, aby ustawić `enableLoggingKnownPii` atrybutu `false`.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
