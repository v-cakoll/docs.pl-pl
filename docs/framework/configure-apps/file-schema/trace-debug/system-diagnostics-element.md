---
title: '&lt;System.Diagnostics&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 090c296ba84043445364b350c8b74587c35b5940
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemdiagnosticsgt-element"></a><span data-ttu-id="34c62-102">&lt;System.Diagnostics&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="34c62-102">&lt;system.diagnostics&gt; Element</span></span>
<span data-ttu-id="34c62-103">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="34c62-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="34c62-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="34c62-104">\<configuration></span></span>  
<span data-ttu-id="34c62-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="34c62-105">\<system.diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34c62-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="34c62-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34c62-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="34c62-107">Attributes and Elements</span></span>  
 <span data-ttu-id="34c62-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="34c62-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34c62-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="34c62-109">Attributes</span></span>  
 <span data-ttu-id="34c62-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="34c62-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="34c62-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="34c62-111">Child Elements</span></span>  
  
|<span data-ttu-id="34c62-112">Element</span><span class="sxs-lookup"><span data-stu-id="34c62-112">Element</span></span>|<span data-ttu-id="34c62-113">Opis</span><span class="sxs-lookup"><span data-stu-id="34c62-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34c62-114">\<Assert ></span><span class="sxs-lookup"><span data-stu-id="34c62-114">\<assert></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<span data-ttu-id="34c62-115">Określa, czy wyświetlać okno komunikatu po wywołaniu <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metody; określa także nazwę pliku do zapisania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="34c62-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="34c62-116">\<liczniki wydajności ></span><span class="sxs-lookup"><span data-stu-id="34c62-116">\<performanceCounters></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|<span data-ttu-id="34c62-117">Określa rozmiar pamięci globalnej współużytkowane przez liczniki wydajności.</span><span class="sxs-lookup"><span data-stu-id="34c62-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="34c62-118">\<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="34c62-118">\<sharedListeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|<span data-ttu-id="34c62-119">Zawiera nasłuchujących może odwoływać się wszystkie źródła lub element śledzenia.</span><span class="sxs-lookup"><span data-stu-id="34c62-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="34c62-120">Obiekty nasłuchujące zidentyfikowane jako udostępnione obiekty nasłuchujące można dodać do źródła lub śledzenie według nazwy.</span><span class="sxs-lookup"><span data-stu-id="34c62-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="34c62-121">\<źródeł ></span><span class="sxs-lookup"><span data-stu-id="34c62-121">\<sources></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|<span data-ttu-id="34c62-122">Określa źródła śledzenia, które inicjują śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="34c62-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="34c62-123">\<przełączniki ></span><span class="sxs-lookup"><span data-stu-id="34c62-123">\<switches></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|<span data-ttu-id="34c62-124">Zawiera przełączniki śledzenia i poziomy, gdzie są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="34c62-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="34c62-125">\<śledzenia ></span><span class="sxs-lookup"><span data-stu-id="34c62-125">\<trace></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|<span data-ttu-id="34c62-126">Zawiera nasłuchujących zbierania, przechowywania i trasy śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="34c62-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34c62-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="34c62-127">Parent Elements</span></span>  
  
|<span data-ttu-id="34c62-128">Element</span><span class="sxs-lookup"><span data-stu-id="34c62-128">Element</span></span>|<span data-ttu-id="34c62-129">Opis</span><span class="sxs-lookup"><span data-stu-id="34c62-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="34c62-130">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34c62-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="34c62-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="34c62-131">Example</span></span>  
 <span data-ttu-id="34c62-132">Poniższy przykład przedstawia sposób osadzenia przełącznika śledzenia i odbiornik śledzenia wewnątrz  **\<system.diagnostics >** elementu.</span><span class="sxs-lookup"><span data-stu-id="34c62-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="34c62-133">`General` Przełącznik śledzenia jest ustawiony na <xref:System.Diagnostics.TraceLevel> poziom.</span><span class="sxs-lookup"><span data-stu-id="34c62-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="34c62-134">Odbiornik śledzenia `myListener` tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="34c62-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34c62-135">W programie .NET Framework w wersji 2.0 tekst można użyć do określenia wartości dla przełącznika.</span><span class="sxs-lookup"><span data-stu-id="34c62-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="34c62-136">Na przykład można określić `true` dla <xref:System.Diagnostics.BooleanSwitch> lub użyj tekst reprezentujący wartości wyliczenia, takich jak `Error` dla <xref:System.Diagnostics.TraceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="34c62-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="34c62-137">Wiersz `<add name="myTraceSwitch" value="Error" />` jest odpowiednikiem `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="34c62-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="34c62-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34c62-138">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="34c62-139">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="34c62-139">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
