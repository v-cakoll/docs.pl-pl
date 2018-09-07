---
title: 'Porady: zapisywanie równoległej pętli For ze zmiennymi lokalnymi wątku'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel for loops, how to use local state
ms.assetid: 68384064-7ee7-41e2-90e3-71f00bde01bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18458e52c6cf38b2900036613676adea3f3b2d0b
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44098925"
---
# <a name="how-to-write-a-parallelfor-loop-with-thread-local-variables"></a>Porady: zapisywanie równoległej pętli For ze zmiennymi lokalnymi wątku
W tym przykładzie pokazano, jak używać zmiennych thread-local do przechowywania i pobierania stanu w każdym zadaniu oddzielne, który jest tworzony przez <xref:System.Threading.Tasks.Parallel.For%2A> pętli. Za pomocą danych lokalnych wątku, można uniknąć konieczności synchronizowania dużej liczby dostęp do udostępnionego stanu. Zamiast pisania do udostępnionego zasobu, w każdej iteracji, obliczeń i przechowywania wartości dopiero po zakończeniu wszystkich iteracji dla zadania. Można następnie jednokrotny wynik końcowy do udostępnionego zasobu lub przekazać go do innej metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wywołuje <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metody w celu obliczenia sumy wartości w tablicy, zawierająca jeden milion elementy. Wartość każdego elementu jest równa jego indeksu.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 Dwa pierwsze parametry, z każdym <xref:System.Threading.Tasks.Parallel.For%2A> metoda Określ początkowy i końcowy wartości iteracji. Tego przeciążenia metody trzeci parametr jest, gdzie należy zainicjować swój stan lokalnego. W tym kontekście lokalnego stan oznacza, że zmienna, którego okres istnienia rozciąga się od tuż przed pierwszą iteracją pętli w bieżącym wątku, tylko po ostatniej iteracji.  
  
 Typ trzeciego parametru to <xref:System.Func%601> gdzie `TResult` jest rodzajem zmiennej, która będzie przechowywać stan wątków lokalnych. Jego typ jest zdefiniowany przez argument typu ogólnego, podczas wywoływania ogólnych <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metody, która w tym przypadku jest <xref:System.Int64>. Argument typu informuje kompilator, typ zmiennej tymczasowej, która będzie służyć do przechowywania stanu lokalnej wątku. W tym przykładzie wyrażenie `() => 0` (lub `Function() 0` w języku Visual Basic) inicjuje zmienną lokalną wątku do zera. Jeśli argument typu ogólnego jest typem referencyjnym lub typem wartości zdefiniowanej przez użytkownika, wyrażenie będzie wyglądać następująco:  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Czwarty parametr definiuje logikę pętli. Musi być delegat lub wyrażenie lambda ma podpis `Func<int, ParallelLoopState, long, long>` w języku C# lub `Func(Of Integer, ParallelLoopState, Long, Long)` w języku Visual Basic. Pierwszy parametr jest wartość licznika pętli dla tej iteracji pętli. Drugi to <xref:System.Threading.Tasks.ParallelLoopState> obiekt, który może służyć do zerwać pętlę; tego obiektu są dostarczane przez <xref:System.Threading.Tasks.Parallel> klasy do każdego wystąpienia pętli. Trzeci parametr jest zmienną lokalną wątku. Ostatni parametr jest typem zwracanym. W tym przypadku jest typ <xref:System.Int64> , ponieważ jest to typ określonej w <xref:System.Threading.Tasks.Parallel.For%2A> argument typu. Zmienna ma nazwę `subtotal` i jest zwracany przez wyrażenie lambda. Wartość zwracana służy do inicjowania `subtotal` przy poszczególnych kolejnych iteracjach pętli. Można również potraktować ten ostatni parametr jako wartość, która jest przekazywany do każdej iteracji, a następnie przekazywane do `localFinally` po zakończeniu ostatniej iteracji.  
  
 Piątego parametru definiuje metodę, która jest wywoływana jeden raz, po zakończeniu wszystkich iteracji w określonym wątku. Typ argumentu wejściowego ponownie odpowiada argument typu <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metoda i typ zwracany przez wyrażenie lambda treści. W tym przykładzie wartość jest dodawana do zmiennej w zakresie klasy w sposób bezpieczny dla wątków, wywołując <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> metody. Za pomocą zmiennej lokalnej wątku, firma Microsoft ma unikać zapisywania tej zmiennej klasy w każdej iteracji pętli.  
  
 Aby uzyskać więcej informacji o sposobie używania wyrażeń lambda, zobacz [wyrażeń Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="see-also"></a>Zobacz także

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
