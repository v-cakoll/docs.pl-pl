---
title: "Porady: synchronizacja jednoczesnych operacji za pomocą bariery"
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
helpviewer_keywords: Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b2e32fe3cec30a4da7467447aee625dfe7e379b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="92858-102">Porady: synchronizacja jednoczesnych operacji za pomocą bariery</span><span class="sxs-lookup"><span data-stu-id="92858-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="92858-103">Poniższy przykład przedstawia sposób synchronizowanie równoczesnych zadań z <xref:System.Threading.Barrier>.</span><span class="sxs-lookup"><span data-stu-id="92858-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92858-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="92858-104">Example</span></span>  
 <span data-ttu-id="92858-105">Następujący program ma zliczania liczby iteracji (lub faz) są wymagane dwa wątków do każdego Znajdź ich połowie rozwiązania do tej samej fazy za pomocą algorytmu randomizing zamieniać wyrazy.</span><span class="sxs-lookup"><span data-stu-id="92858-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="92858-106">Po każdy wątek jest przemieszane jego wyrazy, operacji po fazie bariery porównuje dwa wyników, aby zobaczyć, czy pełnym zdaniem zostało wyrenderowane w odpowiedniej kolejności programu word.</span><span class="sxs-lookup"><span data-stu-id="92858-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="92858-107">A <xref:System.Threading.Barrier> jest obiekt, który uniemożliwia pojedynczych zadań w operacji równoległej przed kontynuowaniem, aż zostanie bariera wszystkie zadania.</span><span class="sxs-lookup"><span data-stu-id="92858-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="92858-108">Jest przydatne w przypadku operacji równoległej odbywa się w fazach i każdej fazy wymaga synchronizacji między zadaniami.</span><span class="sxs-lookup"><span data-stu-id="92858-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="92858-109">W tym przykładzie są dwie fazy, aby wykonać operację.</span><span class="sxs-lookup"><span data-stu-id="92858-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="92858-110">W pierwszej fazie każdego zadania wypełnia sekcji buforu z danymi.</span><span class="sxs-lookup"><span data-stu-id="92858-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="92858-111">Po zakończeniu każdego zadania wypełnianie sekcji zadanie sygnalizuje bariery, który jest gotowy kontynuować, a następnie czeka.</span><span class="sxs-lookup"><span data-stu-id="92858-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="92858-112">Gdy wszystkie zadania mają sygnalizowane bariery, są one odblokowane i uruchamia na drugim etapie.</span><span class="sxs-lookup"><span data-stu-id="92858-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="92858-113">Bariera jest konieczne, ponieważ na drugim etapie musi mieć wszystkie zadania dostępu do wszystkich danych, który został wygenerowany w tym punkcie.</span><span class="sxs-lookup"><span data-stu-id="92858-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="92858-114">Bez bariery pierwszego zadania do wykonania może podjąć próbę odczytu z buforów, które nie zostały wypełnione jeszcze przez inne zadania.</span><span class="sxs-lookup"><span data-stu-id="92858-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="92858-115">Możesz zsynchronizować dowolną liczbę etapów w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="92858-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92858-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92858-116">See Also</span></span>  
 [<span data-ttu-id="92858-117">Struktury danych dla programowania równoległego</span><span class="sxs-lookup"><span data-stu-id="92858-117">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
