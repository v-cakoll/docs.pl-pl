---
title: 'Porady: włączanie śledzenia wątków w strukturze SpinLock'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93303ba84538a85350fd09b78f9963558668b91b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="58869-102">Porady: włączanie śledzenia wątków w strukturze SpinLock</span><span class="sxs-lookup"><span data-stu-id="58869-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="58869-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> jest blokady niskiego poziomu wzajemne wykluczenie używanej w scenariuszach, w których czasy oczekiwania bardzo krótki.</span><span class="sxs-lookup"><span data-stu-id="58869-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="58869-104"><xref:System.Threading.SpinLock> nie jest wielobieżnej.</span><span class="sxs-lookup"><span data-stu-id="58869-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="58869-105">Od wątku wejścia blokady, jego musi się zakończyć blokady prawidłowo przed można wprowadzić ponownie.</span><span class="sxs-lookup"><span data-stu-id="58869-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="58869-106">Zazwyczaj próba ponowne wprowadzenie blokady spowodowałoby zakleszczenie i zakleszczenie może być bardzo trudne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="58869-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="58869-107">Jako pomoc do rozwoju <xref:System.Threading.SpinLock?displayProperty=nameWithType> obsługuje tryb śledzenia wątków, powodujący wyjątek zostanie wygenerowany, gdy wątek próbuje ponowne wprowadzenie blokady, który już zawiera.</span><span class="sxs-lookup"><span data-stu-id="58869-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="58869-108">Dzięki temu można łatwo zlokalizować więcej punktu, jaką blokady nie został zakończony poprawnie.</span><span class="sxs-lookup"><span data-stu-id="58869-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="58869-109">Tryb śledzenia wątków można włączyć za pomocą <xref:System.Threading.SpinLock> wejściowych konstruktora, który przyjmuje wartość logiczną parametru i przekazywanie w argumencie `true`.</span><span class="sxs-lookup"><span data-stu-id="58869-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="58869-110">Po zakończeniu tworzenia i testowania fazy, należy wyłączyć tryb śledzenia wątków w celu poprawy wydajności.</span><span class="sxs-lookup"><span data-stu-id="58869-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58869-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="58869-111">Example</span></span>  
 <span data-ttu-id="58869-112">W poniższym przykładzie pokazano śledzenia wątków.</span><span class="sxs-lookup"><span data-stu-id="58869-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="58869-113">Wiersze, które prawidłowo zakończyć blokady są oznaczone jako komentarz do symulowania błąd kodowania, który powoduje, że jeden z następujących wyników:</span><span class="sxs-lookup"><span data-stu-id="58869-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
-   <span data-ttu-id="58869-114">Jest zwracany wyjątek, jeśli <xref:System.Threading.SpinLock> został utworzony przy użyciu argumentu `true` (`True` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="58869-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
-   <span data-ttu-id="58869-115">Jeśli do zakleszczenia <xref:System.Threading.SpinLock> został utworzony przy użyciu argumentu `false` (`False` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="58869-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="58869-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58869-116">See Also</span></span>  
 [<span data-ttu-id="58869-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="58869-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
