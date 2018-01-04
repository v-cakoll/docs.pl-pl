---
title: "Schemat ustawień śledzenia i debugowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracing [.NET Framework], trace and debug settings schema
- configuration schema [.NET Framework], trace and debug settings
- configuration settings [.NET Framework], tracing
- schema configuration settings
- configuration settings [.NET Framework], debugging
- trace listeners, trace and debug settings schema
- configuration sections [.NET Framework]
- elements [.NET Framework], trace and debug settings
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: e6d9e5ca97e4d5940dd9de3f3ffbd4db4183196c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="trace-and-debug-settings-schema"></a><span data-ttu-id="8fc88-102">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="8fc88-102">Trace and Debug Settings Schema</span></span>
<span data-ttu-id="8fc88-103">Ustawienia śledzenia i debugowania Określ obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8fc88-103">Trace and debug settings specify trace listeners that collect, store, and route messages, and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="8fc88-104">W poniższej tabeli opisano funkcję każdy element Ustawienia śledzenia i debugowania.</span><span class="sxs-lookup"><span data-stu-id="8fc88-104">The following table describes the function of each trace and debug settings element.</span></span>  
  
|<span data-ttu-id="8fc88-105">Element</span><span class="sxs-lookup"><span data-stu-id="8fc88-105">Element</span></span>|<span data-ttu-id="8fc88-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8fc88-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8fc88-107">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="8fc88-107">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="8fc88-108">Dodaje odbiornika do `Listeners` kolekcji źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8fc88-108">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="8fc88-109">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="8fc88-109">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="8fc88-110">Dodaje odbiornika do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8fc88-110">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="8fc88-111">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="8fc88-111">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-sharedlisteners.md)|<span data-ttu-id="8fc88-112">Dodaje odbiornika do `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8fc88-112">Adds a listener to the `sharedListeners` collection.</span></span>|  
|[<span data-ttu-id="8fc88-113">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="8fc88-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="8fc88-114">Określa poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8fc88-114">Specifies the level where a trace switch is set.</span></span>|  
|[<span data-ttu-id="8fc88-115">\<Assert ></span><span class="sxs-lookup"><span data-stu-id="8fc88-115">\<assert></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<span data-ttu-id="8fc88-116">Określa, czy wyświetlać okno komunikatu po wywołaniu <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metody; określa także nazwę pliku do zapisania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8fc88-116">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="8fc88-117">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="8fc88-117">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="8fc88-118">Czyści `Listeners` kolekcji źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8fc88-118">Clears the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="8fc88-119">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="8fc88-119">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|<span data-ttu-id="8fc88-120">Czyści `Listeners` kolekcji do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8fc88-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="8fc88-121">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="8fc88-121">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="8fc88-122">Dodaje filtr do odbiornika w `Listeners` kolekcji źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8fc88-122">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="8fc88-123">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="8fc88-123">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="8fc88-124">Dodaje filtr do odbiornika w `Listeners` kolekcji do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8fc88-124">Adds a filter to a listener in the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="8fc88-125">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="8fc88-125">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="8fc88-126">Dodaje filtr do odbiornika w `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8fc88-126">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
|[<span data-ttu-id="8fc88-127">\<obiekty nasłuchujące ></span><span class="sxs-lookup"><span data-stu-id="8fc88-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="8fc88-128">Określa odbiorników dla `Listeners` kolekcji źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8fc88-128">Specifies listeners for the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="8fc88-129">\<obiekty nasłuchujące ></span><span class="sxs-lookup"><span data-stu-id="8fc88-129">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|<span data-ttu-id="8fc88-130">Określa odbiorników dla `Listeners` kolekcji do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8fc88-130">Specifies listeners for the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="8fc88-131">\<liczniki wydajności ></span><span class="sxs-lookup"><span data-stu-id="8fc88-131">\<performanceCounters></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|<span data-ttu-id="8fc88-132">Określa rozmiar pamięci globalnej współużytkowane przez liczniki wydajności.</span><span class="sxs-lookup"><span data-stu-id="8fc88-132">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="8fc88-133">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="8fc88-133">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|<span data-ttu-id="8fc88-134">Usuwa odbiornik z `Listeners` kolekcji do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8fc88-134">Removes a listener from the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="8fc88-135">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="8fc88-135">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="8fc88-136">Usuwa odbiornik z `Listeners` kolekcji źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8fc88-136">Removes a listener from the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="8fc88-137">\<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="8fc88-137">\<sharedListeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|<span data-ttu-id="8fc88-138">Zawiera nasłuchujących może odwoływać się wszystkie źródła lub element śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8fc88-138">Contains listeners that any source or trace element can reference.</span></span>|  
|[<span data-ttu-id="8fc88-139">\<źródeł ></span><span class="sxs-lookup"><span data-stu-id="8fc88-139">\<sources></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|<span data-ttu-id="8fc88-140">Zawiera źródła śledzenia, które inicjują śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8fc88-140">Contains trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="8fc88-141">\<źródło ></span><span class="sxs-lookup"><span data-stu-id="8fc88-141">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="8fc88-142">Określa źródło śledzenia, który inicjuje śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8fc88-142">Specifies a trace source that initiates tracing messages.</span></span>|  
|[<span data-ttu-id="8fc88-143">\<przełączniki ></span><span class="sxs-lookup"><span data-stu-id="8fc88-143">\<switches></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|<span data-ttu-id="8fc88-144">Zawiera przełączniki śledzenia i poziom, gdzie są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8fc88-144">Contains trace switches and the level where the trace switches are set.</span></span>|  
|[<span data-ttu-id="8fc88-145">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="8fc88-145">\<system.diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/system-diagnostics-element.md)|<span data-ttu-id="8fc88-146">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8fc88-146">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|[<span data-ttu-id="8fc88-147">\<śledzenia ></span><span class="sxs-lookup"><span data-stu-id="8fc88-147">\<trace></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|<span data-ttu-id="8fc88-148">Zawiera nasłuchujących zbierania, przechowywania i trasy śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8fc88-148">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8fc88-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8fc88-149">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="8fc88-150">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8fc88-150">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
