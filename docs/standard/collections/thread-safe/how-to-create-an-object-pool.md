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
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a>Porady: tworzenie puli obiektów przy użyciu ConcurrentBag
W tym przykładzie pokazano, jak za pomocą równoczesnych worka do zaimplementowania puli obiektów. Pule obiektów może zwiększyć wydajność aplikacji w sytuacjach, gdy wymagane jest wiele wystąpień klasy i klasy jest kosztowne do utworzenia lub zniszczenia. Gdy program kliencki żąda nowego obiektu, pula obiektów najpierw próbuje podać taki, który został już utworzony i zwrócony do puli. Jeśli brak jest dostępny, tylko wtedy jest nowy obiekt utworzony.  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601>służy do przechowywania obiektów, ponieważ obsługuje szybkie wstawianie i usuwanie, zwłaszcza gdy ten sam wątek jest zarówno dodawanie i usuwanie elementów. Ten przykład może być dodatkowo rozszerzony, <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>aby być zbudowany wokół , które <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Concurrent.ConcurrentStack%601>struktura danych worka implementuje, podobnie jak i .  
  
## <a name="example"></a>Przykład  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a>Zobacz też

- [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
