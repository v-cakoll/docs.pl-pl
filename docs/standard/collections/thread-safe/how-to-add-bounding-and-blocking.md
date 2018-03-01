---
title: "Porady: dodawanie do kolekcji funkcji blokujących i ograniczających"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7fe57d99382c3472d0af5e5f64f7b237692b921b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a><span data-ttu-id="5daa4-102">Porady: dodawanie do kolekcji funkcji blokujących i ograniczających</span><span class="sxs-lookup"><span data-stu-id="5daa4-102">How to: Add Bounding and Blocking Functionality to a Collection</span></span>
<span data-ttu-id="5daa4-103">W tym przykładzie przedstawiono sposób dodawania funkcji do takiej klasy kolekcji niestandardowych blokujących implementując i ograniczających <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> interfejsu w klasie, a następnie użyć wystąpienia klasy jako mechanizm wewnętrzny magazyn <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5daa4-103">This example shows how to add bounding and blocking functionality to a custom collection class by implementing the <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> interface in the class, and then using a class instance as the internal storage mechanism for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5daa4-104">Aby uzyskać więcej informacji na temat blokujących i ograniczających, zobacz [BlockingCollection — Przegląd](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5daa4-104">For more information about bounding and blocking, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5daa4-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="5daa4-105">Example</span></span>  
 <span data-ttu-id="5daa4-106">Klasa kolekcji niestandardowej jest kolejką priorytetem podstawowy, w których poziomy priorytetu są reprezentowane jako tablica <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> obiektów.</span><span class="sxs-lookup"><span data-stu-id="5daa4-106">The custom collection class is a basic priority queue in which the priority levels are represented as an array of <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="5daa4-107">Dodatkowe kolejność nie jest wykonywane w ramach każdej kolejki.</span><span class="sxs-lookup"><span data-stu-id="5daa4-107">No additional ordering is performed within each queue.</span></span>  
  
 <span data-ttu-id="5daa4-108">W kodzie klienta trzy zadania są uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="5daa4-108">In the client code, three tasks are started.</span></span> <span data-ttu-id="5daa4-109">Pierwszym zadaniem sonduje tylko dla pociągnięć klawiatury włączyć anulowania w dowolnym momencie podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5daa4-109">The first task just polls for keyboard strokes to enable cancellation at any point during execution.</span></span> <span data-ttu-id="5daa4-110">Drugie zadanie jest wątku producent; Dodaje nowe elementy do blokowania kolekcji, a daje każdego elementu na podstawie wartości losowych priorytet.</span><span class="sxs-lookup"><span data-stu-id="5daa4-110">The second task is the producer thread; it adds new items to the blocking collection and gives each item a priority based on a random value.</span></span> <span data-ttu-id="5daa4-111">Trzeci zadanie powoduje usunięcie elementów z kolekcji jako staną się dostępne.</span><span class="sxs-lookup"><span data-stu-id="5daa4-111">The third task removes items from the collection as they become available.</span></span>  
  
 <span data-ttu-id="5daa4-112">Można dostosować zachowanie aplikacji poprzez jeden z wątków działają szybciej niż innych.</span><span class="sxs-lookup"><span data-stu-id="5daa4-112">You can adjust the behavior of the application by making one of the threads run faster than the other.</span></span> <span data-ttu-id="5daa4-113">Producent działa szybciej, można zauważyć ograniczający funkcji jako blokowania kolekcji zapobiega dodawaniu Jeśli już zawiera liczbę elementów, który jest określony w Konstruktorze elementów.</span><span class="sxs-lookup"><span data-stu-id="5daa4-113">If the producer runs faster, you will notice the bounding functionality as the blocking collection prevents items from being added if it already contains the number of items that is specified in the constructor.</span></span> <span data-ttu-id="5daa4-114">Jeśli użytkownik uruchamia szybciej, można zauważyć, funkcją blokowania jako klient czeka na nowy element do dodania.</span><span class="sxs-lookup"><span data-stu-id="5daa4-114">If the consumer runs faster, you will notice the blocking functionality as the consumer waits for a new item to be added.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 <span data-ttu-id="5daa4-115">Domyślnie magazyn dla <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> jest <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5daa4-115">By default, the storage for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> is <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5daa4-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5daa4-116">See Also</span></span>  
 [<span data-ttu-id="5daa4-117">Kolekcje bezpieczne wątkowo</span><span class="sxs-lookup"><span data-stu-id="5daa4-117">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
