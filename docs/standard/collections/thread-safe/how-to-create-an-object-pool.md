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
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47113546"
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a>Porady: tworzenie puli obiektów przy użyciu ConcurrentBag
Ten przykład pokazuje, jak wdrożyć puli obiektów za pomocą współbieżnego zbioru. Pule obiektu może poprawić wydajność aplikacji w sytuacjach, w którym wymagają wielu wystąpień klasy i klasa jest kosztowne do utworzenia lub zniszczenia. Gdy program kliencki zażąda nowego obiektu, puli obiektów najpierw próbuje Podaj jeden, który został już utworzony i zwrócony do puli. Jeśli żaden nie jest dostępny, następnie jest tworzony nowy obiekt.  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601> Służy do przechowywania obiektów, ponieważ obsługuje on ostatniego wstawienia i usunięcia, szczególnie w przypadku tego samego wątku jest dodawanie i usuwanie elementów. W tym przykładzie można dodatkowo rozszerzone na mają zostać zbudowane wokół <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, który implementuje zbiór struktury danych, tak jak <xref:System.Collections.Concurrent.ConcurrentQueue%601> i <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a>Zobacz także

- [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
