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
ms.openlocfilehash: 2e13dfb277807eb0a9f256f74c2845f5a4d2a047
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279300"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="fdf26-102">Porady: synchronizacja jednoczesnych operacji za pomocą bariery</span><span class="sxs-lookup"><span data-stu-id="fdf26-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="fdf26-103">Poniższy przykład pokazuje, jak zsynchronizować współbieżne zadania z <xref:System.Threading.Barrier> .</span><span class="sxs-lookup"><span data-stu-id="fdf26-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdf26-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="fdf26-104">Example</span></span>  
 <span data-ttu-id="fdf26-105">Celem następującego programu jest określenie, ile iteracji (lub faz) jest wymaganych przez dwa wątki do każdego odnalezienia połowy rozwiązania na tej samej fazie przy użyciu algorytmu losowego w celu wygenerowania wyrazów.</span><span class="sxs-lookup"><span data-stu-id="fdf26-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="fdf26-106">Po pobraniu przez każdy wątek słów kluczowych operacja przeprowadzenia bariery porównuje dwa wyniki, aby zobaczyć, czy pełne zdanie zostało renderowane w prawidłowym porządku wyrazów.</span><span class="sxs-lookup"><span data-stu-id="fdf26-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="fdf26-107">A <xref:System.Threading.Barrier> to obiekt, który uniemożliwia wykonywanie poszczególnych zadań w równoległej operacji, dopóki wszystkie zadania osiągną barierę.</span><span class="sxs-lookup"><span data-stu-id="fdf26-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="fdf26-108">Jest to przydatne, gdy operacja równoległa występuje w fazach, a każda faza wymaga synchronizacji między zadaniami.</span><span class="sxs-lookup"><span data-stu-id="fdf26-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="fdf26-109">W tym przykładzie istnieją dwie fazy operacji.</span><span class="sxs-lookup"><span data-stu-id="fdf26-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="fdf26-110">W pierwszej fazie każde zadanie wypełnia swoją sekcję buforu danymi.</span><span class="sxs-lookup"><span data-stu-id="fdf26-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="fdf26-111">Gdy każde zadanie zakończy wypełnienie jego sekcji, zadanie sygnalizuje barierę, która jest gotowa do kontynuowania, a następnie czeka.</span><span class="sxs-lookup"><span data-stu-id="fdf26-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="fdf26-112">Gdy wszystkie zadania zasygnalizują barierę, są odblokowane i rozpocznie się druga faza.</span><span class="sxs-lookup"><span data-stu-id="fdf26-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="fdf26-113">Bariera jest konieczna, ponieważ druga faza wymaga, aby każde zadanie miało dostęp do wszystkich danych, które zostały wygenerowane w tym punkcie.</span><span class="sxs-lookup"><span data-stu-id="fdf26-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="fdf26-114">Bez bariery pierwsze zadania do wykonania mogą próbować odczytać z buforów, które nie zostały jeszcze wypełnione przez inne zadania.</span><span class="sxs-lookup"><span data-stu-id="fdf26-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="fdf26-115">W ten sposób można synchronizować dowolną liczbę faz.</span><span class="sxs-lookup"><span data-stu-id="fdf26-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdf26-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdf26-116">See also</span></span>

- [<span data-ttu-id="fdf26-117">Struktury danych dla programowania równoległego</span><span class="sxs-lookup"><span data-stu-id="fdf26-117">Data Structures for Parallel Programming</span></span>](../parallel-programming/data-structures-for-parallel-programming.md)
