---
title: < element > System. Diagnostics
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: dc05c46cb1ba74baceaaeadc2959a6889faf19c9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699193"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="91fee-102">\<element > System. Diagnostics</span><span class="sxs-lookup"><span data-stu-id="91fee-102">\<system.diagnostics> Element</span></span>
<span data-ttu-id="91fee-103">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="91fee-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
[<span data-ttu-id="91fee-104"> **> konfiguracji \<** </span><span class="sxs-lookup"><span data-stu-id="91fee-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="91fee-105">&nbsp;&nbsp; **\<system. diagnostics >**</span><span class="sxs-lookup"><span data-stu-id="91fee-105">&nbsp;&nbsp;**\<system.diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91fee-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="91fee-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91fee-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="91fee-107">Attributes and Elements</span></span>  
 <span data-ttu-id="91fee-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="91fee-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91fee-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="91fee-109">Attributes</span></span>  
 <span data-ttu-id="91fee-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="91fee-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="91fee-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="91fee-111">Child Elements</span></span>  
  
|<span data-ttu-id="91fee-112">Element</span><span class="sxs-lookup"><span data-stu-id="91fee-112">Element</span></span>|<span data-ttu-id="91fee-113">Opis</span><span class="sxs-lookup"><span data-stu-id="91fee-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91fee-114">\<Assert ></span><span class="sxs-lookup"><span data-stu-id="91fee-114">\<assert></span></span>](assert-element.md)|<span data-ttu-id="91fee-115">Określa, czy podczas wywoływania metody <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ma być wyświetlane okno komunikatu. określa również nazwę pliku, do którego mają być zapisane wiadomości.</span><span class="sxs-lookup"><span data-stu-id="91fee-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="91fee-116">\<liczniki wydajności ></span><span class="sxs-lookup"><span data-stu-id="91fee-116">\<performanceCounters></span></span>](performancecounters-element.md)|<span data-ttu-id="91fee-117">Określa rozmiar pamięci globalnej udostępnionej przez liczniki wydajności.</span><span class="sxs-lookup"><span data-stu-id="91fee-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="91fee-118">\<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="91fee-118">\<sharedListeners></span></span>](sharedlisteners-element.md)|<span data-ttu-id="91fee-119">Zawiera detektory, do których może odwoływać się każdy element źródłowy lub Trace.</span><span class="sxs-lookup"><span data-stu-id="91fee-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="91fee-120">Odbiorniki identyfikowane jako odbiorniki udostępnione mogą być dodawane do źródeł lub śladów według nazwy.</span><span class="sxs-lookup"><span data-stu-id="91fee-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="91fee-121">\<źródła ></span><span class="sxs-lookup"><span data-stu-id="91fee-121">\<sources></span></span>](sources-element.md)|<span data-ttu-id="91fee-122">Określa źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="91fee-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="91fee-123">\<przełączniki ></span><span class="sxs-lookup"><span data-stu-id="91fee-123">\<switches></span></span>](switches-element.md)|<span data-ttu-id="91fee-124">Zawiera przełączniki śledzenia i poziomy, w których są ustawiane przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="91fee-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="91fee-125">\<trace></span><span class="sxs-lookup"><span data-stu-id="91fee-125">\<trace></span></span>](trace-element.md)|<span data-ttu-id="91fee-126">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="91fee-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91fee-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="91fee-127">Parent Elements</span></span>  
  
|<span data-ttu-id="91fee-128">Element</span><span class="sxs-lookup"><span data-stu-id="91fee-128">Element</span></span>|<span data-ttu-id="91fee-129">Opis</span><span class="sxs-lookup"><span data-stu-id="91fee-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="91fee-130">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91fee-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="91fee-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="91fee-131">Example</span></span>  
 <span data-ttu-id="91fee-132">Poniższy przykład pokazuje, jak osadzić przełącznik śledzenia i odbiornik śledzenia wewnątrz elementu **\<system. diagnostics >** .</span><span class="sxs-lookup"><span data-stu-id="91fee-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="91fee-133">Przełącznik śledzenia `General` jest ustawiony na poziom <xref:System.Diagnostics.TraceLevel>.</span><span class="sxs-lookup"><span data-stu-id="91fee-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="91fee-134">Odbiornik śledzenia `myListener` tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="91fee-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91fee-135">W .NET Framework w wersji 2,0 można użyć tekstu, aby określić wartość dla przełącznika.</span><span class="sxs-lookup"><span data-stu-id="91fee-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="91fee-136">Na przykład można określić `true` dla <xref:System.Diagnostics.BooleanSwitch> lub użyć tekstu reprezentującego wartość wyliczenia, taką jak `Error` dla <xref:System.Diagnostics.TraceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="91fee-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="91fee-137">Wiersz `<add name="myTraceSwitch" value="Error" />` jest równoznaczny z `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="91fee-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="91fee-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91fee-138">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="91fee-139">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="91fee-139">Trace and Debug Settings Schema</span></span>](index.md)
