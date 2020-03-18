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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137972"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Porady: synchronizacja jednoczesnych operacji za pomocą bariery
W poniższym przykładzie pokazano, jak <xref:System.Threading.Barrier>synchronizować równoczesne zadania z .  
  
## <a name="example"></a>Przykład  
 Celem następującego programu jest zliczanie, ile iteracji (lub faz) są wymagane dla dwóch wątków do każdego znaleźć ich połowę rozwiązania na tej samej fazie przy użyciu algorytmu randomizacji do zmiany słów. Po każdym wątku tasuje jego słowa, operacji po fazie bariery porównuje dwa wyniki, aby sprawdzić, czy pełne zdanie zostało wykonane w prawidłowej kolejności wyrazów.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 A <xref:System.Threading.Barrier> jest obiektem, który uniemożliwia poszczególnym zadaniom w operacji równoległej kontynuowanie, dopóki wszystkie zadania nie dotrą do bariery. Jest to przydatne, gdy operacja równoległa występuje w fazach, a każda faza wymaga synchronizacji między zadaniami. W tym przykładzie istnieją dwie fazy operacji. W pierwszej fazie każde zadanie wypełnia swoją sekcję buforu danymi. Po zakończeniu każdego zadania wypełnianie jego sekcji, zadanie sygnalizuje barierę, że jest gotowy do kontynuowania, a następnie czeka. Gdy wszystkie zadania zasygnalizowały barierę, zostaną odblokowane i rozpocznie się druga faza. Bariera jest niezbędna, ponieważ druga faza wymaga, aby każde zadanie miało dostęp do wszystkich danych, które zostały wygenerowane do tego momentu. Bez bariery pierwsze zadania do wykonania mogą próbować odczytać z buforów, które nie zostały jeszcze wypełnione przez inne zadania. W ten sposób można zsynchronizować dowolną liczbę faz.  
  
## <a name="see-also"></a>Zobacz też

- [Struktury danych dla Programowania równoległego](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
