---
title: Dostawca WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: a170a20212791d789af589c1ff99dcd1abad1c9e
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094777"
---
# <a name="wmi-provider"></a>Dostawca WMI
Ten przykład pokazuje, jak zbierać dane z usług Windows Communication Foundation (WCF) w środowisku uruchomieniowym przy użyciu dostawcy Instrumentacja zarządzania Windows (WMI) wbudowanego w funkcję WCF. Ponadto w tym przykładzie pokazano, jak dodać obiekt usługi WMI zdefiniowany przez użytkownika do usługi. Przykład aktywuje dostawcę WMI dla [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i pokazuje, jak zbierać dane z usługi `ICalculator` w czasie wykonywania.  
  
 Usługa WMI to implementacja standardu opartego na sieci Web (WBEM) firmy Microsoft. Aby uzyskać więcej informacji na temat zestawu WMI SDK, zobacz [Instrumentacja zarządzania Windows](/windows/desktop/WmiSdk/wmi-start-page). WBEM to standardowy branża, w której aplikacje uwidaczniają Instrumentację zarządzania w zewnętrznych narzędziach do zarządzania.  
  
 Funkcja WCF implementuje dostawcę WMI, składnik, który udostępnia instrumentację w czasie wykonywania za pomocą interfejsu zgodnego z pakietem WBEM. Narzędzia do zarządzania programu mogą łączyć się z usługami za pomocą interfejsu w czasie wykonywania. Funkcja WCF udostępnia atrybuty usług, takie jak adresy, powiązania, zachowania i odbiorniki.  
  
 Wbudowany Dostawca usługi WMI jest aktywowany w pliku konfiguracji aplikacji. Odbywa się to za pomocą atrybutu `wmiProviderEnabled` [diagnostyki\<>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) w sekcji [\<system. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , jak pokazano w poniższej konfiguracji przykładowej:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Ten wpis konfiguracji uwidacznia interfejs WMI. Aplikacje zarządzania mogą teraz łączyć się za pomocą tego interfejsu i uzyskiwać dostęp do Instrumentacji zarządzania aplikacji.  
  
## <a name="custom-wmi-object"></a>Niestandardowy obiekt WMI  
 Dodanie obiektów usługi WMI do usługi umożliwia ujawnienie informacji zdefiniowanych przez użytkownika oraz wbudowanych informacji o dostawcach WMI. Jest to realizowane przez opublikowanie schematu usługi w usłudze WMI przy użyciu aplikacji Installutil. exe. Instrukcje do osiągnięcia tego, a także więcej szczegółów można znaleźć w instrukcjach instalacji na końcu tematu.  
  
## <a name="accessing-wmi-information"></a>Uzyskiwanie dostępu do informacji WMI  

Dostęp do danych usługi WMI można uzyskać na wiele różnych sposobów. Firma Microsoft udostępnia interfejsy API usługi WMI dla skryptów, C++ aplikacji Visual Basic, aplikacji i .NET Framework. Aby uzyskać więcej informacji, zobacz [Korzystanie z usługi WMI](/windows/desktop/wmisdk/using-wmi).
  
 W tym przykładzie zastosowano dwa skrypty Java: jeden do wyliczania usług działających na komputerze wraz z niektórymi właściwościami, a drugą, aby wyświetlić dane usługi WMI zdefiniowane przez użytkownika. Skrypt otwiera połączenie z dostawcą WMI, analizuje dane i wyświetla zebrane dane.  
  
 Rozpocznij przykład, aby utworzyć uruchomione wystąpienie usługi WCF. Gdy usługa jest uruchomiona, uruchom każdy skrypt Java za pomocą następującego polecenia w wierszu polecenia:  
  
```console  
cscript EnumerateServices.js  
```  
  
 Skrypt uzyskuje dostęp do Instrumentacji zawartej w usłudze i tworzy następujące dane wyjściowe:  
  
```console  
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
  
 Następnie Uruchom drugi skrypt języka Java, aby wyświetlić dane zdefiniowane przez użytkownika usługi WMI:  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 Skrypt uzyskuje dostęp do zdefiniowanej przez użytkownika Instrumentacji zawartej w usługach i tworzy następujące dane wyjściowe:  
  
```console 
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 Dane wyjściowe pokazują, że na komputerze jest uruchomiona jedna usługa. Usługa udostępnia jeden punkt końcowy, który implementuje kontrakt `ICalculator`. Ustawienia zachowania i powiązania, które są implementowane przez punkt końcowy, są wyświetlane jako suma poszczególnych elementów stosu komunikatów.  
  
 Usługa WMI nie jest ograniczona do uwidaczniania Instrumentacji zarządzania infrastruktury WCF. Aplikacja może uwidaczniać własne specyficzne dla domeny elementy danych za pomocą tego samego mechanizmu. Usługa WMI to ujednolicony mechanizm kontroli i kontroli nad usługą sieci Web.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Opublikuj schemat usług w usłudze WMI, uruchamiając InstallUtil. exe (domyślne lokalizacje dla InstallUtil. exe to "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") w pliku Service. dll w katalogu hostingu. Ten krok należy wykonać tylko po wprowadzeniu zmian w pliku. dll usługi.
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > W przypadku zainstalowania programu WCF po zainstalowaniu ASP.NET może być konieczne uruchomienie "% WINDIR% \ Microsoft. Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe "-r-x", aby nadać kontu ASPNET uprawnienie do publikowania obiektów usługi WMI.  
  
5. Dane z przykładu są wyświetlane za pośrednictwem usługi WMI przy użyciu poleceń: `cscript EnumerateServices.js` lub `cscript EnumerateCustomObjects.js`.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Zobacz też

- [Przykłady monitorowania oprogramowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
