---
title: <filter>Element <add> dla <listeners> dla<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 0cb668782de263d5f784691f46cb8b74541d942b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153519"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="a5d21-102">\<filtr> Element \<dodawania> dla \<> dla> \<źródłowych</span><span class="sxs-lookup"><span data-stu-id="a5d21-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="a5d21-103">Dodaje filtr do odbiornika `Listeners` w kolekcji dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a5d21-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="a5d21-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a5d21-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a5d21-105">&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="a5d21-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="a5d21-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<źródeł>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="a5d21-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="a5d21-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>źródłowe**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="a5d21-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="a5d21-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<słuchacze>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="a5d21-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="a5d21-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dodaj>**](add-element-for-listeners-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="a5d21-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)</span></span>\
<span data-ttu-id="a5d21-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>filtra**</span><span class="sxs-lookup"><span data-stu-id="a5d21-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a5d21-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5d21-111">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5d21-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a5d21-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a5d21-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a5d21-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5d21-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a5d21-114">Attributes</span></span>  
  
|<span data-ttu-id="a5d21-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a5d21-115">Attribute</span></span>|<span data-ttu-id="a5d21-116">Opis</span><span class="sxs-lookup"><span data-stu-id="a5d21-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="a5d21-117">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="a5d21-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="a5d21-118">Określa typ filtru, który powinien dziedziczyć z <xref:System.Diagnostics.TraceFilter> klasy.</span><span class="sxs-lookup"><span data-stu-id="a5d21-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="a5d21-119">Można użyć nazwy kwalifikowanej obszaru nazw typu, która odpowiada <xref:System.Type.FullName%2A> właściwości typu, lub można użyć w pełni kwalifikowanej nazwy typu, <xref:System.Type.AssemblyQualifiedName%2A> w tym informacji o zestawie, która odpowiada właściwości.</span><span class="sxs-lookup"><span data-stu-id="a5d21-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="a5d21-120">Aby uzyskać informacje o w pełni kwalifikowanych nazwach typów, zobacz [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="a5d21-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="a5d21-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a5d21-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a5d21-122">Ciąg przekazany do konstruktora dla określonej klasy filtru.</span><span class="sxs-lookup"><span data-stu-id="a5d21-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5d21-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a5d21-123">Child Elements</span></span>  
 <span data-ttu-id="a5d21-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="a5d21-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5d21-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a5d21-125">Parent Elements</span></span>  
  
|<span data-ttu-id="a5d21-126">Element</span><span class="sxs-lookup"><span data-stu-id="a5d21-126">Element</span></span>|<span data-ttu-id="a5d21-127">Opis</span><span class="sxs-lookup"><span data-stu-id="a5d21-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a5d21-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a5d21-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a5d21-129">Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a5d21-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="a5d21-130">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a5d21-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="a5d21-131">Określa źródło śledzenia, które inicjuje śledzenie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a5d21-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="a5d21-132">Zawiera odbiorniki, które zbierają, przechowują i rozsyłają wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a5d21-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="a5d21-133">Detektory kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a5d21-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="a5d21-134">Dodaje odbiornik do `Listeners` kolekcji dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a5d21-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5d21-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5d21-135">Remarks</span></span>  
 <span data-ttu-id="a5d21-136">Element `<filter>` musi być zawarty `<add>` w elemencie dla odbiornika źródła śledzenia, który określa typ odbiornika, a nie tylko nazwę odbiornika zdefiniowaną [ \<w sharedListeners>](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="a5d21-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="a5d21-137">Jeśli odbiornik jest zdefiniowany w [ \<sharedListeners>, ](sharedlisteners-element.md)filtr dla tego odbiornika musi być zdefiniowany w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="a5d21-137">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="a5d21-138">Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a5d21-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5d21-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5d21-139">Example</span></span>  
 <span data-ttu-id="a5d21-140">W poniższym przykładzie `<filter>` pokazano, jak użyć elementu, `console` aby `Listeners` dodać filtr `myTraceSource`do odbiornika w kolekcji dla źródła śledzenia, określając poziom zdarzenia filtru jako `Error`.</span><span class="sxs-lookup"><span data-stu-id="a5d21-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a5d21-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5d21-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="a5d21-142">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="a5d21-142">Trace and Debug Settings Schema</span></span>](index.md)
