---
title: Dostawca WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 04fdbb7efcae6fdbb78f467352e6106ac5218799
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183190"
---
# <a name="wmi-provider"></a>Dostawca WMI
W tym przykładzie pokazano, jak zbierać dane z usług Windows Communication Foundation (WCF) w czasie wykonywania przy użyciu dostawcy instrumentacji zarządzania windows (WMI), który jest wbudowany w WCF. Ponadto w tym przykładzie pokazano, jak dodać obiekt WMI zdefiniowane przez użytkownika do usługi. Przykład aktywuje dostawcę usługi WMI dla [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i pokazuje, `ICalculator` jak zbierać dane z usługi w czasie wykonywania.  
  
 WMI jest wdrożenie microsoftu web-based Enterprise Management (WBEM) standard. Aby uzyskać więcej informacji na temat zestawie WMI SDK, zobacz [Instrumentacja zarządzania windowsem](/windows/desktop/WmiSdk/wmi-start-page). WBEM jest standardem branżowym w zakresie sposobu, w jaki aplikacje narażają instrumentację zarządzania na zewnętrzne narzędzia do zarządzania.  
  
 WCF implementuje dostawcę WMI, składnik, który udostępnia instrumentacji w czasie wykonywania za pośrednictwem interfejsu zgodnego z WBEM. Narzędzia do zarządzania można połączyć się z usługami za pośrednictwem interfejsu w czasie wykonywania. WCF udostępnia atrybuty usług, takich jak adresy, powiązania, zachowania i detektory.  
  
 Wbudowany dostawca WMI jest aktywowany w pliku konfiguracyjnym aplikacji. Odbywa się to `wmiProviderEnabled` za pomocą atrybutu [ \<diagnostyki>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) w sekcji [ \<system.serviceModel>,](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) jak pokazano w poniższej konfiguracji przykładowej:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Ten wpis konfiguracji udostępnia interfejs WMI. Aplikacje do zarządzania mogą teraz łączyć się za pośrednictwem tego interfejsu i uzyskiwać dostęp do instrumentacji zarządzania aplikacji.  
  
## <a name="custom-wmi-object"></a>Niestandardowy obiekt WMI  
 Dodanie obiektów WMI do usługi umożliwia ujawnienie informacji zdefiniowanych przez użytkownika wraz z wbudowanymi informacjami o dostawcy WMI. Jest to realizowane przez opublikowanie schematu usługi do usługi WMI przy użyciu aplikacji Installutil.exe. Instrukcje, aby to osiągnąć, wraz z więcej szczegółów można znaleźć w instrukcji konfiguracji na końcu tematu.  
  
## <a name="accessing-wmi-information"></a>Uzyskiwanie dostępu do informacji w u obiektu WMI  

Dostęp do danych usługi WMI można uzyskać na wiele różnych sposobów. Firma Microsoft udostępnia interfejsy API usługi WMI dla skryptów, aplikacji Visual Basic, aplikacji W++ i programu .NET Framework. Aby uzyskać więcej informacji, zobacz [Korzystanie z usługi WMI](/windows/desktop/wmisdk/using-wmi).
  
 W tym przykładzie użyto dwóch skryptów Java: jednego do wyliczenia usług uruchomionych na komputerze wraz z niektórymi ich właściwościami, a drugi do wyświetlania zdefiniowanych przez użytkownika danych WMI. Skrypt otwiera połączenie z dostawcą usługi WMI, analizuje dane i wyświetla zebrane dane.  
  
 Uruchom próbkę, aby utworzyć uruchomione wystąpienie usługi WCF. Gdy usługa jest uruchomiona, uruchom każdy skrypt Java przy użyciu następującego polecenia w wierszu polecenia:  
  
```console  
cscript EnumerateServices.js  
```  
  
 Skrypt uzyskuje dostęp do instrumentacji zawartej w usłudze i generuje następujące dane wyjściowe:  
  
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
  
 Następnie uruchom drugi skrypt Java, aby wyświetlić zdefiniowane przez użytkownika dane WMI:  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 Skrypt uzyskuje dostęp do instrumentacji zdefiniowanej przez użytkownika zawartej w usługach i generuje następujące dane wyjściowe:  
  
```console
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 Dane wyjściowe pokazują, że na komputerze jest uruchomiona jedna usługa. Usługa udostępnia jeden punkt końcowy, `ICalculator` który implementuje umowy. Ustawienia zachowania i powiązania, które są implementowane przez punkt końcowy są wymienione jako suma poszczególnych elementów stosu obsługi wiadomości.  
  
 WMI nie ogranicza się do narażania instrumentacji zarządzania infrastruktury WCF. Aplikacja może udostępniać własne elementy danych specyficzne dla domeny za pośrednictwem tego samego mechanizmu. Usługa WMI to ujednolicony mechanizm inspekcji i kontroli usługi sieci Web.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Opublikuj schemat usług w UMI, uruchamiając plik InstallUtil.exe (domyślne lokalizacje installUtil.exe to "%WINDIR%\Microsoft.NET\Framework\v4.30319") w pliku service.dll w katalogu hostingu. Ten krok musi być wykonywany tylko po wprowadzeniu zmian w pliku service.dll.
  
4. Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Jeśli po zainstalowaniu WCF po zainstalowaniu ASP.NET, może być konieczne uruchomienie "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x, aby nadać kontu ASPNET uprawnienia do publikowania obiektów WMI.  
  
5. Wyświetlanie danych z próbki na powierzchni za pomocą `cscript EnumerateServices.js` usługi `cscript EnumerateCustomObjects.js`WMI za pomocą poleceń: lub .  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Zobacz też

- [Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
