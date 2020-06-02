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
ms.openlocfilehash: 2e13dfb277807eb0a9f256f74c2845f5a4d2a047
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279300"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Porady: synchronizacja jednoczesnych operacji za pomocą bariery
Poniższy przykład pokazuje, jak zsynchronizować współbieżne zadania z <xref:System.Threading.Barrier> .  
  
## <a name="example"></a>Przykład  
 Celem następującego programu jest określenie, ile iteracji (lub faz) jest wymaganych przez dwa wątki do każdego odnalezienia połowy rozwiązania na tej samej fazie przy użyciu algorytmu losowego w celu wygenerowania wyrazów. Po pobraniu przez każdy wątek słów kluczowych operacja przeprowadzenia bariery porównuje dwa wyniki, aby zobaczyć, czy pełne zdanie zostało renderowane w prawidłowym porządku wyrazów.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 A <xref:System.Threading.Barrier> to obiekt, który uniemożliwia wykonywanie poszczególnych zadań w równoległej operacji, dopóki wszystkie zadania osiągną barierę. Jest to przydatne, gdy operacja równoległa występuje w fazach, a każda faza wymaga synchronizacji między zadaniami. W tym przykładzie istnieją dwie fazy operacji. W pierwszej fazie każde zadanie wypełnia swoją sekcję buforu danymi. Gdy każde zadanie zakończy wypełnienie jego sekcji, zadanie sygnalizuje barierę, która jest gotowa do kontynuowania, a następnie czeka. Gdy wszystkie zadania zasygnalizują barierę, są odblokowane i rozpocznie się druga faza. Bariera jest konieczna, ponieważ druga faza wymaga, aby każde zadanie miało dostęp do wszystkich danych, które zostały wygenerowane w tym punkcie. Bez bariery pierwsze zadania do wykonania mogą próbować odczytać z buforów, które nie zostały jeszcze wypełnione przez inne zadania. W ten sposób można synchronizować dowolną liczbę faz.  
  
## <a name="see-also"></a>Zobacz także

- [Struktury danych dla programowania równoległego](../parallel-programming/data-structures-for-parallel-programming.md)
