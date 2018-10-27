---
title: Dostawca WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 4541c411d6bd1f13a03a0b6750e6683a7c2b3f3f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194907"
---
# <a name="wmi-provider"></a>Dostawca WMI
W tym przykładzie pokazano, jak zbieranie danych z usługi Windows Communication Foundation (WCF) w czasie wykonywania przy użyciu dostawcy Instrumentacji zarządzania Windows (WMI), która jest wbudowana w usługi WCF. Ponadto w tym przykładzie przedstawiono sposób dodawania obiektu WMI zdefiniowanych przez użytkownika do usługi. Przykładowe aktywuje dostawcy WMI o [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i pokazuje, jak zbierać dane z `ICalculator` usługi w czasie wykonywania.  
  
 WMI jest implementacja firmy Microsoft opartego na sieci Web Enterprise Management (WBEM) standardowa. Aby uzyskać więcej informacji na temat zestawu SDK usługi WMI, zobacz [Instrumentacji zarządzania Windows](/windows/desktop/WmiSdk/wmi-start-page). Technologia WBEM jest branżowy standard jak aplikacje uwidocznić Instrumentacji zarządzania do narzędzi zarządzania zewnętrznego.  
  
 Usługi WCF implementuje dostawcę WMI składnika, który udostępnia Instrumentacji w czasie wykonywania za pomocą interfejsu WBEM zgodne. Narzędzia do zarządzania może nawiązać połączenia usług za pośrednictwem interfejsu w czasie wykonywania. Usługa WCF umożliwia atrybuty usługi, takie jak adresy, powiązania, zachowań i odbiorników.  
  
 Wbudowany dostawca usługi WMI jest ono aktywowane w pliku konfiguracji aplikacji. Jest to realizowane `wmiProviderEnabled` atrybutu [ \<Diagnostyka >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) w [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) sekcji, jak pokazano w następującym przykładzie Konfiguracja:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Ten wpis konfiguracji udostępnia interfejs usługi WMI. Aplikacje do zarządzania można teraz nawiązać połączenie za pośrednictwem tego interfejsu i uzyskać dostęp z Instrumentacją zarządzania aplikacji.  
  
## <a name="custom-wmi-object"></a>Obiektu WMI niestandardowe  
 Dodawanie obiektów WMI do usługi umożliwia do ujawnienia informacji użytkownika wraz z wbudowaną informacji o dostawcy WMI. Jest to realizowane przez opublikowanie schemat usługi WMI za pomocą aplikacji Installutil.exe. Instrukcje, aby to osiągnąć, podając więcej szczegółów można znaleźć w instrukcjach instalacji na końcu tego tematu.  
  
## <a name="accessing-wmi-information"></a>Uzyskiwanie dostępu do informacji usługi WMI  
 Dane usługi WMI są dostępne wiele różnych sposobów. Firma Microsoft udostępnia interfejsy API usługi WMI dla skryptów, aplikacji Visual Basic, aplikacji w języku C++ i [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (https://docs.microsoft.com/windows/desktop/wmisdk/using-wmi).  
  
 W tym przykładzie użyto dwóch skryptów języka Java: jeden wyliczyć usługi uruchomione na komputerze oraz niektóre z ich właściwości, a druga do wyświetlania danych WMI zdefiniowanych przez użytkownika. Skrypt otwiera połączenie z dostawcą WMI, analizuje dane i wyświetla dane zebrane.  
  
 Uruchom przykład, aby utworzyć uruchomionego wystąpienia usługi WCF. Gdy usługa jest uruchomiona, uruchom każdego skryptu języka Java przy użyciu następującego polecenia w wierszu polecenia:  
  
```  
cscript EnumerateServices.js  
```  
  
 Skrypt uzyskuje dostęp do Instrumentacji znajdujących się w usłudze, a także generuje następujące wyniki:  
  
```  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 Następnie uruchom drugi skryptu Java, aby wyświetlić dane WMI zdefiniowanych przez użytkownika:  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 Skrypt uzyskuje dostęp do Instrumentacji zdefiniowanych przez użytkownika, zawartych w usługach i generuje następujące wyniki:  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 Dane wyjściowe pokazują, że istnieje jednej usługi uruchomione na komputerze. Usługa udostępnia jeden punkt końcowy, który implementuje `ICalculator` kontraktu. Ustawienia zachowania i powiązanie, które są implementowane przez punkt końcowy jest wyświetlany tekst sumę poszczególne elementy stosem obsługi wiadomości.  
  
 Usługa WMI nie jest ograniczona do uwidaczniania Instrumentacji zarządzania infrastrukturą usługi WCF. Aplikacja może uwidocznić własne elementy danych specyficznych dla domeny przez ten sam mechanizm. Usługa WMI jest mechanizmem ujednoliconego inspekcji i kontroli usługi sieci Web.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, kiedy została wykonana [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Opublikuj schemat usługi WMI, uruchamiając InstallUtil.exe (domyślne lokalizacje programu InstallUtil.exe jest "% WINDIR%\Microsoft.NET\Framework\v4.0.30319") w pliku service.dll w katalogu macierzystym. Ten krok wymaga tylko do wykonania, gdy wprowadzono zmiany w pliku service.dll.
  
4.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Po zainstalowaniu programu WCF po zainstalowaniu programu ASP.NET, może być konieczne uruchomienie "%WINDIR%\ Foundation\servicemodelreg.exe komunikacji Microsoft.Net\Framework\v3.0\Windows "- r - x, aby udzielić uprawnień konto ASPNET, aby opublikować obiektów WMI.  
  
5.  Wyświetlanie danych z przykładu udostępniane za pośrednictwem usługi WMI za pomocą poleceń: `cscript EnumerateServices.js` lub `cscript EnumerateCustomObjects.js`.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
