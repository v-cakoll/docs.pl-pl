---
title: Blokada zabezpieczeń PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: ad4f4a024b04a028b815faedded58713e001cab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144269"
---
# <a name="pii-security-lockdown"></a>Blokada zabezpieczeń PII
W tym przykładzie pokazano, jak kontrolować kilka funkcji związanych z zabezpieczeniami usługi Windows Communication Foundation (WCF) przez:  
  
- Szyfrowanie poufnych informacji w pliku konfiguracyjnym usługi.  
  
- Blokowanie elementów w pliku konfiguracyjnym, tak aby zagnieżdżone podkatalogi usługi nie mogły zastąpić ustawień.  
  
- Kontrolowanie rejestrowania informacji umożliwiających identyfikację użytkownika w dziennikach śledzenia i wiadomości.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Dyskusji  
 Każda z tych funkcji może być używana oddzielnie lub razem do kontrolowania aspektów zabezpieczeń usługi. Nie jest to ostateczny przewodnik do zabezpieczania usługi WCF.  
  
 Pliki konfiguracyjne programu .NET Framework mogą zawierać poufne informacje, takie jak parametry połączenia umożliwiające łączenie się z bazami danych. W scenariuszach udostępnionych hostowanych w sieci Web może być pożądane zaszyfrowanie tych informacji w pliku konfiguracyjnym dla usługi, tak aby dane zawarte w pliku konfiguracyjnym były odporne na zwykłe wyświetlanie. Program .NET Framework 2.0 i nowsze elementy mają możliwość szyfrowania części pliku konfiguracyjnego przy użyciu interfejsu programowania aplikacji ochrony danych systemu Windows (DPAPI) lub dostawcy kryptograficznego RSA. Program aspnet_regiis.exe korzystający z dpapi lub rsa może szyfrować wybrane części pliku konfiguracyjnego.  
  
 W scenariuszach hostowanych w sieci Web można mieć usługi w podkatalogach innych usług. Domyślna semantyczna do określania wartości konfiguracji umożliwia plikom konfiguracyjnym w katalogach zagnieżdżonych zastępowanie wartości konfiguracji w katalogu nadrzędnym. W niektórych sytuacjach może to być niepożądane z różnych powodów. Konfiguracja usługi WCF obsługuje blokowanie wartości konfiguracji, dzięki czemu zagnieżdżona konfiguracja generuje wyjątki, gdy usługa zagnieżdżona jest uruchamiana przy użyciu zastąpionych wartości konfiguracji.  
  
 W tym przykładzie pokazano, jak kontrolować rejestrowanie znanych informacji umożliwiających identyfikację użytkownika w dziennikach śledzenia i wiadomości, takich jak nazwa użytkownika i hasło. Domyślnie rejestrowanie znanych identyfikatorów umożliwiających identyfikację jest wyłączone, jednak w niektórych sytuacjach rejestrowanie danych umożliwiających identyfikację może być ważne podczas debugowania aplikacji. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Ponadto w tym przykładzie używa śledzenia i rejestrowania wiadomości. Aby uzyskać więcej informacji, zobacz [śledzenie i rejestrowanie wiadomości](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) próbki.  
  
## <a name="encrypting-configuration-file-elements"></a>Szyfrowanie elementów plików konfiguracji  
 Ze względów bezpieczeństwa w środowisku hostingu sieci Web udostępnionego hostingu sieci Web może być pożądane szyfrowanie niektórych elementów konfiguracji, takich jak parametry połączenia bazy danych, które mogą zawierać poufne informacje. Element konfiguracji może być szyfrowany przy użyciu narzędzia aspnet_regiis.exe znajdującego się w folderze .NET Framework Na przykład %WINDIR%\Microsoft.NET\Framework\v4.0.20728.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>Aby zaszyfrować wartości w sekcji appSettings w witrynie Web.config dla przykładu  
  
1. Otwórz wiersz polecenia przy użyciu polecenia Start->Run.... Wpisz `cmd` i kliknij przycisk **OK**.  
  
2. Przejdź do bieżącego katalogu programu .NET Framework, `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`wydając następujące polecenie: .  
  
3. Zaszyfruj ustawienia konfiguracji appSettings w folderze Web.config, wydając następujące polecenie: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.  
  
 Więcej informacji na temat szyfrowania sekcji plików konfiguracyjnych można znaleźć, czytając instrukcje dotyczące DPAPI w ASP.NET konfiguracji[(Tworzenie bezpiecznych aplikacji ASP.NET: Uwierzytelnianie, autoryzacja i bezpieczna komunikacja)](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))oraz instrukcje dotyczące rsa w konfiguracji ASP.NET[(How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))).  
  
## <a name="locking-configuration-file-elements"></a>Blokowanie elementów pliku konfiguracyjnego  
 W scenariuszach hostowanych w sieci Web jest możliwe, aby mieć usługi w podkatalogach usług. W takich sytuacjach wartości konfiguracyjne usługi w podkatalogu są obliczane przez badanie wartości w pliku Machine.config i sukcesywne scalanie z dowolnymi plikami Web.config w katalogach nadrzędnych przechodzących w dół drzewa katalogów i wreszcie scalających Web.config w katalogu zawierającym usługę. Domyślnym zachowaniem większości elementów konfiguracji jest zezwolenie na zastąpienie wartości ustawionych w katalogach nadrzędnych przez pliki konfiguracyjne w podkatalogach. W niektórych sytuacjach może być pożądane uniemożliwienie plików konfiguracyjnych w podkatalogach zastępowania wartości ustawionych w konfiguracji katalogu nadrzędnego.  
  
 .NET Framework umożliwia zablokowanie elementów pliku konfiguracji, dzięki czemu konfiguracje, które zastępują zablokowane elementy konfiguracji, zgłaszają wyjątki czasu wykonywania.  
  
 Element konfiguracji można zablokować, określając `lockItem` atrybut węzła w pliku konfiguracyjnym, na przykład, aby zablokować węzeł CalculatorServiceBehavior w pliku konfiguracyjnym, tak aby usługi kalkulatora w zagnieżdżonych plikach konfiguracyjnych nie mogły zmienić zachowania, można użyć następującej konfiguracji.  
  
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
  
 Blokowanie elementów konfiguracyjnych może być bardziej szczegółowe. Listę elementów można określić jako `lockElements` wartość, aby zablokować zestaw elementów w kolekcji podelementów. Listę atrybutów można określić jako `lockAttributes` wartość, aby zablokować zestaw atrybutów w elemencie. Cała kolekcja elementów lub atrybutów może być zablokowana z `lockAllElementsExcept` `lockAllAttributesExcept` wyjątkiem określonej listy, określając atrybuty lub w węźle.  
  
## <a name="pii-logging-configuration"></a>Konfiguracja rejestrowania pii  
 Rejestrowanie danych umożliwiających identyfikację użytkownika jest kontrolowane przez dwa przełączniki: ustawienie dla całego komputera w pliku Machine.config, które umożliwia administratorowi komputera zezwalanie lub odmawianie rejestrowania danych umożliwiających identyfikację użytkownika oraz ustawienie aplikacji, które umożliwia administratorowi aplikacji przełączanie rejestrowania danych umożliwiających identyfikację użytkownika dla każdego źródła w pliku Web.config lub App.config.  
  
 Ustawienie dla całego komputera jest `enableLoggingKnownPii` `true` kontrolowane `false`przez `machineSettings` ustawienie lub , w elemencie w Machine.config. Na przykład następujące umożliwia aplikacjom włączyć rejestrowanie identyfikatorów PII.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> Plik Machine.config ma domyślną lokalizację: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 Jeśli `enableLoggingKnownPii` atrybut nie jest obecny w Machine.config, rejestrowanie identyfikatorów PII jest niedozwolone.  
  
 Włączenie rejestrowania danych umożliwiających identyfikację użytkownika `logKnownPii` dla aplikacji odbywa się `true` `false` przez ustawienie atrybutu elementu źródłowego na lub w pliku Web.config lub App.config. Na przykład następujące umożliwia rejestrowanie identyfikatorów umożliwiających identyfikację podczas rejestrowania wiadomości i rejestrowania śledzenia.  
  
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
  
 Jeśli `logKnownPii` atrybut nie jest określony, informacje umożliwiające identyfikację nie są rejestrowane.  
  
 Dane umożliwiające identyfikację `enableLoggingKnownPii` jest rejestrowane `true`tylko `logKnownPii` wtedy, `true`gdy oba są ustawione na , i jest ustawiona na .  
  
> [!NOTE]
> System.Diagnostics ignoruje wszystkie atrybuty we wszystkich źródłach z wyjątkiem pierwszego wymienionego w pliku konfiguracyjnym. Dodanie `logKnownPii` atrybutu do drugiego źródła w pliku konfiguracyjnym nie ma wpływu.  
  
> [!IMPORTANT]
> Aby uruchomić ten przykład obejmuje ręczną modyfikację Machine.config. Należy zwrócić uwagę podczas modyfikowania Machine.config jako niepoprawne wartości lub składni może uniemożliwić wszystkie aplikacje .NET Framework z systemem.  
  
 Możliwe jest również szyfrowanie elementów pliku konfiguracji przy użyciu DPAPI i RSA. Aby uzyskać więcej informacji, skorzystaj z następujących linków:  
  
- [Tworzenie bezpiecznych aplikacji ASP.NET: uwierzytelnianie, autoryzacja i bezpieczna komunikacja](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))  
  
- [Jak: Szyfrowanie sekcji konfiguracji w ASP.NET 2.0 Przy użyciu rsa](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Edytuj plik Machine.config, `enableLoggingKnownPii` aby `true`ustawić atrybut , dodając węzły nadrzędne, jeśli to konieczne.  
  
3. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
#### <a name="to-clean-up-the-sample"></a>Aby wyczyścić próbkę  
  
1. Edytuj plik Machine.config, `enableLoggingKnownPii` aby `false`ustawić atrybut na .  
  
## <a name="see-also"></a>Zobacz też

- [Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
