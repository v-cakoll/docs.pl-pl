---
title: <clear>Element dla <listeners> elementu<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 768d51a74b4c31d1250d2f5d6517f760f886e0a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920554"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="595e3-102">\<Wyczyść > element dla \<odbiorników > \<dla źródła ></span><span class="sxs-lookup"><span data-stu-id="595e3-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="595e3-103">`Listeners` Czyści kolekcję dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="595e3-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="595e3-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="595e3-104">\<configuration></span></span>  
<span data-ttu-id="595e3-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="595e3-105">\<system.diagnostics></span></span>  
<span data-ttu-id="595e3-106">\<> źródeł</span><span class="sxs-lookup"><span data-stu-id="595e3-106">\<sources></span></span>  
<span data-ttu-id="595e3-107">\<> źródłowa</span><span class="sxs-lookup"><span data-stu-id="595e3-107">\<source></span></span>  
<span data-ttu-id="595e3-108">\<> odbiorników</span><span class="sxs-lookup"><span data-stu-id="595e3-108">\<listeners></span></span>  
<span data-ttu-id="595e3-109">\<clear></span><span class="sxs-lookup"><span data-stu-id="595e3-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="595e3-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="595e3-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="595e3-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="595e3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="595e3-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="595e3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="595e3-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="595e3-113">Attributes</span></span>  
 <span data-ttu-id="595e3-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="595e3-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="595e3-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="595e3-115">Child Elements</span></span>  
 <span data-ttu-id="595e3-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="595e3-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="595e3-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="595e3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="595e3-118">Element</span><span class="sxs-lookup"><span data-stu-id="595e3-118">Element</span></span>|<span data-ttu-id="595e3-119">Opis</span><span class="sxs-lookup"><span data-stu-id="595e3-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="595e3-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="595e3-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="595e3-121">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="595e3-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="595e3-122">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="595e3-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="595e3-123">Określa źródło śledzenia, które inicjuje komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="595e3-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="595e3-124">Określa detektory, które zbierają, przechowują i rozsyłają komunikaty.</span><span class="sxs-lookup"><span data-stu-id="595e3-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="595e3-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="595e3-125">Remarks</span></span>  
 <span data-ttu-id="595e3-126">Element usuwa wszystkie odbiorniki `Listeners` z kolekcji dla źródła śledzenia, włącznie z <xref:System.Diagnostics.DefaultTraceListener>. `<clear>`</span><span class="sxs-lookup"><span data-stu-id="595e3-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="595e3-127">Możesz użyć `<clear>` elementu przed użyciem elementu, `<add>` aby mieć pewność, że w kolekcji nie ma żadnych innych aktywnych odbiorników.</span><span class="sxs-lookup"><span data-stu-id="595e3-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="595e3-128">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="595e3-128">Configuration File</span></span>  
 <span data-ttu-id="595e3-129">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="595e3-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="595e3-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="595e3-130">Example</span></span>  
 <span data-ttu-id="595e3-131">Poniższy przykład pokazuje, `<clear>` jak używać elementu przed `<add>` użyciem elementów, aby dodać detektory `console` oraz `textListener` do `Listeners` kolekcji dla źródła `TraceSourceApp`śledzenia.</span><span class="sxs-lookup"><span data-stu-id="595e3-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="595e3-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="595e3-132">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="595e3-133">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="595e3-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="595e3-134">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="595e3-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
