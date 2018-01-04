---
title: "&lt;Filtr&gt; elementu &lt;dodać&gt; dla &lt;odbiorników&gt; dla &lt;źródła&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: ff5acf8edcda68979c04f5e62237464ee6f040a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="108d0-102">&lt;Filtr&gt; elementu &lt;dodać&gt; dla &lt;odbiorników&gt; dla &lt;źródła&gt;</span><span class="sxs-lookup"><span data-stu-id="108d0-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="108d0-103">Dodaje filtr do odbiornika w `Listeners` kolekcji źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="108d0-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="108d0-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="108d0-104">\<configuration></span></span>  
<span data-ttu-id="108d0-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="108d0-105">\<system.diagnostics></span></span>  
<span data-ttu-id="108d0-106">\<źródeł ></span><span class="sxs-lookup"><span data-stu-id="108d0-106">\<sources></span></span>  
<span data-ttu-id="108d0-107">\<źródło ></span><span class="sxs-lookup"><span data-stu-id="108d0-107">\<source></span></span>  
<span data-ttu-id="108d0-108">\<obiekty nasłuchujące ></span><span class="sxs-lookup"><span data-stu-id="108d0-108">\<listeners></span></span>  
<span data-ttu-id="108d0-109">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="108d0-109">\<add></span></span>  
<span data-ttu-id="108d0-110">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="108d0-110">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="108d0-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="108d0-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="108d0-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="108d0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="108d0-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="108d0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="108d0-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="108d0-114">Attributes</span></span>  
  
|<span data-ttu-id="108d0-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="108d0-115">Attribute</span></span>|<span data-ttu-id="108d0-116">Opis</span><span class="sxs-lookup"><span data-stu-id="108d0-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="108d0-117">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="108d0-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="108d0-118">Określa typ filtr, który powinien dziedziczyć <xref:System.Diagnostics.TraceFilter> klasy.</span><span class="sxs-lookup"><span data-stu-id="108d0-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="108d0-119">Można użyć nazwa kwalifikowana przestrzeni nazw, typu, który odpowiada na typ <xref:System.Type.FullName%2A> właściwości lub użyć pełni kwalifikowana nazwa typu w tym informacje o zestawie, który odpowiada <xref:System.Type.AssemblyQualifiedName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="108d0-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="108d0-120">Aby uzyskać informacje dotyczące w pełni kwalifikowane nazwy typów, zobacz [określenie pełni kwalifikowane nazwy typów](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="108d0-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="108d0-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="108d0-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="108d0-122">Ciąg przekazany do konstruktora dla klasy określonego filtru.</span><span class="sxs-lookup"><span data-stu-id="108d0-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="108d0-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="108d0-123">Child Elements</span></span>  
 <span data-ttu-id="108d0-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="108d0-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="108d0-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="108d0-125">Parent Elements</span></span>  
  
|<span data-ttu-id="108d0-126">Element</span><span class="sxs-lookup"><span data-stu-id="108d0-126">Element</span></span>|<span data-ttu-id="108d0-127">Opis</span><span class="sxs-lookup"><span data-stu-id="108d0-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="108d0-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="108d0-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="108d0-129">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="108d0-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="108d0-130">Zawiera źródła śledzenia, które inicjują śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="108d0-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="108d0-131">Określa źródło śledzenia, który inicjuje śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="108d0-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="108d0-132">Zawiera nasłuchujących zbierania, przechowywania i kierowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="108d0-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="108d0-133">Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="108d0-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="108d0-134">Dodaje odbiornika do `Listeners` kolekcji źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="108d0-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="108d0-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="108d0-135">Remarks</span></span>  
 <span data-ttu-id="108d0-136">`<filter>` Elementu muszą być zawarte w `<add>` dla odbiornika źródła śledzenia, która określa typ odbiornika, nie tylko nazwę odbiornik w zdefiniowany element [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="108d0-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="108d0-137">Jeśli odbiornik jest zdefiniowany w [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtr dla tego odbiornika musi być zdefiniowana w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="108d0-137">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="108d0-138">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="108d0-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="108d0-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="108d0-139">Example</span></span>  
 <span data-ttu-id="108d0-140">Poniższy przykład przedstawia użycie `<filter>` element, aby dodać filtr do odbiornika `console` w `Listeners` kolekcji źródła śledzenia `myTraceSource`, określając poziom zdarzenia filtru jako `Error`.</span><span class="sxs-lookup"><span data-stu-id="108d0-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="108d0-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="108d0-141">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [<span data-ttu-id="108d0-142">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="108d0-142">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
