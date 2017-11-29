---
title: "Zalecane ustawienia śledzenia i rejestrowania komunikatów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b6986c775db50ea5b763288f8f3b9bdcf1bf7e67
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>Zalecane ustawienia śledzenia i rejestrowania komunikatów
W tym temacie opisano ustawienia rejestrowania komunikatów dla różnych środowisk operacyjnych i śledzenie zalecane.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Zalecane ustawienia dla środowiska produkcyjnego  
 W środowisku produkcyjnym, jeśli używasz źródła śledzenia WCF, ustaw `switchValue` na ostrzeżenie. Jeśli używasz usługi WCF `System.ServiceModel` źródło śledzenia, należy ustawić `switchValue` atrybutu `Warning` i `propagateActivity` atrybutu `true`. Jeśli używasz źródła śledzenia zdefiniowanych przez użytkownika, należy ustawić `switchValue` atrybutu `Warning, ActivityTracing`. Można to zrobić ręcznie przy użyciu [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Jeśli nie będą trafień wydajności, możesz ustawić `switchValue` atrybutu `Information` we wszystkich przypadkach opisanych powyżej, który generuje stosunkowo dużej ilości danych śledzenia. W poniższym przykładzie pokazano tych zalecanych ustawień.  
  
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
 W celu wdrażania lub debugowania środowiska, wybierz `Information` lub `Verbose`, wraz z `ActivityTracing` dla obu zdefiniowanej przez użytkownika lub `System.ServiceModel` źródła śledzenia. Aby poprawić, debugowanie, należy również dodać dodatkowe źródła (`System.ServiceModel.MessageLogging`) w konfiguracji, aby włączyć rejestrowanie komunikatów. Zwróć uwagę, że `switchValue` atrybut nie ma wpływu na tego źródła śledzenia.  
  
 W poniższym przykładzie pokazano zalecanych ustawień, za pomocą udostępnionego odbiornik, który korzysta z `XmlWriterTraceListener`.  
  
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
  
## <a name="using-wmi-to-modify-settings"></a>Aby zmodyfikować ustawienia za pomocą usługi WMI  
 Przy użyciu usługi WMI do zmiany ustawień konfiguracji w czasie wykonywania (włączając `wmiProviderEnabled` atrybut w konfiguracji, jak pokazano w wcześniej przykładzie konfiguracji). Na przykład umożliwia WMI w CIM Studio Zmienianie poziomów źródła śledzenia z ostrzegawczego do informacji w czasie wykonywania. Należy pamiętać, że koszt wydajności debugowania na żywo w ten sposób mogą być bardzo duże. Aby uzyskać więcej informacji o korzystaniu z usługi WMI, zobacz [przy użyciu Instrumentacji zarządzania Windows dla diagnostyki](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) tematu.  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>Włącz zdarzenia skorelowane w śledzenie na platformie ASP.NET  
 Zdarzenia ASP.NET nie należy ustawiać identyfikator korelacji (identyfikator), chyba że jest włączone śledzenie zdarzeń programu ASP.NET. Aby wyświetlić zdarzenia skorelowane prawidłowo, należy włączyć na zdarzenia ASP.NET śledzenia przy użyciu następującego polecenia w konsoli poleceń, które można wywołać, przechodząc do **Start**, **Uruchom** i typ **cmd** ,  
  
```  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 Aby wyłączyć śledzenie zdarzeń programu ASP.NET, użyj następującego polecenia,  
  
```  
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Za pomocą Instrumentacji zarządzania Windows dla diagnostyki](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
