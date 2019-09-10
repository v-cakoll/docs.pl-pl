---
title: Zalecane ustawienia śledzenia i rejestrowania komunikatów
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 6e671762edb2d1ca71ce14cb6ef66c64e02bc297
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856086"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>Zalecane ustawienia śledzenia i rejestrowania komunikatów
W tym temacie opisano zalecane ustawienia śledzenia i rejestrowania komunikatów dla różnych środowisk operacyjnych.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Zalecane ustawienia dla środowiska produkcyjnego  
 W przypadku środowiska produkcyjnego, jeśli używasz źródeł śledzenia WCF, ustaw `switchValue` opcję na ostrzeżenie. Jeśli używasz źródła śledzenia WCF `System.ServiceModel` , `switchValue` ustaw atrybut na `Warning` i `propagateActivity` atrybut na `true`. Jeśli używasz źródła śledzenia zdefiniowanego przez użytkownika, ustaw `switchValue` atrybut na. `Warning, ActivityTracing` Można to zrobić ręcznie przy użyciu [Narzędzia Edytora konfiguracji (SvcConfigEditor. exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Jeśli nie przewidujesz trafienia wydajności, możesz ustawić `switchValue` atrybut na `Information` we wszystkich wymienionych wcześniej przypadkach, co generuje dość dużą ilość danych śledzenia. Poniższy przykład ilustruje te zalecane ustawienia.  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a>Zalecane ustawienia dla wdrożenia lub debugowania  
 W przypadku środowiska wdrażania lub debugowania wybierz `Information` lub `Verbose`, a także `ActivityTracing` dla źródła zdefiniowanego przez użytkownika lub `System.ServiceModel` śledzenia. Aby ulepszyć debugowanie, należy również dodać do konfiguracji dodatkowe źródło śledzenia`System.ServiceModel.MessageLogging`() w celu umożliwienia rejestrowania komunikatów. Zwróć uwagę, `switchValue` że atrybut nie ma wpływu na to źródło śledzenia.  
  
 Poniższy przykład ilustruje zalecane ustawienia przy użyciu współużytkowanego odbiornika, który korzysta z `XmlWriterTraceListener`.  
  
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
  
## <a name="using-wmi-to-modify-settings"></a>Modyfikowanie ustawień przy użyciu usługi WMI  
 Za pomocą usługi WMI można zmienić ustawienia konfiguracji w czasie wykonywania (przez włączenie `wmiProviderEnabled` atrybutu w konfiguracji, jak pokazano w poprzednim przykładzie konfiguracji). Można na przykład użyć usługi WMI w programie CIM Studio, aby zmienić poziomy źródła śledzenia z ostrzeżeń na informacje w czasie wykonywania. Należy pamiętać, że koszt wydajności debugowania na żywo w ten sposób może być bardzo wysoki. Aby uzyskać więcej informacji na temat korzystania z usługi WMI, zobacz temat [używanie Instrumentacja zarządzania Windows do diagnostyki](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) .  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>Włącz skorelowane zdarzenia w śledzeniu ASP.NET  
 Zdarzenia ASP.NET nie ustawiają identyfikatora korelacji (ActivityID), chyba że jest włączone ASP.NET śledzenie zdarzeń. Aby sprawdzić poprawność zdarzeń skorelowanych, należy włączyć śledzenie zdarzeń ASP.NET za pomocą następującego polecenia w konsoli poleceń, które można wywołać, przechodząc do **menu Start**, **Run** i Type **cmd**,  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 Aby wyłączyć śledzenie zdarzeń ASP.NET, użyj następującego polecenia:  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Zobacz także

- [Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
