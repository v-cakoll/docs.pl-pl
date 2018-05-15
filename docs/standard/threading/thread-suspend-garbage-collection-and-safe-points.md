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
ms.openlocfilehash: ded5c057b1c257e8bcf3c8427f5810720eaf0947
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a><span data-ttu-id="fcc4d-102">Thread.Suspend, odzyskiwanie pamięci i punkty bezpieczeństwa</span><span class="sxs-lookup"><span data-stu-id="fcc4d-102">Thread.Suspend, Garbage Collection, and Safe Points</span></span>
<span data-ttu-id="fcc4d-103">Podczas wywoływania <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> w wątku, system uwagi dotyczące czy zawieszenia wątku zażądano i umożliwia wątku do wykonania, dopóki osiągnie bezpiecznym faktycznie wstrzymania wątku.</span><span class="sxs-lookup"><span data-stu-id="fcc4d-103">When you call <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> on a thread, the system notes that a thread suspension has been requested and allows the thread to execute until it has reached a safe point before actually suspending the thread.</span></span> <span data-ttu-id="fcc4d-104">Bezpieczne punktu dla wątku jest punktem w pamięci, które mogą być wykonywane kolekcji podczas jej wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fcc4d-104">A safe point for a thread is a point in its execution at which garbage collection can be performed.</span></span>  
  
 <span data-ttu-id="fcc4d-105">Po osiągnięciu punktu bezpieczne środowisko uruchomieniowe gwarantuje, że wątku zawieszonym nie dokona żadnych dalszych postępów w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="fcc4d-105">Once a safe point is reached, the runtime guarantees that the suspended thread will not make any further progress in managed code.</span></span> <span data-ttu-id="fcc4d-106">Wątek wykonywania poza kod zarządzany jest zawsze bezpieczne dla wyrzucanie elementów bezużytecznych i jego wykonywanie będzie kontynuowane, dopóki próbuje wznowić wykonywanie kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="fcc4d-106">A thread executing outside managed code is always safe for garbage collection, and its execution continues until it attempts to resume execution of managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fcc4d-107">Aby można było wykonać wyrzucania elementów bezużytecznych, środowiska uruchomieniowego musi zawiesić wszystkie wątki oprócz wątku wykonywania kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fcc4d-107">In order to perform a garbage collection, the runtime must suspend all the threads except the thread performing the collection.</span></span> <span data-ttu-id="fcc4d-108">Każdy wątek musi być wprowadzane do bezpiecznego punktu przed może zostać zawieszone.</span><span class="sxs-lookup"><span data-stu-id="fcc4d-108">Each thread must be brought to a safe point before it can be suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcc4d-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fcc4d-109">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [<span data-ttu-id="fcc4d-110">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="fcc4d-110">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="fcc4d-111">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="fcc4d-111">Automatic Memory Management</span></span>](../../../docs/standard/automatic-memory-management.md)
