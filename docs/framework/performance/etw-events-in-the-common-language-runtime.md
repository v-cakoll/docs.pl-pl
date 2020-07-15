---
title: Zdarzenia ETW w środowisku CLR
description: Przeczytaj podsumowanie i Wyświetl linki dotyczące zdarzeń śledzenia zdarzeń systemu Windows (ETW) w środowisku uruchomieniowym języka wspólnego (CLR).
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
ms.openlocfilehash: aa422dcb7efbc0f6f7f09e09a6c9e44b40ada86b
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309485"
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="fbac7-103">Zdarzenia ETW w środowisku CLR</span><span class="sxs-lookup"><span data-stu-id="fbac7-103">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="fbac7-104">Środowisko uruchomieniowe języka wspólnego (CLR) zapewnia użyteczne informacje diagnostyczne śledzenia zdarzeń systemu Windows (ETW) za pomocą dużej różnorodności zdarzeń debugowania i profilowania.</span><span class="sxs-lookup"><span data-stu-id="fbac7-104">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="fbac7-105">Zdarzenia ETW CLR wykorzystują system śledzenia funkcji ETW systemu Windows w celu rozszerzenia istniejącej obsługi profilowania i debugowania zapewnianej przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="fbac7-105">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="fbac7-106">Więcej informacji na temat funkcji ETW jest dostępnych w artykule [ulepszanie debugowania i dostrajania wydajności za pomocą funkcji ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) .</span><span class="sxs-lookup"><span data-stu-id="fbac7-106">More information about ETW is available in the [Improve Debugging and Performance Tuning with ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) article.</span></span> <span data-ttu-id="fbac7-107">Informacje na temat Xperf można znaleźć w wpisie [Windows Performance Toolkit-Xperf](https://docs.microsoft.com/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) w blogu NTDebugging.</span><span class="sxs-lookup"><span data-stu-id="fbac7-107">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](https://docs.microsoft.com/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="fbac7-108">W przypadku wszystkich zdarzeń opisanych w temacie zdarzenia jest wymagany .NET Framework 4 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="fbac7-108">The .NET Framework 4 or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="fbac7-109">System operacyjny Windows Vista jest minimalnym obsługiwanym klientem, a system Windows Server 2008 jest minimalnym obsługiwanym serwerem.</span><span class="sxs-lookup"><span data-stu-id="fbac7-109">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fbac7-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fbac7-110">In This Section</span></span>  
 [<span data-ttu-id="fbac7-111">Kontrolowanie logowania w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fbac7-111">Controlling .NET Framework Logging</span></span>](controlling-logging.md)  
 <span data-ttu-id="fbac7-112">Opisuje narzędzia i polecenia służące do przechwytywania i wyświetlania zdarzeń ETW.</span><span class="sxs-lookup"><span data-stu-id="fbac7-112">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="fbac7-113">Dostawcy CLR ETW</span><span class="sxs-lookup"><span data-stu-id="fbac7-113">CLR ETW Providers</span></span>](clr-etw-providers.md)  
 <span data-ttu-id="fbac7-114">Zawiera informacje o dostawcach środowiska uruchomieniowego i uwalniania oraz sposobie ich używania na potrzeby zbierania danych funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="fbac7-114">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="fbac7-115">Słowa kluczowe i poziomy ETW CLR</span><span class="sxs-lookup"><span data-stu-id="fbac7-115">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="fbac7-116">Zawiera opis słów kluczowych dla dostawców środowiska uruchomieniowego i rozmieszczonia, które umożliwiają filtrowanie zdarzeń według kategorii.</span><span class="sxs-lookup"><span data-stu-id="fbac7-116">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="fbac7-117">Zdarzenia ETW CLR</span><span class="sxs-lookup"><span data-stu-id="fbac7-117">CLR ETW Events</span></span>](clr-etw-events.md)  
 <span data-ttu-id="fbac7-118">Zawiera szczegółowe informacje na temat zdarzeń ETW CLR, ich słów kluczowych, poziomów i danych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fbac7-118">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbac7-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fbac7-119">See also</span></span>

- [<span data-ttu-id="fbac7-120">Zdarzenia ETW w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fbac7-120">ETW Events in the .NET Framework</span></span>](etw-events.md)
