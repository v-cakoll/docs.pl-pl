---
title: <filter> Element <add> dla <listeners> dla <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: 5961125e1b8d0d0f5711f8b942b68ba71d61888f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143432"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="0409b-102">\<Filtr >, Element dla \<Dodaj > dla \<odbiorników > dla \<śledzenia ></span><span class="sxs-lookup"><span data-stu-id="0409b-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="0409b-103">Dodaje filtr do odbiornika w `Listeners` kolekcji dla śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0409b-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
 <span data-ttu-id="0409b-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="0409b-104">\<configuration></span></span>  
<span data-ttu-id="0409b-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="0409b-105">\<system.diagnostics></span></span>  
<span data-ttu-id="0409b-106">\<trace></span><span class="sxs-lookup"><span data-stu-id="0409b-106">\<trace></span></span>  
<span data-ttu-id="0409b-107">\<listeners></span><span class="sxs-lookup"><span data-stu-id="0409b-107">\<listeners></span></span>  
<span data-ttu-id="0409b-108">\<add></span><span class="sxs-lookup"><span data-stu-id="0409b-108">\<add></span></span>  
<span data-ttu-id="0409b-109">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="0409b-109">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0409b-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="0409b-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0409b-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0409b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0409b-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0409b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0409b-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0409b-113">Attributes</span></span>  
  
|<span data-ttu-id="0409b-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0409b-114">Attribute</span></span>|<span data-ttu-id="0409b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="0409b-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="0409b-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="0409b-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="0409b-117">Określa typ filtr, który powinien dziedziczyć <xref:System.Diagnostics.TraceFilter> klasy.</span><span class="sxs-lookup"><span data-stu-id="0409b-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="0409b-118">Można użyć w przestrzeni nazw, kwalifikowana nazwa typu, który odnosi się do typu <xref:System.Type.FullName%2A> właściwości lub można użyć w pełni kwalifikowana nazwa typu w tym informacje o zestawie, który odpowiada <xref:System.Type.AssemblyQualifiedName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0409b-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="0409b-119">Aby dowiedzieć się, w pełni kwalifikowanych nazw typów, zobacz [określanie w pełni kwalifikowanej nazwy typu](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="0409b-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="0409b-120">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0409b-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0409b-121">Ciąg przekazany do konstruktora dla klasy określony filtr.</span><span class="sxs-lookup"><span data-stu-id="0409b-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0409b-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0409b-122">Child Elements</span></span>  
 <span data-ttu-id="0409b-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="0409b-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0409b-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0409b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0409b-125">Element</span><span class="sxs-lookup"><span data-stu-id="0409b-125">Element</span></span>|<span data-ttu-id="0409b-126">Opis</span><span class="sxs-lookup"><span data-stu-id="0409b-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0409b-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0409b-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0409b-128">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0409b-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="0409b-129">Zawiera obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0409b-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="0409b-130">Zawiera obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów w postaci.</span><span class="sxs-lookup"><span data-stu-id="0409b-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="0409b-131">Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="0409b-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="0409b-132">Dodaje odbiornik do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0409b-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0409b-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0409b-133">Remarks</span></span>  
 <span data-ttu-id="0409b-134">`<filter>` Element musi być zawarty w `<add>` elementu dla odbiornika śledzenia, który określa typ odbiornika, nie tylko nazwy odbiornik zdefiniowane w [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="0409b-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="0409b-135">Jeśli odbiornik jest zdefiniowany w [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtr dla tego odbiornika musi być zdefiniowany w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="0409b-135">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="0409b-136">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0409b-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0409b-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="0409b-137">Example</span></span>  
 <span data-ttu-id="0409b-138">Poniższy przykład pokazuje, jak używać `<filter>` elementu Dodawanie filtru do odbiornika `console` w `Listeners` kolekcji śledzenie, określając poziom zdarzenia filtru jako `Error`.</span><span class="sxs-lookup"><span data-stu-id="0409b-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0409b-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0409b-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="0409b-140">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="0409b-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
