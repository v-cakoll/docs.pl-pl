---
title: 'Porady: tworzenie puli obiektów przy użyciu ConcurrentBag'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
ms.openlocfilehash: 888521eb5c3c3169c4b39a26e82fef2e35c286d9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711275"
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="e64bb-102">Porady: tworzenie puli obiektów przy użyciu ConcurrentBag</span><span class="sxs-lookup"><span data-stu-id="e64bb-102">How to: Create an Object Pool by Using a ConcurrentBag</span></span>
<span data-ttu-id="e64bb-103">Ten przykład pokazuje, jak używać współbieżnego zbioru do implementowania puli obiektów.</span><span class="sxs-lookup"><span data-stu-id="e64bb-103">This example shows how to use a concurrent bag to implement an object pool.</span></span> <span data-ttu-id="e64bb-104">Pule obiektów mogą zwiększyć wydajność aplikacji w sytuacjach, gdy wymagana jest wiele wystąpień klasy, a Klasa jest kosztowna do tworzenia lub niszczenia.</span><span class="sxs-lookup"><span data-stu-id="e64bb-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="e64bb-105">Gdy program kliencki żąda nowego obiektu, Pula obiektów najpierw próbuje dostarczyć taką, która została już utworzona i zwrócona do puli.</span><span class="sxs-lookup"><span data-stu-id="e64bb-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="e64bb-106">Jeśli żaden nie jest dostępny, tylko wtedy jest tworzony nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="e64bb-106">If none is available, only then is a new object created.</span></span>  
  
 <span data-ttu-id="e64bb-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> jest używany do przechowywania obiektów, ponieważ obsługuje szybkie Wstawianie i usuwanie, szczególnie gdy ten sam wątek dodaje i usuwa elementy.</span><span class="sxs-lookup"><span data-stu-id="e64bb-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="e64bb-108">Ten przykład może być dodatkowo rozszerzany, aby można było skompilować <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, który jest implementowany przez strukturę danych zbioru, jak <xref:System.Collections.Concurrent.ConcurrentQueue%601> i <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="e64bb-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e64bb-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="e64bb-109">Example</span></span>  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="e64bb-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e64bb-110">See also</span></span>

- [<span data-ttu-id="e64bb-111">Kolekcje bezpieczne wątkowo</span><span class="sxs-lookup"><span data-stu-id="e64bb-111">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
