---
title: "&lt;Filtr&gt; elementu &lt;dodać&gt; dla &lt;odbiorników&gt; dla &lt;śledzenia&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: efd31d03960fa516886586c4cf0a3e080d904977
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="8b194-102">&lt;Filtr&gt; elementu &lt;dodać&gt; dla &lt;odbiorników&gt; dla &lt;śledzenia&gt;</span><span class="sxs-lookup"><span data-stu-id="8b194-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="8b194-103">Dodaje filtr do odbiornika w `Listeners` kolekcji dla śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8b194-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
 <span data-ttu-id="8b194-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="8b194-104">\<configuration></span></span>  
<span data-ttu-id="8b194-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="8b194-105">\<system.diagnostics></span></span>  
<span data-ttu-id="8b194-106">\<śledzenia ></span><span class="sxs-lookup"><span data-stu-id="8b194-106">\<trace></span></span>  
<span data-ttu-id="8b194-107">\<obiekty nasłuchujące ></span><span class="sxs-lookup"><span data-stu-id="8b194-107">\<listeners></span></span>  
<span data-ttu-id="8b194-108">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="8b194-108">\<add></span></span>  
<span data-ttu-id="8b194-109">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="8b194-109">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b194-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b194-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b194-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8b194-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8b194-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8b194-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b194-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8b194-113">Attributes</span></span>  
  
|<span data-ttu-id="8b194-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8b194-114">Attribute</span></span>|<span data-ttu-id="8b194-115">Opis</span><span class="sxs-lookup"><span data-stu-id="8b194-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="8b194-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="8b194-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="8b194-117">Określa typ filtr, który powinien dziedziczyć <xref:System.Diagnostics.TraceFilter> klasy.</span><span class="sxs-lookup"><span data-stu-id="8b194-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="8b194-118">Można użyć nazwa kwalifikowana przestrzeni nazw, typu, który odpowiada na typ <xref:System.Type.FullName%2A> właściwości lub użyć pełni kwalifikowana nazwa typu w tym informacje o zestawie, który odpowiada <xref:System.Type.AssemblyQualifiedName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8b194-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="8b194-119">Aby uzyskać informacje dotyczące w pełni kwalifikowane nazwy typów, zobacz [określenie pełni kwalifikowane nazwy typów](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="8b194-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="8b194-120">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8b194-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="8b194-121">Ciąg przekazany do konstruktora dla klasy określonego filtru.</span><span class="sxs-lookup"><span data-stu-id="8b194-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b194-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8b194-122">Child Elements</span></span>  
 <span data-ttu-id="8b194-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="8b194-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b194-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8b194-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8b194-125">Element</span><span class="sxs-lookup"><span data-stu-id="8b194-125">Element</span></span>|<span data-ttu-id="8b194-126">Opis</span><span class="sxs-lookup"><span data-stu-id="8b194-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8b194-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8b194-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8b194-128">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8b194-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="8b194-129">Zawiera nasłuchujących zbierania, przechowywania i trasy śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8b194-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="8b194-130">Zawiera nasłuchujących zbierania, przechowywania i kierowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8b194-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="8b194-131">Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="8b194-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="8b194-132">Dodaje odbiornika do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8b194-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b194-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b194-133">Remarks</span></span>  
 <span data-ttu-id="8b194-134">`<filter>` Elementu muszą być zawarte w `<add>` dla odbiornika śledzenia, która określa typ odbiornika, nie tylko nazwę odbiornik w zdefiniowany element [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="8b194-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="8b194-135">Jeśli odbiornik jest zdefiniowany w [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtr dla tego odbiornika musi być zdefiniowana w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="8b194-135">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="8b194-136">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b194-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b194-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="8b194-137">Example</span></span>  
 <span data-ttu-id="8b194-138">Poniższy przykład przedstawia użycie `<filter>` element, aby dodać filtr do odbiornika `console` w `Listeners` kolekcji do śledzenia, określając poziom zdarzenia filtru jako `Error`.</span><span class="sxs-lookup"><span data-stu-id="8b194-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b194-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b194-139">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [<span data-ttu-id="8b194-140">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="8b194-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
