---
title: <filter><add>Dla elementu for <listeners><source>
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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153519"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="d4832-102">\<filter>\<add>Dla elementu for \<listeners>\<source></span><span class="sxs-lookup"><span data-stu-id="d4832-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="d4832-103">Dodaje filtr do odbiornika w `Listeners` kolekcji dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d4832-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="d4832-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4832-104">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4832-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d4832-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d4832-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d4832-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4832-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d4832-107">Attributes</span></span>  
  
|<span data-ttu-id="d4832-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d4832-108">Attribute</span></span>|<span data-ttu-id="d4832-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d4832-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="d4832-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="d4832-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="d4832-111">Określa typ filtru, który powinien dziedziczyć po <xref:System.Diagnostics.TraceFilter> klasie.</span><span class="sxs-lookup"><span data-stu-id="d4832-111">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="d4832-112">Można użyć nazwy typu kwalifikowanej przestrzeni nazw, która odpowiada <xref:System.Type.FullName%2A> właściwości typu, lub można użyć w pełni kwalifikowanej nazwy typu, w tym informacji o zestawie, która odpowiada <xref:System.Type.AssemblyQualifiedName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d4832-112">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="d4832-113">Aby uzyskać informacje na temat w pełni kwalifikowanych nazw typów, zobacz [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="d4832-113">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="d4832-114">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d4832-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d4832-115">Ciąg przesłany do konstruktora dla określonej klasy filtru.</span><span class="sxs-lookup"><span data-stu-id="d4832-115">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4832-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d4832-116">Child Elements</span></span>  
 <span data-ttu-id="d4832-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="d4832-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4832-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d4832-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d4832-119">Element</span><span class="sxs-lookup"><span data-stu-id="d4832-119">Element</span></span>|<span data-ttu-id="d4832-120">Opis</span><span class="sxs-lookup"><span data-stu-id="d4832-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d4832-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d4832-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d4832-122">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d4832-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="d4832-123">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d4832-123">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="d4832-124">Określa źródło śledzenia, które inicjuje komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d4832-124">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="d4832-125">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty.</span><span class="sxs-lookup"><span data-stu-id="d4832-125">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="d4832-126">Odbiorniki kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="d4832-126">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="d4832-127">Dodaje odbiornik do `Listeners` kolekcji dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d4832-127">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4832-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4832-128">Remarks</span></span>  
 <span data-ttu-id="d4832-129">`<filter>`Element musi być zawarty w `<add>` elemencie dla odbiornika źródła śledzenia, który określa typ odbiornika, a nie tylko nazwę odbiornika zdefiniowanego w [\<sharedListeners>](sharedlisteners-element.md) .</span><span class="sxs-lookup"><span data-stu-id="d4832-129">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="d4832-130">Jeśli odbiornik jest zdefiniowany w [\<sharedListeners>](sharedlisteners-element.md) , filtr dla tego odbiornika musi być zdefiniowany w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="d4832-130">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="d4832-131">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d4832-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4832-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="d4832-132">Example</span></span>  
 <span data-ttu-id="d4832-133">Poniższy przykład pokazuje, jak za pomocą `<filter>` elementu dodać filtr do odbiornika `console` w `Listeners` kolekcji dla źródła śledzenia `myTraceSource` , określając poziom zdarzenia filtru jako `Error` .</span><span class="sxs-lookup"><span data-stu-id="d4832-133">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d4832-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4832-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="d4832-135">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="d4832-135">Trace and Debug Settings Schema</span></span>](index.md)
