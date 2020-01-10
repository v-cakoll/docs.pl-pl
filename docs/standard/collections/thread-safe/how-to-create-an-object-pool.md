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
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a>Porady: tworzenie puli obiektów przy użyciu ConcurrentBag
Ten przykład pokazuje, jak używać współbieżnego zbioru do implementowania puli obiektów. Pule obiektów mogą zwiększyć wydajność aplikacji w sytuacjach, gdy wymagana jest wiele wystąpień klasy, a Klasa jest kosztowna do tworzenia lub niszczenia. Gdy program kliencki żąda nowego obiektu, Pula obiektów najpierw próbuje dostarczyć taką, która została już utworzona i zwrócona do puli. Jeśli żaden nie jest dostępny, tylko wtedy jest tworzony nowy obiekt.  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601> jest używany do przechowywania obiektów, ponieważ obsługuje szybkie Wstawianie i usuwanie, szczególnie gdy ten sam wątek dodaje i usuwa elementy. Ten przykład może być dodatkowo rozszerzany, aby można było skompilować <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, który jest implementowany przez strukturę danych zbioru, jak <xref:System.Collections.Concurrent.ConcurrentQueue%601> i <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a>Zobacz także

- [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
