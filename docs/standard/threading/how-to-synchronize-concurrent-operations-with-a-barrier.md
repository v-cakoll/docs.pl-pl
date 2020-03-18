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
ms.openlocfilehash: 33098878764c2f8a8c1f83a122028da40b984243
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137972"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="50614-102">Porady: synchronizacja jednoczesnych operacji za pomocą bariery</span><span class="sxs-lookup"><span data-stu-id="50614-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="50614-103">W poniższym przykładzie pokazano, jak <xref:System.Threading.Barrier>synchronizować równoczesne zadania z .</span><span class="sxs-lookup"><span data-stu-id="50614-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50614-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="50614-104">Example</span></span>  
 <span data-ttu-id="50614-105">Celem następującego programu jest zliczanie, ile iteracji (lub faz) są wymagane dla dwóch wątków do każdego znaleźć ich połowę rozwiązania na tej samej fazie przy użyciu algorytmu randomizacji do zmiany słów.</span><span class="sxs-lookup"><span data-stu-id="50614-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="50614-106">Po każdym wątku tasuje jego słowa, operacji po fazie bariery porównuje dwa wyniki, aby sprawdzić, czy pełne zdanie zostało wykonane w prawidłowej kolejności wyrazów.</span><span class="sxs-lookup"><span data-stu-id="50614-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="50614-107">A <xref:System.Threading.Barrier> jest obiektem, który uniemożliwia poszczególnym zadaniom w operacji równoległej kontynuowanie, dopóki wszystkie zadania nie dotrą do bariery.</span><span class="sxs-lookup"><span data-stu-id="50614-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="50614-108">Jest to przydatne, gdy operacja równoległa występuje w fazach, a każda faza wymaga synchronizacji między zadaniami.</span><span class="sxs-lookup"><span data-stu-id="50614-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="50614-109">W tym przykładzie istnieją dwie fazy operacji.</span><span class="sxs-lookup"><span data-stu-id="50614-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="50614-110">W pierwszej fazie każde zadanie wypełnia swoją sekcję buforu danymi.</span><span class="sxs-lookup"><span data-stu-id="50614-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="50614-111">Po zakończeniu każdego zadania wypełnianie jego sekcji, zadanie sygnalizuje barierę, że jest gotowy do kontynuowania, a następnie czeka.</span><span class="sxs-lookup"><span data-stu-id="50614-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="50614-112">Gdy wszystkie zadania zasygnalizowały barierę, zostaną odblokowane i rozpocznie się druga faza.</span><span class="sxs-lookup"><span data-stu-id="50614-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="50614-113">Bariera jest niezbędna, ponieważ druga faza wymaga, aby każde zadanie miało dostęp do wszystkich danych, które zostały wygenerowane do tego momentu.</span><span class="sxs-lookup"><span data-stu-id="50614-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="50614-114">Bez bariery pierwsze zadania do wykonania mogą próbować odczytać z buforów, które nie zostały jeszcze wypełnione przez inne zadania.</span><span class="sxs-lookup"><span data-stu-id="50614-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="50614-115">W ten sposób można zsynchronizować dowolną liczbę faz.</span><span class="sxs-lookup"><span data-stu-id="50614-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50614-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50614-116">See also</span></span>

- [<span data-ttu-id="50614-117">Struktury danych dla Programowania równoległego</span><span class="sxs-lookup"><span data-stu-id="50614-117">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
