---
title: '&lt;śledzenia&gt; — Element'
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 59d5083632630513d2afc1f8d78400310451e46f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746062"
---
# <a name="lttracegt-element"></a><span data-ttu-id="efe25-102">&lt;śledzenia&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="efe25-102">&lt;trace&gt; Element</span></span>
<span data-ttu-id="efe25-103">Zawiera nasłuchujących zbierania, przechowywania i trasy śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="efe25-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
 <span data-ttu-id="efe25-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="efe25-104">\<configuration></span></span>  
<span data-ttu-id="efe25-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="efe25-105">\<system.diagnostics></span></span>  
<span data-ttu-id="efe25-106">\<śledzenia ></span><span class="sxs-lookup"><span data-stu-id="efe25-106">\<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efe25-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="efe25-107">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efe25-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="efe25-108">Attributes and Elements</span></span>  
 <span data-ttu-id="efe25-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="efe25-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efe25-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="efe25-110">Attributes</span></span>  
  
|<span data-ttu-id="efe25-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="efe25-111">Attribute</span></span>|<span data-ttu-id="efe25-112">Opis</span><span class="sxs-lookup"><span data-stu-id="efe25-112">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="efe25-113">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="efe25-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="efe25-114">Określa, czy odbiorniki śledzenia automatycznie opróżniania buforu wyjściowego po każdej operacji zapisu.</span><span class="sxs-lookup"><span data-stu-id="efe25-114">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="efe25-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="efe25-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="efe25-116">Określa liczbę spacji wcięcia.</span><span class="sxs-lookup"><span data-stu-id="efe25-116">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="efe25-117">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="efe25-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="efe25-118">Wskazuje, czy globalne blokady powinien być używany.</span><span class="sxs-lookup"><span data-stu-id="efe25-118">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="efe25-119">AutoFlush atrybutu</span><span class="sxs-lookup"><span data-stu-id="efe25-119">autoflush Attribute</span></span>  
  
|<span data-ttu-id="efe25-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="efe25-120">Value</span></span>|<span data-ttu-id="efe25-121">Opis</span><span class="sxs-lookup"><span data-stu-id="efe25-121">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="efe25-122">Nie automatycznie opróżnić buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="efe25-122">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="efe25-123">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="efe25-123">This is the default.</span></span>|  
|`true`|<span data-ttu-id="efe25-124">Automatycznie opróżnia bufor wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="efe25-124">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="efe25-125">useGlobalLock atrybutu</span><span class="sxs-lookup"><span data-stu-id="efe25-125">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="efe25-126">Wartość</span><span class="sxs-lookup"><span data-stu-id="efe25-126">Value</span></span>|<span data-ttu-id="efe25-127">Opis</span><span class="sxs-lookup"><span data-stu-id="efe25-127">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="efe25-128">Nie używa globalnej blokady, jeśli odbiornik jest wielowątkowość; w przeciwnym razie używa globalnej blokady.</span><span class="sxs-lookup"><span data-stu-id="efe25-128">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="efe25-129">Wykorzystuje globalne blokady niezależnie od tego, czy odbiornik bezpieczne dla wątków.</span><span class="sxs-lookup"><span data-stu-id="efe25-129">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="efe25-130">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="efe25-130">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efe25-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="efe25-131">Child Elements</span></span>  
  
|<span data-ttu-id="efe25-132">Element</span><span class="sxs-lookup"><span data-stu-id="efe25-132">Element</span></span>|<span data-ttu-id="efe25-133">Opis</span><span class="sxs-lookup"><span data-stu-id="efe25-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efe25-134">\<obiekty nasłuchujące ></span><span class="sxs-lookup"><span data-stu-id="efe25-134">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|<span data-ttu-id="efe25-135">Określa odbiornika zbiera, magazynów i kieruje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="efe25-135">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="efe25-136">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="efe25-136">Parent Elements</span></span>  
  
|<span data-ttu-id="efe25-137">Element</span><span class="sxs-lookup"><span data-stu-id="efe25-137">Element</span></span>|<span data-ttu-id="efe25-138">Opis</span><span class="sxs-lookup"><span data-stu-id="efe25-138">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="efe25-139">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="efe25-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="efe25-140">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="efe25-140">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="efe25-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="efe25-141">Example</span></span>  
 <span data-ttu-id="efe25-142">Poniższy przykład przedstawia użycie `<trace>` elementu do dodania odbiornika `MyListener` do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="efe25-142">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="efe25-143">`MyListener` Tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="efe25-143">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="efe25-144">`useGlobalLock` Atrybut ma ustawioną `false`, co powoduje, że globalne blokady nie powinna być używana, jeśli odbiornik śledzenia jest bezpieczne dla wątków.</span><span class="sxs-lookup"><span data-stu-id="efe25-144">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="efe25-145">`autoflush` Atrybut ma ustawioną `true`, co powoduje, że nasłuchującego śledzenia do zapisania do pliku, niezależnie od tego, czy <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="efe25-145">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="efe25-146">`indentsize` Atrybut jest ustawiony na 0 (zero), co powoduje, że odbiornika do zera wcięć przy <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="efe25-146">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="efe25-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efe25-147">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [<span data-ttu-id="efe25-148">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="efe25-148">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
