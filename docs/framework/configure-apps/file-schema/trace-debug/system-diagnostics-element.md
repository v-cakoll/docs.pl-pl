---
title: <system.diagnostyka> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 4f831592d7d178276b1625e1ef7d8512085342af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153210"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="9902a-102">\<element> system.diagnostics</span><span class="sxs-lookup"><span data-stu-id="9902a-102">\<system.diagnostics> Element</span></span>
<span data-ttu-id="9902a-103">Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9902a-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
[<span data-ttu-id="9902a-104">**\<>konfiguracyjne**</span><span class="sxs-lookup"><span data-stu-id="9902a-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="9902a-105">&nbsp;&nbsp;**\<>system.diagnostics**</span><span class="sxs-lookup"><span data-stu-id="9902a-105">&nbsp;&nbsp;**\<system.diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9902a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9902a-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9902a-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9902a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="9902a-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9902a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9902a-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9902a-109">Attributes</span></span>  
 <span data-ttu-id="9902a-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="9902a-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9902a-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9902a-111">Child Elements</span></span>  
  
|<span data-ttu-id="9902a-112">Element</span><span class="sxs-lookup"><span data-stu-id="9902a-112">Element</span></span>|<span data-ttu-id="9902a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9902a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9902a-114">\<dochodzić></span><span class="sxs-lookup"><span data-stu-id="9902a-114">\<assert></span></span>](assert-element.md)|<span data-ttu-id="9902a-115">Określa, czy okno komunikatu ma <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> być wyświetlane podczas wywoływania metody; określa również nazwę pliku, do który mają być zapisywane wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9902a-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="9902a-116">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="9902a-116">\<performanceCounters></span></span>](performancecounters-element.md)|<span data-ttu-id="9902a-117">Określa rozmiar pamięci globalnej współużytkowanej przez liczniki wydajności.</span><span class="sxs-lookup"><span data-stu-id="9902a-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="9902a-118">\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="9902a-118">\<sharedListeners></span></span>](sharedlisteners-element.md)|<span data-ttu-id="9902a-119">Zawiera detektory, do których może odwoływać się dowolne źródło lub element śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9902a-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="9902a-120">Detektory zidentyfikowane jako detektory udostępnione można dodać do źródeł lub śladów według nazwy.</span><span class="sxs-lookup"><span data-stu-id="9902a-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="9902a-121">\<źródeł></span><span class="sxs-lookup"><span data-stu-id="9902a-121">\<sources></span></span>](sources-element.md)|<span data-ttu-id="9902a-122">Określa źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9902a-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="9902a-123">\<przełączniki></span><span class="sxs-lookup"><span data-stu-id="9902a-123">\<switches></span></span>](switches-element.md)|<span data-ttu-id="9902a-124">Zawiera przełączniki śledzenia i poziomy, na których są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9902a-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="9902a-125">\<>śledzenia</span><span class="sxs-lookup"><span data-stu-id="9902a-125">\<trace></span></span>](trace-element.md)|<span data-ttu-id="9902a-126">Zawiera odbiorniki, które zbierają, przechowują i trasy śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9902a-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9902a-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9902a-127">Parent Elements</span></span>  
  
|<span data-ttu-id="9902a-128">Element</span><span class="sxs-lookup"><span data-stu-id="9902a-128">Element</span></span>|<span data-ttu-id="9902a-129">Opis</span><span class="sxs-lookup"><span data-stu-id="9902a-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9902a-130">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9902a-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9902a-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="9902a-131">Example</span></span>  
 <span data-ttu-id="9902a-132">W poniższym przykładzie pokazano, jak osadzić przełącznik śledzenia i odbiornik śledzenia wewnątrz \*\* \<elementu>system.diagnostics.\*\*</span><span class="sxs-lookup"><span data-stu-id="9902a-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="9902a-133">Przełącznik `General` śledzenia jest ustawiony <xref:System.Diagnostics.TraceLevel> na poziomie.</span><span class="sxs-lookup"><span data-stu-id="9902a-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="9902a-134">Odbiornik śledzenia `myListener` tworzy plik `MyListener.log` o nazwie i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="9902a-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9902a-135">W .NET Framework w wersji 2.0 można użyć tekstu, aby określić wartość przełącznika.</span><span class="sxs-lookup"><span data-stu-id="9902a-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="9902a-136">Na przykład można `true` określić <xref:System.Diagnostics.BooleanSwitch> dla tekstu lub użyć tekstu reprezentującego `Error` wartość <xref:System.Diagnostics.TraceSwitch>wyliczenia, taką jak dla .</span><span class="sxs-lookup"><span data-stu-id="9902a-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="9902a-137">Linia `<add name="myTraceSwitch" value="Error" />` jest równoważna `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="9902a-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9902a-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9902a-138">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="9902a-139">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="9902a-139">Trace and Debug Settings Schema</span></span>](index.md)
