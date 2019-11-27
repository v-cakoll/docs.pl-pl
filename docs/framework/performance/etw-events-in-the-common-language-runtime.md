---
title: Zdarzenia ETW w środowisku CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83246f42275425bca48530915c7bf5c19f3b9f04
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447669"
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="ebba7-102">Zdarzenia ETW w środowisku CLR</span><span class="sxs-lookup"><span data-stu-id="ebba7-102">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="ebba7-103">Środowisko uruchomieniowe języka wspólnego (CLR) zapewnia użyteczne informacje diagnostyczne śledzenia zdarzeń systemu Windows (ETW) za pomocą dużej różnorodności zdarzeń debugowania i profilowania.</span><span class="sxs-lookup"><span data-stu-id="ebba7-103">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="ebba7-104">Zdarzenia ETW CLR wykorzystują system śledzenia funkcji ETW systemu Windows w celu rozszerzenia istniejącej obsługi profilowania i debugowania zapewnianej przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="ebba7-104">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="ebba7-105">Więcej informacji na temat funkcji ETW jest dostępnych w artykule [ulepszanie debugowania i dostrajania wydajności za pomocą funkcji ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) .</span><span class="sxs-lookup"><span data-stu-id="ebba7-105">More information about ETW is available in the [Improve Debugging and Performance Tuning with ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) article.</span></span> <span data-ttu-id="ebba7-106">Informacje na temat Xperf można znaleźć w wpisie [Windows Performance Toolkit-Xperf](https://blogs.msdn.microsoft.com/ntdebugging/2008/04/03/windows-performance-toolkit-xperf/) w blogu NTDebugging.</span><span class="sxs-lookup"><span data-stu-id="ebba7-106">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](https://blogs.msdn.microsoft.com/ntdebugging/2008/04/03/windows-performance-toolkit-xperf/) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="ebba7-107">W przypadku wszystkich zdarzeń opisanych w temacie zdarzenia jest wymagany .NET Framework 4 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ebba7-107">The .NET Framework 4 or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="ebba7-108">System operacyjny Windows Vista jest minimalnym obsługiwanym klientem, a system Windows Server 2008 jest minimalnym obsługiwanym serwerem.</span><span class="sxs-lookup"><span data-stu-id="ebba7-108">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ebba7-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ebba7-109">In This Section</span></span>  
 [<span data-ttu-id="ebba7-110">Kontrolowanie logowania w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ebba7-110">Controlling .NET Framework Logging</span></span>](controlling-logging.md)  
 <span data-ttu-id="ebba7-111">Opisuje narzędzia i polecenia służące do przechwytywania i wyświetlania zdarzeń ETW.</span><span class="sxs-lookup"><span data-stu-id="ebba7-111">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="ebba7-112">Dostawcy CLR ETW</span><span class="sxs-lookup"><span data-stu-id="ebba7-112">CLR ETW Providers</span></span>](clr-etw-providers.md)  
 <span data-ttu-id="ebba7-113">Zawiera informacje o dostawcach środowiska uruchomieniowego i uwalniania oraz sposobie ich używania na potrzeby zbierania danych funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="ebba7-113">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="ebba7-114">Słowa kluczowe i poziomy ETW CLR</span><span class="sxs-lookup"><span data-stu-id="ebba7-114">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="ebba7-115">Zawiera opis słów kluczowych dla dostawców środowiska uruchomieniowego i rozmieszczonia, które umożliwiają filtrowanie zdarzeń według kategorii.</span><span class="sxs-lookup"><span data-stu-id="ebba7-115">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="ebba7-116">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="ebba7-116">CLR ETW Events</span></span>](clr-etw-events.md)  
 <span data-ttu-id="ebba7-117">Zawiera szczegółowe informacje na temat zdarzeń ETW CLR, ich słów kluczowych, poziomów i danych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ebba7-117">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebba7-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebba7-118">See also</span></span>

- [<span data-ttu-id="ebba7-119">Zdarzenia ETW w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ebba7-119">ETW Events in the .NET Framework</span></span>](etw-events.md)
