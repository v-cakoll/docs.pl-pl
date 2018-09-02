---
title: Zdarzenia ETW CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 983c38567667da911132217dcfda37c009dc833c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423488"
---
# <a name="clr-etw-events"></a><span data-ttu-id="ae848-102">Zdarzenia ETW CLR</span><span class="sxs-lookup"><span data-stu-id="ae848-102">CLR ETW Events</span></span>
<span data-ttu-id="ae848-103">W tematach w tej sekcji opisano śledzenie zdarzeń systemu Windows (ETW) zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae848-103">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="ae848-104">Każde zdarzenie ma skojarzone słowo kluczowe i poziomu, które są opisane w [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="ae848-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="ae848-105">Środowisko CLR ma dwóch dostawców na potrzeby zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="ae848-105">The CLR has two providers for the events:</span></span>  
  
-   <span data-ttu-id="ae848-106">Dostawca środowiska uruchomieniowego wywołuje zdarzenia, w zależności od tego, które są włączone słów kluczowych (kategorie zdarzeń).</span><span class="sxs-lookup"><span data-stu-id="ae848-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="ae848-107">Identyfikator GUID dostawcy środowiska uruchomieniowego CLR to e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="ae848-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
-   <span data-ttu-id="ae848-108">Dostawca podsumowań, który ma zastosowań specjalnych.</span><span class="sxs-lookup"><span data-stu-id="ae848-108">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="ae848-109">Identyfikator GUID dostawcy podsumowań CLR jest a669021c-c450-4609-a035-5af59af4df18.</span><span class="sxs-lookup"><span data-stu-id="ae848-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="ae848-110">Aby uzyskać więcej informacji na temat dostawców zobacz [dostawcy ETW CLR](../../../docs/framework/performance/clr-etw-providers.md).</span><span class="sxs-lookup"><span data-stu-id="ae848-110">For more information about the providers, see [CLR ETW Providers](../../../docs/framework/performance/clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ae848-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ae848-111">In This Section</span></span>  
 [<span data-ttu-id="ae848-112">Informacje o zdarzeniach środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ae848-112">Runtime Information Events</span></span>](../../../docs/framework/performance/runtime-information-etw-events.md)  
 <span data-ttu-id="ae848-113">Rejestruje informacje o środowisku uruchomieniowym jednostki SKU i numer wersji, w taki sposób, w którym został aktywowany środowiska uruchomieniowego, w tym parametry wiersza polecenia, który został uruchomiony przy użyciu identyfikatora GUID (jeśli dotyczy) oraz inne istotne informacje.</span><span class="sxs-lookup"><span data-stu-id="ae848-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="ae848-114">Zdarzenie wyjątku ETW Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="ae848-114">Exception Thrown_V1 Event</span></span>](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="ae848-115">Znajdują się informacje dotyczące wyjątków, które są generowane.</span><span class="sxs-lookup"><span data-stu-id="ae848-115">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="ae848-116">Zdarzenia rywalizacji</span><span class="sxs-lookup"><span data-stu-id="ae848-116">Contention Events</span></span>](../../../docs/framework/performance/contention-etw-events.md)  
 <span data-ttu-id="ae848-117">Przechwytuje informacje o Rywalizacja o blokady monitora lub natywnych blokad, których używa środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ae848-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="ae848-118">Zdarzenia puli wątków</span><span class="sxs-lookup"><span data-stu-id="ae848-118">Thread Pool Events</span></span>](../../../docs/framework/performance/thread-pool-etw-events.md)  
 <span data-ttu-id="ae848-119">Przechwytuje informacji na temat pul wątków procesów roboczych i pul wątków We/Wy.</span><span class="sxs-lookup"><span data-stu-id="ae848-119">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="ae848-120">Zdarzenia modułu ładującego</span><span class="sxs-lookup"><span data-stu-id="ae848-120">Loader Events</span></span>](../../../docs/framework/performance/loader-etw-events.md)  
 <span data-ttu-id="ae848-121">Przechwytuje informacje dotyczące ładowanie i zwalnianie domen aplikacji, zestawów i modułów.</span><span class="sxs-lookup"><span data-stu-id="ae848-121">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="ae848-122">Zdarzenia metod</span><span class="sxs-lookup"><span data-stu-id="ae848-122">Method Events</span></span>](../../../docs/framework/performance/method-etw-events.md)  
 <span data-ttu-id="ae848-123">Przechwytuje informacje o metodach CLR dla rozpoznawania symboli.</span><span class="sxs-lookup"><span data-stu-id="ae848-123">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="ae848-124">Zdarzenia odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="ae848-124">Garbage Collection Events</span></span>](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 <span data-ttu-id="ae848-125">Przechwytuje informacje dotyczące wyrzucania elementów bezużytecznych, aby pomóc w Diagnostyka i debugowanie.</span><span class="sxs-lookup"><span data-stu-id="ae848-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="ae848-126">Zdarzenia śledzenia JIT</span><span class="sxs-lookup"><span data-stu-id="ae848-126">JIT Tracing Events</span></span>](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 <span data-ttu-id="ae848-127">Przechwytuje informacje dotyczące just-in-time (JIT) wbudowanie i wywołania zakończenia.</span><span class="sxs-lookup"><span data-stu-id="ae848-127">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="ae848-128">Zdarzenia międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="ae848-128">Interop Events</span></span>](../../../docs/framework/performance/interop-etw-events.md)  
 <span data-ttu-id="ae848-129">Przechwytuje informacje dotyczące generowania szkieletu intermediate language (MSIL) firmy Microsoft i buforowania.</span><span class="sxs-lookup"><span data-stu-id="ae848-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="ae848-130">Zdarzenia ARM</span><span class="sxs-lookup"><span data-stu-id="ae848-130">ARM Events</span></span>](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="ae848-131">Przechwytywanie szczegółowych informacji diagnostycznych o stanie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ae848-131">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="ae848-132">Zdarzenia zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ae848-132">Security Events</span></span>](../../../docs/framework/performance/security-etw-events.md)  
 <span data-ttu-id="ae848-133">Przechwytuje informacje o silnej nazwie i weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="ae848-133">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="ae848-134">Zdarzenie stosu</span><span class="sxs-lookup"><span data-stu-id="ae848-134">Stack Event</span></span>](../../../docs/framework/performance/stack-etw-event.md)  
 <span data-ttu-id="ae848-135">Przechwytuje informacje, które jest używany z innymi zdarzeniami można wygenerować ślady stosu, po wydarzenie jest podniesione.</span><span class="sxs-lookup"><span data-stu-id="ae848-135">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae848-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae848-136">See Also</span></span>  
 [<span data-ttu-id="ae848-137">Poprawić debugowania i dostrajania wydajności za pomocą funkcji ETW</span><span class="sxs-lookup"><span data-stu-id="ae848-137">Improve Debugging And Performance Tuning With ETW</span></span>](https://go.microsoft.com/fwlink/?LinkId=179696)  
 [<span data-ttu-id="ae848-138">Blog poświęcony wydajności Windows</span><span class="sxs-lookup"><span data-stu-id="ae848-138">Windows Performance Blog</span></span>](https://go.microsoft.com/fwlink/?LinkId=179509)  
 [<span data-ttu-id="ae848-139">Kontrolowanie logowania w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ae848-139">Controlling .NET Framework Logging</span></span>](../../../docs/framework/performance/controlling-logging.md)  
 [<span data-ttu-id="ae848-140">Dostawcy CLR ETW</span><span class="sxs-lookup"><span data-stu-id="ae848-140">CLR ETW Providers</span></span>](../../../docs/framework/performance/clr-etw-providers.md)  
 [<span data-ttu-id="ae848-141">Słowa kluczowe i poziomy ETW CLR</span><span class="sxs-lookup"><span data-stu-id="ae848-141">CLR ETW Keywords and Levels</span></span>](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 [<span data-ttu-id="ae848-142">Zdarzenia ETW w środowisku CLR</span><span class="sxs-lookup"><span data-stu-id="ae848-142">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
