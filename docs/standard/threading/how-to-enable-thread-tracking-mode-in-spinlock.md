---
title: "Porady: włączanie śledzenia wątków w strukturze SpinLock"
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
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f3d5b40f1f7b4b7534a44f4f7ab542d33d373702
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="67b04-102">Porady: włączanie śledzenia wątków w strukturze SpinLock</span><span class="sxs-lookup"><span data-stu-id="67b04-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="67b04-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType>jest blokady niskiego poziomu wzajemne wykluczenie używanej w scenariuszach, w których czasy oczekiwania bardzo krótki.</span><span class="sxs-lookup"><span data-stu-id="67b04-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="67b04-104"><xref:System.Threading.SpinLock>nie jest wielobieżnej.</span><span class="sxs-lookup"><span data-stu-id="67b04-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="67b04-105">Od wątku wejścia blokady, jego musi się zakończyć blokady prawidłowo przed można wprowadzić ponownie.</span><span class="sxs-lookup"><span data-stu-id="67b04-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="67b04-106">Zazwyczaj próba ponowne wprowadzenie blokady spowodowałoby zakleszczenie i zakleszczenie może być bardzo trudne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="67b04-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="67b04-107">Jako pomoc do rozwoju <xref:System.Threading.SpinLock?displayProperty=nameWithType> obsługuje tryb śledzenia wątków, powodujący wyjątek zostanie wygenerowany, gdy wątek próbuje ponowne wprowadzenie blokady, który już zawiera.</span><span class="sxs-lookup"><span data-stu-id="67b04-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="67b04-108">Dzięki temu można łatwo zlokalizować więcej punktu, jaką blokady nie został zakończony poprawnie.</span><span class="sxs-lookup"><span data-stu-id="67b04-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="67b04-109">Tryb śledzenia wątków można włączyć za pomocą <xref:System.Threading.SpinLock> wejściowych konstruktora, który przyjmuje wartość logiczną parametru i przekazywanie w argumencie `true`.</span><span class="sxs-lookup"><span data-stu-id="67b04-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="67b04-110">Po zakończeniu tworzenia i testowania fazy, należy wyłączyć tryb śledzenia wątków w celu poprawy wydajności.</span><span class="sxs-lookup"><span data-stu-id="67b04-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67b04-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="67b04-111">Example</span></span>  
 <span data-ttu-id="67b04-112">W poniższym przykładzie pokazano śledzenia wątków.</span><span class="sxs-lookup"><span data-stu-id="67b04-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="67b04-113">Wiersze, które prawidłowo zakończyć blokady są oznaczone jako komentarz do symulowania błąd kodowania, który powoduje, że jeden z następujących wyników:</span><span class="sxs-lookup"><span data-stu-id="67b04-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
-   <span data-ttu-id="67b04-114">Jest zwracany wyjątek, jeśli <xref:System.Threading.SpinLock> został utworzony przy użyciu argumentu `true` (`True` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="67b04-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
-   <span data-ttu-id="67b04-115">Jeśli do zakleszczenia <xref:System.Threading.SpinLock> został utworzony przy użyciu argumentu `false` (`False` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="67b04-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="67b04-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67b04-116">See Also</span></span>  
 [<span data-ttu-id="67b04-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="67b04-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
