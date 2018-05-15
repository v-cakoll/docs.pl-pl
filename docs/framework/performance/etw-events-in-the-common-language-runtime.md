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
ms.openlocfilehash: 7855007c7566d3be0012bbff2cb124ee2681cb6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="92c3a-102">Zdarzenia ETW w środowisku CLR</span><span class="sxs-lookup"><span data-stu-id="92c3a-102">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="92c3a-103">Środowisko uruchomieniowe języka wspólnego (CLR) zawiera przydatne zdarzenia śledzenia dla systemu Windows (ETW) informacje diagnostyczne do szerokiej gamy debugowanie i profilowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="92c3a-103">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="92c3a-104">Zdarzenia CLR ETW wykorzystać systemu śledzenia ETW systemu Windows można rozszerzyć istniejące profilowania i debugowanie udostępniane przez środowisko uruchomieniowe języka wspólnego pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="92c3a-104">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="92c3a-105">Więcej informacji na temat funkcji ETW jest dostępna w artykule [poprawy debugowania i dostrajania wydajności za pomocą funkcji ETW](http://go.microsoft.com/fwlink/?LinkID=161142) w witrynie MSDN.</span><span class="sxs-lookup"><span data-stu-id="92c3a-105">More information about ETW is available in the article [Improve Debugging and Performance Tuning with ETW](http://go.microsoft.com/fwlink/?LinkID=161142) on MSDN.</span></span> <span data-ttu-id="92c3a-106">Informacje o program Xperf można znaleźć we wpisie [Toolkit wydajności systemu Windows — program Xperf](http://go.microsoft.com/fwlink/?LinkID=161144) w blogu NTDebugging.</span><span class="sxs-lookup"><span data-stu-id="92c3a-106">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](http://go.microsoft.com/fwlink/?LinkID=161144) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="92c3a-107">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] Lub nowszy jest wymagany na potrzeby wszystkie zdarzenia opisane w przypadku tematów.</span><span class="sxs-lookup"><span data-stu-id="92c3a-107">The [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="92c3a-108">System operacyjny Windows Vista jest minimalny obsługiwany klient i systemu Windows Server 2008 jest minimalna obsługiwana serwera.</span><span class="sxs-lookup"><span data-stu-id="92c3a-108">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92c3a-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="92c3a-109">In This Section</span></span>  
 [<span data-ttu-id="92c3a-110">Kontrolowanie logowania w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="92c3a-110">Controlling .NET Framework Logging</span></span>](../../../docs/framework/performance/controlling-logging.md)  
 <span data-ttu-id="92c3a-111">W tym artykule opisano narzędzia i polecenia służące do przechwytywania i wyświetlanie zdarzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="92c3a-111">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="92c3a-112">Dostawcy CLR ETW</span><span class="sxs-lookup"><span data-stu-id="92c3a-112">CLR ETW Providers</span></span>](../../../docs/framework/performance/clr-etw-providers.md)  
 <span data-ttu-id="92c3a-113">Udostępnia informacje na temat środowiska uruchomieniowego i stert dostawców i używania ich do zbierania danych funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="92c3a-113">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="92c3a-114">Słowa kluczowe i poziomy ETW CLR</span><span class="sxs-lookup"><span data-stu-id="92c3a-114">CLR ETW Keywords and Levels</span></span>](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="92c3a-115">W tym artykule opisano słowa kluczowe dla środowiska uruchomieniowego i stert dostawców, które umożliwiają filtrowanie zdarzenia według kategorii.</span><span class="sxs-lookup"><span data-stu-id="92c3a-115">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="92c3a-116">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="92c3a-116">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)  
 <span data-ttu-id="92c3a-117">Zawiera szczegółowe informacje dotyczące CLR ETW zdarzenia, słowa kluczowe, poziomy i dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="92c3a-117">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92c3a-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92c3a-118">See Also</span></span>  
 [<span data-ttu-id="92c3a-119">Zdarzenia ETW w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="92c3a-119">ETW Events in the .NET Framework</span></span>](../../../docs/framework/performance/etw-events.md)
