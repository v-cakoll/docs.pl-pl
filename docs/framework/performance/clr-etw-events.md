---
title: Zdarzenia ETW CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
ms.openlocfilehash: 3763e93ff3a14819f59102a01cf3285e85afd12d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716210"
---
# <a name="clr-etw-events"></a><span data-ttu-id="d0db5-102">Zdarzenia ETW CLR</span><span class="sxs-lookup"><span data-stu-id="d0db5-102">CLR ETW Events</span></span>
<span data-ttu-id="d0db5-103">W tematach w tej sekcji opisano zdarzenia śledzenia zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="d0db5-103">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="d0db5-104">Każde zdarzenie ma skojarzone słowo kluczowe i poziom, które są opisane w temacie [słowa kluczowe ETW środowiska CLR i poziomy](clr-etw-keywords-and-levels.md) .</span><span class="sxs-lookup"><span data-stu-id="d0db5-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="d0db5-105">Środowisko CLR ma dwóch dostawców dla zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="d0db5-105">The CLR has two providers for the events:</span></span>  
  
- <span data-ttu-id="d0db5-106">Dostawca środowiska uruchomieniowego, który wywołuje zdarzenia w zależności od tego, które słowa kluczowe (kategorie zdarzeń) są włączone.</span><span class="sxs-lookup"><span data-stu-id="d0db5-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="d0db5-107">Identyfikator GUID dostawcy środowiska uruchomieniowego CLR to e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="d0db5-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
- <span data-ttu-id="d0db5-108">Dostawca uwalniania, który ma specjalne zastosowania.</span><span class="sxs-lookup"><span data-stu-id="d0db5-108">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="d0db5-109">Identyfikator GUID dostawcy uwalniania CLR to a669021c-c450-4609-a035-5af59af4df18.</span><span class="sxs-lookup"><span data-stu-id="d0db5-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="d0db5-110">Więcej informacji o dostawcach znajduje się w temacie [dostawcy CLR ETW](clr-etw-providers.md).</span><span class="sxs-lookup"><span data-stu-id="d0db5-110">For more information about the providers, see [CLR ETW Providers](clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0db5-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d0db5-111">In This Section</span></span>  
 [<span data-ttu-id="d0db5-112">Informacje o zdarzeniach środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d0db5-112">Runtime Information Events</span></span>](runtime-information-etw-events.md)  
 <span data-ttu-id="d0db5-113">Przechwytuje informacje o środowisku uruchomieniowym, w tym jednostkę SKU, numer wersji, sposób aktywowania środowiska uruchomieniowego, parametry wiersza polecenia, które zostały uruchomione, identyfikator GUID (jeśli dotyczy) i inne istotne informacje.</span><span class="sxs-lookup"><span data-stu-id="d0db5-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="d0db5-114">Zdarzenie wyjątku ETW Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="d0db5-114">Exception Thrown_V1 Event</span></span>](exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="d0db5-115">Przechwytuje informacje o wygenerowanych wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="d0db5-115">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="d0db5-116">Zdarzenia rywalizacji</span><span class="sxs-lookup"><span data-stu-id="d0db5-116">Contention Events</span></span>](contention-etw-events.md)  
 <span data-ttu-id="d0db5-117">Przechwytuje informacje o rywalizacji o blokady monitora lub blokady natywne używane przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="d0db5-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="d0db5-118">Zdarzenia puli wątków</span><span class="sxs-lookup"><span data-stu-id="d0db5-118">Thread Pool Events</span></span>](thread-pool-etw-events.md)  
 <span data-ttu-id="d0db5-119">Przechwytuje informacje o pulach wątków roboczych i pulach wątków we/wy.</span><span class="sxs-lookup"><span data-stu-id="d0db5-119">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="d0db5-120">Zdarzenia modułu ładującego</span><span class="sxs-lookup"><span data-stu-id="d0db5-120">Loader Events</span></span>](loader-etw-events.md)  
 <span data-ttu-id="d0db5-121">Przechwytuje informacje dotyczące ładowania i zwalniania domen aplikacji, zestawów i modułów.</span><span class="sxs-lookup"><span data-stu-id="d0db5-121">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="d0db5-122">Zdarzenia metod</span><span class="sxs-lookup"><span data-stu-id="d0db5-122">Method Events</span></span>](method-etw-events.md)  
 <span data-ttu-id="d0db5-123">Przechwytuje informacje o metodach CLR rozpoznawania symboli.</span><span class="sxs-lookup"><span data-stu-id="d0db5-123">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="d0db5-124">Zdarzenia odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="d0db5-124">Garbage Collection Events</span></span>](garbage-collection-etw-events.md)  
 <span data-ttu-id="d0db5-125">Przechwytuje informacje dotyczące wyrzucania elementów bezużytecznych, aby ułatwić diagnostykę i debugowanie.</span><span class="sxs-lookup"><span data-stu-id="d0db5-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="d0db5-126">Zdarzenia śledzenia JIT</span><span class="sxs-lookup"><span data-stu-id="d0db5-126">JIT Tracing Events</span></span>](jit-tracing-etw-events.md)  
 <span data-ttu-id="d0db5-127">Przechwytuje informacje o wywołaniach deokładzinowych i końcowych just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="d0db5-127">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="d0db5-128">Zdarzenia międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="d0db5-128">Interop Events</span></span>](interop-etw-events.md)  
 <span data-ttu-id="d0db5-129">Przechwytuje informacje o generacji i buforowaniu klasy języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="d0db5-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="d0db5-130">Zdarzenia ARM</span><span class="sxs-lookup"><span data-stu-id="d0db5-130">ARM Events</span></span>](application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="d0db5-131">Przechwytuje szczegółowe informacje diagnostyczne o stanie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0db5-131">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="d0db5-132">Zdarzenia zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d0db5-132">Security Events</span></span>](security-etw-events.md)  
 <span data-ttu-id="d0db5-133">Przechwytuje informacje o silnych nazwach i weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="d0db5-133">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="d0db5-134">Zdarzenie stosu</span><span class="sxs-lookup"><span data-stu-id="d0db5-134">Stack Event</span></span>](stack-etw-event.md)  
 <span data-ttu-id="d0db5-135">Przechwytuje informacje, które są używane z innymi zdarzeniami do generowania śladów stosu po podniesieniu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d0db5-135">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0db5-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0db5-136">See also</span></span>

- [<span data-ttu-id="d0db5-137">Ulepszanie debugowania i dostrajania wydajności za pomocą funkcji ETW</span><span class="sxs-lookup"><span data-stu-id="d0db5-137">Improve Debugging And Performance Tuning With ETW</span></span>](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)
- [<span data-ttu-id="d0db5-138">Blog o wydajności systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d0db5-138">Windows Performance Blog</span></span>](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/)
- [<span data-ttu-id="d0db5-139">Kontrolowanie logowania w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d0db5-139">Controlling .NET Framework Logging</span></span>](controlling-logging.md)
- [<span data-ttu-id="d0db5-140">Dostawcy CLR ETW</span><span class="sxs-lookup"><span data-stu-id="d0db5-140">CLR ETW Providers</span></span>](clr-etw-providers.md)
- [<span data-ttu-id="d0db5-141">Słowa kluczowe i poziomy ETW CLR</span><span class="sxs-lookup"><span data-stu-id="d0db5-141">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)
- [<span data-ttu-id="d0db5-142">Zdarzenia ETW w środowisku CLR</span><span class="sxs-lookup"><span data-stu-id="d0db5-142">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
