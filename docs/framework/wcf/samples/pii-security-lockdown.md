---
title: Blokada zabezpieczeń PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: f82d3f19a3bf6fc6a5ac038034880dafc03fcce1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044798"
---
# <a name="pii-security-lockdown"></a>Blokada zabezpieczeń PII
Ten przykład pokazuje, jak kontrolować kilka funkcji związanych z zabezpieczeniami usługi Windows Communication Foundation (WCF) przez:  
  
- Szyfrowanie poufnych informacji w pliku konfiguracji usługi.  
  
- Blokowanie elementów w pliku konfiguracji, aby zagnieżdżone podkatalogi usługi nie można zastąpić ustawień.  
  
- Kontrolowanie rejestrowania danych osobowych (dane osobowe) w dziennikach śledzenia i komunikatów.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Dyskusji  
 Każda z tych funkcji może być używana osobno lub razem w celu kontrolowania aspektów zabezpieczeń usługi. Nie jest to ostateczny Przewodnik dotyczący zabezpieczania usługi WCF.  
  
 Pliki konfiguracji .NET Framework mogą zawierać informacje poufne, takie jak parametry połączenia do łączenia się z bazami danych. W udostępnionych scenariuszach hostowanych w sieci Web może być pożądane zaszyfrowanie tych informacji w pliku konfiguracji usługi, dzięki czemu dane zawarte w pliku konfiguracyjnym są odporne na wyświetlanie. .NET Framework 2,0 i nowsze mogą szyfrować fragmenty pliku konfiguracji przy użyciu interfejsu programowania aplikacji ochrony danych (DPAPI) systemu Windows lub dostawcy usług kryptograficznych RSA. Narzędzie Aspnet_regiis. exe korzystające z interfejsu DPAPI lub RSA może szyfrować wybrane fragmenty pliku konfiguracji.  
  
 W scenariuszach hostowanych w sieci Web można korzystać z usług w podkatalogach innych usług. Domyślna semantyka do określania wartości konfiguracyjnych zezwala na pliki konfiguracyjne w katalogach zagnieżdżonych w celu zastąpienia wartości konfiguracji w katalogu nadrzędnym. W niektórych sytuacjach może to być niepożądane z różnych powodów. Konfiguracja usługi WCF obsługuje blokowanie wartości konfiguracyjnych, dzięki czemu konfiguracja zagnieżdżona generuje wyjątki, gdy usługa zagnieżdżona jest uruchamiana przy użyciu zastąpionych wartości konfiguracyjnych.  
  
 Ten przykład pokazuje, jak sterować rejestrowaniem znanych danych osobowych użytkownika w dziennikach śledzenia i komunikatów, takich jak nazwa użytkownika i hasło. Domyślnie rejestrowanie znanego elementu dane OSOBowe jest wyłączone, jednak w niektórych sytuacjach rejestrowanie się w charakterze dane OSOBowe może być ważne podczas debugowania aplikacji. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Ponadto ten przykład używa śledzenia i rejestrowania komunikatów. Aby uzyskać więcej informacji, zobacz [śledzenie i rejestrowanie komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) .  
  
## <a name="encrypting-configuration-file-elements"></a>Szyfrowanie elementów pliku konfiguracji  
 Ze względów bezpieczeństwa w udostępnianym środowisku hostingu sieci Web może być pożądane zaszyfrowanie niektórych elementów konfiguracji, takich jak parametry połączenia bazy danych, które mogą zawierać informacje poufne. Element konfiguracji można zaszyfrować za pomocą narzędzia Aspnet_regiis. exe dostępnego w folderze .NET Framework, na przykład%WINDIR%\Microsoft.NET\Framework\v4.0.20728.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>Aby zaszyfrować wartości w sekcji appSettings w pliku Web. config dla przykładu  
  
1. Otwórz wiersz polecenia, korzystając z uruchamiania > Uruchom.... Wpisz, a następnie kliknij przycisk **OK.** `cmd`  
  
2. Przejdź do bieżącego katalogu .NET Framework, wydając następujące polecenie: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.  
  
3. Zaszyfruj ustawienia konfiguracji appSettings w folderze Web. config, wydając następujące polecenie: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.  
  
 Więcej informacji o szyfrowaniu części plików konfiguracji można znaleźć, odczytując instrukcje dotyczące interfejsu DPAPI w konfiguracji ASP.NET ([tworzenie bezpiecznych aplikacji ASP.NET: Uwierzytelnianie, autoryzacja i Bezpieczna komunikacja](https://go.microsoft.com/fwlink/?LinkId=95137)oraz informacje na temat uwierzytelniania RSA w konfiguracji ASP.NET ([instrukcje: Szyfruj sekcje konfiguracyjne w ASP.NET 2,0 przy](https://go.microsoft.com/fwlink/?LinkId=95138)użyciu RSA).  
  
## <a name="locking-configuration-file-elements"></a>Blokowanie elementów pliku konfiguracji  
 W scenariuszach hostowanych w sieci Web możliwe jest posiadanie usług w podkatalogach usług. W takich sytuacjach wartości konfiguracyjne usługi w podkatalogu są obliczane przez badanie wartości w pliku Machine. config i ponowne scalanie z dowolnym plikami Web. config w katalogach nadrzędnych, przenosząc drzewo katalogów i wreszcie scalając Plik Web. config w katalogu zawierającym usługę. Domyślne zachowanie większości elementów konfiguracji polega na umożliwieniu plików konfiguracji w podkatalogach w celu zastąpienia wartości ustawionych w katalogach nadrzędnych. W niektórych sytuacjach może być wskazane, aby zapobiec zastępowaniu plików konfiguracji w podkatalogach przed zastępowaniem wartości ustawionych w konfiguracji katalogu nadrzędnego.  
  
 .NET Framework umożliwia zablokowanie elementów pliku konfiguracji, aby konfiguracje, które przesłaniają zablokowane elementy konfiguracji, zgłaszają wyjątki w czasie wykonywania.  
  
 Element konfiguracji można zablokować przez określenie `lockItem` atrybutu dla węzła w pliku konfiguracji, na przykład, aby zablokować węzeł CalculatorServiceBehavior w pliku konfiguracji, tak aby usługi kalkulatora w zagnieżdżonych plikach konfiguracji nie można zmienić zachowania, można użyć poniższej konfiguracji.  
  
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
  
 Blokowanie elementów konfiguracji może być bardziej szczegółowe. Lista elementów może być określona jako wartość `lockElements` w celu zablokowania zestawu elementów w kolekcji elementów podrzędnych. Listę atrybutów można określić jako wartość `lockAttributes` w celu zablokowania zestawu atrybutów w obrębie elementu. Cała kolekcja elementów lub atrybutów można zablokować z wyjątkiem określonej listy przez określenie `lockAllElementsExcept` atrybutów lub `lockAllAttributesExcept` w węźle.  
  
## <a name="pii-logging-configuration"></a>Konfiguracja rejestrowania dane OSOBowe  
 Rejestrowanie dane OSOBowe są kontrolowane przez dwa przełączniki: ustawienie na poziomie całego komputera w pliku Machine. config pozwala administratorowi komputera zezwolić na logowanie się lub odmówić rejestrowania dane OSOBowe oraz ustawienia aplikacji, które umożliwiają administratorowi aplikacji przełączanie rejestrowania elementów osobowych dla każdej z nich Źródło w pliku Web. config lub App. config.  
  
 Ustawienie na poziomie całego komputera jest kontrolowane przez ustawienie `enableLoggingKnownPii` do `true` lub `false`, w `machineSettings` elemencie pliku Machine. config. Na przykład następujące polecenie umożliwia aplikacjom włączenie rejestrowania danych osobowych.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> Plik Machine. config ma domyślną lokalizację:%WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 `enableLoggingKnownPii` Jeśli atrybut nie jest obecny w pliku Machine. config, rejestrowanie dane osobowe nie jest dozwolone.  
  
 Włączanie rejestrowania danych osobowych dla aplikacji jest wykonywane przez ustawienie `logKnownPii` atrybutu elementu źródłowego na `true` lub `false` w pliku Web. config lub App. config. Na przykład następujące umożliwia rejestrowanie danych osobowych zarówno w przypadku rejestrowania komunikatów, jak i rejestrowania śledzenia.  
  
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
  
 Jeśli atrybut `logKnownPii` nie jest określony, dane osobowe nie są rejestrowane.  
  
 Dane osobowe są rejestrowane tylko `enableLoggingKnownPii` wtedy, gdy `true`oba są `logKnownPii` ustawione na i `true`są ustawione na.  
  
> [!NOTE]
> System. Diagnostics ignoruje wszystkie atrybuty we wszystkich źródłach z wyjątkiem pierwszego z nich wymienionych w pliku konfiguracji. `logKnownPii` Dodanie atrybutu do drugiego źródła w pliku konfiguracji nie ma żadnego skutku.  
  
> [!IMPORTANT]
> Do uruchomienia tego przykładu zawarto ręczną modyfikację pliku Machine. config. Należy zachować ostrożność podczas modyfikowania pliku Machine. config, ponieważ nieprawidłowe wartości lub Składnia mogą uniemożliwić uruchamianie wszystkich aplikacji .NET Framework.  
  
 Istnieje również możliwość szyfrowania elementów plików konfiguracji przy użyciu funkcji DPAPI i RSA. Aby uzyskać więcej informacji, zobacz następujące linki:  
  
- [Tworzenie bezpiecznych aplikacji ASP.NET: Uwierzytelnianie, autoryzacja i Bezpieczna komunikacja](https://go.microsoft.com/fwlink/?LinkId=95137)  
  
- [Instrukcje: Szyfruj sekcje konfiguracyjne w ASP.NET 2,0 przy użyciu RSA](https://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Edytuj plik Machine. config, aby `enableLoggingKnownPii` ustawić atrybut `true`na, dodając węzły nadrzędne w razie potrzeby.  
  
3. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
#### <a name="to-clean-up-the-sample"></a>Aby oczyścić przykład  
  
1. Edytuj plik Machine. config, aby `enableLoggingKnownPii` ustawić atrybut `false`na.  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady monitorowania oprogramowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
