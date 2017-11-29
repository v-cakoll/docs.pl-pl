---
title: Zdarzenia ETW CLR
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
caps.latest.revision: "45"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1d0619388b429bd1824a62bc29ccb222eea1ffde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="clr-etw-events"></a><span data-ttu-id="91a0d-102">Zdarzenia ETW CLR</span><span class="sxs-lookup"><span data-stu-id="91a0d-102">CLR ETW Events</span></span>
<span data-ttu-id="91a0d-103">W tematach w tej sekcji opisano zdarzenia śledzenia dla zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="91a0d-103">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="91a0d-104">Każde zdarzenie ma skojarzone — słowo kluczowe i poziomu, które są opisane w [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="91a0d-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="91a0d-105">Środowisko CLR ma dwóch dostawców na potrzeby zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="91a0d-105">The CLR has two providers for the events:</span></span>  
  
-   <span data-ttu-id="91a0d-106">Dostawcy środowiska uruchomieniowego, który informuje o zdarzeniach, w zależności od tego, które są włączone słowa kluczowe (kategorie zdarzeń).</span><span class="sxs-lookup"><span data-stu-id="91a0d-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="91a0d-107">Dostawca środowiska uruchomieniowego CLR identyfikator GUID jest e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="91a0d-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
-   <span data-ttu-id="91a0d-108">Używa stert dostawcy, który ma specjalnych.</span><span class="sxs-lookup"><span data-stu-id="91a0d-108">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="91a0d-109">Dostawca stert CLR identyfikator GUID jest a669021c-c450-4609-a035-5af59af4df18.</span><span class="sxs-lookup"><span data-stu-id="91a0d-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="91a0d-110">Aby uzyskać więcej informacji o dostawcach, zobacz [dostawcy ETW CLR](../../../docs/framework/performance/clr-etw-providers.md).</span><span class="sxs-lookup"><span data-stu-id="91a0d-110">For more information about the providers, see [CLR ETW Providers](../../../docs/framework/performance/clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="91a0d-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="91a0d-111">In This Section</span></span>  
 [<span data-ttu-id="91a0d-112">Środowisko uruchomieniowe informacje o zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="91a0d-112">Runtime Information Events</span></span>](../../../docs/framework/performance/runtime-information-etw-events.md)  
 <span data-ttu-id="91a0d-113">Przechwytuje informacji na temat środowiska uruchomieniowego, jednostka SKU, numer wersji, sposób, w którym środowiska wykonawczego został aktywowany, w tym parametry wiersza polecenia, który został uruchomiony z identyfikatorem GUID (jeśli dotyczy) oraz inne istotne informacje.</span><span class="sxs-lookup"><span data-stu-id="91a0d-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="91a0d-114">Zdarzenie wyjątku ETW Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="91a0d-114">Exception Thrown_V1 Event</span></span>](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="91a0d-115">Przechwytuje informacje dotyczące wyjątków, które są zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="91a0d-115">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="91a0d-116">Zdarzenia rywalizacji</span><span class="sxs-lookup"><span data-stu-id="91a0d-116">Contention Events</span></span>](../../../docs/framework/performance/contention-etw-events.md)  
 <span data-ttu-id="91a0d-117">Przechwytuje informacje o rywalizacji blokad monitora lub blokad natywnego używane przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="91a0d-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="91a0d-118">Zdarzenia puli wątków</span><span class="sxs-lookup"><span data-stu-id="91a0d-118">Thread Pool Events</span></span>](../../../docs/framework/performance/thread-pool-etw-events.md)  
 <span data-ttu-id="91a0d-119">Przechwytuje informacje o puli wątków roboczych i pule wątków We/Wy.</span><span class="sxs-lookup"><span data-stu-id="91a0d-119">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="91a0d-120">Zdarzenia modułu ładującego</span><span class="sxs-lookup"><span data-stu-id="91a0d-120">Loader Events</span></span>](../../../docs/framework/performance/loader-etw-events.md)  
 <span data-ttu-id="91a0d-121">Przechwytuje informacje dotyczące ładowanie i zwalnianie domen aplikacji, zestawów i modułów.</span><span class="sxs-lookup"><span data-stu-id="91a0d-121">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="91a0d-122">Zdarzenia metod</span><span class="sxs-lookup"><span data-stu-id="91a0d-122">Method Events</span></span>](../../../docs/framework/performance/method-etw-events.md)  
 <span data-ttu-id="91a0d-123">Przechwytuje informacje o metodach CLR do rozpoznawania symboli.</span><span class="sxs-lookup"><span data-stu-id="91a0d-123">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="91a0d-124">Zdarzenia wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="91a0d-124">Garbage Collection Events</span></span>](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 <span data-ttu-id="91a0d-125">Przechwytuje informacje dotyczące pamięci, aby pomóc w diagnostyki i debugowanie.</span><span class="sxs-lookup"><span data-stu-id="91a0d-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="91a0d-126">Zdarzenia śledzenia JIT</span><span class="sxs-lookup"><span data-stu-id="91a0d-126">JIT Tracing Events</span></span>](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 <span data-ttu-id="91a0d-127">Przechwytuje informacje dotyczące just-in-time (JIT) ze śródwierszowaniem i wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="91a0d-127">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="91a0d-128">Zdarzenia międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="91a0d-128">Interop Events</span></span>](../../../docs/framework/performance/interop-etw-events.md)  
 <span data-ttu-id="91a0d-129">Przechwytuje informacje dotyczące generowania szkieletu język pośredni (MSIL) firmy Microsoft i buforowania.</span><span class="sxs-lookup"><span data-stu-id="91a0d-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="91a0d-130">Zdarzenia ARM</span><span class="sxs-lookup"><span data-stu-id="91a0d-130">ARM Events</span></span>](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="91a0d-131">Przechwytywanie szczegółowe informacje diagnostyczne o stanie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91a0d-131">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="91a0d-132">Zdarzenia zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="91a0d-132">Security Events</span></span>](../../../docs/framework/performance/security-etw-events.md)  
 <span data-ttu-id="91a0d-133">Przechwytuje informacje o silnej nazwie i weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="91a0d-133">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="91a0d-134">Zdarzenie stosu</span><span class="sxs-lookup"><span data-stu-id="91a0d-134">Stack Event</span></span>](../../../docs/framework/performance/stack-etw-event.md)  
 <span data-ttu-id="91a0d-135">Przechwytuje informacje, które jest używany z innymi zdarzeniami do generowania ślady stosu, po wywołaniu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="91a0d-135">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a0d-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91a0d-136">See Also</span></span>  
 [<span data-ttu-id="91a0d-137">Poprawa debugowania i dostrajania wydajności za pomocą funkcji ETW</span><span class="sxs-lookup"><span data-stu-id="91a0d-137">Improve Debugging And Performance Tuning With ETW</span></span>](http://go.microsoft.com/fwlink/?LinkId=179696)  
 [<span data-ttu-id="91a0d-138">Blog dotyczący wydajności systemu Windows</span><span class="sxs-lookup"><span data-stu-id="91a0d-138">Windows Performance Blog</span></span>](http://go.microsoft.com/fwlink/?LinkId=179509)  
 [<span data-ttu-id="91a0d-139">Kontrolowanie .NET Framework rejestrowania</span><span class="sxs-lookup"><span data-stu-id="91a0d-139">Controlling .NET Framework Logging</span></span>](../../../docs/framework/performance/controlling-logging.md)  
 [<span data-ttu-id="91a0d-140">Dostawcy CLR ETW</span><span class="sxs-lookup"><span data-stu-id="91a0d-140">CLR ETW Providers</span></span>](../../../docs/framework/performance/clr-etw-providers.md)  
 [<span data-ttu-id="91a0d-141">Słowa kluczowe CLR ETW i poziomy</span><span class="sxs-lookup"><span data-stu-id="91a0d-141">CLR ETW Keywords and Levels</span></span>](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 [<span data-ttu-id="91a0d-142">Zdarzenia ETW w środowisko uruchomieniowe języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="91a0d-142">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
