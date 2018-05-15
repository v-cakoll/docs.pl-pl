---
title: Zalecane ustawienia śledzenia i rejestrowania komunikatów
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 44cdf90572cc52d5daf95368a644759be0ad1ee0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="66c7c-102">Zalecane ustawienia śledzenia i rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="66c7c-102">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="66c7c-103">W tym temacie opisano ustawienia rejestrowania komunikatów dla różnych środowisk operacyjnych i śledzenie zalecane.</span><span class="sxs-lookup"><span data-stu-id="66c7c-103">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="66c7c-104">Zalecane ustawienia dla środowiska produkcyjnego</span><span class="sxs-lookup"><span data-stu-id="66c7c-104">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="66c7c-105">W środowisku produkcyjnym, jeśli używasz źródła śledzenia WCF, ustaw `switchValue` na ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="66c7c-105">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="66c7c-106">Jeśli używasz usługi WCF `System.ServiceModel` źródło śledzenia, należy ustawić `switchValue` atrybutu `Warning` i `propagateActivity` atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="66c7c-106">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="66c7c-107">Jeśli używasz źródła śledzenia zdefiniowanych przez użytkownika, należy ustawić `switchValue` atrybutu `Warning, ActivityTracing`.</span><span class="sxs-lookup"><span data-stu-id="66c7c-107">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="66c7c-108">Można to zrobić ręcznie przy użyciu [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="66c7c-108">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="66c7c-109">Jeśli nie będą trafień wydajności, możesz ustawić `switchValue` atrybutu `Information` we wszystkich przypadkach opisanych powyżej, który generuje stosunkowo dużej ilości danych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="66c7c-109">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="66c7c-110">W poniższym przykładzie pokazano tych zalecanych ustawień.</span><span class="sxs-lookup"><span data-stu-id="66c7c-110">The following example demonstrates these recommended settings.</span></span>  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="66c7c-111">Zalecane ustawienia wdrażania i debugowania</span><span class="sxs-lookup"><span data-stu-id="66c7c-111">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="66c7c-112">W celu wdrażania lub debugowania środowiska, wybierz `Information` lub `Verbose`, wraz z `ActivityTracing` dla obu zdefiniowanej przez użytkownika lub `System.ServiceModel` źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="66c7c-112">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="66c7c-113">Aby poprawić, debugowanie, należy również dodać dodatkowe źródła (`System.ServiceModel.MessageLogging`) w konfiguracji, aby włączyć rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="66c7c-113">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="66c7c-114">Zwróć uwagę, że `switchValue` atrybut nie ma wpływu na tego źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="66c7c-114">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="66c7c-115">W poniższym przykładzie pokazano zalecanych ustawień, za pomocą udostępnionego odbiornik, który korzysta z `XmlWriterTraceListener`.</span><span class="sxs-lookup"><span data-stu-id="66c7c-115">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
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
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="66c7c-116">Aby zmodyfikować ustawienia za pomocą usługi WMI</span><span class="sxs-lookup"><span data-stu-id="66c7c-116">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="66c7c-117">Przy użyciu usługi WMI do zmiany ustawień konfiguracji w czasie wykonywania (włączając `wmiProviderEnabled` atrybut w konfiguracji, jak pokazano w wcześniej przykładzie konfiguracji).</span><span class="sxs-lookup"><span data-stu-id="66c7c-117">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="66c7c-118">Na przykład umożliwia WMI w CIM Studio Zmienianie poziomów źródła śledzenia z ostrzegawczego do informacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="66c7c-118">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="66c7c-119">Należy pamiętać, że koszt wydajności debugowania na żywo w ten sposób mogą być bardzo duże.</span><span class="sxs-lookup"><span data-stu-id="66c7c-119">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="66c7c-120">Aby uzyskać więcej informacji o korzystaniu z usługi WMI, zobacz [przy użyciu Instrumentacji zarządzania Windows dla diagnostyki](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="66c7c-120">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="66c7c-121">Włącz zdarzenia skorelowane w śledzenie na platformie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="66c7c-121">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="66c7c-122">Zdarzenia ASP.NET nie należy ustawiać identyfikator korelacji (identyfikator), chyba że jest włączone śledzenie zdarzeń programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="66c7c-122">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="66c7c-123">Aby wyświetlić zdarzenia skorelowane prawidłowo, należy włączyć na zdarzenia ASP.NET śledzenia przy użyciu następującego polecenia w konsoli poleceń, które można wywołać, przechodząc do **Start**, **Uruchom** i typ **cmd** ,</span><span class="sxs-lookup"><span data-stu-id="66c7c-123">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="66c7c-124">Aby wyłączyć śledzenie zdarzeń programu ASP.NET, użyj następującego polecenia,</span><span class="sxs-lookup"><span data-stu-id="66c7c-124">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```  
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="66c7c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66c7c-125">See Also</span></span>  
 [<span data-ttu-id="66c7c-126">Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki</span><span class="sxs-lookup"><span data-stu-id="66c7c-126">Using Windows Management Instrumentation for Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
