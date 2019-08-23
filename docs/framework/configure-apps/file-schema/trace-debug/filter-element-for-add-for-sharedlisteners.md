---
title: <filter>Element dla <add> elementu<sharedListeners>
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
ms.openlocfilehash: 571a3add232f3e4f9747040dc104b85e8cc3085e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920511"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="30d63-102">\<Filtr > elementu do \<dodania > dla \<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="30d63-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="30d63-103">Dodaje filtr do odbiornika w `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="30d63-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  
  
 <span data-ttu-id="30d63-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="30d63-104">\<configuration></span></span>  
<span data-ttu-id="30d63-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="30d63-105">\<system.diagnostics></span></span>  
<span data-ttu-id="30d63-106">\<sharedListeners, element ></span><span class="sxs-lookup"><span data-stu-id="30d63-106">\<sharedListeners> Element</span></span>  
<span data-ttu-id="30d63-107">\<add></span><span class="sxs-lookup"><span data-stu-id="30d63-107">\<add></span></span>  
<span data-ttu-id="30d63-108">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="30d63-108">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30d63-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="30d63-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30d63-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="30d63-110">Attributes and Elements</span></span>  
 <span data-ttu-id="30d63-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="30d63-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30d63-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="30d63-112">Attributes</span></span>  
  
|<span data-ttu-id="30d63-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="30d63-113">Attribute</span></span>|<span data-ttu-id="30d63-114">Opis</span><span class="sxs-lookup"><span data-stu-id="30d63-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30d63-115">**type**</span><span class="sxs-lookup"><span data-stu-id="30d63-115">**type**</span></span>|<span data-ttu-id="30d63-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="30d63-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="30d63-117">Określa typ filtru.</span><span class="sxs-lookup"><span data-stu-id="30d63-117">Specifies the type of the filter.</span></span> <span data-ttu-id="30d63-118">Można użyć tylko pełnej nazwy typu (w formacie <xref:System.Type.FullName%2A?displayProperty=nameWithType> właściwości) lub użyć w pełni kwalifikowanej nazwy typu, w tym informacji o zestawie (w formacie <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> właściwości).</span><span class="sxs-lookup"><span data-stu-id="30d63-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="30d63-119">Aby uzyskać informacje na temat tworzenia w pełni kwalifikowanej nazwy typu, zobacz [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="30d63-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="30d63-120">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="30d63-120">**initializeData**</span></span>|<span data-ttu-id="30d63-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="30d63-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="30d63-122">Ciąg przesłany do konstruktora dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="30d63-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30d63-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="30d63-123">Child Elements</span></span>  
 <span data-ttu-id="30d63-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="30d63-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30d63-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="30d63-125">Parent Elements</span></span>  
  
|<span data-ttu-id="30d63-126">Element</span><span class="sxs-lookup"><span data-stu-id="30d63-126">Element</span></span>|<span data-ttu-id="30d63-127">Opis</span><span class="sxs-lookup"><span data-stu-id="30d63-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="30d63-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="30d63-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="30d63-129">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="30d63-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="30d63-130">Kolekcja detektorów, które mogą odwoływać się do każdego elementu źródłowego lub śledzenia.</span><span class="sxs-lookup"><span data-stu-id="30d63-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="30d63-131">Dodaje odbiornik do kolekcji **sharedListeners** .</span><span class="sxs-lookup"><span data-stu-id="30d63-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30d63-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="30d63-132">Remarks</span></span>  
 <span data-ttu-id="30d63-133">Jeśli odbiornik jest zdefiniowany `<add>` w elemencie `<sharedListeners>` elementu, filtr dla tego odbiornika `<filter>` powinien być zdefiniowany w elemencie, który jest elementem podrzędnym `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="30d63-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="30d63-134">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30d63-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30d63-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="30d63-135">Example</span></span>  
 <span data-ttu-id="30d63-136">Poniższy przykład pokazuje, `<filter>` jak za pomocą elementu dodać filtr do odbiornika `console` śledzenia w `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="30d63-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="30d63-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30d63-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="30d63-138">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="30d63-138">Trace and Debug Settings Schema</span></span>](index.md)
