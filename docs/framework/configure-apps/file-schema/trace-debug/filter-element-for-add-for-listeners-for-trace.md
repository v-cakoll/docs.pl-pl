---
title: '&lt;Filtr&gt; elementu &lt;Dodaj&gt; dla &lt;odbiorników&gt; dla &lt;śledzenia&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 85d81beead84be48730ba3a4469e8efdff1bbb0b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523700"
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="a8011-102">&lt;Filtr&gt; elementu &lt;Dodaj&gt; dla &lt;odbiorników&gt; dla &lt;śledzenia&gt;</span><span class="sxs-lookup"><span data-stu-id="a8011-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="a8011-103">Dodaje filtr do odbiornika w `Listeners` kolekcji dla śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a8011-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
 <span data-ttu-id="a8011-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="a8011-104">\<configuration></span></span>  
<span data-ttu-id="a8011-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="a8011-105">\<system.diagnostics></span></span>  
<span data-ttu-id="a8011-106">\<trace></span><span class="sxs-lookup"><span data-stu-id="a8011-106">\<trace></span></span>  
<span data-ttu-id="a8011-107">\<listeners></span><span class="sxs-lookup"><span data-stu-id="a8011-107">\<listeners></span></span>  
<span data-ttu-id="a8011-108">\<add></span><span class="sxs-lookup"><span data-stu-id="a8011-108">\<add></span></span>  
<span data-ttu-id="a8011-109">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="a8011-109">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8011-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="a8011-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8011-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a8011-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a8011-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a8011-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8011-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a8011-113">Attributes</span></span>  
  
|<span data-ttu-id="a8011-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a8011-114">Attribute</span></span>|<span data-ttu-id="a8011-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a8011-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="a8011-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="a8011-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="a8011-117">Określa typ filtr, który powinien dziedziczyć <xref:System.Diagnostics.TraceFilter> klasy.</span><span class="sxs-lookup"><span data-stu-id="a8011-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="a8011-118">Można użyć w przestrzeni nazw, kwalifikowana nazwa typu, który odnosi się do typu <xref:System.Type.FullName%2A> właściwości lub można użyć w pełni kwalifikowana nazwa typu w tym informacje o zestawie, który odpowiada <xref:System.Type.AssemblyQualifiedName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a8011-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="a8011-119">Aby dowiedzieć się, w pełni kwalifikowanych nazw typów, zobacz [określanie w pełni kwalifikowanej nazwy typu](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="a8011-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="a8011-120">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a8011-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a8011-121">Ciąg przekazany do konstruktora dla klasy określony filtr.</span><span class="sxs-lookup"><span data-stu-id="a8011-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8011-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a8011-122">Child Elements</span></span>  
 <span data-ttu-id="a8011-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="a8011-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8011-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a8011-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a8011-125">Element</span><span class="sxs-lookup"><span data-stu-id="a8011-125">Element</span></span>|<span data-ttu-id="a8011-126">Opis</span><span class="sxs-lookup"><span data-stu-id="a8011-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a8011-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8011-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a8011-128">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a8011-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="a8011-129">Zawiera obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a8011-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="a8011-130">Zawiera obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów w postaci.</span><span class="sxs-lookup"><span data-stu-id="a8011-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="a8011-131">Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a8011-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="a8011-132">Dodaje odbiornik do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a8011-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8011-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a8011-133">Remarks</span></span>  
 <span data-ttu-id="a8011-134">`<filter>` Element musi być zawarty w `<add>` elementu dla odbiornika śledzenia, który określa typ odbiornika, nie tylko nazwy odbiornik zdefiniowane w [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="a8011-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="a8011-135">Jeśli odbiornik jest zdefiniowany w [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtr dla tego odbiornika musi być zdefiniowany w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="a8011-135">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="a8011-136">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a8011-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8011-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8011-137">Example</span></span>  
 <span data-ttu-id="a8011-138">Poniższy przykład pokazuje, jak używać `<filter>` elementu Dodawanie filtru do odbiornika `console` w `Listeners` kolekcji śledzenie, określając poziom zdarzenia filtru jako `Error`.</span><span class="sxs-lookup"><span data-stu-id="a8011-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a8011-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8011-139">See also</span></span>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="a8011-140">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="a8011-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
