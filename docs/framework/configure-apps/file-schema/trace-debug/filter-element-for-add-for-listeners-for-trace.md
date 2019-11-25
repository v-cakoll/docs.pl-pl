---
title: Element <filter> dla <add> <listeners> dla <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: cc970240ac07ad3ea72be50d1e9af452da638fa9
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088890"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="70d8a-102">\<filtru > elementu \<Dodaj > dla odbiorników \<> śledzenia \<</span><span class="sxs-lookup"><span data-stu-id="70d8a-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="70d8a-103">Dodaje filtr do odbiornika w kolekcji `Listeners` do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="70d8a-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

<span data-ttu-id="70d8a-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="70d8a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="70d8a-105">&nbsp;&nbsp;[ **\<system. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="70d8a-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="70d8a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Trace**](trace-element.md) ></span><span class="sxs-lookup"><span data-stu-id="70d8a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="70d8a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**odbiorników**](listeners-element-for-trace.md) ></span><span class="sxs-lookup"><span data-stu-id="70d8a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="70d8a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dodaj >** ](add-element-for-listeners-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="70d8a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)</span></span>\
<span data-ttu-id="70d8a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**filter >**</span><span class="sxs-lookup"><span data-stu-id="70d8a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="70d8a-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="70d8a-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70d8a-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="70d8a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="70d8a-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="70d8a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70d8a-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="70d8a-113">Attributes</span></span>  
  
|<span data-ttu-id="70d8a-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="70d8a-114">Attribute</span></span>|<span data-ttu-id="70d8a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="70d8a-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="70d8a-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="70d8a-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="70d8a-117">Określa typ filtru, który powinien dziedziczyć z klasy <xref:System.Diagnostics.TraceFilter>.</span><span class="sxs-lookup"><span data-stu-id="70d8a-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="70d8a-118">Można użyć kwalifikowanej przestrzeni nazw typu, który odpowiada właściwości <xref:System.Type.FullName%2A> typu, lub można użyć w pełni kwalifikowanej nazwy typu, w tym informacji o zestawie, która odpowiada właściwości <xref:System.Type.AssemblyQualifiedName%2A>.</span><span class="sxs-lookup"><span data-stu-id="70d8a-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="70d8a-119">Aby uzyskać informacje na temat w pełni kwalifikowanych nazw typów, zobacz [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="70d8a-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="70d8a-120">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="70d8a-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="70d8a-121">Ciąg przesłany do konstruktora dla określonej klasy filtru.</span><span class="sxs-lookup"><span data-stu-id="70d8a-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70d8a-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="70d8a-122">Child Elements</span></span>  
 <span data-ttu-id="70d8a-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="70d8a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70d8a-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="70d8a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="70d8a-125">Element</span><span class="sxs-lookup"><span data-stu-id="70d8a-125">Element</span></span>|<span data-ttu-id="70d8a-126">Opis</span><span class="sxs-lookup"><span data-stu-id="70d8a-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="70d8a-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70d8a-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="70d8a-128">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="70d8a-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="70d8a-129">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="70d8a-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="70d8a-130">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty.</span><span class="sxs-lookup"><span data-stu-id="70d8a-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="70d8a-131">Odbiorniki kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="70d8a-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="70d8a-132">Dodaje odbiornik do kolekcji `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="70d8a-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70d8a-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70d8a-133">Remarks</span></span>  
 <span data-ttu-id="70d8a-134">Element `<filter>` musi być zawarty w elemencie `<add>` dla odbiornika śledzenia, który określa typ odbiornika, a nie tylko nazwę odbiornika zdefiniowanego w [\<> sharedListeners](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="70d8a-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="70d8a-135">Jeśli odbiornik jest zdefiniowany w [\<sharedListeners >](sharedlisteners-element.md), filtr dla tego odbiornika musi być zdefiniowany w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="70d8a-135">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="70d8a-136">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70d8a-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70d8a-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="70d8a-137">Example</span></span>  
 <span data-ttu-id="70d8a-138">Poniższy przykład pokazuje, jak używać elementu `<filter>`, aby dodać filtr do `console` odbiornika w kolekcji `Listeners` na potrzeby śledzenia, określając poziom zdarzeń filtru jako `Error`.</span><span class="sxs-lookup"><span data-stu-id="70d8a-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70d8a-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70d8a-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="70d8a-140">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="70d8a-140">Trace and Debug Settings Schema</span></span>](index.md)
