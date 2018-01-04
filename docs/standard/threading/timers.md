---
title: Czasomierze
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 80b4cee03e934d3aec98ca323aac43f934c56455
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="timers"></a><span data-ttu-id="5208e-102">Czasomierze</span><span class="sxs-lookup"><span data-stu-id="5208e-102">Timers</span></span>
<span data-ttu-id="5208e-103">Czasomierze są lekkie obiekty, które umożliwiają określenie delegata do wywołania w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="5208e-103">Timers are lightweight objects that enable you to specify a delegate to be called at a specified time.</span></span> <span data-ttu-id="5208e-104">Wątek w puli wątków wykonuje operację oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="5208e-104">A thread in the thread pool performs the wait operation.</span></span>  
  
 <span data-ttu-id="5208e-105">Przy użyciu <xref:System.Threading.Timer?displayProperty=nameWithType> klasy jest prosta.</span><span class="sxs-lookup"><span data-stu-id="5208e-105">Using the <xref:System.Threading.Timer?displayProperty=nameWithType> class is straightforward.</span></span> <span data-ttu-id="5208e-106">Możesz utworzyć **czasomierza**, przechodzącą <xref:System.Threading.TimerCallback> delegowany do metody wywołania zwrotnego, obiekt reprezentujący stan, który zostanie przekazany do wywołania zwrotnego, zgłoś początkowej czas i czas reprezentujący w okresie między wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="5208e-106">You create a **Timer**, passing a <xref:System.Threading.TimerCallback> delegate to the callback method, an object representing state that will be passed to the callback, an initial raise time, and a time representing the period between callback invocations.</span></span> <span data-ttu-id="5208e-107">Aby anulować oczekujące czasomierza, należy wywołać **Timer.Dispose** funkcji.</span><span class="sxs-lookup"><span data-stu-id="5208e-107">To cancel a pending timer, call the **Timer.Dispose** function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5208e-108">Istnieją dwa inne klasy czasomierza.</span><span class="sxs-lookup"><span data-stu-id="5208e-108">There are two other timer classes.</span></span> <span data-ttu-id="5208e-109"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType> Klasy jest formant, który działa za pomocą wizualnych projektantów i ma być używany w kontekstach interfejsu użytkownika; zgłasza zdarzenia w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5208e-109">The <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> class is a control that works with visual designers and is meant to be used in user interface contexts; it raises events on the user interface thread.</span></span> <span data-ttu-id="5208e-110"><xref:System.Timers.Timer?displayProperty=nameWithType> Pochodną klasy <xref:System.ComponentModel.Component>, dlatego może służyć za pomocą wizualnych projektantów; zgłasza zdarzeń, ale uruchamia je na <xref:System.Threading.ThreadPool> wątku.</span><span class="sxs-lookup"><span data-stu-id="5208e-110">The <xref:System.Timers.Timer?displayProperty=nameWithType> class derives from <xref:System.ComponentModel.Component>, so it can be used with visual designers; it also raises events, but it raises them on a <xref:System.Threading.ThreadPool> thread.</span></span> <span data-ttu-id="5208e-111"><xref:System.Threading.Timer?displayProperty=nameWithType> Klasy nawiązuje wywołania zwrotne <xref:System.Threading.ThreadPool> wątku i nie używa modelu zdarzeń w ogóle.</span><span class="sxs-lookup"><span data-stu-id="5208e-111">The <xref:System.Threading.Timer?displayProperty=nameWithType> class makes callbacks on a <xref:System.Threading.ThreadPool> thread and does not use the event model at all.</span></span> <span data-ttu-id="5208e-112">Umożliwia także obiekt stanu do metody wywołania zwrotnego, które nie zawierają innych czasomierzy.</span><span class="sxs-lookup"><span data-stu-id="5208e-112">It also provides a state object to the callback method, which the other timers do not.</span></span> <span data-ttu-id="5208e-113">Jest bardzo uproszczonego.</span><span class="sxs-lookup"><span data-stu-id="5208e-113">It is extremely lightweight.</span></span>  
  
 <span data-ttu-id="5208e-114">Poniższy przykładowy kod uruchamia czasomierz, która rozpoczyna się po jednej sekundy (1000 milisekund) i znaczniki co sekundę, dopóki nie zostanie naciśnięty klawisz **Enter** klucza.</span><span class="sxs-lookup"><span data-stu-id="5208e-114">The following code example starts a timer that starts after one second (1000 milliseconds) and ticks every second until you press the **Enter** key.</span></span> <span data-ttu-id="5208e-115">Zmienna zawierające odwołania do czasomierz jest polem poziomie klasy, aby upewnić się, że Czasomierz nie podlega wyrzucanie elementów bezużytecznych podczas nadal działa.</span><span class="sxs-lookup"><span data-stu-id="5208e-115">The variable containing the reference to the timer is a class-level field, to ensure that the timer is not subject to garbage collection while it is still running.</span></span> <span data-ttu-id="5208e-116">Aby uzyskać więcej informacji na agresywne wyrzucanie elementów bezużytecznych, zobacz <xref:System.GC.KeepAlive%2A>.</span><span class="sxs-lookup"><span data-stu-id="5208e-116">For more information on aggressive garbage collection, see <xref:System.GC.KeepAlive%2A>.</span></span>  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5208e-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5208e-117">See Also</span></span>  
 <xref:System.Threading.Timer>  
 [<span data-ttu-id="5208e-118">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="5208e-118">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
