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
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="71620-102">Zalecane ustawienia śledzenia i rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="71620-102">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="71620-103">W tym temacie opisano zalecane ustawienia śledzenia i rejestrowania wiadomości dla różnych środowisk operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="71620-103">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="71620-104">Zalecane ustawienia dla środowiska produkcyjnego</span><span class="sxs-lookup"><span data-stu-id="71620-104">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="71620-105">W środowisku produkcyjnym, jeśli używasz źródeł śledzenia `switchValue` WCF, ustaw na Ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="71620-105">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="71620-106">Jeśli używasz źródła śledzenia `System.ServiceModel` WCF, `switchValue` ustaw `Warning` atrybut `propagateActivity` i atrybut `true`.</span><span class="sxs-lookup"><span data-stu-id="71620-106">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="71620-107">Jeśli używasz źródła śledzenia zdefiniowanego przez `switchValue` użytkownika, `Warning, ActivityTracing`ustaw atrybut na .</span><span class="sxs-lookup"><span data-stu-id="71620-107">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="71620-108">Można to zrobić ręcznie za pomocą [narzędzia Edytor konfiguracji (SvcConfigEditor.exe).](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)</span><span class="sxs-lookup"><span data-stu-id="71620-108">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="71620-109">Jeśli nie przewidujesz trafienia w wydajności, `switchValue` można ustawić `Information` atrybut we wszystkich wcześniej wymienionych przypadkach, który generuje dość dużą ilość danych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71620-109">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="71620-110">W poniższym przykładzie przedstawiono te zalecane ustawienia.</span><span class="sxs-lookup"><span data-stu-id="71620-110">The following example demonstrates these recommended settings.</span></span>  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="71620-111">Zalecane ustawienia wdrażania lub debugowania</span><span class="sxs-lookup"><span data-stu-id="71620-111">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="71620-112">W przypadku środowiska wdrażania lub `Information` `Verbose`debugowania `ActivityTracing` wybierz lub , wraz `System.ServiceModel` ze źródłem zdefiniowanym przez użytkownika lub śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71620-112">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="71620-113">Aby poprawić debugowanie, należy również dodać`System.ServiceModel.MessageLogging`dodatkowe źródło śledzenia ( ) do konfiguracji, aby włączyć rejestrowanie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="71620-113">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="71620-114">Należy zauważyć, że `switchValue` atrybut nie ma wpływu na to źródło śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71620-114">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="71620-115">W poniższym przykładzie przedstawiono zalecane ustawienia przy użyciu `XmlWriterTraceListener`udostępnionego odbiornika, który korzysta z pliku .</span><span class="sxs-lookup"><span data-stu-id="71620-115">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
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
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="71620-116">Modyfikowanie ustawień za pomocą usługi WMI</span><span class="sxs-lookup"><span data-stu-id="71620-116">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="71620-117">Za pomocą usługi WMI można zmienić ustawienia konfiguracji `wmiProviderEnabled` w czasie wykonywania (włączając atrybut w konfiguracji, jak pokazano w przykładzie poprzedniej konfiguracji).</span><span class="sxs-lookup"><span data-stu-id="71620-117">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="71620-118">Na przykład można użyć WMI w programie CIM Studio, aby zmienić poziomy źródła śledzenia z ostrzeżenie na informacje w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="71620-118">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="71620-119">Należy pamiętać, że koszt wydajności debugowania na żywo w ten sposób może być bardzo wysoki.</span><span class="sxs-lookup"><span data-stu-id="71620-119">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="71620-120">Aby uzyskać więcej informacji na temat korzystania z usługi WMI, zobacz [using Windows Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) topic.</span><span class="sxs-lookup"><span data-stu-id="71620-120">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="71620-121">Włączanie zdarzeń skorelowanych w ASP.NET śledzenia</span><span class="sxs-lookup"><span data-stu-id="71620-121">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="71620-122">ASP.NET zdarzenia nie ustawiają identyfikatora korelacji (ActivityID), chyba że jest włączone śledzenie zdarzeń ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="71620-122">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="71620-123">Aby poprawnie wyświetlić skorelowane zdarzenia, należy włączyć śledzenie zdarzeń ASP.NET za pomocą następującego polecenia w konsoli poleceń, które można wywołać, przechodząc do **ekranu Start**, **Uruchom** i wpisując **polecenie cmd**,</span><span class="sxs-lookup"><span data-stu-id="71620-123">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="71620-124">Aby wyłączyć śledzenie zdarzeń ASP.NET, użyj następującego polecenia,</span><span class="sxs-lookup"><span data-stu-id="71620-124">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="71620-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71620-125">See also</span></span>

- [<span data-ttu-id="71620-126">Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki</span><span class="sxs-lookup"><span data-stu-id="71620-126">Using Windows Management Instrumentation for Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
