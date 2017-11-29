---
title: "&lt;Wyczyść&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d5e8518f2ca8a04d91f5bfdd9f6389c741d0278e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="ee650-102">&lt;Wyczyść&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;</span><span class="sxs-lookup"><span data-stu-id="ee650-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="ee650-103">Czyści `Listeners` kolekcji źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ee650-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="ee650-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="ee650-104">\<configuration></span></span>  
<span data-ttu-id="ee650-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="ee650-105">\<system.diagnostics></span></span>  
<span data-ttu-id="ee650-106">\<źródeł ></span><span class="sxs-lookup"><span data-stu-id="ee650-106">\<sources></span></span>  
<span data-ttu-id="ee650-107">\<źródło ></span><span class="sxs-lookup"><span data-stu-id="ee650-107">\<source></span></span>  
<span data-ttu-id="ee650-108">\<obiekty nasłuchujące ></span><span class="sxs-lookup"><span data-stu-id="ee650-108">\<listeners></span></span>  
<span data-ttu-id="ee650-109">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="ee650-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee650-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee650-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee650-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ee650-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ee650-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ee650-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee650-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ee650-113">Attributes</span></span>  
 <span data-ttu-id="ee650-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="ee650-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ee650-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ee650-115">Child Elements</span></span>  
 <span data-ttu-id="ee650-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="ee650-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee650-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ee650-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ee650-118">Element</span><span class="sxs-lookup"><span data-stu-id="ee650-118">Element</span></span>|<span data-ttu-id="ee650-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ee650-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ee650-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ee650-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ee650-121">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ee650-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="ee650-122">Zawiera źródła śledzenia, które inicjują śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ee650-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="ee650-123">Określa źródło śledzenia, który inicjuje śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ee650-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="ee650-124">Określa nasłuchujących zbierania, przechowywania i kierowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ee650-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee650-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee650-125">Remarks</span></span>  
 <span data-ttu-id="ee650-126">`<clear>` Elementu spowoduje usunięcie wszystkich odbiorników z `Listeners` kolekcji źródłowej śledzenia, łącznie z <xref:System.Diagnostics.DefaultTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="ee650-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="ee650-127">Można użyć `<clear>` element, aby można było używać `<add>` elementu, aby mieć pewność, istnieją inne odbiorników active w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ee650-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="ee650-128">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ee650-128">Configuration File</span></span>  
 <span data-ttu-id="ee650-129">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ee650-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee650-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee650-130">Example</span></span>  
 <span data-ttu-id="ee650-131">Poniższy przykład przedstawia użycie `<clear>` element, aby można było używać `<add>` elementy do dodania odbiorniki `console` i `textListener` do `Listeners` kolekcji źródła śledzenia `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="ee650-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ee650-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee650-132">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="ee650-133">Schemat ustawień debugowania i śledzenia</span><span class="sxs-lookup"><span data-stu-id="ee650-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="ee650-134">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="ee650-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
