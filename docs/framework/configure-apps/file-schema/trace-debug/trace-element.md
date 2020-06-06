---
title: <trace> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 7d8a989219d84e8604e767456c84c0092bc73b22
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153169"
---
# <a name="trace-element"></a><span data-ttu-id="00d60-102">\<trace> Element</span><span class="sxs-lookup"><span data-stu-id="00d60-102">\<trace> Element</span></span>
<span data-ttu-id="00d60-103">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="00d60-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**  
  
## <a name="syntax"></a><span data-ttu-id="00d60-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00d60-104">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00d60-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="00d60-105">Attributes and Elements</span></span>  
 <span data-ttu-id="00d60-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="00d60-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00d60-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="00d60-107">Attributes</span></span>  
  
|<span data-ttu-id="00d60-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="00d60-108">Attribute</span></span>|<span data-ttu-id="00d60-109">Opis</span><span class="sxs-lookup"><span data-stu-id="00d60-109">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="00d60-110">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="00d60-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="00d60-111">Określa, czy odbiorniki śledzenia automatycznie opróżniają bufor wyjściowy po każdej operacji zapisu.</span><span class="sxs-lookup"><span data-stu-id="00d60-111">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="00d60-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="00d60-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="00d60-113">Określa liczbę spacji do wcięcia.</span><span class="sxs-lookup"><span data-stu-id="00d60-113">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="00d60-114">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="00d60-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="00d60-115">Wskazuje, czy globalna blokada powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="00d60-115">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="00d60-116">AutoFlush — atrybut</span><span class="sxs-lookup"><span data-stu-id="00d60-116">autoflush Attribute</span></span>  
  
|<span data-ttu-id="00d60-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="00d60-117">Value</span></span>|<span data-ttu-id="00d60-118">Opis</span><span class="sxs-lookup"><span data-stu-id="00d60-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="00d60-119">Nie opróżnia bufora wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="00d60-119">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="00d60-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="00d60-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="00d60-121">Automatycznie opróżnia bufor wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="00d60-121">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="00d60-122">useGlobalLock — Atrybut</span><span class="sxs-lookup"><span data-stu-id="00d60-122">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="00d60-123">Wartość</span><span class="sxs-lookup"><span data-stu-id="00d60-123">Value</span></span>|<span data-ttu-id="00d60-124">Opis</span><span class="sxs-lookup"><span data-stu-id="00d60-124">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="00d60-125">Nie używa blokady globalnej, jeśli odbiornik jest bezpieczny wątkowo; w przeciwnym razie używa blokady globalnej.</span><span class="sxs-lookup"><span data-stu-id="00d60-125">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="00d60-126">Używa blokady globalnej niezależnie od tego, czy odbiornik jest bezpieczny wątkowo.</span><span class="sxs-lookup"><span data-stu-id="00d60-126">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="00d60-127">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="00d60-127">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00d60-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="00d60-128">Child Elements</span></span>  
  
|<span data-ttu-id="00d60-129">Element</span><span class="sxs-lookup"><span data-stu-id="00d60-129">Element</span></span>|<span data-ttu-id="00d60-130">Opis</span><span class="sxs-lookup"><span data-stu-id="00d60-130">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="00d60-131">Określa odbiornik, który zbiera, przechowuje i kieruje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="00d60-131">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="00d60-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="00d60-132">Parent Elements</span></span>  
  
|<span data-ttu-id="00d60-133">Element</span><span class="sxs-lookup"><span data-stu-id="00d60-133">Element</span></span>|<span data-ttu-id="00d60-134">Opis</span><span class="sxs-lookup"><span data-stu-id="00d60-134">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="00d60-135">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00d60-135">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="00d60-136">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="00d60-136">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="00d60-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="00d60-137">Example</span></span>  
 <span data-ttu-id="00d60-138">Poniższy przykład pokazuje, jak użyć elementu, `<trace>` Aby dodać odbiornik `MyListener` do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="00d60-138">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="00d60-139">`MyListener`tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="00d60-139">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="00d60-140">`useGlobalLock`Atrybut jest ustawiony na `false` , co powoduje, że globalna blokada nie zostanie użyta, jeśli odbiornik śledzenia jest bezpieczny wątkowo.</span><span class="sxs-lookup"><span data-stu-id="00d60-140">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="00d60-141">`autoflush`Atrybut jest ustawiony na `true` , co powoduje, że odbiornik śledzenia ma zapisywać do pliku bez względu na to, czy <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> Metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="00d60-141">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="00d60-142">`indentsize`Atrybut jest ustawiony na 0 (zero), co powoduje, że odbiornik ma wcięcie zerowej spacji, gdy <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> wywoływana jest metoda.</span><span class="sxs-lookup"><span data-stu-id="00d60-142">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="00d60-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00d60-143">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="00d60-144">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="00d60-144">Trace and Debug Settings Schema</span></span>](index.md)
