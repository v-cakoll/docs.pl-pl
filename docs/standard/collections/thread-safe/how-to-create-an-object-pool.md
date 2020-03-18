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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711275"
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="0ed42-102">Porady: tworzenie puli obiektów przy użyciu ConcurrentBag</span><span class="sxs-lookup"><span data-stu-id="0ed42-102">How to: Create an Object Pool by Using a ConcurrentBag</span></span>
<span data-ttu-id="0ed42-103">W tym przykładzie pokazano, jak za pomocą równoczesnych worka do zaimplementowania puli obiektów.</span><span class="sxs-lookup"><span data-stu-id="0ed42-103">This example shows how to use a concurrent bag to implement an object pool.</span></span> <span data-ttu-id="0ed42-104">Pule obiektów może zwiększyć wydajność aplikacji w sytuacjach, gdy wymagane jest wiele wystąpień klasy i klasy jest kosztowne do utworzenia lub zniszczenia.</span><span class="sxs-lookup"><span data-stu-id="0ed42-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="0ed42-105">Gdy program kliencki żąda nowego obiektu, pula obiektów najpierw próbuje podać taki, który został już utworzony i zwrócony do puli.</span><span class="sxs-lookup"><span data-stu-id="0ed42-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="0ed42-106">Jeśli brak jest dostępny, tylko wtedy jest nowy obiekt utworzony.</span><span class="sxs-lookup"><span data-stu-id="0ed42-106">If none is available, only then is a new object created.</span></span>  
  
 <span data-ttu-id="0ed42-107"><xref:System.Collections.Concurrent.ConcurrentBag%601>służy do przechowywania obiektów, ponieważ obsługuje szybkie wstawianie i usuwanie, zwłaszcza gdy ten sam wątek jest zarówno dodawanie i usuwanie elementów.</span><span class="sxs-lookup"><span data-stu-id="0ed42-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="0ed42-108">Ten przykład może być dodatkowo rozszerzony, <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>aby być zbudowany wokół , które <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Concurrent.ConcurrentStack%601>struktura danych worka implementuje, podobnie jak i .</span><span class="sxs-lookup"><span data-stu-id="0ed42-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ed42-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ed42-109">Example</span></span>  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="0ed42-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ed42-110">See also</span></span>

- [<span data-ttu-id="0ed42-111">Kolekcje bezpieczne wątkowo</span><span class="sxs-lookup"><span data-stu-id="0ed42-111">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
