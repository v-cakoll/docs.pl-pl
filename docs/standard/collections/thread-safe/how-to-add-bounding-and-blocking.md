---
title: 'Porady: dodawanie do kolekcji funkcji blokujących i ograniczających'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f52d1067a8aa907c8f1cf8b550eec82d1133b3f
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46516824"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>Porady: dodawanie do kolekcji funkcji blokujących i ograniczających
W tym przykładzie przedstawiono sposób dodawania funkcji blokujących i do klasy kolekcji niestandardowej implementując <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> interfejsu w klasie, a następnie przy użyciu wystąpienia klasy jako mechanizm wewnętrzny magazyn dla <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>. Aby uzyskać więcej informacji na temat blokujących i ograniczających zobacz [BlockingCollection — Przegląd](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
## <a name="example"></a>Przykład  
 Klasa kolekcji niestandardowej jest kolejką priorytetem podstawowy, w których poziomy priorytetów są reprezentowane jako tablicę <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> obiektów. Dodatkowe kolejność nie jest wykonywane w ramach każdej kolejki.  
  
 W kodzie klienta trzy zadania zostaną uruchomione. Pierwsze zadanie po prostu sonduje pod kątem pociągnięcia klawiatury, aby włączyć anulowania w dowolnym momencie w czasie wykonywania. Drugie zadanie jest wątek producentów; on dodawane są nowe elementy do kolekcji blokującej i zapewnia każdego elementu priorytet na podstawie wartości losowych. Trzecie zadanie usuwa elementy z kolekcji w miarę ich udostępniania.  
  
 Można dostosować zachowanie aplikacji poprzez określenie jednego z wątków, działają szybciej niż ten drugi. Jeśli producent działa szybciej, zauważysz otaczający funkcji zgodnie z kolekcji blokującej zapobiega dodawaniu Jeśli już zawiera liczbę elementów, który jest określony w Konstruktorze elementów. Konsument działa szybciej, można zauważyć blokowania funkcji jako użytkownik czeka na nowy element do dodania.  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 Domyślnie magazyn dla <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> jest <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
