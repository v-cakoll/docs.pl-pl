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
helpviewer_keywords: object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f7cb18157122d8bc053f34b21f623f3ab1e14305
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a>Porady: tworzenie puli obiektów przy użyciu ConcurrentBag
Ten przykład przedstawia użycie zbiór równoczesnych do zaimplementowania puli obiektów. Pule obiektu może poprawić wydajność aplikacji w sytuacji, gdy wymagają wielu wystąpień klasy i klasa jest kosztowne do utworzenia lub zniszczenia. Gdy program kliencki zażąda nowy obiekt, puli obiektów najpierw próbuje udostępnić, który został już utworzony i zwrócony do puli. Jeśli żaden nie jest dostępny, następnie jest tworzony nowy obiekt.  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601>Służy do przechowywania obiektów, ponieważ obsługuje on szybkiego wstawiania i usuwania, szczególnie w przypadku tego samego wątku jest dodawanie i usuwanie elementów. W tym przykładzie może zostać rozszerzony dodatkowe ma zostać utworzony wokół <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, który implementuje zbioru struktury danych, tak jak <xref:System.Collections.Concurrent.ConcurrentQueue%601> i <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcje obsługujące wielowątkowość](../../../../docs/standard/collections/thread-safe/index.md)
