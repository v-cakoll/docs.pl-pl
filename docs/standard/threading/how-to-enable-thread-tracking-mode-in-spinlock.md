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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138034"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="1dfbe-102">Porady: włączanie śledzenia wątków w strukturze SpinLock</span><span class="sxs-lookup"><span data-stu-id="1dfbe-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="1dfbe-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType>jest niskopoziomową blokadą wzajemnego wykluczenia, której można użyć w scenariuszach, które mają bardzo krótki czas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="1dfbe-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="1dfbe-104"><xref:System.Threading.SpinLock>nie jest ponownie wchodzącym na rynek.</span><span class="sxs-lookup"><span data-stu-id="1dfbe-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="1dfbe-105">Po wejściu gwintu do zamka, musi wyjść z blokady poprawnie, zanim będzie mógł wejść ponownie.</span><span class="sxs-lookup"><span data-stu-id="1dfbe-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="1dfbe-106">Zazwyczaj każda próba ponownego wprowadzenia blokady spowoduje zakleszczenie, a zakleszczenia mogą być bardzo trudne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="1dfbe-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="1dfbe-107">Jako pomoc dla <xref:System.Threading.SpinLock?displayProperty=nameWithType> rozwoju obsługuje tryb śledzenia wątków, który powoduje wyjątek, który ma zostać wygenerowany, gdy wątek próbuje ponownie wprowadzić blokadę, która już posiada.</span><span class="sxs-lookup"><span data-stu-id="1dfbe-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="1dfbe-108">Dzięki temu łatwiej zlokalizować punkt, w którym blokada nie została poprawnie wypuszczona.</span><span class="sxs-lookup"><span data-stu-id="1dfbe-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="1dfbe-109">Tryb śledzenia wątków można włączyć <xref:System.Threading.SpinLock> przy użyciu konstruktora, który przyjmuje parametr `true`wejściowy logiczny i przekazując argument .</span><span class="sxs-lookup"><span data-stu-id="1dfbe-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="1dfbe-110">Po zakończeniu fazy tworzenia i testowania wyłącz tryb śledzenia wątków, aby uzyskać lepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="1dfbe-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dfbe-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="1dfbe-111">Example</span></span>  
 <span data-ttu-id="1dfbe-112">W poniższym przykładzie przedstawiono tryb śledzenia wątków.</span><span class="sxs-lookup"><span data-stu-id="1dfbe-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="1dfbe-113">Wiersze, które poprawnie zakończyć blokadę są komentowane w celu symulacji błędu kodowania, który powoduje jeden z następujących wyników:</span><span class="sxs-lookup"><span data-stu-id="1dfbe-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
- <span data-ttu-id="1dfbe-114">Wyjątek jest zgłaszany, <xref:System.Threading.SpinLock> jeśli został utworzony `true` przy`True` użyciu argumentu ( w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="1dfbe-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
- <span data-ttu-id="1dfbe-115">Zakleszczenie, <xref:System.Threading.SpinLock> jeśli został utworzony `false` `False` przy użyciu argumentu ( w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="1dfbe-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="1dfbe-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1dfbe-116">See also</span></span>

- [<span data-ttu-id="1dfbe-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="1dfbe-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
