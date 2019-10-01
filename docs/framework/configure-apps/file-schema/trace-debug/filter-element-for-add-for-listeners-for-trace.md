---
title: Element <filter> dla <add> dla <listeners> dla <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: f6b1ec99c5aab8e85df7f1920aca32f49a5be066
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699365"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="894db-102">\<filter > elementu \<add > dla @no__t 2listeners > dla \<trace ></span><span class="sxs-lookup"><span data-stu-id="894db-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="894db-103">Dodaje filtr do odbiornika w kolekcji `Listeners` w celu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="894db-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
[<span data-ttu-id="894db-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="894db-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="894db-105">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="894db-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="894db-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="894db-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="894db-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="894db-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>  
<span data-ttu-id="894db-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0add >** ](add-element-for-listeners-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="894db-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)</span></span>  
<span data-ttu-id="894db-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 **&nbsp;1filter >**</span><span class="sxs-lookup"><span data-stu-id="894db-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="894db-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="894db-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="894db-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="894db-111">Attributes and Elements</span></span>  
 <span data-ttu-id="894db-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="894db-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="894db-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="894db-113">Attributes</span></span>  
  
|<span data-ttu-id="894db-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="894db-114">Attribute</span></span>|<span data-ttu-id="894db-115">Opis</span><span class="sxs-lookup"><span data-stu-id="894db-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="894db-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="894db-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="894db-117">Określa typ filtru, który powinien dziedziczyć z klasy <xref:System.Diagnostics.TraceFilter>.</span><span class="sxs-lookup"><span data-stu-id="894db-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="894db-118">Można użyć kwalifikowanej przestrzeni nazw typu, który odpowiada właściwości <xref:System.Type.FullName%2A>, lub można użyć w pełni kwalifikowanej nazwy typu, w tym informacji o zestawie, która odpowiada właściwości <xref:System.Type.AssemblyQualifiedName%2A>.</span><span class="sxs-lookup"><span data-stu-id="894db-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="894db-119">Aby uzyskać informacje na temat w pełni kwalifikowanych nazw typów, zobacz [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="894db-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="894db-120">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="894db-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="894db-121">Ciąg przesłany do konstruktora dla określonej klasy filtru.</span><span class="sxs-lookup"><span data-stu-id="894db-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="894db-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="894db-122">Child Elements</span></span>  
 <span data-ttu-id="894db-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="894db-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="894db-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="894db-124">Parent Elements</span></span>  
  
|<span data-ttu-id="894db-125">Element</span><span class="sxs-lookup"><span data-stu-id="894db-125">Element</span></span>|<span data-ttu-id="894db-126">Opis</span><span class="sxs-lookup"><span data-stu-id="894db-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="894db-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="894db-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="894db-128">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="894db-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="894db-129">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="894db-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="894db-130">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty.</span><span class="sxs-lookup"><span data-stu-id="894db-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="894db-131">Odbiorniki kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="894db-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="894db-132">Dodaje odbiornik do kolekcji `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="894db-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="894db-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="894db-133">Remarks</span></span>  
 <span data-ttu-id="894db-134">Element `<filter>` musi być zawarty w elemencie `<add>` dla odbiornika śledzenia, który określa typ odbiornika, a nie tylko nazwę odbiornika zdefiniowaną w [> \<sharedListeners](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="894db-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="894db-135">Jeśli odbiornik jest zdefiniowany w [@no__t 1sharedListeners >](sharedlisteners-element.md), filtr dla tego odbiornika musi być zdefiniowany w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="894db-135">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="894db-136">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="894db-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="894db-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="894db-137">Example</span></span>  
 <span data-ttu-id="894db-138">Poniższy przykład pokazuje, jak za pomocą elementu `<filter>` dodać filtr do odbiornika `console` w kolekcji `Listeners` w celu śledzenia, określając poziom zdarzeń filtru jako `Error`.</span><span class="sxs-lookup"><span data-stu-id="894db-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="894db-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="894db-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="894db-140">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="894db-140">Trace and Debug Settings Schema</span></span>](index.md)
