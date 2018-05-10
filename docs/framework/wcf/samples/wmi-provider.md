---
title: Dostawca WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: d135466c402fa21b6a1b11f208ca900f58748bdb
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="wmi-provider"></a>Dostawca WMI
W tym przykładzie pokazano, jak można zebrać danych z usługi Windows Communication Foundation (WCF) w czasie wykonywania za pomocą dostawcy Instrumentacji zarządzania Windows (WMI), który jest wbudowany w usługi WCF. Ponadto w przykładzie pokazano sposób dodawania obiektu WMI zdefiniowane przez użytkownika do usługi. Przykład aktywuje dostawcy WMI o [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i pokazuje, jak zbierać dane z `ICalculator` usługi w czasie wykonywania.  
  
 Usługa WMI stanowi implementację firmy Microsoft w sieci Web-Based Enterprise Management (WBEM) standardowa. Aby uzyskać więcej informacji o zestawie SDK usługi WMI, zobacz [Instrumentacji zarządzania Windows](https://msdn.microsoft.com/library/aa394582.aspx). Technologia WBEM jest branżowy standard jak aplikacje ujawnia Instrumentacji zarządzania do narzędzia do zarządzania zewnętrznego.  
  
 Usługi WCF implementuje dostawcę WMI składnik, który ujawnia Instrumentacji w czasie wykonywania za pośrednictwem interfejsu zgodnego WBEM. Narzędzia do zarządzania mogą łączyć się usługi za pomocą interfejsu w czasie wykonywania. Usługa WCF umożliwia atrybuty usług, takich jak adresy, powiązania zachowania i odbiorników.  
  
 Wbudowane dostawcy WMI jest aktywowana w pliku konfiguracji aplikacji. Jest to zrobić za pomocą `wmiProviderEnabled` atrybutu [ \<diagnostyki >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) w [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) sekcji, jak pokazano w następującym przykładowym Konfiguracja:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Ten wpis konfiguracji uwidacznia interfejs WMI. Aplikacje do zarządzania można teraz łączenie się za pośrednictwem tego interfejsu i uzyskać dostęp z Instrumentacją zarządzania aplikacji.  
  
## <a name="custom-wmi-object"></a>Obiekt WMI niestandardowych  
 Dodawanie obiektów WMI z usługą umożliwia ujawnić informacje zdefiniowane przez użytkownika wraz z wbudowanych informacji o dostawcy WMI. Jest to osiągane przez publikowanie schemat usługi WMI za pomocą aplikacji Installutil.exe. Instrukcje w tym celu, wraz z bardziej szczegółowe informacje można znaleźć w instrukcjach instalacji na końcu tego tematu.  
  
## <a name="accessing-wmi-information"></a>Uzyskiwanie dostępu do informacji usługi WMI  
 Dane usługi WMI są dostępne wiele różnych sposobów. Firma Microsoft udostępnia interfejsy API usługi WMI dla skryptów aplikacji Visual Basic, aplikacji C++ i [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).  
  
 W przykładzie użyto dwóch skryptów Java: jeden wyliczyć usługi uruchomione na komputerze wraz z niektórych właściwości i drugiego do wyświetlania danych usługi WMI zdefiniowane przez użytkownika. Skrypt otwiera połączenie z dostawcą WMI, analizuje dane i wyświetla zbieranych danych.  
  
 Uruchom przykład, aby utworzyć działającego wystąpienia usługi WCF. Gdy usługa jest uruchomiona, uruchom każdego skryptu języka Java przy użyciu następującego polecenia w wierszu polecenia:  
  
```  
cscript EnumerateServices.js  
```  
  
 Skrypt uzyskuje dostęp do zawartych w usłudze Instrumentacja i następujących danych wyjściowych:  
  
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
  
 Następnie uruchom skrypt Java drugi do wyświetlania danych usługi WMI zdefiniowane przez użytkownika:  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 Skrypt uzyskuje dostęp do zawartych w usługach Instrumentacja zdefiniowane przez użytkownika i następujących danych wyjściowych:  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 Dane wyjściowe wskazuje, że istnieje pojedynczą usługę uruchomionej na komputerze. Usługa udostępnia jeden punkt końcowy, który implementuje `ICalculator` kontraktu. Ustawienia zachowania i powiązania, które są implementowane przez punkt końcowy są wyświetlane jako sumę poszczególne elementy stosem obsługi wiadomości.  
  
 Usługa WMI nie jest ograniczone do udostępnianie Instrumentacji zarządzania infrastrukturą usługi WCF. Aplikacja może narazić elementy dane specyficzne dla domeny przez ten sam mechanizm. Usługa WMI stanowi mechanizm ujednoliconego inspekcji i kontroli usługi sieci Web.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, można zlecić [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Opublikuj schemat usługi WMI, uruchamiając InstallUtil.exe (domyślne lokalizacje InstallUtil.exe jest "% WINDIR%\Microsoft.NET\Framework\v4.0.30319") w pliku service.dll w katalogu macierzystego. Ten krok tylko musi być wykonywana w przypadku zmiany zostały wprowadzone w pliku service.dll. Aby uzyskać więcej informacji, zobacz dostarczanie informacji dotyczących zarządzania przez aplikacje Instrumentacji w: http://msdn2.microsoft.com/library/ms186147.aspx w sekcji "Jak do: publikowanie schematu do usługi WMI dla Instrumentacji aplikacji".  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Jeśli WCF jest zainstalowany po zainstalowaniu programu ASP.NET, może być konieczne uruchomienie "%WINDIR%\ Foundation\servicemodelreg.exe komunikacji Microsoft.Net\Framework\v3.0\Windows "- r - x, aby udzielić ASPNET uprawnienia konta do publikowania obiektów WMI.  
  
5.  Wyświetl dane przykładowe udostępniane za pośrednictwem usługi WMI za pomocą poleceń: `cscript EnumerateServices.js` lub `cscript EnumerateCustomObjects.js`.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
