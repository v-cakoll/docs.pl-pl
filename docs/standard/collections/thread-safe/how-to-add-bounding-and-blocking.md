---
title: 'Porady: dodawanie do kolekcji funkcji blokujących i ograniczających'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6262822e0916e142c7c543d2e2546c8540cb73a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>Porady: dodawanie do kolekcji funkcji blokujących i ograniczających
W tym przykładzie przedstawiono sposób dodawania funkcji do takiej klasy kolekcji niestandardowych blokujących implementując i ograniczających <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> interfejsu w klasie, a następnie użyć wystąpienia klasy jako mechanizm wewnętrzny magazyn <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>. Aby uzyskać więcej informacji na temat blokujących i ograniczających, zobacz [BlockingCollection — Przegląd](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
## <a name="example"></a>Przykład  
 Klasa kolekcji niestandardowej jest kolejką priorytetem podstawowy, w których poziomy priorytetu są reprezentowane jako tablica <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> obiektów. Dodatkowe kolejność nie jest wykonywane w ramach każdej kolejki.  
  
 W kodzie klienta trzy zadania są uruchamiane. Pierwszym zadaniem sonduje tylko dla pociągnięć klawiatury włączyć anulowania w dowolnym momencie podczas wykonywania. Drugie zadanie jest wątku producent; Dodaje nowe elementy do blokowania kolekcji, a daje każdego elementu na podstawie wartości losowych priorytet. Trzeci zadanie powoduje usunięcie elementów z kolekcji jako staną się dostępne.  
  
 Można dostosować zachowanie aplikacji poprzez jeden z wątków działają szybciej niż innych. Producent działa szybciej, można zauważyć ograniczający funkcji jako blokowania kolekcji zapobiega dodawaniu Jeśli już zawiera liczbę elementów, który jest określony w Konstruktorze elementów. Jeśli użytkownik uruchamia szybciej, można zauważyć, funkcją blokowania jako klient czeka na nowy element do dodania.  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 Domyślnie magazyn dla <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> jest <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
