---
title: <filter>Element <add> dla <listeners> dla<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: b6c2c2bf7fe953a75f9d8129039ef33b4d8a3f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153469"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="0e481-102">\<filtr> Element dodawania \<> dla \<słuchaczy>> \<śledzenia</span><span class="sxs-lookup"><span data-stu-id="0e481-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="0e481-103">Dodaje filtr do odbiornika `Listeners` w kolekcji dla śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0e481-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

<span data-ttu-id="0e481-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0e481-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0e481-105">&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="0e481-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="0e481-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>śledzenia**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="0e481-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="0e481-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<słuchacze>**](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="0e481-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="0e481-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dodaj>**](add-element-for-listeners-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="0e481-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)</span></span>\
<span data-ttu-id="0e481-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>filtra**</span><span class="sxs-lookup"><span data-stu-id="0e481-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0e481-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e481-110">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e481-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0e481-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0e481-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0e481-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e481-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0e481-113">Attributes</span></span>  
  
|<span data-ttu-id="0e481-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0e481-114">Attribute</span></span>|<span data-ttu-id="0e481-115">Opis</span><span class="sxs-lookup"><span data-stu-id="0e481-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="0e481-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="0e481-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="0e481-117">Określa typ filtru, który powinien dziedziczyć z <xref:System.Diagnostics.TraceFilter> klasy.</span><span class="sxs-lookup"><span data-stu-id="0e481-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="0e481-118">Można użyć nazwy kwalifikowanej obszaru nazw typu, która odpowiada <xref:System.Type.FullName%2A> właściwości typu, lub można użyć w pełni kwalifikowanej nazwy typu, <xref:System.Type.AssemblyQualifiedName%2A> w tym informacji o zestawie, która odpowiada właściwości.</span><span class="sxs-lookup"><span data-stu-id="0e481-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="0e481-119">Aby uzyskać informacje o w pełni kwalifikowanych nazwach typów, zobacz [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="0e481-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="0e481-120">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0e481-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0e481-121">Ciąg przekazany do konstruktora dla określonej klasy filtru.</span><span class="sxs-lookup"><span data-stu-id="0e481-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e481-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0e481-122">Child Elements</span></span>  
 <span data-ttu-id="0e481-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="0e481-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e481-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0e481-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0e481-125">Element</span><span class="sxs-lookup"><span data-stu-id="0e481-125">Element</span></span>|<span data-ttu-id="0e481-126">Opis</span><span class="sxs-lookup"><span data-stu-id="0e481-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0e481-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0e481-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0e481-128">Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0e481-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="0e481-129">Zawiera odbiorniki, które zbierają, przechowują i trasy śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0e481-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="0e481-130">Zawiera odbiorniki, które zbierają, przechowują i rozsyłają wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0e481-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="0e481-131">Detektory kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="0e481-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="0e481-132">Dodaje odbiornik do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0e481-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e481-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e481-133">Remarks</span></span>  
 <span data-ttu-id="0e481-134">Element `<filter>` musi być zawarty `<add>` w elemencie dla odbiornika śledzenia, który określa typ odbiornika, a nie tylko nazwę odbiornika zdefiniowaną [ \<w sharedListeners>](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="0e481-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="0e481-135">Jeśli odbiornik jest zdefiniowany w [ \<sharedListeners>, ](sharedlisteners-element.md)filtr dla tego odbiornika musi być zdefiniowany w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="0e481-135">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="0e481-136">Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0e481-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e481-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e481-137">Example</span></span>  
 <span data-ttu-id="0e481-138">W poniższym przykładzie `<filter>` pokazano, jak użyć elementu, `console` aby `Listeners` dodać filtr do odbiornika w `Error`kolekcji do śledzenia, określając poziom zdarzenia filtru jako .</span><span class="sxs-lookup"><span data-stu-id="0e481-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0e481-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e481-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="0e481-140">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="0e481-140">Trace and Debug Settings Schema</span></span>](index.md)
