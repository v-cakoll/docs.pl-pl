---
title: Zalecane ustawienia śledzenia i rejestrowania komunikatów
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: fa6dc74a26f6a76591a15c549a892f31a65c521e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779733"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>Zalecane ustawienia śledzenia i rejestrowania komunikatów
W tym temacie opisano zalecane śledzenia i ustawienia rejestrowania komunikatów dla różnych środowisk operacyjnych.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Zalecane ustawienia dla środowiska produkcyjnego  
 W środowisku produkcyjnym, jeśli używasz źródła śledzenia WCF, ustaw `switchValue` na ostrzeżenie. Jeśli używasz WCF `System.ServiceModel` śledzenia źródła, ustaw `switchValue` atrybutu `Warning` i `propagateActivity` atrybutu `true`. Jeśli używasz źródła śledzenia zdefiniowanych przez użytkownika, ustaw `switchValue` atrybutu `Warning, ActivityTracing`. Można to zrobić ręcznie przy użyciu [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Jeśli nie przewidujesz trafień wydajności, możesz ustawić `switchValue` atrybutu `Information` we wszystkich przypadkach opisanych powyżej, która generuje stosunkowo dużej ilości danych śledzenia. W poniższym przykładzie pokazano te zalecanych ustawień.  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Warning"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Warning, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="recommended-settings-for-deployment-or-debugging"></a>Zalecane ustawienia wdrażania i debugowania  
 Dla wdrożenia lub w środowisku debugowania wybierz `Information` lub `Verbose`, wraz z `ActivityTracing` dla obu zdefiniowanej przez użytkownika lub `System.ServiceModel` źródła śledzenia. Aby zwiększyć możliwości debugowania, należy również dodać dodatkowe źródła (`System.ServiceModel.MessageLogging`) do konfiguracji, aby włączyć rejestrowanie komunikatów. Należy zauważyć, że `switchValue` atrybut nie ma wpływu na tego źródła śledzenia.  
  
 W poniższym przykładzie pokazano zalecane ustawienia, za pomocą udostępnionego odbiornik, który korzysta z `XmlWriterTraceListener`.  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Information, ActivityTracing"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="System.ServiceModel.MessageLogging">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Information, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
 <system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
      <messageLogging   
           logEntireMessage="true"   
           logMalformedMessages="true"  
           logMessagesAtServiceLevel="true"   
           logMessagesAtTransportLevel="true"  
           maxMessagesToLog="3000"   
       />  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-wmi-to-modify-settings"></a>Aby zmodyfikować ustawienia przy użyciu usługi WMI  
 WMI umożliwia zmianę ustawień konfiguracji w czasie wykonywania (włączając `wmiProviderEnabled` atrybut w konfiguracji, jak pokazano w wcześniej przykładzie konfiguracji). Na przykład można użyć WMI CIM Studio, można zmienić poziomu źródła śledzenia z ostrzegawczego do informacji w czasie wykonywania. Należy pamiętać, że spadek wydajności debugowania na żywo w ten sposób mogą być bardzo duże. Aby uzyskać więcej informacji na temat przy użyciu usługi WMI, zobacz [przy użyciu Instrumentacji zarządzania Windows Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) tematu.  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>Włącz zdarzenia skorelowane w śledzenie na platformie ASP.NET  
 Zdarzenia programu ASP.NET nie należy ustawiać identyfikator korelacji (identyfikator), o ile nie jest włączone śledzenie zdarzeń programu ASP.NET. Aby wyświetlić zdarzenia skorelowane prawidłowo, należy włączyć na zdarzenia ASP.NET śledzenia, używając następującego polecenia w konsoli poleceń, który może być wywołana przechodząc do **Start**, **Uruchom** i typ **cmd** ,  
  
```  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 Aby wyłączyć śledzenie zdarzeń programu ASP.NET, użyj następującego polecenia,  
  
```  
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Zobacz także

- [Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
