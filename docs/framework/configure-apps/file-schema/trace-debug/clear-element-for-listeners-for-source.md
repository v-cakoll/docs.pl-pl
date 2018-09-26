---
title: '&lt;Wyczyść&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 3674b5e8f54735010da901c76b77bd617218891e
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47071756"
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="d1d3d-102">&lt;Wyczyść&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;</span><span class="sxs-lookup"><span data-stu-id="d1d3d-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="d1d3d-103">Czyści `Listeners` kolekcję dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d1d3d-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="d1d3d-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="d1d3d-104">\<configuration></span></span>  
<span data-ttu-id="d1d3d-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="d1d3d-105">\<system.diagnostics></span></span>  
<span data-ttu-id="d1d3d-106">\<źródła ></span><span class="sxs-lookup"><span data-stu-id="d1d3d-106">\<sources></span></span>  
<span data-ttu-id="d1d3d-107">\<źródło ></span><span class="sxs-lookup"><span data-stu-id="d1d3d-107">\<source></span></span>  
<span data-ttu-id="d1d3d-108">\<odbiorniki ></span><span class="sxs-lookup"><span data-stu-id="d1d3d-108">\<listeners></span></span>  
<span data-ttu-id="d1d3d-109">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="d1d3d-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1d3d-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1d3d-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1d3d-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d1d3d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d1d3d-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d1d3d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1d3d-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d1d3d-113">Attributes</span></span>  
 <span data-ttu-id="d1d3d-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="d1d3d-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d1d3d-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d1d3d-115">Child Elements</span></span>  
 <span data-ttu-id="d1d3d-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="d1d3d-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1d3d-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d1d3d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d1d3d-118">Element</span><span class="sxs-lookup"><span data-stu-id="d1d3d-118">Element</span></span>|<span data-ttu-id="d1d3d-119">Opis</span><span class="sxs-lookup"><span data-stu-id="d1d3d-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d1d3d-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d1d3d-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d1d3d-121">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d1d3d-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="d1d3d-122">Zawiera źródła śledzenia, które inicjują komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d1d3d-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="d1d3d-123">Określa źródło śledzenia, który inicjuje komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d1d3d-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="d1d3d-124">Określa obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów w postaci.</span><span class="sxs-lookup"><span data-stu-id="d1d3d-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1d3d-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1d3d-125">Remarks</span></span>  
 <span data-ttu-id="d1d3d-126">`<clear>` Elementu usuwa wszystkie odbiorniki z `Listeners` kolekcję dla źródła śledzenia, łącznie z <xref:System.Diagnostics.DefaultTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="d1d3d-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="d1d3d-127">Możesz użyć `<clear>` element przed użyciem `<add>` elementu, aby mieć pewność, istnieją nie aktywne odbiorniki w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d1d3d-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="d1d3d-128">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d1d3d-128">Configuration File</span></span>  
 <span data-ttu-id="d1d3d-129">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d1d3d-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1d3d-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1d3d-130">Example</span></span>  
 <span data-ttu-id="d1d3d-131">Poniższy przykład pokazuje, jak używać `<clear>` element przed użyciem `<add>` elementy do dodania odbiorniki `console` i `textListener` do `Listeners` kolekcji dla źródła śledzenia `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="d1d3d-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="d1d3d-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1d3d-132">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="d1d3d-133">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="d1d3d-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="d1d3d-134">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="d1d3d-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
