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
ms.openlocfilehash: f52a844284cf46bcace3f54f8b320d336050a64e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138034"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="b0d1a-102">Porady: włączanie śledzenia wątków w strukturze SpinLock</span><span class="sxs-lookup"><span data-stu-id="b0d1a-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="b0d1a-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> to blokada wzajemnego wykluczania niskiego poziomu, która może być używana w scenariuszach, które mają bardzo krótkie czasy oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="b0d1a-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="b0d1a-104"><xref:System.Threading.SpinLock> nie jest w odróżnieniu od siebie.</span><span class="sxs-lookup"><span data-stu-id="b0d1a-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="b0d1a-105">Po przejściu przez wątek na blokadę należy prawidłowo zamknąć blokadę, aby można było wprowadzić ją ponownie.</span><span class="sxs-lookup"><span data-stu-id="b0d1a-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="b0d1a-106">Zwykle każda próba ponownego wprowadzenia blokady spowodowałaby zakleszczenie i zakleszczenie może być bardzo trudne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="b0d1a-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="b0d1a-107">Jako pomoc dla rozwoju, <xref:System.Threading.SpinLock?displayProperty=nameWithType> obsługuje tryb śledzenia wątków, który powoduje, że wyjątek jest zgłaszany, gdy wątek próbuje ponownie wprowadzić blokadę, która już mieści się.</span><span class="sxs-lookup"><span data-stu-id="b0d1a-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="b0d1a-108">Umożliwia to łatwiejsze lokalizowanie punktu, w którym blokada nie została prawidłowo zakończona.</span><span class="sxs-lookup"><span data-stu-id="b0d1a-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="b0d1a-109">Tryb śledzenia wątków można włączyć, używając konstruktora <xref:System.Threading.SpinLock>, który przyjmuje parametr wejściowy Boolean i przekazując argument `true`.</span><span class="sxs-lookup"><span data-stu-id="b0d1a-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="b0d1a-110">Po zakończeniu etapów tworzenia i testowania Wyłącz tryb śledzenia wątków, aby uzyskać lepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="b0d1a-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0d1a-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0d1a-111">Example</span></span>  
 <span data-ttu-id="b0d1a-112">Poniższy przykład ilustruje tryb śledzenia wątków.</span><span class="sxs-lookup"><span data-stu-id="b0d1a-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="b0d1a-113">Wiersze, które prawidłowo zamykają blokadę, są oznaczone jako komentarze, aby symulować błąd kodowania, który powoduje wystąpienie jednego z następujących wyników:</span><span class="sxs-lookup"><span data-stu-id="b0d1a-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
- <span data-ttu-id="b0d1a-114">Wyjątek jest generowany, jeśli <xref:System.Threading.SpinLock> został utworzony przy użyciu argumentu `true` (`True` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b0d1a-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
- <span data-ttu-id="b0d1a-115">Zakleszczenie, jeśli <xref:System.Threading.SpinLock> został utworzony przy użyciu argumentu `false` (`False` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b0d1a-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="b0d1a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0d1a-116">See also</span></span>

- [<span data-ttu-id="b0d1a-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="b0d1a-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
