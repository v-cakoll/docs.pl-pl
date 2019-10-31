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
ms.openlocfilehash: 14f4f1402f564d38bb508e893521a3951c1509f4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139707"
---
# <a name="how-to-write-a-parallelfor-loop-with-thread-local-variables"></a>Porady: zapisywanie równoległej pętli For ze zmiennymi lokalnymi wątku
Ten przykład pokazuje, jak używać zmiennych lokalnych wątku do przechowywania i pobierania stanu w każdym osobnym zadaniu, które jest tworzone przez pętlę <xref:System.Threading.Tasks.Parallel.For%2A>. Przy użyciu danych z wątków lokalnych można uniknąć obciążenia synchronizacji dużej liczby dostępu do stanu udostępnionego. Zamiast zapisywać do zasobu udostępnionego dla każdej iteracji, obliczenia i przechowywanie wartości będą wykonywane do momentu ukończenia wszystkich iteracji dla zadania. Następnie można napisać ostatni wynik do zasobu udostępnionego lub przekazać go do innej metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wywołuje metodę <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29>, aby obliczyć sumę wartości w tablicy zawierającej elementy 1 000 000. Wartość każdego elementu jest równa jego indeksowi.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 Pierwsze dwa parametry każdej metody <xref:System.Threading.Tasks.Parallel.For%2A> określają początkową i końcową wartość iteracji. W tym przeciążeniu metody trzeci parametr polega na zainicjowaniu stanu lokalnego. W tym kontekście stan lokalny oznacza zmienną, której okres istnienia rozciąga się od tuż przed pierwszą iteracją pętli w bieżącym wątku, do tuż po ostatniej iteracji.  
  
 Typ trzeciego parametru to <xref:System.Func%601>, gdzie `TResult` jest typem zmiennej, w której będzie przechowywany stan wątku lokalnego. Jego typ jest definiowany przez argument typu ogólnego dostarczone podczas wywoływania metody ogólnej <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29>, która w tym przypadku jest <xref:System.Int64>. Argument typu nakazuje kompilatorowi typ zmiennej tymczasowej, która będzie używana do przechowywania stanu wątku-lokalnego. W tym przykładzie wyrażenie `() => 0` (lub `Function() 0` w Visual Basic) inicjuje zmienną lokalną wątku na zero. Jeśli argument typu ogólnego jest typem referencyjnym lub typem wartości zdefiniowanym przez użytkownika, wyrażenie będzie wyglądać następująco:  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Czwarty parametr definiuje logikę pętli. Musi być delegatem lub wyrażeniem lambda, którego podpis jest `Func<int, ParallelLoopState, long, long>` C# w lub `Func(Of Integer, ParallelLoopState, Long, Long)` w Visual Basic. Pierwszy parametr jest wartością licznika pętli dla tej iteracji pętli. Drugi jest obiektem <xref:System.Threading.Tasks.ParallelLoopState>, którego można użyć do przerwania pętli; Ten obiekt jest dostarczany przez klasę <xref:System.Threading.Tasks.Parallel> do każdego wystąpienia pętli. Trzeci parametr jest zmienną lokalną wątku. Ostatni parametr jest typem zwracanym. W tym przypadku typem jest <xref:System.Int64>, ponieważ jest to typ określony w argumencie typu <xref:System.Threading.Tasks.Parallel.For%2A>. Ta zmienna nosi nazwę `subtotal` i jest zwracana przez wyrażenie lambda. Wartość zwracana jest używana do inicjowania `subtotal` w każdej kolejnej iteracji pętli. Ten ostatni parametr można również traktować jako wartość, która jest przesyłana do każdej iteracji, a następnie przekazywać do delegata `localFinally` po zakończeniu ostatniej iteracji.  
  
 Piąty parametr definiuje metodę, która jest wywoływana raz, po ukończeniu wszystkich iteracji w określonym wątku. Typ argumentu wejściowego jest ponownie odnosił się do argumentu typu metody <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> i typu zwracanego przez wyrażenie lambda Body. W tym przykładzie wartość jest dodawana do zmiennej w zakresie klasy w bezpiecznym wątku przez wywołanie metody <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType>. Za pomocą zmiennej lokalnej wątku, możemy uniknąć zapisywania do tej zmiennej klasy w każdej iteracji pętli.  
  
 Aby uzyskać więcej informacji na temat używania wyrażeń lambda, zobacz [lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="see-also"></a>Zobacz także

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
