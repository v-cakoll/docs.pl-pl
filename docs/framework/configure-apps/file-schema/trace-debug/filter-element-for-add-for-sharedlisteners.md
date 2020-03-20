---
title: <filter>Element <add> dla<sharedListeners>
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
ms.openlocfilehash: 6fb52cdfa5792ab6059b60d8dbb91c107cd666ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153456"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="1604a-102">\<filtr> Element \<dodawania> \<dla sharedListeners></span><span class="sxs-lookup"><span data-stu-id="1604a-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="1604a-103">Dodaje filtr do odbiornika `sharedListeners` w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1604a-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

<span data-ttu-id="1604a-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1604a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1604a-105">&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="1604a-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="1604a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="1604a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>\
<span data-ttu-id="1604a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dodaj>**](add-element-for-sharedlisteners.md)</span><span class="sxs-lookup"><span data-stu-id="1604a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)</span></span>\
<span data-ttu-id="1604a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>filtra**</span><span class="sxs-lookup"><span data-stu-id="1604a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1604a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="1604a-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1604a-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1604a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1604a-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1604a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1604a-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1604a-112">Attributes</span></span>  
  
|<span data-ttu-id="1604a-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1604a-113">Attribute</span></span>|<span data-ttu-id="1604a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1604a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1604a-115">**Typu**</span><span class="sxs-lookup"><span data-stu-id="1604a-115">**type**</span></span>|<span data-ttu-id="1604a-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1604a-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="1604a-117">Określa typ filtru.</span><span class="sxs-lookup"><span data-stu-id="1604a-117">Specifies the type of the filter.</span></span> <span data-ttu-id="1604a-118">Można użyć tylko pełnej nazwy typu (w <xref:System.Type.FullName%2A?displayProperty=nameWithType> formacie właściwości) lub można użyć w pełni kwalifikowanej nazwy typu, w tym informacji o zestawie (w formacie <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> właściwości).</span><span class="sxs-lookup"><span data-stu-id="1604a-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="1604a-119">Aby uzyskać informacje na temat tworzenia w pełni kwalifikowanej nazwy typu, zobacz [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="1604a-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="1604a-120">**Initializedata**</span><span class="sxs-lookup"><span data-stu-id="1604a-120">**initializeData**</span></span>|<span data-ttu-id="1604a-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="1604a-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="1604a-122">Ciąg przekazany do konstruktora dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="1604a-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1604a-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1604a-123">Child Elements</span></span>  
 <span data-ttu-id="1604a-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="1604a-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1604a-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1604a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="1604a-126">Element</span><span class="sxs-lookup"><span data-stu-id="1604a-126">Element</span></span>|<span data-ttu-id="1604a-127">Opis</span><span class="sxs-lookup"><span data-stu-id="1604a-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1604a-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1604a-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="1604a-129">Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1604a-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="1604a-130">Kolekcja odbiorników, do których można odwoływać się do dowolnego źródła lub elementu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1604a-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="1604a-131">Dodaje odbiornik do **sharedListeners** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1604a-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1604a-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1604a-132">Remarks</span></span>  
 <span data-ttu-id="1604a-133">Jeśli odbiornik jest zdefiniowany `<add>` w `<sharedListeners>` elemencie elementu, filtr dla tego `<filter>` odbiornika powinny być `<add>` zdefiniowane w elemencie, który jest elementem podrzędnym elementu.</span><span class="sxs-lookup"><span data-stu-id="1604a-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="1604a-134">Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1604a-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1604a-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="1604a-135">Example</span></span>  
 <span data-ttu-id="1604a-136">W poniższym przykładzie `<filter>` pokazano, jak użyć elementu, `console` aby `sharedListeners` dodać filtr do odbiornika śledzenia w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1604a-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1604a-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1604a-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="1604a-138">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="1604a-138">Trace and Debug Settings Schema</span></span>](index.md)
