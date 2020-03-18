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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139707"
---
# <a name="how-to-write-a-parallelfor-loop-with-thread-local-variables"></a>Porady: zapisywanie równoległej pętli For ze zmiennymi lokalnymi wątku
W tym przykładzie pokazano, jak używać zmiennych lokalnych wątku do przechowywania <xref:System.Threading.Tasks.Parallel.For%2A> i pobierania stanu w każdym oddzielnym zadaniu utworzonym przez pętlę. Za pomocą danych lokalnych wątku, można uniknąć narzutów synchronizacji dużej liczby dostępu do stanu udostępnionego. Zamiast zapisywać do zasobu udostępnionego na każdej iteracji, należy obliczyć i przechowywać wartość, dopóki wszystkie iteracje dla zadania zostaną zakończone. Następnie można zapisać wynik końcowy raz do zasobu udostępnionego lub przekazać go do innej metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wywołuje <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metodę do obliczania sumy wartości w tablicy, która zawiera milion elementów. Wartość każdego elementu jest równa jego indeksu.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 Pierwsze dwa parametry każdej <xref:System.Threading.Tasks.Parallel.For%2A> metody określają początkowe i końcowe wartości iteracji. W tym przeciążeniu metody trzeci parametr jest, gdzie zainicjować stan lokalny. W tym kontekście stan lokalny oznacza zmienną, której okres istnienia rozciąga się od tuż przed pierwszą iteracją pętli w bieżącym wątku, do tuż po ostatniej iteracji.  
  
 Typ trzeciego parametru jest <xref:System.Func%601> `TResult` where jest typem zmiennej, która będzie przechowywać stan lokalny wątku. Jego typ jest zdefiniowany przez argument typu <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> ogólnego podany podczas <xref:System.Int64>wywoływania metody ogólnej, która w tym przypadku jest . Argument typu informuje kompilator typu zmiennej tymczasowej, która będzie używana do przechowywania stanu lokalnego wątku. W tym przykładzie `() => 0` wyrażenie `Function() 0` (lub w języku Visual Basic) inicjuje zmienną lokalną wątku do zera. Jeśli argument typu ogólnego jest typem odwołania lub typem wartości zdefiniowanym przez użytkownika, wyrażenie będzie wyglądać tak:  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Czwarty parametr definiuje logikę pętli. Musi to być wyrażenie delegata lub lambda, którego podpis znajduje się `Func<int, ParallelLoopState, long, long>` w języku C# lub `Func(Of Integer, ParallelLoopState, Long, Long)` w języku Visual Basic. Pierwszy parametr jest wartością licznika pętli dla tej iteracji pętli. Drugi to <xref:System.Threading.Tasks.ParallelLoopState> obiekt, który może służyć do wyrwania się z pętli; ten obiekt jest <xref:System.Threading.Tasks.Parallel> dostarczany przez klasę do każdego wystąpienia pętli. Trzeci parametr jest zmienną lokalną wątku. Ostatni parametr jest typem zwracania. W takim przypadku typ <xref:System.Int64> jest, ponieważ jest to <xref:System.Threading.Tasks.Parallel.For%2A> typ, który określił w argument typu. Ta zmienna `subtotal` jest nazwany i jest zwracany przez wyrażenie lambda. Wartość zwracana jest używana `subtotal` do inicjowania na każdej kolejnej iteracji pętli. Ten ostatni parametr można również pomyśleć jako wartość, która jest przekazywana `localFinally` do każdej iteracji, a następnie przekazywana do pełnomocnika po zakończeniu ostatniej iteracji.  
  
 Piąty parametr definiuje metodę, która jest wywoływana raz, po zakończeniu wszystkich iteracji w określonym wątku. Typ argumentu wejściowego ponownie odpowiada argumentowi <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> typu metody i typowi zwróconemu przez wyrażenie lambda. W tym przykładzie wartość jest dodawana do zmiennej w <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> zakresie klasy w bezpieczny sposób wątku, wywołując metodę. Za pomocą zmiennej lokalnej wątku, uniknięliśmy zapisywania do tej zmiennej klasy na każdej iteracji pętli.  
  
 Aby uzyskać więcej informacji na temat używania wyrażeń lambda, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="see-also"></a>Zobacz też

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
