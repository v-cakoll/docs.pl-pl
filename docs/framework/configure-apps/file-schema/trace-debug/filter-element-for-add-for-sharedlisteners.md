---
title: Element <filter> dla <add> <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: e04ecd773bd6aa7791858711edbd72128dc391ea
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088881"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="93dec-102">\<> filtru elementu \<dodać > \<</span><span class="sxs-lookup"><span data-stu-id="93dec-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="93dec-103">Dodaje filtr do odbiornika w kolekcji `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="93dec-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

<span data-ttu-id="93dec-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="93dec-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="93dec-105">&nbsp;&nbsp;[ **\<system. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="93dec-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="93dec-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sharedListeners >** ](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="93dec-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>\
<span data-ttu-id="93dec-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dodaj >** ](add-element-for-sharedlisteners.md)</span><span class="sxs-lookup"><span data-stu-id="93dec-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)</span></span>\
<span data-ttu-id="93dec-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<filtru >**</span><span class="sxs-lookup"><span data-stu-id="93dec-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="93dec-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="93dec-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93dec-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="93dec-110">Attributes and Elements</span></span>  
 <span data-ttu-id="93dec-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="93dec-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93dec-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="93dec-112">Attributes</span></span>  
  
|<span data-ttu-id="93dec-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="93dec-113">Attribute</span></span>|<span data-ttu-id="93dec-114">Opis</span><span class="sxs-lookup"><span data-stu-id="93dec-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93dec-115">**Wprowadź**</span><span class="sxs-lookup"><span data-stu-id="93dec-115">**type**</span></span>|<span data-ttu-id="93dec-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="93dec-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="93dec-117">Określa typ filtru.</span><span class="sxs-lookup"><span data-stu-id="93dec-117">Specifies the type of the filter.</span></span> <span data-ttu-id="93dec-118">Można użyć tylko pełnej nazwy typu (w formacie właściwości <xref:System.Type.FullName%2A?displayProperty=nameWithType>) lub użyć w pełni kwalifikowanej nazwy typu, w tym informacji o zestawie (w formacie właściwości <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="93dec-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="93dec-119">Aby uzyskać informacje na temat tworzenia w pełni kwalifikowanej nazwy typu, zobacz [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="93dec-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="93dec-120">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="93dec-120">**initializeData**</span></span>|<span data-ttu-id="93dec-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="93dec-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="93dec-122">Ciąg przesłany do konstruktora dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="93dec-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93dec-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="93dec-123">Child Elements</span></span>  
 <span data-ttu-id="93dec-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="93dec-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93dec-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="93dec-125">Parent Elements</span></span>  
  
|<span data-ttu-id="93dec-126">Element</span><span class="sxs-lookup"><span data-stu-id="93dec-126">Element</span></span>|<span data-ttu-id="93dec-127">Opis</span><span class="sxs-lookup"><span data-stu-id="93dec-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="93dec-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="93dec-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="93dec-129">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="93dec-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="93dec-130">Kolekcja detektorów, które mogą odwoływać się do każdego elementu źródłowego lub śledzenia.</span><span class="sxs-lookup"><span data-stu-id="93dec-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="93dec-131">Dodaje odbiornik do kolekcji **sharedListeners** .</span><span class="sxs-lookup"><span data-stu-id="93dec-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93dec-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93dec-132">Remarks</span></span>  
 <span data-ttu-id="93dec-133">Jeśli odbiornik jest zdefiniowany w `<add>` elementu `<sharedListeners>`, filtr dla tego odbiornika powinien być zdefiniowany w `<filter>` elementu, który jest elementem podrzędnym elementu `<add>`.</span><span class="sxs-lookup"><span data-stu-id="93dec-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="93dec-134">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="93dec-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93dec-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="93dec-135">Example</span></span>  
 <span data-ttu-id="93dec-136">Poniższy przykład pokazuje, jak użyć elementu `<filter>`, aby dodać filtr do `console` odbiornika śledzenia w kolekcji `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="93dec-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"   
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"   
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="93dec-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93dec-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="93dec-138">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="93dec-138">Trace and Debug Settings Schema</span></span>](index.md)
