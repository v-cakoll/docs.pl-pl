---
title: 'Porady: synchronizacja jednoczesnych operacji za pomocą bariery'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16dc60fa9cd8782efbe1b6028413138b5991839e
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44513796"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="0ab92-102">Porady: synchronizacja jednoczesnych operacji za pomocą bariery</span><span class="sxs-lookup"><span data-stu-id="0ab92-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="0ab92-103">Poniższy przykład pokazuje, jak synchronizować równoczesnych zadań za pomocą <xref:System.Threading.Barrier>.</span><span class="sxs-lookup"><span data-stu-id="0ab92-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ab92-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ab92-104">Example</span></span>  
 <span data-ttu-id="0ab92-105">Następujący program ma policzyć ile iteracji (lub fazy) są wymagane dla dwóch wątków do każdego znalezienia ich połowie rozwiązania do tej samej fazy za pomocą algorytmu randomizing zamieniać wyrazy.</span><span class="sxs-lookup"><span data-stu-id="0ab92-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="0ab92-106">Po każdy wątek ma przekazanych jego słów, operację po fazie bariery porównuje dwa wyniki, aby zobaczyć, jeśli pełnym zdaniem zostało wyrenderowane w odpowiedniej kolejności programu word.</span><span class="sxs-lookup"><span data-stu-id="0ab92-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="0ab92-107">Element <xref:System.Threading.Barrier> jest obiektem, który uniemożliwia poszczególne zadania w operacji równoległej z dalszego barierę aż wszystkie zadania.</span><span class="sxs-lookup"><span data-stu-id="0ab92-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="0ab92-108">Jest to przydatne, gdy operacji równoległej odbywa się w fazach, a każda faza wymaga synchronizacji między zadaniami.</span><span class="sxs-lookup"><span data-stu-id="0ab92-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="0ab92-109">W tym przykładzie istnieją dwie fazy, aby wykonać operację.</span><span class="sxs-lookup"><span data-stu-id="0ab92-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="0ab92-110">W pierwszej fazie każdego zadania wypełnia sekcji buforu z danymi.</span><span class="sxs-lookup"><span data-stu-id="0ab92-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="0ab92-111">Po zakończeniu każdego zadania wypełnianie swojego zadania sygnalizuje bariery, które ma być kontynuowana, a następnie czeka.</span><span class="sxs-lookup"><span data-stu-id="0ab92-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="0ab92-112">Gdy wszystkie zadania zostały zasygnalizowane barierę, są one odblokowane i rozpoczyna się w drugim etapie.</span><span class="sxs-lookup"><span data-stu-id="0ab92-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="0ab92-113">Bariera to konieczne, ponieważ drugi etap wymaga, że każde zadanie podrzędne mają dostęp do wszystkich danych, który został wygenerowany z tym punktem.</span><span class="sxs-lookup"><span data-stu-id="0ab92-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="0ab92-114">Bez barierze pierwszego zadania do wykonania może próbować odczytywać buforów, które nie zostały wypełnione jeszcze przez inne zadania.</span><span class="sxs-lookup"><span data-stu-id="0ab92-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="0ab92-115">Możliwe jest zsynchronizowanie dowolną liczbę etapów w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="0ab92-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ab92-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ab92-116">See also</span></span>

- [<span data-ttu-id="0ab92-117">Struktury danych dla programowania równoległego</span><span class="sxs-lookup"><span data-stu-id="0ab92-117">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
