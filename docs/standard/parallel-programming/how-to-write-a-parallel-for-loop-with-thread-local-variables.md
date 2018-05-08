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
ms.openlocfilehash: a70b8e3d1f56eafc04b97a19a1582d9c664e587d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-a-parallelfor-loop-with-thread-local-variables"></a>Porady: zapisywanie równoległej pętli For ze zmiennymi lokalnymi wątku
W tym przykładzie przedstawiono użycie zmiennych thread-local do przechowywania i pobierania stanu w każdej oddzielne zadanie, które jest tworzony przez <xref:System.Threading.Tasks.Parallel.For%2A> pętli. Przy użyciu danych lokalnych wątku, można uniknąć obciążenie synchronizowania dużej liczby operacji uzyskania dostępu do stanu udostępnionego. Zamiast zapisywania do udostępnionego zasobu w każdej iteracji, obliczania i przechowywania wartości do momentu zakończenia wszystkich iteracji dla zadania. Można następnie jednokrotnego zapisu wynik końcowy udostępnianego zasobu lub przekaż go do innej metody.  
  
## <a name="example"></a>Przykład  
 Następujące przykładowe wywołania <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metodę obliczania sumę wartości w tablicy, który zawiera elementy milion. Wartość każdego elementu jest równa jego indeksu.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 Pierwsze dwa parametry co <xref:System.Threading.Tasks.Parallel.For%2A> metody Określ początkowy i końcowy wartości iteracji. To przeciążenie metody trzeci parametr jest, gdzie zainicjować stanu użytkownika lokalnego. W tym kontekście stanu lokalnego oznacza zmienną, której czas życia rozciąga się od bezpośrednio przed pierwszym iteracji pętli w bieżącym wątku, aby tylko po ostatnim iteracji.  
  
 Typ trzeciego parametru jest <xref:System.Func%601> gdzie `TResult` jest typ zmiennej, która będzie przechowywać stanu lokalnej wątku. Jego typ jest zdefiniowany przez podany podczas wywoływania metody ogólnej argument typu ogólnego <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metodę, która jest w tym przypadku <xref:System.Int64>. Argument typu informuje kompilator, typ zmiennej tymczasowej, która będzie służyć do przechowywania stanu lokalnej wątku. W tym przykładzie wyrażenie `() => 0` (lub `Function() 0` w języku Visual Basic) inicjuje zmiennej lokalnej wątku od zera. W przypadku typu odwołanie lub typ zdefiniowany przez użytkownika wartości argumentu typu ogólnego wyrażenie będzie wyglądać następująco:  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Czwartego parametru definiuje logiki pętli. Delegat lub wyrażenie lambda której sygnatura to musi być `Func<int, ParallelLoopState, long, long>` w języku C# lub `Func(Of Integer, ParallelLoopState, Long, Long)` w języku Visual Basic. Pierwszym parametrem jest wartości licznika pętli dla tej iteracji pętli. Druga <xref:System.Threading.Tasks.ParallelLoopState> obiektu, który może służyć do wyjścia z pętli; ten obiekt jest zapewniana przez <xref:System.Threading.Tasks.Parallel> klasy do każdego wystąpienia pętli. Trzeci parametr jest zmiennej lokalnej wątku. Ostatni parametr jest typu zwracanego. W tym przypadku jest typ <xref:System.Int64> , ponieważ jest to typ, możemy określone w <xref:System.Threading.Tasks.Parallel.For%2A> argument typu. Tej zmiennej o nazwie `subtotal` i zwróconego przez wyrażenie lambda. Wartość zwracana służy do inicjowania `subtotal` na kolejnych iteracji pętli. Ponadto można traktować jako wartość, która jest przekazywany do każdej iteracji, a następnie przekazywane do tego ostatniego parametru `localFinally` delegować po zakończeniu ostatniej iteracji.  
  
 Parametrowi piątej definiuje metodę, która jest wywoływana raz, po zakończeniu wszystkich iteracji w szczególności wątku. Typ argumentu wejściowego ponownie odpowiada argument typu <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> — metoda i typ zwracany przez treści wyrażenia lambda. W tym przykładzie wartość jest dodawana do zmiennej w zakresie klasy w bezpieczny sposób wątku przez wywołanie metody <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> metody. Przy użyciu zmiennej lokalnej wątku, firma Microsoft ma unikać pisania do zmiennej klasy w każdej iteracji pętli.  
  
 Aby uzyskać więcej informacji o sposobie używania wyrażeń lambda, zobacz [wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
 [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
