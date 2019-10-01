---
title: Element <filter> dla <add> dla <listeners> dla <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: ec288685f47c8a35e2371c31d359b604a4967196
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697165"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="cac94-102">\<filter > elementu \<add > dla @no__t 2listeners > dla \<source ></span><span class="sxs-lookup"><span data-stu-id="cac94-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="cac94-103">Dodaje filtr do odbiornika w kolekcji `Listeners` dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cac94-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
[<span data-ttu-id="cac94-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="cac94-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="cac94-105">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="cac94-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="cac94-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="cac94-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="cac94-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<source >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="cac94-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="cac94-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0listeners >** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="cac94-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>  
<span data-ttu-id="cac94-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9[ **&nbsp;2add >** ](add-element-for-listeners-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="cac94-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)</span></span>  
<span data-ttu-id="cac94-110">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 @ no__t-10 @ no__t-11 **&nbsp;3filter >**</span><span class="sxs-lookup"><span data-stu-id="cac94-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cac94-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="cac94-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cac94-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cac94-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cac94-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cac94-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cac94-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cac94-114">Attributes</span></span>  
  
|<span data-ttu-id="cac94-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cac94-115">Attribute</span></span>|<span data-ttu-id="cac94-116">Opis</span><span class="sxs-lookup"><span data-stu-id="cac94-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="cac94-117">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="cac94-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="cac94-118">Określa typ filtru, który powinien dziedziczyć z klasy <xref:System.Diagnostics.TraceFilter>.</span><span class="sxs-lookup"><span data-stu-id="cac94-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="cac94-119">Można użyć kwalifikowanej przestrzeni nazw typu, który odpowiada właściwości <xref:System.Type.FullName%2A>, lub można użyć w pełni kwalifikowanej nazwy typu, w tym informacji o zestawie, która odpowiada właściwości <xref:System.Type.AssemblyQualifiedName%2A>.</span><span class="sxs-lookup"><span data-stu-id="cac94-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="cac94-120">Aby uzyskać informacje na temat w pełni kwalifikowanych nazw typów, zobacz [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="cac94-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="cac94-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cac94-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="cac94-122">Ciąg przesłany do konstruktora dla określonej klasy filtru.</span><span class="sxs-lookup"><span data-stu-id="cac94-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cac94-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cac94-123">Child Elements</span></span>  
 <span data-ttu-id="cac94-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="cac94-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cac94-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cac94-125">Parent Elements</span></span>  
  
|<span data-ttu-id="cac94-126">Element</span><span class="sxs-lookup"><span data-stu-id="cac94-126">Element</span></span>|<span data-ttu-id="cac94-127">Opis</span><span class="sxs-lookup"><span data-stu-id="cac94-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cac94-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cac94-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="cac94-129">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cac94-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="cac94-130">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cac94-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="cac94-131">Określa źródło śledzenia, które inicjuje komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cac94-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="cac94-132">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty.</span><span class="sxs-lookup"><span data-stu-id="cac94-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="cac94-133">Odbiorniki kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="cac94-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="cac94-134">Dodaje odbiornik do kolekcji `Listeners` dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cac94-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cac94-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cac94-135">Remarks</span></span>  
 <span data-ttu-id="cac94-136">Element `<filter>` musi być zawarty w elemencie `<add>` dla odbiornika źródła śledzenia, który określa typ odbiornika, a nie tylko nazwę odbiornika zdefiniowaną w [> \<sharedListeners](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="cac94-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="cac94-137">Jeśli odbiornik jest zdefiniowany w [@no__t 1sharedListeners >](sharedlisteners-element.md), filtr dla tego odbiornika musi być zdefiniowany w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="cac94-137">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="cac94-138">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cac94-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cac94-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="cac94-139">Example</span></span>  
 <span data-ttu-id="cac94-140">W poniższym przykładzie pokazano, jak za pomocą elementu `<filter>` dodać filtr do odbiornika `console` w kolekcji `Listeners` dla źródła śledzenia `myTraceSource`, określając poziom zdarzeń filtru jako `Error`.</span><span class="sxs-lookup"><span data-stu-id="cac94-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cac94-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cac94-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="cac94-142">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="cac94-142">Trace and Debug Settings Schema</span></span>](index.md)
