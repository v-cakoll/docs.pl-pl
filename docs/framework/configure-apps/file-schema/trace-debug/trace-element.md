---
title: <trace>, element
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153169"
---
# <a name="trace-element"></a><span data-ttu-id="b55a4-102">\<element> śledzenia</span><span class="sxs-lookup"><span data-stu-id="b55a4-102">\<trace> Element</span></span>
<span data-ttu-id="b55a4-103">Zawiera odbiorniki, które zbierają, przechowują i trasy śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b55a4-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[<span data-ttu-id="b55a4-104">**\<>konfiguracyjne**</span><span class="sxs-lookup"><span data-stu-id="b55a4-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="b55a4-105">&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="b55a4-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="b55a4-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<>śledzenia**</span><span class="sxs-lookup"><span data-stu-id="b55a4-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b55a4-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="b55a4-107">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b55a4-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b55a4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b55a4-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b55a4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b55a4-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b55a4-110">Attributes</span></span>  
  
|<span data-ttu-id="b55a4-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b55a4-111">Attribute</span></span>|<span data-ttu-id="b55a4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b55a4-112">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="b55a4-113">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b55a4-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b55a4-114">Określa, czy detektory śledzenia automatycznie opróżniają bufor wyjściowy po każdej operacji zapisu.</span><span class="sxs-lookup"><span data-stu-id="b55a4-114">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="b55a4-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b55a4-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b55a4-116">Określa liczbę spacji do wcięcie.</span><span class="sxs-lookup"><span data-stu-id="b55a4-116">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="b55a4-117">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b55a4-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b55a4-118">Wskazuje, czy blokada globalna powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="b55a4-118">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="b55a4-119">Atrybut autoflush</span><span class="sxs-lookup"><span data-stu-id="b55a4-119">autoflush Attribute</span></span>  
  
|<span data-ttu-id="b55a4-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="b55a4-120">Value</span></span>|<span data-ttu-id="b55a4-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b55a4-121">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b55a4-122">Nie opróżnia automatycznie buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="b55a4-122">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="b55a4-123">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="b55a4-123">This is the default.</span></span>|  
|`true`|<span data-ttu-id="b55a4-124">Automatycznie opróżnia bufor wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="b55a4-124">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="b55a4-125">useGlobalLock Atrybut</span><span class="sxs-lookup"><span data-stu-id="b55a4-125">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="b55a4-126">Wartość</span><span class="sxs-lookup"><span data-stu-id="b55a4-126">Value</span></span>|<span data-ttu-id="b55a4-127">Opis</span><span class="sxs-lookup"><span data-stu-id="b55a4-127">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b55a4-128">Nie używa blokady globalnej, jeśli odbiornik jest bezpieczny dla wątków; w przeciwnym razie używa blokady globalnej.</span><span class="sxs-lookup"><span data-stu-id="b55a4-128">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="b55a4-129">Używa blokady globalnej, niezależnie od tego, czy odbiornik jest bezpieczny dla wątków.</span><span class="sxs-lookup"><span data-stu-id="b55a4-129">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="b55a4-130">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="b55a4-130">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b55a4-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b55a4-131">Child Elements</span></span>  
  
|<span data-ttu-id="b55a4-132">Element</span><span class="sxs-lookup"><span data-stu-id="b55a4-132">Element</span></span>|<span data-ttu-id="b55a4-133">Opis</span><span class="sxs-lookup"><span data-stu-id="b55a4-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b55a4-134">\<słuchacze></span><span class="sxs-lookup"><span data-stu-id="b55a4-134">\<listeners></span></span>](listeners-element-for-trace.md)|<span data-ttu-id="b55a4-135">Określa odbiornik, który zbiera, przechowuje i kieruje wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b55a4-135">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b55a4-136">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b55a4-136">Parent Elements</span></span>  
  
|<span data-ttu-id="b55a4-137">Element</span><span class="sxs-lookup"><span data-stu-id="b55a4-137">Element</span></span>|<span data-ttu-id="b55a4-138">Opis</span><span class="sxs-lookup"><span data-stu-id="b55a4-138">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b55a4-139">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b55a4-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b55a4-140">Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b55a4-140">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b55a4-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="b55a4-141">Example</span></span>  
 <span data-ttu-id="b55a4-142">W poniższym przykładzie `<trace>` pokazano, jak użyć `MyListener` elementu, aby dodać odbiornik do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b55a4-142">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="b55a4-143">`MyListener`tworzy plik, który `MyListener.log` jest nazwany i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="b55a4-143">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="b55a4-144">Atrybut `useGlobalLock` jest ustawiony `false`na , co powoduje, że blokada globalna nie ma być używany, jeśli odbiornik śledzenia jest bezpieczny dla wątków.</span><span class="sxs-lookup"><span data-stu-id="b55a4-144">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="b55a4-145">Atrybut `autoflush` jest ustawiony `true`na , co powoduje, że odbiornik śledzenia do <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> zapisu do pliku, niezależnie od tego, czy metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="b55a4-145">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="b55a4-146">Atrybut `indentsize` jest ustawiony na 0 (zero), co powoduje, że odbiornik <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> wcięcie zero spacji, gdy metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="b55a4-146">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b55a4-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b55a4-147">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="b55a4-148">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="b55a4-148">Trace and Debug Settings Schema</span></span>](index.md)
