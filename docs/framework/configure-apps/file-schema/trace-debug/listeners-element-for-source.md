---
title: '&lt;odbiorniki&gt; elementu &lt;źródła&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 86b85779f4eff72e8ab910a5ccd32fd369270509
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48027822"
---
# <a name="ltlistenersgt-element-for-ltsourcegt"></a><span data-ttu-id="ba275-102">&lt;odbiorniki&gt; elementu &lt;źródła&gt;</span><span class="sxs-lookup"><span data-stu-id="ba275-102">&lt;listeners&gt; Element for &lt;source&gt;</span></span>
<span data-ttu-id="ba275-103">Dodaje lub usuwa słuchaczy w <xref:System.Diagnostics.TraceSource.Listeners%2A> kolekcji <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="ba275-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="ba275-104">Odbiornik kieruje dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takie jak dziennik, okno lub pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="ba275-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="ba275-105">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="ba275-105">\<configuration></span></span>  
<span data-ttu-id="ba275-106">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="ba275-106">\<system.diagnostics></span></span>  
<span data-ttu-id="ba275-107">\<źródła ></span><span class="sxs-lookup"><span data-stu-id="ba275-107">\<sources></span></span>  
<span data-ttu-id="ba275-108">\<źródło ></span><span class="sxs-lookup"><span data-stu-id="ba275-108">\<source></span></span>  
<span data-ttu-id="ba275-109">\<odbiorniki > Element</span><span class="sxs-lookup"><span data-stu-id="ba275-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba275-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba275-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba275-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ba275-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ba275-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ba275-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba275-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ba275-113">Attributes</span></span>  
 <span data-ttu-id="ba275-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="ba275-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ba275-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ba275-115">Child Elements</span></span>  
  
|<span data-ttu-id="ba275-116">Element</span><span class="sxs-lookup"><span data-stu-id="ba275-116">Element</span></span>|<span data-ttu-id="ba275-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ba275-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba275-118">\<add></span><span class="sxs-lookup"><span data-stu-id="ba275-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="ba275-119">Dodaje odbiornik do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ba275-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="ba275-120">\<remove></span><span class="sxs-lookup"><span data-stu-id="ba275-120">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="ba275-121">Usuwa odbiornik z `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ba275-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="ba275-122">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="ba275-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="ba275-123">Czyści `Listeners` kolekcję dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ba275-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ba275-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ba275-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ba275-125">Element</span><span class="sxs-lookup"><span data-stu-id="ba275-125">Element</span></span>|<span data-ttu-id="ba275-126">Opis</span><span class="sxs-lookup"><span data-stu-id="ba275-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ba275-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba275-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ba275-128">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ba275-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="ba275-129">Zawiera źródła śledzenia, które inicjują komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ba275-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="ba275-130">Określa źródło śledzenia, który inicjuje komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ba275-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba275-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba275-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="ba275-132">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ba275-132">Configuration File</span></span>  
 <span data-ttu-id="ba275-133">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ba275-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba275-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba275-134">Example</span></span>  
 <span data-ttu-id="ba275-135">Poniższy przykład pokazuje, jak używać `<listeners>` elementu do dodania detektor śledzenia konsoli do `mySource` źródła i usunąć odbiornik śledzenia domyślnego.</span><span class="sxs-lookup"><span data-stu-id="ba275-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba275-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba275-136">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="ba275-137">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="ba275-137">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="ba275-138">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="ba275-138">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
