---
title: 'Instrukcje: Włączanie śledzenia wątków w strukturze SpinLock'
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
ms.openlocfilehash: 111ab87ca419217f425eb5d4bc9b52f5f30f0237
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644844"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="c21e8-102">Instrukcje: Włączanie śledzenia wątków w strukturze SpinLock</span><span class="sxs-lookup"><span data-stu-id="c21e8-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="c21e8-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> jest blokadę niskiego poziomu wzajemne wykluczenie, która służy do scenariuszy, które mają bardzo krótkim czasie oczekiwania, czas.</span><span class="sxs-lookup"><span data-stu-id="c21e8-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="c21e8-104"><xref:System.Threading.SpinLock> nie jest wielobieżnej.</span><span class="sxs-lookup"><span data-stu-id="c21e8-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="c21e8-105">Po wątku przechodzi blokady, jego musi się zakończyć blokady poprawnie przed można wprowadzić ponownie.</span><span class="sxs-lookup"><span data-stu-id="c21e8-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="c21e8-106">Zwykle wszelkie próby ponownego wprowadzania blokady spowodowałoby zakleszczenia i zakleszczenia mogą być bardzo trudne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="c21e8-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="c21e8-107">Jako pomoc do tworzenia <xref:System.Threading.SpinLock?displayProperty=nameWithType> obsługuje tryb śledzenia wątków, który powoduje wyjątek zgłaszany, gdy wątek próbuje ponownie wprowadź blokadę, który już posiada.</span><span class="sxs-lookup"><span data-stu-id="c21e8-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="c21e8-108">Dzięki temu można więcej łatwy dostęp do punktu, jaką blokady nie został zakończony poprawnie.</span><span class="sxs-lookup"><span data-stu-id="c21e8-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="c21e8-109">Tryb śledzenia wątków można włączyć za pomocą <xref:System.Threading.SpinLock> konstruktora, który przyjmuje wartość logiczną wprowadź parametr i przekazywanie w argumencie `true`.</span><span class="sxs-lookup"><span data-stu-id="c21e8-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="c21e8-110">Po zakończeniu tworzenia i testowania fazy wyłączyć tryb śledzenia wątków w celu zapewnienia lepszej wydajności.</span><span class="sxs-lookup"><span data-stu-id="c21e8-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c21e8-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c21e8-111">Example</span></span>  
 <span data-ttu-id="c21e8-112">W poniższym przykładzie pokazano śledzenia wątków.</span><span class="sxs-lookup"><span data-stu-id="c21e8-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="c21e8-113">Wiersze, które poprawnie zamknąć blokady są ujęte w komentarz do symulacji błędu w kodzie, który powoduje, że jeden z następujących wyników:</span><span class="sxs-lookup"><span data-stu-id="c21e8-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
- <span data-ttu-id="c21e8-114">Wyjątek jest generowany, jeśli <xref:System.Threading.SpinLock> został utworzony przy użyciu argumentu `true` (`True` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c21e8-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
- <span data-ttu-id="c21e8-115">Zakleszczenie Jeśli <xref:System.Threading.SpinLock> został utworzony przy użyciu argumentu `false` (`False` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c21e8-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="c21e8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c21e8-116">See also</span></span>

- [<span data-ttu-id="c21e8-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="c21e8-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
