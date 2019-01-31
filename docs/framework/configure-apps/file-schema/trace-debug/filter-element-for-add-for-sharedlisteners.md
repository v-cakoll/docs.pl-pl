---
title: <filter> — Element do <add> dla <sharedListeners>
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
ms.openlocfilehash: 739acedcc83cd207a7ef4c10c220d27695dd713d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269305"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="154b7-102">\<Filtr >, Element dla \<Dodaj > dla \<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="154b7-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="154b7-103">Dodaje filtr do odbiornika w `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="154b7-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  
  
 <span data-ttu-id="154b7-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="154b7-104">\<configuration></span></span>  
<span data-ttu-id="154b7-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="154b7-105">\<system.diagnostics></span></span>  
<span data-ttu-id="154b7-106">\<sharedListeners > Element</span><span class="sxs-lookup"><span data-stu-id="154b7-106">\<sharedListeners> Element</span></span>  
<span data-ttu-id="154b7-107">\<add></span><span class="sxs-lookup"><span data-stu-id="154b7-107">\<add></span></span>  
<span data-ttu-id="154b7-108">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="154b7-108">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="154b7-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="154b7-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="154b7-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="154b7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="154b7-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="154b7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="154b7-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="154b7-112">Attributes</span></span>  
  
|<span data-ttu-id="154b7-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="154b7-113">Attribute</span></span>|<span data-ttu-id="154b7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="154b7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="154b7-115">**type**</span><span class="sxs-lookup"><span data-stu-id="154b7-115">**type**</span></span>|<span data-ttu-id="154b7-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="154b7-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="154b7-117">Określa typ filtru.</span><span class="sxs-lookup"><span data-stu-id="154b7-117">Specifies the type of the filter.</span></span> <span data-ttu-id="154b7-118">Można użyć tylko pełną nazwę tego typu (w formacie <xref:System.Type.FullName%2A?displayProperty=nameWithType> właściwości), lub można użyć w pełni kwalifikowana nazwa typu w tym informacje o zestawie (w formacie <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> właściwości).</span><span class="sxs-lookup"><span data-stu-id="154b7-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="154b7-119">Aby uzyskać informacje dotyczące tworzenia w pełni kwalifikowaną nazwę typu, zobacz [określanie w pełni kwalifikowanej nazwy typu](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="154b7-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="154b7-120">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="154b7-120">**initializeData**</span></span>|<span data-ttu-id="154b7-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="154b7-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="154b7-122">Ciąg przekazany do konstruktora dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="154b7-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="154b7-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="154b7-123">Child Elements</span></span>  
 <span data-ttu-id="154b7-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="154b7-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="154b7-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="154b7-125">Parent Elements</span></span>  
  
|<span data-ttu-id="154b7-126">Element</span><span class="sxs-lookup"><span data-stu-id="154b7-126">Element</span></span>|<span data-ttu-id="154b7-127">Opis</span><span class="sxs-lookup"><span data-stu-id="154b7-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="154b7-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="154b7-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="154b7-129">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="154b7-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="154b7-130">Kolekcja obiektów nasłuchujących dowolnego źródła i elementu śledzenia można odwoływać się do.</span><span class="sxs-lookup"><span data-stu-id="154b7-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="154b7-131">Dodaje odbiornik do **sharedListeners** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="154b7-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="154b7-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="154b7-132">Remarks</span></span>  
 <span data-ttu-id="154b7-133">Jeśli odbiornik jest zdefiniowany w `<add>` elementu `<sharedListeners>` elementu filtru dla tego odbiornika powinien być zdefiniowany w `<filter>` element, który jest elementem podrzędnym `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="154b7-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="154b7-134">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="154b7-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="154b7-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="154b7-135">Example</span></span>  
 <span data-ttu-id="154b7-136">Poniższy przykład pokazuje, jak używać `<filter>` elementu Dodawanie filtru do odbiornika śledzenia `console` w `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="154b7-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="154b7-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="154b7-137">See also</span></span>
- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="154b7-138">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="154b7-138">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
