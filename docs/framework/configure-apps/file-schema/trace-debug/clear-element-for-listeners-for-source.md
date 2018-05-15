---
title: '&lt;Wyczyść&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8c6ef51dae36e94fa4a4fdc5ad8983380e78bde3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="bdefd-102">&lt;Wyczyść&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;</span><span class="sxs-lookup"><span data-stu-id="bdefd-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="bdefd-103">Czyści `Listeners` kolekcji źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bdefd-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="bdefd-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="bdefd-104">\<configuration></span></span>  
<span data-ttu-id="bdefd-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="bdefd-105">\<system.diagnostics></span></span>  
<span data-ttu-id="bdefd-106">\<źródeł ></span><span class="sxs-lookup"><span data-stu-id="bdefd-106">\<sources></span></span>  
<span data-ttu-id="bdefd-107">\<źródło ></span><span class="sxs-lookup"><span data-stu-id="bdefd-107">\<source></span></span>  
<span data-ttu-id="bdefd-108">\<obiekty nasłuchujące ></span><span class="sxs-lookup"><span data-stu-id="bdefd-108">\<listeners></span></span>  
<span data-ttu-id="bdefd-109">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="bdefd-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdefd-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="bdefd-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bdefd-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bdefd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bdefd-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bdefd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bdefd-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bdefd-113">Attributes</span></span>  
 <span data-ttu-id="bdefd-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="bdefd-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bdefd-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bdefd-115">Child Elements</span></span>  
 <span data-ttu-id="bdefd-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="bdefd-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bdefd-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bdefd-117">Parent Elements</span></span>  
  
|<span data-ttu-id="bdefd-118">Element</span><span class="sxs-lookup"><span data-stu-id="bdefd-118">Element</span></span>|<span data-ttu-id="bdefd-119">Opis</span><span class="sxs-lookup"><span data-stu-id="bdefd-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bdefd-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bdefd-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="bdefd-121">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bdefd-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="bdefd-122">Zawiera źródła śledzenia, które inicjują śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bdefd-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="bdefd-123">Określa źródło śledzenia, który inicjuje śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bdefd-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="bdefd-124">Określa nasłuchujących zbierania, przechowywania i kierowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bdefd-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdefd-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bdefd-125">Remarks</span></span>  
 <span data-ttu-id="bdefd-126">`<clear>` Elementu spowoduje usunięcie wszystkich odbiorników z `Listeners` kolekcji źródłowej śledzenia, łącznie z <xref:System.Diagnostics.DefaultTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="bdefd-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="bdefd-127">Można użyć `<clear>` element, aby można było używać `<add>` elementu, aby mieć pewność, istnieją inne odbiorników active w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="bdefd-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="bdefd-128">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bdefd-128">Configuration File</span></span>  
 <span data-ttu-id="bdefd-129">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdefd-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdefd-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="bdefd-130">Example</span></span>  
 <span data-ttu-id="bdefd-131">Poniższy przykład przedstawia użycie `<clear>` element, aby można było używać `<add>` elementy do dodania odbiorniki `console` i `textListener` do `Listeners` kolekcji źródła śledzenia `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="bdefd-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bdefd-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bdefd-132">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="bdefd-133">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="bdefd-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="bdefd-134">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="bdefd-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
