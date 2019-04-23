---
title: <clear> Element <listeners> dla <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 63d3bb272fcdbee2c59b0569c85f8183cdac8666
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158356"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="a06a9-102">\<Wyczyść >, Element dla \<odbiorników > dla \<źródła ></span><span class="sxs-lookup"><span data-stu-id="a06a9-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="a06a9-103">Czyści `Listeners` kolekcję dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a06a9-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="a06a9-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="a06a9-104">\<configuration></span></span>  
<span data-ttu-id="a06a9-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="a06a9-105">\<system.diagnostics></span></span>  
<span data-ttu-id="a06a9-106">\<źródła ></span><span class="sxs-lookup"><span data-stu-id="a06a9-106">\<sources></span></span>  
<span data-ttu-id="a06a9-107">\<source></span><span class="sxs-lookup"><span data-stu-id="a06a9-107">\<source></span></span>  
<span data-ttu-id="a06a9-108">\<listeners></span><span class="sxs-lookup"><span data-stu-id="a06a9-108">\<listeners></span></span>  
<span data-ttu-id="a06a9-109">\<clear></span><span class="sxs-lookup"><span data-stu-id="a06a9-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a06a9-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="a06a9-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a06a9-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a06a9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a06a9-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a06a9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a06a9-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a06a9-113">Attributes</span></span>  
 <span data-ttu-id="a06a9-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="a06a9-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a06a9-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a06a9-115">Child Elements</span></span>  
 <span data-ttu-id="a06a9-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="a06a9-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a06a9-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a06a9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a06a9-118">Element</span><span class="sxs-lookup"><span data-stu-id="a06a9-118">Element</span></span>|<span data-ttu-id="a06a9-119">Opis</span><span class="sxs-lookup"><span data-stu-id="a06a9-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a06a9-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a06a9-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a06a9-121">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a06a9-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="a06a9-122">Zawiera źródła śledzenia, które inicjują komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a06a9-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="a06a9-123">Określa źródło śledzenia, który inicjuje komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a06a9-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="a06a9-124">Określa obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów w postaci.</span><span class="sxs-lookup"><span data-stu-id="a06a9-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a06a9-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a06a9-125">Remarks</span></span>  
 <span data-ttu-id="a06a9-126">`<clear>` Elementu usuwa wszystkie odbiorniki z `Listeners` kolekcję dla źródła śledzenia, łącznie z <xref:System.Diagnostics.DefaultTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="a06a9-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="a06a9-127">Możesz użyć `<clear>` element przed użyciem `<add>` elementu, aby mieć pewność, istnieją nie aktywne odbiorniki w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a06a9-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="a06a9-128">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a06a9-128">Configuration File</span></span>  
 <span data-ttu-id="a06a9-129">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a06a9-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a06a9-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="a06a9-130">Example</span></span>  
 <span data-ttu-id="a06a9-131">Poniższy przykład pokazuje, jak używać `<clear>` element przed użyciem `<add>` elementy do dodania odbiorniki `console` i `textListener` do `Listeners` kolekcji dla źródła śledzenia `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="a06a9-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a06a9-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a06a9-132">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="a06a9-133">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="a06a9-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="a06a9-134">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="a06a9-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
