---
title: 'Instrukcje: Zapisywanie pętli Parallel.For ze zmiennymi lokalnymi wątku'
description: Zobacz przykład sposobu pisania równoległej pętli for w programie .NET, która używa zmiennych lokalnych wątków, które przechowują i pobierają stan w poszczególnych zadaniach w pętli.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel for loops, how to use local state
ms.assetid: 68384064-7ee7-41e2-90e3-71f00bde01bb
ms.openlocfilehash: 9cff507757aab2e5676df2fabb02a237a2172c17
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599792"
---
# <a name="how-to-write-a-parallelfor-loop-with-thread-local-variables"></a>Instrukcje: Zapisywanie pętli Parallel.For ze zmiennymi lokalnymi wątku
Ten przykład pokazuje, jak używać zmiennych lokalnych wątku do przechowywania i pobierania stanu w każdym osobnym zadaniu, które jest tworzone przez <xref:System.Threading.Tasks.Parallel.For%2A> pętlę. Przy użyciu danych z wątków lokalnych można uniknąć obciążenia synchronizacji dużej liczby dostępu do stanu udostępnionego. Zamiast zapisywać do zasobu udostępnionego dla każdej iteracji, obliczenia i przechowywanie wartości będą wykonywane do momentu ukończenia wszystkich iteracji dla zadania. Następnie można napisać ostatni wynik do zasobu udostępnionego lub przekazać go do innej metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wywołuje metodę, <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> Aby obliczyć sumę wartości w tablicy zawierającej elementy 1 000 000. Wartość każdego elementu jest równa jego indeksowi.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 Pierwsze dwa parametry każdej <xref:System.Threading.Tasks.Parallel.For%2A> metody określają początkową i końcową wartość iteracji. W tym przeciążeniu metody trzeci parametr polega na zainicjowaniu stanu lokalnego. W tym kontekście stan lokalny oznacza zmienną, której okres istnienia rozciąga się od tuż przed pierwszą iteracją pętli w bieżącym wątku, do tuż po ostatniej iteracji.  
  
 Typ trzeciego parametru to <xref:System.Func%601> gdzie `TResult` jest typem zmiennej, w której będzie przechowywany stan wątku lokalnego. Jego typ jest definiowany przez argument typu ogólnego dostarczone podczas wywoływania metody generycznej <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> , która w tym przypadku jest <xref:System.Int64> . Argument typu nakazuje kompilatorowi typ zmiennej tymczasowej, która będzie używana do przechowywania stanu wątku-lokalnego. W tym przykładzie wyrażenie `() => 0` (lub `Function() 0` w Visual Basic) inicjuje zmienną lokalną wątku na zero. Jeśli argument typu ogólnego jest typem referencyjnym lub typem wartości zdefiniowanym przez użytkownika, wyrażenie będzie wyglądać następująco:  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Czwarty parametr definiuje logikę pętli. Musi być delegatem lub wyrażeniem lambda, którego sygnatura jest `Func<int, ParallelLoopState, long, long>` w języku C# lub `Func(Of Integer, ParallelLoopState, Long, Long)` w Visual Basic. Pierwszy parametr jest wartością licznika pętli dla tej iteracji pętli. Sekunda jest <xref:System.Threading.Tasks.ParallelLoopState> obiektem, którego można użyć do rozbicia pętli; ten obiekt jest dostarczany przez <xref:System.Threading.Tasks.Parallel> klasę do każdego wystąpienia pętli. Trzeci parametr jest zmienną lokalną wątku. Ostatni parametr jest typem zwracanym. W tym przypadku typem jest, <xref:System.Int64> ponieważ jest to typ, który został określony w <xref:System.Threading.Tasks.Parallel.For%2A> argumencie typu. Ta zmienna ma nazwę `subtotal` i jest zwracana przez wyrażenie lambda. Wartość zwracana jest używana do inicjowania `subtotal` dla każdej kolejnej iteracji pętli. Ten ostatni parametr można również traktować jako wartość, która jest przesyłana do każdej iteracji, a następnie przekazać do `localFinally` delegata po zakończeniu ostatniej iteracji.  
  
 Piąty parametr definiuje metodę, która jest wywoływana raz, po ukończeniu wszystkich iteracji w określonym wątku. Typ argumentu wejściowego jest ponownie odnosił się do argumentu typu <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metody i typu zwracanego przez wyrażenie lambda Body. W tym przykładzie wartość jest dodawana do zmiennej w zakresie klasy w bezpiecznym wątku przez wywołanie <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> metody. Za pomocą zmiennej lokalnej wątku, możemy uniknąć zapisywania do tej zmiennej klasy w każdej iteracji pętli.  
  
 Aby uzyskać więcej informacji na temat używania wyrażeń lambda, zobacz [lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="see-also"></a>Zobacz też

- [Równoległość danych](data-parallelism-task-parallel-library.md)
- [Programowanie równoległe](index.md)
- [Biblioteka zadań równoległych (TPL)](task-parallel-library-tpl.md)
- [Wyrażenia lambda w PLINQ i TPL](lambda-expressions-in-plinq-and-tpl.md)
