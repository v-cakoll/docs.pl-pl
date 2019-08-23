---
title: <listeners>, element dla <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 853bc94978218fd4d426e6070b3a36e20435cd6d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920489"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="ffe33-102">\<> elementu odbiorników \<dla > źródłowych</span><span class="sxs-lookup"><span data-stu-id="ffe33-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="ffe33-103">Dodaje lub usuwa detektory w <xref:System.Diagnostics.TraceSource.Listeners%2A> kolekcji dla elementu <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="ffe33-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="ffe33-104">Odbiornik kieruje dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takiego jak dziennik, okno lub plik tekstowy.</span><span class="sxs-lookup"><span data-stu-id="ffe33-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="ffe33-105">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ffe33-105">\<configuration></span></span>  
<span data-ttu-id="ffe33-106">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="ffe33-106">\<system.diagnostics></span></span>  
<span data-ttu-id="ffe33-107">\<> źródeł</span><span class="sxs-lookup"><span data-stu-id="ffe33-107">\<sources></span></span>  
<span data-ttu-id="ffe33-108">\<> źródłowa</span><span class="sxs-lookup"><span data-stu-id="ffe33-108">\<source></span></span>  
<span data-ttu-id="ffe33-109">\<Elementy > odbiorników</span><span class="sxs-lookup"><span data-stu-id="ffe33-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffe33-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="ffe33-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffe33-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ffe33-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ffe33-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ffe33-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ffe33-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ffe33-113">Attributes</span></span>  
 <span data-ttu-id="ffe33-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="ffe33-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ffe33-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ffe33-115">Child Elements</span></span>  
  
|<span data-ttu-id="ffe33-116">Element</span><span class="sxs-lookup"><span data-stu-id="ffe33-116">Element</span></span>|<span data-ttu-id="ffe33-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ffe33-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ffe33-118">\<add></span><span class="sxs-lookup"><span data-stu-id="ffe33-118">\<add></span></span>](add-element-for-listeners-for-source.md)|<span data-ttu-id="ffe33-119">Dodaje odbiornik do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ffe33-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="ffe33-120">\<remove></span><span class="sxs-lookup"><span data-stu-id="ffe33-120">\<remove></span></span>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="ffe33-121">Usuwa odbiornik z `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ffe33-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="ffe33-122">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="ffe33-122">\<clear></span></span>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="ffe33-123">`Listeners` Czyści kolekcję dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ffe33-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ffe33-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ffe33-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ffe33-125">Element</span><span class="sxs-lookup"><span data-stu-id="ffe33-125">Element</span></span>|<span data-ttu-id="ffe33-126">Opis</span><span class="sxs-lookup"><span data-stu-id="ffe33-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ffe33-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ffe33-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ffe33-128">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ffe33-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="ffe33-129">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ffe33-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="ffe33-130">Określa źródło śledzenia, które inicjuje komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ffe33-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffe33-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ffe33-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="ffe33-132">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ffe33-132">Configuration File</span></span>  
 <span data-ttu-id="ffe33-133">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ffe33-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffe33-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="ffe33-134">Example</span></span>  
 <span data-ttu-id="ffe33-135">Poniższy przykład pokazuje, jak użyć elementu, `<listeners>` aby dodać odbiornik śledzenia konsoli `mySource` do źródła i usunąć domyślny odbiornik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ffe33-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffe33-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffe33-136">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="ffe33-137">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="ffe33-137">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ffe33-138">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="ffe33-138">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
