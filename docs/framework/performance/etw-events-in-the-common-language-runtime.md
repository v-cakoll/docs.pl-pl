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
ms.openlocfilehash: 1d059a5d4df402b309f628bf3e9393114c4cdeec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191396"
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="95dd2-102">Zdarzenia ETW w środowisku CLR</span><span class="sxs-lookup"><span data-stu-id="95dd2-102">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="95dd2-103">Środowisko uruchomieniowe języka wspólnego (CLR) zapewnia śledzenie zdarzeń użyteczne informacje diagnostyczne Windows (ETW) przy użyciu szerokiej gamy debugowania i profilowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="95dd2-103">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="95dd2-104">Zdarzenia CLR ETW korzystać z systemu Windows funkcji ETW śledzenia, rozszerzyć istniejące profilowanie i debugowanie pomoc techniczna jest świadczona przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="95dd2-104">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="95dd2-105">Więcej informacji na temat funkcji ETW jest dostępna w artykule [poprawić debugowania i dostrajania wydajności za pomocą funkcji ETW](https://go.microsoft.com/fwlink/?LinkID=161142) w witrynie MSDN.</span><span class="sxs-lookup"><span data-stu-id="95dd2-105">More information about ETW is available in the article [Improve Debugging and Performance Tuning with ETW](https://go.microsoft.com/fwlink/?LinkID=161142) on MSDN.</span></span> <span data-ttu-id="95dd2-106">Informacji dotyczących narzędzia Xperf można znaleźć we wpisie [narzędzi wydajności systemu Windows — narzędzia Xperf](https://go.microsoft.com/fwlink/?LinkID=161144) w blogu NTDebugging.</span><span class="sxs-lookup"><span data-stu-id="95dd2-106">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](https://go.microsoft.com/fwlink/?LinkID=161144) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="95dd2-107">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] Lub nowszy jest wymagany na potrzeby wszystkich zdarzeń w zdarzeniu opisane tematów.</span><span class="sxs-lookup"><span data-stu-id="95dd2-107">The [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="95dd2-108">System operacyjny Windows Vista jest minimalny obsługiwany klient, a system Windows Server 2008 jest minimalny obsługiwany serwer.</span><span class="sxs-lookup"><span data-stu-id="95dd2-108">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="95dd2-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="95dd2-109">In This Section</span></span>  
 [<span data-ttu-id="95dd2-110">Kontrolowanie logowania w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="95dd2-110">Controlling .NET Framework Logging</span></span>](../../../docs/framework/performance/controlling-logging.md)  
 <span data-ttu-id="95dd2-111">W tym artykule opisano narzędzia i polecenia do przechwytywania i wyświetlania zdarzeń ETW.</span><span class="sxs-lookup"><span data-stu-id="95dd2-111">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="95dd2-112">Dostawcy CLR ETW</span><span class="sxs-lookup"><span data-stu-id="95dd2-112">CLR ETW Providers</span></span>](../../../docs/framework/performance/clr-etw-providers.md)  
 <span data-ttu-id="95dd2-113">Zawiera informacje na temat środowiska uruchomieniowego i podsumowania dostawców i jak ich używać do zbierania danych zdarzeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="95dd2-113">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="95dd2-114">Słowa kluczowe i poziomy ETW CLR</span><span class="sxs-lookup"><span data-stu-id="95dd2-114">CLR ETW Keywords and Levels</span></span>](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="95dd2-115">W tym artykule opisano kluczowe dla środowiska uruchomieniowego i podsumowania dostawców, które umożliwiają filtrowanie zdarzeń według kategorii.</span><span class="sxs-lookup"><span data-stu-id="95dd2-115">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="95dd2-116">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="95dd2-116">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)  
 <span data-ttu-id="95dd2-117">Zawiera szczegółowe informacje na temat CLR ETW, zdarzenia, ich słów kluczowych, poziomy i dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="95dd2-117">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95dd2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95dd2-118">See also</span></span>

- [<span data-ttu-id="95dd2-119">Zdarzenia ETW w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="95dd2-119">ETW Events in the .NET Framework</span></span>](../../../docs/framework/performance/etw-events.md)
