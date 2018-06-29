---
title: 'Porady: zapisywanie równoległej pętli Foreach ze zmiennymi lokalnymi partycji'
ms.date: 06/26/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to use local state
ms.assetid: 24b10041-b30b-45cb-aa65-66cf568ca76d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: edcc390014cfc70f4da4f72270c7dd53f9b9423b
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37076267"
---
# <a name="how-to-write-a-parallelforeach-loop-with-partition-local-variables"></a>Porady: zapisywanie równoległej pętli Foreach ze zmiennymi lokalnymi partycji
Poniższy przykład przedstawia sposób zapisania <xref:System.Threading.Tasks.Parallel.ForEach%2A> metody, która używa zmiennych lokalnych partycji. Gdy wykonywana jest pętla <xref:System.Threading.Tasks.Parallel.ForEach%2A>, kolekcja źródłowa jest dzielona na wiele partycji. Każda partycja ma własną kopię zmiennej lokalnej partycji. Zmiennej lokalnej partycji jest podobny do [zmiennej lokalnej wątku](xref:System.Threading.ThreadLocal%601), z wyjątkiem tego, że wiele partycji można uruchomić w jednym wątku.
  
 Kod i parametry w przykładzie przypominają zbliżone w odpowiadającej metodzie <xref:System.Threading.Tasks.Parallel.For%2A>. Aby uzyskać więcej informacji, zobacz [porady: zapisywanie równoległej pętli for ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md).  
  
 Aby użyć zmiennej lokalnej partycji w <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli, należy wywołać jednego z przeciążeń metody, które przyjmuje dwa parametry typu. Pierwszy parametr typu `TSource`, określa typ elementu źródła, a drugi parametr typu `TLocal`, określa typ zmiennej lokalnej partycji.  
  
## <a name="example"></a>Przykład  
 Następujące przykładowe wywołania <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> przeciążenia do obliczenia sumy tablicę elementów milion. To przeciążenie ma cztery parametry:  
  
-   `source`, który jest źródłem danych. Musi on implementować <xref:System.Collections.Generic.IEnumerable%601>. Źródło danych w tym przykładzie jest elementem członkowskim milion `IEnumerable<Int32>` obiektu zwróconego przez <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> metody.  
  
-   `localInit`, lub funkcji, która inicjuje zmiennej lokalnej partycji. Ta funkcja jest wywoływana raz dla każdej partycji, w którym <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> wykonuje operację. Naszym przykładzie inicjuje zmiennej lokalnej partycji od zera.  
  
-   `body`, <xref:System.Func%604> który jest wywoływany przez równoległej pętli w każdej iteracji pętli. Podpis jest `Func\<TSource, ParallelLoopState, TLocal, TLocal>`. Podaj kod dla obiekt delegowany i przekazuje pętli w parametrach wejściowych, które są:  
  
    -   Bieżący element <xref:System.Collections.Generic.IEnumerable%601>.
  
    -   A <xref:System.Threading.Tasks.ParallelLoopState> zmiennej, czy można użyć w kodzie pełnomocnika, aby sprawdzić stan pętli.  
  
    -   Zmiennej lokalnej partycji.  
  
     Pełnomocnika zwraca zmiennej lokalnej partycji, które są następnie przekazywane do następnej iteracji pętli, które wykonuje w tej określonej partycji. Każda partycja pętli przechowuje oddzielnego wystąpienia tej zmiennej.  
  
     W tym przykładzie delegat dodaje wartość całkowitą każdej zmiennej lokalnej partycji, co umożliwia utrzymywanie uruchomionej całkowitej wartości elementów całkowitą w tej partycji.  
  
-   `localFinally`, `Action<TLocal>` delegata, który <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> wywołuje po zakończeniu operacji pętli w każdej partycji. <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> Metoda przekazuje Twojej `Action<TLocal>` delegowanie końcowa wartość zmiennej lokalnej partycji dla tej partycji pętli i podaj kod, który wykonuje akcję wymagane połączenie wyniku z tej partycji z wyników partycje. Delegat może być wywoływany współbieżnie przez wiele zadań. W związku z tym w przykładzie użyto <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> metody synchronizujący dostęp do `total` zmiennej. Ponieważ typ delegata to <xref:System.Action%601>, żadna wartość nie jest zwracana.  
  
 [!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
 [!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Instrukcje: zapisywanie pętli Parallel.For ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)  
 [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
