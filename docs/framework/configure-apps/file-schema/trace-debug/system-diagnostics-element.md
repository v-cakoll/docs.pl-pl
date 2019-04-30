---
title: Element < system.diagnostics >
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 026805ffb9b89aa55e84cf9a5c4afb8ed63cec09
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673696"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="05e18-102">\<system.diagnostics> Element</span><span class="sxs-lookup"><span data-stu-id="05e18-102">\<system.diagnostics> Element</span></span>
<span data-ttu-id="05e18-103">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="05e18-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="05e18-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="05e18-104">\<configuration></span></span>  
<span data-ttu-id="05e18-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="05e18-105">\<system.diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05e18-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="05e18-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05e18-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="05e18-107">Attributes and Elements</span></span>  
 <span data-ttu-id="05e18-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="05e18-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05e18-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="05e18-109">Attributes</span></span>  
 <span data-ttu-id="05e18-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="05e18-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="05e18-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="05e18-111">Child Elements</span></span>  
  
|<span data-ttu-id="05e18-112">Element</span><span class="sxs-lookup"><span data-stu-id="05e18-112">Element</span></span>|<span data-ttu-id="05e18-113">Opis</span><span class="sxs-lookup"><span data-stu-id="05e18-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05e18-114">\<asercja ></span><span class="sxs-lookup"><span data-stu-id="05e18-114">\<assert></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<span data-ttu-id="05e18-115">Określa, czy należy wyświetlić okno komunikatu, gdy wywołujesz <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metody; określa także nazwę pliku do zapisywania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="05e18-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="05e18-116">\<liczniki wydajności ></span><span class="sxs-lookup"><span data-stu-id="05e18-116">\<performanceCounters></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|<span data-ttu-id="05e18-117">Określa rozmiar pamięci globalnej współużytkowane przez liczniki wydajności.</span><span class="sxs-lookup"><span data-stu-id="05e18-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="05e18-118">\<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="05e18-118">\<sharedListeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|<span data-ttu-id="05e18-119">Zawiera dowolnego źródła i elementu śledzenia można odwoływać się do obiektów nasłuchujących.</span><span class="sxs-lookup"><span data-stu-id="05e18-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="05e18-120">Odbiorniki zidentyfikowane jako współdzielonych detektorów można dodać do źródła lub śledzenie według nazwy.</span><span class="sxs-lookup"><span data-stu-id="05e18-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="05e18-121">\<źródła ></span><span class="sxs-lookup"><span data-stu-id="05e18-121">\<sources></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|<span data-ttu-id="05e18-122">Określa źródła śledzenia, które inicjują komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="05e18-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="05e18-123">\<przełączniki ></span><span class="sxs-lookup"><span data-stu-id="05e18-123">\<switches></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|<span data-ttu-id="05e18-124">Zawiera poziomy, gdzie są ustawione przełączniki śledzenia i przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="05e18-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="05e18-125">\<trace></span><span class="sxs-lookup"><span data-stu-id="05e18-125">\<trace></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|<span data-ttu-id="05e18-126">Zawiera obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="05e18-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="05e18-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="05e18-127">Parent Elements</span></span>  
  
|<span data-ttu-id="05e18-128">Element</span><span class="sxs-lookup"><span data-stu-id="05e18-128">Element</span></span>|<span data-ttu-id="05e18-129">Opis</span><span class="sxs-lookup"><span data-stu-id="05e18-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="05e18-130">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="05e18-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="05e18-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="05e18-131">Example</span></span>  
 <span data-ttu-id="05e18-132">Poniższy przykład pokazuje, jak osadzać przełącznikiem śledzenia i detektor śledzenia wewnątrz  **\<system.diagnostics >** elementu.</span><span class="sxs-lookup"><span data-stu-id="05e18-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="05e18-133">`General` Przełącznikiem śledzenia jest równa <xref:System.Diagnostics.TraceLevel> poziom.</span><span class="sxs-lookup"><span data-stu-id="05e18-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="05e18-134">Odbiornik śledzenia `myListener` tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="05e18-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05e18-135">W .NET Framework w wersji 2.0 można użyć tekstu, aby określić wartość dla przełącznika.</span><span class="sxs-lookup"><span data-stu-id="05e18-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="05e18-136">Na przykład można określić `true` dla <xref:System.Diagnostics.BooleanSwitch> lub Użyj tekstu, takie jak reprezentujących wartości wyliczenia `Error` dla <xref:System.Diagnostics.TraceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="05e18-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="05e18-137">Wiersz `<add name="myTraceSwitch" value="Error" />` jest odpowiednikiem `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="05e18-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05e18-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05e18-138">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="05e18-139">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="05e18-139">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
