---
title: Równoległość danych (Biblioteka zadań równoległych)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, data
ms.assetid: 3f05f33f-f1da-4b16-81c2-9ceff1bef449
caps.latest.revision: 25
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8d048c89ee416de0b225d3e58cd24e73e1570785
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="data-parallelism-task-parallel-library"></a>Równoległość danych (Biblioteka zadań równoległych)
*Równoległość danych* odwołuje się do scenariuszy, w których tej samej operacji jest wykonywane jednocześnie (równolegle w) w przypadku elementów w źródłowej kolekcji lub tablicy. W operacji równoległych danych kolekcji źródłowej jest partycjonowany, dzięki czemu wiele wątków może działać jednocześnie w różnych segmentach.  
  
 Zadania biblioteki równoległych (TPL) obsługuje równoległość danych za pośrednictwem <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> klasy. Ta klasa udostępnia oparte na metodzie równoległych wdrożeń [dla](~/docs/csharp/language-reference/keywords/for.md) i [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) pętli (`For` i `For Each` w języku Visual Basic). Pisanie pętli logikę <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> lub <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pętli, podobnie jak loop sekwencyjnych. Nie trzeba utworzyć wątków lub elementów pracy w kolejce. W pętli podstawowe masz nie wykonuj blokad. TPL obsługuje wszystkie niskiego poziomu pracy związanej z. Aby uzyskać szczegółowe informacje dotyczące korzystania z <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, Pobierz dokument [wzorce dla programowania równoległego: opis i stosowanie wzorów równoległych z programu .NET Framework 4](http://www.microsoft.com/download/details.aspx?id=19222). Poniższy przykładowy kod przedstawia prostą `foreach` pętli i jego odpowiednik równoległych.  
  
> [!NOTE]
>  Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie masz doświadczenia z wyrażenia lambda w języku C# lub Visual Basic, zobacz [wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Gdy równoległego pętla działa, partycje TPL źródła danych, aby pętli mogą działać jednocześnie na wielu części. W tle harmonogram zadań partycje zadań na podstawie zasobów systemowych i obciążenia. Jeśli to możliwe, harmonogram ponownie dystrybuuje pracy między wiele wątków i procesory, jeśli obciążenie staje się równowagi.  
  
> [!NOTE]
>  Można również podać własnych niestandardowych partycjonera lub harmonogram. Aby uzyskać więcej informacji, zobacz [niestandardowe Partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) i [planiści zadań](http://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65).  
  
 Zarówno <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody ma kilka przeciążeń umożliwiające można zatrzymać lub Przerwij wykonywanie pętli, monitorować stan pętli na inne wątki, zarządzania stanem lokalnej wątku, finalize obiektów wątków lokalnych, sterowania stopniem współbieżności, i tak dalej. Typy pomocnika, które włączyć tę funkcję zawierają <xref:System.Threading.Tasks.ParallelLoopState>, <xref:System.Threading.Tasks.ParallelOptions>, <xref:System.Threading.Tasks.ParallelLoopResult>, <xref:System.Threading.CancellationToken>, i <xref:System.Threading.CancellationTokenSource>.  
  
 Aby uzyskać więcej informacji, zobacz [wzorce dla programowania równoległego: opis i stosowanie wzorów równoległych z programu .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222).  
  
 Równoległość danych ze składnią deklaratywne lub typu kwerendy jest obsługiwana przez PLINQ. Aby uzyskać więcej informacji, zobacz [równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: zapisywanie prostej pętli Parallel.For](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|Opisuje sposób zapisania <xref:System.Threading.Tasks.Parallel.For%2A> pętli za pośrednictwem tablicy lub które można indeksować <xref:System.Collections.Generic.IEnumerable%601> źródła kolekcji.|  
|[Instrukcje: zapisywanie prostej pętli Parallel.ForEach](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|Opisuje sposób zapisania <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli żadnego <xref:System.Collections.Generic.IEnumerable%601> źródła kolekcji.|  
|[Porady: zatrzymywanie lub przerwa w równoległej pętli for](https://msdn.microsoft.com/library/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e)|Opisuje sposób zatrzymania lub przerwać pętlę równoległą poinformowania wszystkie wątki akcji.|  
|[Instrukcje: zapisywanie pętli Parallel.For ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Opisuje sposób zapisania <xref:System.Threading.Tasks.Parallel.For%2A> pętli, w którym każdy wątek przechowuje prywatnej zmiennej, która nie jest widoczny dla innych wątków i synchronizowanie wyniki ze wszystkich wątków po zakończeniu pętli.|  
|[Instrukcje: zapisywanie pętli Parallel.ForEach ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md)|Opisuje sposób zapisania <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli, w którym każdy wątek przechowuje prywatnej zmiennej, która nie jest widoczny dla innych wątków i synchronizowanie wyniki ze wszystkich wątków po zakończeniu pętli.|  
|[Instrukcje: anulowanie pętli Parallel.For lub ForEach](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|Opisuje sposób anulowanie równoległej pętli przy użyciu <xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Instrukcje: przyspieszanie małych jednostek pętli](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|W tym artykule opisano jeden ze sposobów przyspieszenia wykonywania, gdy wnętrze pętli jest bardzo mała.|  
|[Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Zawiera omówienie Biblioteka zadań równoległych.|  
|[Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)|Wprowadza Programowanie równoległe w .NET Framework.|  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
