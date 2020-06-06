---
title: <element> system. Diagnostics
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 4f831592d7d178276b1625e1ef7d8512085342af
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153210"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="1a370-102">\<system.diagnostics> Element</span><span class="sxs-lookup"><span data-stu-id="1a370-102">\<system.diagnostics> Element</span></span>
<span data-ttu-id="1a370-103">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1a370-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="1a370-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a370-104">Syntax</span></span>  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a370-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1a370-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1a370-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1a370-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a370-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1a370-107">Attributes</span></span>  
 <span data-ttu-id="1a370-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="1a370-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1a370-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1a370-109">Child Elements</span></span>  
  
|<span data-ttu-id="1a370-110">Element</span><span class="sxs-lookup"><span data-stu-id="1a370-110">Element</span></span>|<span data-ttu-id="1a370-111">Opis</span><span class="sxs-lookup"><span data-stu-id="1a370-111">Description</span></span>|  
|-------------|-----------------|  
|[\<assert>](assert-element.md)|<span data-ttu-id="1a370-112">Określa, czy podczas wywoływania metody ma być wyświetlane okno komunikatu <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> , a także określa nazwę pliku, w którym mają zostać zapisane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="1a370-112">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[\<performanceCounters>](performancecounters-element.md)|<span data-ttu-id="1a370-113">Określa rozmiar pamięci globalnej udostępnionej przez liczniki wydajności.</span><span class="sxs-lookup"><span data-stu-id="1a370-113">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[\<sharedListeners>](sharedlisteners-element.md)|<span data-ttu-id="1a370-114">Zawiera detektory, do których może odwoływać się każdy element źródłowy lub Trace.</span><span class="sxs-lookup"><span data-stu-id="1a370-114">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="1a370-115">Odbiorniki identyfikowane jako odbiorniki udostępnione mogą być dodawane do źródeł lub śladów według nazwy.</span><span class="sxs-lookup"><span data-stu-id="1a370-115">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[\<sources>](sources-element.md)|<span data-ttu-id="1a370-116">Określa źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1a370-116">Specifies trace sources that initiate tracing messages.</span></span>|  
|[\<switches>](switches-element.md)|<span data-ttu-id="1a370-117">Zawiera przełączniki śledzenia i poziomy, w których są ustawiane przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1a370-117">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[\<trace>](trace-element.md)|<span data-ttu-id="1a370-118">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1a370-118">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1a370-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1a370-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1a370-120">Element</span><span class="sxs-lookup"><span data-stu-id="1a370-120">Element</span></span>|<span data-ttu-id="1a370-121">Opis</span><span class="sxs-lookup"><span data-stu-id="1a370-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1a370-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1a370-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1a370-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a370-123">Example</span></span>  
 <span data-ttu-id="1a370-124">Poniższy przykład pokazuje, jak osadzić przełącznik śledzenia i odbiornik śledzenia wewnątrz **\<system.diagnostics>** elementu.</span><span class="sxs-lookup"><span data-stu-id="1a370-124">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="1a370-125">`General`Przełącznik śledzenia jest ustawiony na <xref:System.Diagnostics.TraceLevel> poziom.</span><span class="sxs-lookup"><span data-stu-id="1a370-125">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="1a370-126">Odbiornik śledzenia `myListener` tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="1a370-126">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a370-127">W .NET Framework w wersji 2,0 można użyć tekstu, aby określić wartość dla przełącznika.</span><span class="sxs-lookup"><span data-stu-id="1a370-127">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="1a370-128">Na przykład można określić `true` dla <xref:System.Diagnostics.BooleanSwitch> lub użyć tekstu reprezentującego wartość wyliczenia, taką jak `Error` dla elementu <xref:System.Diagnostics.TraceSwitch> .</span><span class="sxs-lookup"><span data-stu-id="1a370-128">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="1a370-129">Wiersz `<add name="myTraceSwitch" value="Error" />` jest odpowiednikiem `<add name="myTraceSwitch" value="1" />` .</span><span class="sxs-lookup"><span data-stu-id="1a370-129">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1a370-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a370-130">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="1a370-131">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="1a370-131">Trace and Debug Settings Schema</span></span>](index.md)
