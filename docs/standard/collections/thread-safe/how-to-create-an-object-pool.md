---
title: "Porady: tworzenie puli obiektów przy użyciu ConcurrentBag"
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
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 66cde52d7453e149510d0c2e1d63f9e9182e3e99
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="d222d-102">Porady: tworzenie puli obiektów przy użyciu ConcurrentBag</span><span class="sxs-lookup"><span data-stu-id="d222d-102">How to: Create an Object Pool by Using a ConcurrentBag</span></span>
<span data-ttu-id="d222d-103">Ten przykład przedstawia użycie zbiór równoczesnych do zaimplementowania puli obiektów.</span><span class="sxs-lookup"><span data-stu-id="d222d-103">This example shows how to use a concurrent bag to implement an object pool.</span></span> <span data-ttu-id="d222d-104">Pule obiektu może poprawić wydajność aplikacji w sytuacji, gdy wymagają wielu wystąpień klasy i klasa jest kosztowne do utworzenia lub zniszczenia.</span><span class="sxs-lookup"><span data-stu-id="d222d-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="d222d-105">Gdy program kliencki zażąda nowy obiekt, puli obiektów najpierw próbuje udostępnić, który został już utworzony i zwrócony do puli.</span><span class="sxs-lookup"><span data-stu-id="d222d-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="d222d-106">Jeśli żaden nie jest dostępny, następnie jest tworzony nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="d222d-106">If none is available, only then is a new object created.</span></span>  
  
 <span data-ttu-id="d222d-107"><xref:System.Collections.Concurrent.ConcurrentBag%601>Służy do przechowywania obiektów, ponieważ obsługuje on szybkiego wstawiania i usuwania, szczególnie w przypadku tego samego wątku jest dodawanie i usuwanie elementów.</span><span class="sxs-lookup"><span data-stu-id="d222d-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="d222d-108">W tym przykładzie może zostać rozszerzony dodatkowe ma zostać utworzony wokół <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, który implementuje zbioru struktury danych, tak jak <xref:System.Collections.Concurrent.ConcurrentQueue%601> i <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="d222d-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d222d-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d222d-109">Example</span></span>  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="d222d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d222d-110">See Also</span></span>  
 [<span data-ttu-id="d222d-111">Kolekcje bezpieczne wątkowo</span><span class="sxs-lookup"><span data-stu-id="d222d-111">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
