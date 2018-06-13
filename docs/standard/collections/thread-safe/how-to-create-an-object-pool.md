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
ms.openlocfilehash: 9239a38d1970a052567f111b57be2b6596f1e5f1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32768310"
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a>Porady: tworzenie puli obiektów przy użyciu ConcurrentBag
Ten przykład przedstawia użycie zbiór równoczesnych do zaimplementowania puli obiektów. Pule obiektu może poprawić wydajność aplikacji w sytuacji, gdy wymagają wielu wystąpień klasy i klasa jest kosztowne do utworzenia lub zniszczenia. Gdy program kliencki zażąda nowy obiekt, puli obiektów najpierw próbuje udostępnić, który został już utworzony i zwrócony do puli. Jeśli żaden nie jest dostępny, następnie jest tworzony nowy obiekt.  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601> Służy do przechowywania obiektów, ponieważ obsługuje on szybkiego wstawiania i usuwania, szczególnie w przypadku tego samego wątku jest dodawanie i usuwanie elementów. W tym przykładzie może zostać rozszerzony dodatkowe ma zostać utworzony wokół <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, który implementuje zbioru struktury danych, tak jak <xref:System.Collections.Concurrent.ConcurrentQueue%601> i <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
