---
title: Zalecane ustawienia śledzenia i rejestrowania komunikatów
description: Informacje na temat zalecanych ustawień śledzenia i rejestrowania komunikatów dla różnych środowisk operacyjnych w programie WCF.
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 71067a4d6f4cec65a148a8162c40e44d82b85784
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245331"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="525a2-103">Zalecane ustawienia śledzenia i rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="525a2-103">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="525a2-104">W tym temacie opisano zalecane ustawienia śledzenia i rejestrowania komunikatów dla różnych środowisk operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="525a2-104">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="525a2-105">Zalecane ustawienia dla środowiska produkcyjnego</span><span class="sxs-lookup"><span data-stu-id="525a2-105">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="525a2-106">W przypadku środowiska produkcyjnego, jeśli używasz źródeł śledzenia WCF, ustaw opcję `switchValue` na ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="525a2-106">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="525a2-107">Jeśli używasz `System.ServiceModel` źródła śledzenia WCF, ustaw `switchValue` atrybut na `Warning` i `propagateActivity` atrybut na `true` .</span><span class="sxs-lookup"><span data-stu-id="525a2-107">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="525a2-108">Jeśli używasz źródła śledzenia zdefiniowanego przez użytkownika, ustaw `switchValue` atrybut na `Warning, ActivityTracing` .</span><span class="sxs-lookup"><span data-stu-id="525a2-108">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="525a2-109">Można to zrobić ręcznie przy użyciu [Narzędzia Edytora konfiguracji (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="525a2-109">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="525a2-110">Jeśli nie przewidujesz trafienia wydajności, możesz ustawić `switchValue` atrybut na `Information` we wszystkich wymienionych wcześniej przypadkach, co generuje dość dużą ilość danych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="525a2-110">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="525a2-111">Poniższy przykład ilustruje te zalecane ustawienia.</span><span class="sxs-lookup"><span data-stu-id="525a2-111">The following example demonstrates these recommended settings.</span></span>  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="525a2-112">Zalecane ustawienia dla wdrożenia lub debugowania</span><span class="sxs-lookup"><span data-stu-id="525a2-112">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="525a2-113">W przypadku środowiska wdrażania lub debugowania wybierz `Information` lub `Verbose` , a także `ActivityTracing` dla źródła zdefiniowanego przez użytkownika lub `System.ServiceModel` śledzenia.</span><span class="sxs-lookup"><span data-stu-id="525a2-113">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="525a2-114">Aby ulepszyć debugowanie, należy również dodać do konfiguracji dodatkowe źródło śledzenia ( `System.ServiceModel.MessageLogging` ) w celu umożliwienia rejestrowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="525a2-114">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="525a2-115">Zwróć uwagę, że `switchValue` atrybut nie ma wpływu na to źródło śledzenia.</span><span class="sxs-lookup"><span data-stu-id="525a2-115">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="525a2-116">Poniższy przykład ilustruje zalecane ustawienia przy użyciu współużytkowanego odbiornika, który korzysta z `XmlWriterTraceListener` .</span><span class="sxs-lookup"><span data-stu-id="525a2-116">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
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
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="525a2-117">Modyfikowanie ustawień przy użyciu usługi WMI</span><span class="sxs-lookup"><span data-stu-id="525a2-117">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="525a2-118">Za pomocą usługi WMI można zmienić ustawienia konfiguracji w czasie wykonywania (przez włączenie `wmiProviderEnabled` atrybutu w konfiguracji, jak pokazano w poprzednim przykładzie konfiguracji).</span><span class="sxs-lookup"><span data-stu-id="525a2-118">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="525a2-119">Można na przykład użyć usługi WMI w programie CIM Studio, aby zmienić poziomy źródła śledzenia z ostrzeżeń na informacje w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="525a2-119">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="525a2-120">Należy pamiętać, że koszt wydajności debugowania na żywo w ten sposób może być bardzo wysoki.</span><span class="sxs-lookup"><span data-stu-id="525a2-120">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="525a2-121">Aby uzyskać więcej informacji na temat korzystania z usługi WMI, zobacz temat [używanie Instrumentacja zarządzania Windows do diagnostyki](../wmi/index.md) .</span><span class="sxs-lookup"><span data-stu-id="525a2-121">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="525a2-122">Włącz skorelowane zdarzenia w śledzeniu ASP.NET</span><span class="sxs-lookup"><span data-stu-id="525a2-122">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="525a2-123">Zdarzenia ASP.NET nie ustawiają identyfikatora korelacji (ActivityID), chyba że jest włączone ASP.NET śledzenie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="525a2-123">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="525a2-124">Aby sprawdzić poprawność zdarzeń skorelowanych, należy włączyć śledzenie zdarzeń ASP.NET za pomocą następującego polecenia w konsoli poleceń, które można wywołać, przechodząc do **menu Start**, **Run** i Type **cmd**,</span><span class="sxs-lookup"><span data-stu-id="525a2-124">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="525a2-125">Aby wyłączyć śledzenie zdarzeń ASP.NET, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="525a2-125">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="525a2-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="525a2-126">See also</span></span>

- [<span data-ttu-id="525a2-127">Używanie Instrumentacja zarządzania Windows do diagnostyki</span><span class="sxs-lookup"><span data-stu-id="525a2-127">Using Windows Management Instrumentation for Diagnostics</span></span>](../wmi/index.md)
