---
title: 'Porady: synchronizacja jednoczesnych operacji za pomocą bariery'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
ms.openlocfilehash: 33098878764c2f8a8c1f83a122028da40b984243
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137972"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Porady: synchronizacja jednoczesnych operacji za pomocą bariery
Poniższy przykład pokazuje, jak synchronizować współbieżne zadania z <xref:System.Threading.Barrier>.  
  
## <a name="example"></a>Przykład  
 Celem następującego programu jest określenie, ile iteracji (lub faz) jest wymaganych przez dwa wątki do każdego odnalezienia połowy rozwiązania na tej samej fazie przy użyciu algorytmu losowego w celu wygenerowania wyrazów. Po pobraniu przez każdy wątek słów kluczowych operacja przeprowadzenia bariery porównuje dwa wyniki, aby zobaczyć, czy pełne zdanie zostało renderowane w prawidłowym porządku wyrazów.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <xref:System.Threading.Barrier> jest obiektem, który uniemożliwia wykonywanie poszczególnych zadań w równoległej operacji, dopóki wszystkie zadania osiągną barierę. Jest to przydatne, gdy operacja równoległa występuje w fazach, a każda faza wymaga synchronizacji między zadaniami. W tym przykładzie istnieją dwie fazy operacji. W pierwszej fazie każde zadanie wypełnia swoją sekcję buforu danymi. Gdy każde zadanie zakończy wypełnienie jego sekcji, zadanie sygnalizuje barierę, która jest gotowa do kontynuowania, a następnie czeka. Gdy wszystkie zadania zasygnalizują barierę, są odblokowane i rozpocznie się druga faza. Bariera jest konieczna, ponieważ druga faza wymaga, aby każde zadanie miało dostęp do wszystkich danych, które zostały wygenerowane w tym punkcie. Bez bariery pierwsze zadania do wykonania mogą próbować odczytać z buforów, które nie zostały jeszcze wypełnione przez inne zadania. W ten sposób można synchronizować dowolną liczbę faz.  
  
## <a name="see-also"></a>Zobacz także

- [Struktury danych dla programowania równoległego](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
