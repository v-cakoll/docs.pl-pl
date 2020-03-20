---
title: Zalecane ustawienia śledzenia i rejestrowania komunikatów
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 604aae2c0a0c5390428e7f1a2c99e17e90ee76a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185731"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>Zalecane ustawienia śledzenia i rejestrowania komunikatów
W tym temacie opisano zalecane ustawienia śledzenia i rejestrowania wiadomości dla różnych środowisk operacyjnych.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Zalecane ustawienia dla środowiska produkcyjnego  
 W środowisku produkcyjnym, jeśli używasz źródeł śledzenia `switchValue` WCF, ustaw na Ostrzeżenie. Jeśli używasz źródła śledzenia `System.ServiceModel` WCF, `switchValue` ustaw `Warning` atrybut `propagateActivity` i atrybut `true`. Jeśli używasz źródła śledzenia zdefiniowanego przez `switchValue` użytkownika, `Warning, ActivityTracing`ustaw atrybut na . Można to zrobić ręcznie za pomocą [narzędzia Edytor konfiguracji (SvcConfigEditor.exe).](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) Jeśli nie przewidujesz trafienia w wydajności, `switchValue` można ustawić `Information` atrybut we wszystkich wcześniej wymienionych przypadkach, który generuje dość dużą ilość danych śledzenia. W poniższym przykładzie przedstawiono te zalecane ustawienia.  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a>Zalecane ustawienia wdrażania lub debugowania  
 W przypadku środowiska wdrażania lub `Information` `Verbose`debugowania `ActivityTracing` wybierz lub , wraz `System.ServiceModel` ze źródłem zdefiniowanym przez użytkownika lub śledzenia. Aby poprawić debugowanie, należy również dodać`System.ServiceModel.MessageLogging`dodatkowe źródło śledzenia ( ) do konfiguracji, aby włączyć rejestrowanie wiadomości. Należy zauważyć, że `switchValue` atrybut nie ma wpływu na to źródło śledzenia.  
  
 W poniższym przykładzie przedstawiono zalecane ustawienia przy użyciu `XmlWriterTraceListener`udostępnionego odbiornika, który korzysta z pliku .  
  
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
  
## <a name="using-wmi-to-modify-settings"></a>Modyfikowanie ustawień za pomocą usługi WMI  
 Za pomocą usługi WMI można zmienić ustawienia konfiguracji `wmiProviderEnabled` w czasie wykonywania (włączając atrybut w konfiguracji, jak pokazano w przykładzie poprzedniej konfiguracji). Na przykład można użyć WMI w programie CIM Studio, aby zmienić poziomy źródła śledzenia z ostrzeżenie na informacje w czasie wykonywania. Należy pamiętać, że koszt wydajności debugowania na żywo w ten sposób może być bardzo wysoki. Aby uzyskać więcej informacji na temat korzystania z usługi WMI, zobacz [using Windows Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) topic.  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>Włączanie zdarzeń skorelowanych w ASP.NET śledzenia  
 ASP.NET zdarzenia nie ustawiają identyfikatora korelacji (ActivityID), chyba że jest włączone śledzenie zdarzeń ASP.NET. Aby poprawnie wyświetlić skorelowane zdarzenia, należy włączyć śledzenie zdarzeń ASP.NET za pomocą następującego polecenia w konsoli poleceń, które można wywołać, przechodząc do **ekranu Start**, **Uruchom** i wpisując **polecenie cmd**,  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 Aby wyłączyć śledzenie zdarzeń ASP.NET, użyj następującego polecenia,  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Zobacz też

- [Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
