---
title: '&lt;Filtr&gt; elementu &lt;Dodaj&gt; dla &lt;odbiorników&gt; dla &lt;źródła&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 19b28c3391a10cc522f17c5353c9ec0726b0a2f8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47073284"
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="71dd1-102">&lt;Filtr&gt; elementu &lt;Dodaj&gt; dla &lt;odbiorników&gt; dla &lt;źródła&gt;</span><span class="sxs-lookup"><span data-stu-id="71dd1-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="71dd1-103">Dodaje filtr do odbiornika w `Listeners` kolekcję dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71dd1-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="71dd1-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="71dd1-104">\<configuration></span></span>  
<span data-ttu-id="71dd1-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="71dd1-105">\<system.diagnostics></span></span>  
<span data-ttu-id="71dd1-106">\<źródła ></span><span class="sxs-lookup"><span data-stu-id="71dd1-106">\<sources></span></span>  
<span data-ttu-id="71dd1-107">\<źródło ></span><span class="sxs-lookup"><span data-stu-id="71dd1-107">\<source></span></span>  
<span data-ttu-id="71dd1-108">\<odbiorniki ></span><span class="sxs-lookup"><span data-stu-id="71dd1-108">\<listeners></span></span>  
<span data-ttu-id="71dd1-109">\<add></span><span class="sxs-lookup"><span data-stu-id="71dd1-109">\<add></span></span>  
<span data-ttu-id="71dd1-110">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="71dd1-110">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71dd1-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="71dd1-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71dd1-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="71dd1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="71dd1-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="71dd1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71dd1-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="71dd1-114">Attributes</span></span>  
  
|<span data-ttu-id="71dd1-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="71dd1-115">Attribute</span></span>|<span data-ttu-id="71dd1-116">Opis</span><span class="sxs-lookup"><span data-stu-id="71dd1-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="71dd1-117">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="71dd1-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="71dd1-118">Określa typ filtr, który powinien dziedziczyć <xref:System.Diagnostics.TraceFilter> klasy.</span><span class="sxs-lookup"><span data-stu-id="71dd1-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="71dd1-119">Można użyć w przestrzeni nazw, kwalifikowana nazwa typu, który odnosi się do typu <xref:System.Type.FullName%2A> właściwości lub można użyć w pełni kwalifikowana nazwa typu w tym informacje o zestawie, który odpowiada <xref:System.Type.AssemblyQualifiedName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="71dd1-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="71dd1-120">Aby dowiedzieć się, w pełni kwalifikowanych nazw typów, zobacz [określanie w pełni kwalifikowanej nazwy typu](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="71dd1-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="71dd1-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="71dd1-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="71dd1-122">Ciąg przekazany do konstruktora dla klasy określony filtr.</span><span class="sxs-lookup"><span data-stu-id="71dd1-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71dd1-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="71dd1-123">Child Elements</span></span>  
 <span data-ttu-id="71dd1-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="71dd1-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71dd1-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="71dd1-125">Parent Elements</span></span>  
  
|<span data-ttu-id="71dd1-126">Element</span><span class="sxs-lookup"><span data-stu-id="71dd1-126">Element</span></span>|<span data-ttu-id="71dd1-127">Opis</span><span class="sxs-lookup"><span data-stu-id="71dd1-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="71dd1-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="71dd1-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="71dd1-129">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71dd1-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="71dd1-130">Zawiera źródła śledzenia, które inicjują komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71dd1-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="71dd1-131">Określa źródło śledzenia, który inicjuje komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71dd1-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="71dd1-132">Zawiera obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów w postaci.</span><span class="sxs-lookup"><span data-stu-id="71dd1-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="71dd1-133">Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="71dd1-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="71dd1-134">Dodaje odbiornik do `Listeners` kolekcję dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71dd1-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71dd1-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71dd1-135">Remarks</span></span>  
 <span data-ttu-id="71dd1-136">`<filter>` Element musi być zawarty w `<add>` elementu dla odbiornika źródła śledzenia, który określa typ odbiornika, nie tylko nazwy odbiornik zdefiniowane w [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="71dd1-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="71dd1-137">Jeśli odbiornik jest zdefiniowany w [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtr dla tego odbiornika musi być zdefiniowany w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="71dd1-137">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="71dd1-138">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71dd1-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71dd1-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="71dd1-139">Example</span></span>  
 <span data-ttu-id="71dd1-140">Poniższy przykład pokazuje, jak używać `<filter>` elementu Dodawanie filtru do odbiornika `console` w `Listeners` kolekcji dla źródła śledzenia `myTraceSource`, określając poziom zdarzenia filtru jako `Error`.</span><span class="sxs-lookup"><span data-stu-id="71dd1-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="71dd1-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71dd1-141">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [<span data-ttu-id="71dd1-142">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="71dd1-142">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
