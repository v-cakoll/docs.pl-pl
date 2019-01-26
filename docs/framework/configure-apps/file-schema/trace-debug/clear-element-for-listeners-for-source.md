---
title: '&lt;Wyczyść&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 362e1d7a4ac4c39309aa86561683df1d239f2ab1
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083873"
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="faffb-102">&lt;Wyczyść&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;</span><span class="sxs-lookup"><span data-stu-id="faffb-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="faffb-103">Czyści `Listeners` kolekcję dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="faffb-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="faffb-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="faffb-104">\<configuration></span></span>  
<span data-ttu-id="faffb-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="faffb-105">\<system.diagnostics></span></span>  
<span data-ttu-id="faffb-106">\<źródła ></span><span class="sxs-lookup"><span data-stu-id="faffb-106">\<sources></span></span>  
<span data-ttu-id="faffb-107">\<source></span><span class="sxs-lookup"><span data-stu-id="faffb-107">\<source></span></span>  
<span data-ttu-id="faffb-108">\<listeners></span><span class="sxs-lookup"><span data-stu-id="faffb-108">\<listeners></span></span>  
<span data-ttu-id="faffb-109">\<clear></span><span class="sxs-lookup"><span data-stu-id="faffb-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faffb-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="faffb-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="faffb-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="faffb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="faffb-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="faffb-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="faffb-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="faffb-113">Attributes</span></span>  
 <span data-ttu-id="faffb-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="faffb-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="faffb-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="faffb-115">Child Elements</span></span>  
 <span data-ttu-id="faffb-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="faffb-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="faffb-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="faffb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="faffb-118">Element</span><span class="sxs-lookup"><span data-stu-id="faffb-118">Element</span></span>|<span data-ttu-id="faffb-119">Opis</span><span class="sxs-lookup"><span data-stu-id="faffb-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="faffb-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="faffb-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="faffb-121">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="faffb-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="faffb-122">Zawiera źródła śledzenia, które inicjują komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="faffb-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="faffb-123">Określa źródło śledzenia, który inicjuje komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="faffb-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="faffb-124">Określa obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów w postaci.</span><span class="sxs-lookup"><span data-stu-id="faffb-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faffb-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="faffb-125">Remarks</span></span>  
 <span data-ttu-id="faffb-126">`<clear>` Elementu usuwa wszystkie odbiorniki z `Listeners` kolekcję dla źródła śledzenia, łącznie z <xref:System.Diagnostics.DefaultTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="faffb-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="faffb-127">Możesz użyć `<clear>` element przed użyciem `<add>` elementu, aby mieć pewność, istnieją nie aktywne odbiorniki w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="faffb-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="faffb-128">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="faffb-128">Configuration File</span></span>  
 <span data-ttu-id="faffb-129">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="faffb-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="faffb-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="faffb-130">Example</span></span>  
 <span data-ttu-id="faffb-131">Poniższy przykład pokazuje, jak używać `<clear>` element przed użyciem `<add>` elementy do dodania odbiorniki `console` i `textListener` do `Listeners` kolekcji dla źródła śledzenia `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="faffb-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="faffb-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="faffb-132">See also</span></span>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="faffb-133">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="faffb-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="faffb-134">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="faffb-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
