---
title: Thread.Suspend, odzyskiwanie pamięci i punkty bezpieczeństwa
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc3af01167fe97b701bdb0c7bc37af02d8e8a77c
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44511909"
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a><span data-ttu-id="cc0c1-102">Thread.Suspend, odzyskiwanie pamięci i punkty bezpieczeństwa</span><span class="sxs-lookup"><span data-stu-id="cc0c1-102">Thread.Suspend, Garbage Collection, and Safe Points</span></span>
<span data-ttu-id="cc0c1-103">Gdy wywołujesz <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> w wątku, system — informacje o że zawieszenia wątku zażądano i zezwala na wykonanie, dopóki osiągnie bezpieczny punkt rzeczywiście wstrzymania wątku wątku.</span><span class="sxs-lookup"><span data-stu-id="cc0c1-103">When you call <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> on a thread, the system notes that a thread suspension has been requested and allows the thread to execute until it has reached a safe point before actually suspending the thread.</span></span> <span data-ttu-id="cc0c1-104">Punkt bezpieczne dla wątków jest punktem w jej wykonanie w pamięci, które mogą być wykonywane kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cc0c1-104">A safe point for a thread is a point in its execution at which garbage collection can be performed.</span></span>  
  
 <span data-ttu-id="cc0c1-105">Po osiągnięciu punktu bezpiecznego środowiska wykonawczego gwarantuje, że wstrzymania wątku nie spowoduje żadnych dalszych postępów w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="cc0c1-105">Once a safe point is reached, the runtime guarantees that the suspended thread will not make any further progress in managed code.</span></span> <span data-ttu-id="cc0c1-106">Wątek wykonywania poza zarządzanego kodu zawsze jest bezpieczny dla wyrzucania elementów bezużytecznych, a jego wykonywanie jest kontynuowane do czasu jej podejmie próbę wznowienia wykonywanie kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="cc0c1-106">A thread executing outside managed code is always safe for garbage collection, and its execution continues until it attempts to resume execution of managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc0c1-107">Aby można było przeprowadzić wyrzucanie elementów bezużytecznych, środowisko wykonawcze musi zawiesić wszystkie wątki z wyjątkiem wątku wykonującego kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cc0c1-107">In order to perform a garbage collection, the runtime must suspend all the threads except the thread performing the collection.</span></span> <span data-ttu-id="cc0c1-108">Każdy wątek można przełączyć do bezpiecznego punktu, zanim może zostać zawieszone.</span><span class="sxs-lookup"><span data-stu-id="cc0c1-108">Each thread must be brought to a safe point before it can be suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc0c1-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc0c1-109">See also</span></span>

- <xref:System.Threading.Thread>  
- <xref:System.GC>  
- [<span data-ttu-id="cc0c1-110">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="cc0c1-110">Threading</span></span>](../../../docs/standard/threading/index.md)  
- [<span data-ttu-id="cc0c1-111">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="cc0c1-111">Automatic Memory Management</span></span>](../../../docs/standard/automatic-memory-management.md)
