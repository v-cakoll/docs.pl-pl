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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bc0c6bebbab6e84c165f41300a4cb16c8746a07
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046464"
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="e0ef4-102">Porady: tworzenie puli obiektów przy użyciu ConcurrentBag</span><span class="sxs-lookup"><span data-stu-id="e0ef4-102">How to: Create an Object Pool by Using a ConcurrentBag</span></span>
<span data-ttu-id="e0ef4-103">Ten przykład pokazuje, jak wdrożyć puli obiektów za pomocą współbieżnego zbioru.</span><span class="sxs-lookup"><span data-stu-id="e0ef4-103">This example shows how to use a concurrent bag to implement an object pool.</span></span> <span data-ttu-id="e0ef4-104">Pule obiektu może poprawić wydajność aplikacji w sytuacjach, w którym wymagają wielu wystąpień klasy i klasa jest kosztowne do utworzenia lub zniszczenia.</span><span class="sxs-lookup"><span data-stu-id="e0ef4-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="e0ef4-105">Gdy program kliencki zażąda nowego obiektu, puli obiektów najpierw próbuje Podaj jeden, który został już utworzony i zwrócony do puli.</span><span class="sxs-lookup"><span data-stu-id="e0ef4-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="e0ef4-106">Jeśli żaden nie jest dostępny, następnie jest tworzony nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="e0ef4-106">If none is available, only then is a new object created.</span></span>  
  
 <span data-ttu-id="e0ef4-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> Służy do przechowywania obiektów, ponieważ obsługuje on ostatniego wstawienia i usunięcia, szczególnie w przypadku tego samego wątku jest dodawanie i usuwanie elementów.</span><span class="sxs-lookup"><span data-stu-id="e0ef4-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="e0ef4-108">W tym przykładzie można dodatkowo rozszerzone na mają zostać zbudowane wokół <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, który implementuje zbiór struktury danych, tak jak <xref:System.Collections.Concurrent.ConcurrentQueue%601> i <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="e0ef4-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0ef4-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0ef4-109">Example</span></span>  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="e0ef4-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0ef4-110">See also</span></span>

- [<span data-ttu-id="e0ef4-111">Kolekcje bezpieczne wątkowo</span><span class="sxs-lookup"><span data-stu-id="e0ef4-111">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
