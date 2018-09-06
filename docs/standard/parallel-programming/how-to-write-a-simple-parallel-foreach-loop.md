---
title: 'Porady: zapisywanie prostej pętli Parallel.ForEach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03aaae7cd0faa7e7628da2e2e8f622f0967102cf
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891161"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Porady: zapisywanie prostej pętli Parallel.ForEach
W tym przykładzie pokazano, jak używać <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pętli, aby włączyć równoległość danych przez dowolny <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> źródła danych.  
  
> [!NOTE]
>  Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [wyrażeń Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 A <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli działa jak <xref:System.Threading.Tasks.Parallel.For%2A> pętli. Kolekcja źródłowa jest podzielona na partycje, a praca jest zaplanowane na wiele wątków, w zależności od środowiska systemu. Więcej procesorów w systemie, tym szybciej parallel — metoda jest uruchamiany. W niektórych kolekcjach źródła pętli sekwencyjnej może być szybciej, w zależności od rozmiaru źródła i rodzaju wykonywanych prac. Aby uzyskać więcej informacji o wydajności, zobacz [potencjalne pułapki związane z Równoległością danych i zadań](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)  
  
 Aby uzyskać więcej informacji na temat pętli równoległych zobacz [porady: zapisywanie prostej pętli Parallel.For](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).  
  
 Aby użyć <xref:System.Threading.Tasks.Parallel.ForEach%2A> z nieogólna kolekcja, możesz użyć <xref:System.Linq.Enumerable.Cast%2A> metodę rozszerzenia, aby przekonwertować kolekcji do kolekcji ogólnej, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 Umożliwia także Parallel LINQ (PLINQ) do zrównoleglenia przetwarzania <xref:System.Collections.Generic.IEnumerable%601> źródeł danych. PLINQ umożliwia użycie składni zapytań deklaratywne określenie zachowania pętli. Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Skopiuj i wklej ten kod do projektu programu Visual Studio 2010 konsoli aplikacji.  
  
-   Dodaj odwołanie do System.Drawing.dll  
  
-   Naciśnij klawisz F5  
  
## <a name="see-also"></a>Zobacz także

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
