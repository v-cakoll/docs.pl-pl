---
title: 'Porady: dodawanie do kolekcji funkcji blokujących i ograniczających'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f52d1067a8aa907c8f1cf8b550eec82d1133b3f
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45516438"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a><span data-ttu-id="6d676-102">Porady: dodawanie do kolekcji funkcji blokujących i ograniczających</span><span class="sxs-lookup"><span data-stu-id="6d676-102">How to: Add Bounding and Blocking Functionality to a Collection</span></span>
<span data-ttu-id="6d676-103">W tym przykładzie przedstawiono sposób dodawania funkcji blokujących i do klasy kolekcji niestandardowej implementując <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> interfejsu w klasie, a następnie przy użyciu wystąpienia klasy jako mechanizm wewnętrzny magazyn dla <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6d676-103">This example shows how to add bounding and blocking functionality to a custom collection class by implementing the <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> interface in the class, and then using a class instance as the internal storage mechanism for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6d676-104">Aby uzyskać więcej informacji na temat blokujących i ograniczających zobacz [BlockingCollection — Przegląd](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6d676-104">For more information about bounding and blocking, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d676-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d676-105">Example</span></span>  
 <span data-ttu-id="6d676-106">Klasa kolekcji niestandardowej jest kolejką priorytetem podstawowy, w których poziomy priorytetów są reprezentowane jako tablicę <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> obiektów.</span><span class="sxs-lookup"><span data-stu-id="6d676-106">The custom collection class is a basic priority queue in which the priority levels are represented as an array of <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="6d676-107">Dodatkowe kolejność nie jest wykonywane w ramach każdej kolejki.</span><span class="sxs-lookup"><span data-stu-id="6d676-107">No additional ordering is performed within each queue.</span></span>  
  
 <span data-ttu-id="6d676-108">W kodzie klienta trzy zadania zostaną uruchomione.</span><span class="sxs-lookup"><span data-stu-id="6d676-108">In the client code, three tasks are started.</span></span> <span data-ttu-id="6d676-109">Pierwsze zadanie po prostu sonduje pod kątem pociągnięcia klawiatury, aby włączyć anulowania w dowolnym momencie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6d676-109">The first task just polls for keyboard strokes to enable cancellation at any point during execution.</span></span> <span data-ttu-id="6d676-110">Drugie zadanie jest wątek producentów; on dodawane są nowe elementy do kolekcji blokującej i zapewnia każdego elementu priorytet na podstawie wartości losowych.</span><span class="sxs-lookup"><span data-stu-id="6d676-110">The second task is the producer thread; it adds new items to the blocking collection and gives each item a priority based on a random value.</span></span> <span data-ttu-id="6d676-111">Trzecie zadanie usuwa elementy z kolekcji w miarę ich udostępniania.</span><span class="sxs-lookup"><span data-stu-id="6d676-111">The third task removes items from the collection as they become available.</span></span>  
  
 <span data-ttu-id="6d676-112">Można dostosować zachowanie aplikacji poprzez określenie jednego z wątków, działają szybciej niż ten drugi.</span><span class="sxs-lookup"><span data-stu-id="6d676-112">You can adjust the behavior of the application by making one of the threads run faster than the other.</span></span> <span data-ttu-id="6d676-113">Jeśli producent działa szybciej, zauważysz otaczający funkcji zgodnie z kolekcji blokującej zapobiega dodawaniu Jeśli już zawiera liczbę elementów, który jest określony w Konstruktorze elementów.</span><span class="sxs-lookup"><span data-stu-id="6d676-113">If the producer runs faster, you will notice the bounding functionality as the blocking collection prevents items from being added if it already contains the number of items that is specified in the constructor.</span></span> <span data-ttu-id="6d676-114">Konsument działa szybciej, można zauważyć blokowania funkcji jako użytkownik czeka na nowy element do dodania.</span><span class="sxs-lookup"><span data-stu-id="6d676-114">If the consumer runs faster, you will notice the blocking functionality as the consumer waits for a new item to be added.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 <span data-ttu-id="6d676-115">Domyślnie magazyn dla <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> jest <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6d676-115">By default, the storage for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> is <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d676-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d676-116">See also</span></span>

- [<span data-ttu-id="6d676-117">Kolekcje bezpieczne wątkowo</span><span class="sxs-lookup"><span data-stu-id="6d676-117">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
