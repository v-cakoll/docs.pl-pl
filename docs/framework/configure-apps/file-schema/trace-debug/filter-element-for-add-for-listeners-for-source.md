---
title: <filter> Element <add> dla <listeners> dla <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 3abfd0bdd40f98a9e4774677fc2cd5068c14333f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186735"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="54935-102">\<Filtr >, Element dla \<Dodaj > dla \<odbiorników > dla \<źródła ></span><span class="sxs-lookup"><span data-stu-id="54935-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="54935-103">Dodaje filtr do odbiornika w `Listeners` kolekcję dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="54935-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="54935-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="54935-104">\<configuration></span></span>  
<span data-ttu-id="54935-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="54935-105">\<system.diagnostics></span></span>  
<span data-ttu-id="54935-106">\<źródła ></span><span class="sxs-lookup"><span data-stu-id="54935-106">\<sources></span></span>  
<span data-ttu-id="54935-107">\<source></span><span class="sxs-lookup"><span data-stu-id="54935-107">\<source></span></span>  
<span data-ttu-id="54935-108">\<listeners></span><span class="sxs-lookup"><span data-stu-id="54935-108">\<listeners></span></span>  
<span data-ttu-id="54935-109">\<add></span><span class="sxs-lookup"><span data-stu-id="54935-109">\<add></span></span>  
<span data-ttu-id="54935-110">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="54935-110">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54935-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="54935-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54935-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="54935-112">Attributes and Elements</span></span>  
 <span data-ttu-id="54935-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="54935-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54935-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="54935-114">Attributes</span></span>  
  
|<span data-ttu-id="54935-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="54935-115">Attribute</span></span>|<span data-ttu-id="54935-116">Opis</span><span class="sxs-lookup"><span data-stu-id="54935-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="54935-117">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="54935-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="54935-118">Określa typ filtr, który powinien dziedziczyć <xref:System.Diagnostics.TraceFilter> klasy.</span><span class="sxs-lookup"><span data-stu-id="54935-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="54935-119">Można użyć w przestrzeni nazw, kwalifikowana nazwa typu, który odnosi się do typu <xref:System.Type.FullName%2A> właściwości lub można użyć w pełni kwalifikowana nazwa typu w tym informacje o zestawie, który odpowiada <xref:System.Type.AssemblyQualifiedName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="54935-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="54935-120">Aby dowiedzieć się, w pełni kwalifikowanych nazw typów, zobacz [określanie w pełni kwalifikowanej nazwy typu](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="54935-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="54935-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="54935-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="54935-122">Ciąg przekazany do konstruktora dla klasy określony filtr.</span><span class="sxs-lookup"><span data-stu-id="54935-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54935-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="54935-123">Child Elements</span></span>  
 <span data-ttu-id="54935-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="54935-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54935-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="54935-125">Parent Elements</span></span>  
  
|<span data-ttu-id="54935-126">Element</span><span class="sxs-lookup"><span data-stu-id="54935-126">Element</span></span>|<span data-ttu-id="54935-127">Opis</span><span class="sxs-lookup"><span data-stu-id="54935-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="54935-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54935-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="54935-129">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="54935-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="54935-130">Zawiera źródła śledzenia, które inicjują komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="54935-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="54935-131">Określa źródło śledzenia, który inicjuje komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="54935-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="54935-132">Zawiera obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów w postaci.</span><span class="sxs-lookup"><span data-stu-id="54935-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="54935-133">Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="54935-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="54935-134">Dodaje odbiornik do `Listeners` kolekcję dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="54935-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54935-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54935-135">Remarks</span></span>  
 <span data-ttu-id="54935-136">`<filter>` Element musi być zawarty w `<add>` elementu dla odbiornika źródła śledzenia, który określa typ odbiornika, nie tylko nazwy odbiornik zdefiniowane w [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="54935-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="54935-137">Jeśli odbiornik jest zdefiniowany w [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtr dla tego odbiornika musi być zdefiniowany w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="54935-137">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="54935-138">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="54935-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54935-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="54935-139">Example</span></span>  
 <span data-ttu-id="54935-140">Poniższy przykład pokazuje, jak używać `<filter>` elementu Dodawanie filtru do odbiornika `console` w `Listeners` kolekcji dla źródła śledzenia `myTraceSource`, określając poziom zdarzenia filtru jako `Error`.</span><span class="sxs-lookup"><span data-stu-id="54935-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54935-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54935-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="54935-142">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="54935-142">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
