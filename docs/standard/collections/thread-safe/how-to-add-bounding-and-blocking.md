---
title: 'Porady: dodawanie do kolekcji funkcji blokujących i ograniczających'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
ms.openlocfilehash: 57a01726e897f4ddbf8df5ede53609c198012d80
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287877"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>Porady: dodawanie do kolekcji funkcji blokujących i ograniczających
Ten przykład pokazuje, jak dodać funkcje ograniczania i blokowania do niestandardowej klasy kolekcji <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> , implementując interfejs w klasie, a następnie używając wystąpienia klasy jako wewnętrznego mechanizmu magazynowania dla <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> . Aby uzyskać więcej informacji na temat ograniczania i blokowania, zobacz [BlockingCollection Overview](blockingcollection-overview.md).  
  
## <a name="example"></a>Przykład  
 Klasa kolekcji niestandardowych jest podstawową kolejką priorytetową, w której poziomy priorytetów są reprezentowane jako tablica <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> obiektów. Żadna dodatkowa kolejność nie jest przeprowadzana w ramach każdej kolejki.  
  
 W kodzie klienta uruchomiono trzy zadania. Pierwsze zadanie po prostu sonduje pod kątem pociągnięć z klawiaturą, aby umożliwić anulowanie w dowolnym momencie wykonywania. Drugie zadanie jest wątkiem producenta; dodaje nowe elementy do kolekcji blokującej i daje każdemu elementowi priorytet oparty na wartości losowej. Trzecie zadanie usuwa elementy z kolekcji, gdy staną się dostępne.  
  
 Można dostosować zachowanie aplikacji, co sprawia, że jeden z wątków działa szybciej niż inne. Jeśli producent działa szybciej, zobaczysz powiązane funkcje, ponieważ kolekcja blokująca uniemożliwia dodanie elementów, jeśli zawiera już liczbę elementów, które są określone w konstruktorze. Jeśli klient działa szybciej, zobaczysz funkcję blokowania, gdy odbiorca czeka na dodanie nowego elementu.  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 Domyślnie magazyn dla programu to <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Zobacz także

- [Kolekcje bezpieczne dla wątków](index.md)
