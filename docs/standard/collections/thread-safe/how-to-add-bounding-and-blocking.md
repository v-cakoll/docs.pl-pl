---
title: 'Porady: dodawanie do kolekcji funkcji blokujących i ograniczających'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
ms.openlocfilehash: 33c0b5a93a9c63e3e743a04e69bb7353ac69fa8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711288"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>Porady: dodawanie do kolekcji funkcji blokujących i ograniczających
W tym przykładzie pokazano, jak dodać funkcje ograniczające i <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> blokujące do klasy kolekcji niestandardowej, implementując interfejs <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>w klasie, a następnie używając wystąpienia klasy jako mechanizmu magazynu wewnętrznego dla . Aby uzyskać więcej informacji na temat granic i blokowania, zobacz [BlockingCollection Omówienie](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
## <a name="example"></a>Przykład  
 Klasa kolekcji niestandardowej jest kolejką priorytetu podstawowego, w której <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> poziomy priorytetu są reprezentowane jako tablica obiektów. W każdej kolejce nie jest wykonywana żadna dodatkowa kolejność.  
  
 W kodzie klienta są uruchamiane trzy zadania. Pierwsze zadanie tylko sonduje dla pociągnięć klawiatury, aby włączyć anulowanie w dowolnym momencie podczas wykonywania. Drugim zadaniem jest wątek producenta; dodaje nowe elementy do kolekcji blokowania i nadaje każdemu elementowi priorytet na podstawie wartości losowej. Trzecie zadanie usuwa elementy z kolekcji, gdy stają się one dostępne.  
  
 Zachowanie aplikacji można dostosować, wykonując jeden z wątków działa szybciej niż inne. Jeśli producent działa szybciej, można zauważyć, że funkcje ograniczające, jak blokowanie kolekcji zapobiega dodania elementów, jeśli już zawiera liczbę elementów, które są określone w konstruktorze. Jeśli konsument działa szybciej, można zauważyć, że funkcja blokowania, jak konsument czeka na nowy element, który ma zostać dodany.  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 Domyślnie magazyn dla <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> a <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>jest .  
  
## <a name="see-also"></a>Zobacz też

- [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
