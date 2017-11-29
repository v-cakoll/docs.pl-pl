---
title: "Porady: zapisywanie równoległej pętli ForEach ze zmiennymi lokalnymi wątku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: parallel foreach loop, how to use local state
ms.assetid: 24b10041-b30b-45cb-aa65-66cf568ca76d
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6102274f75d2fe66b89f917cf9095d3a6dfaa3e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-parallelforeach-loop-with-thread-local-variables"></a>Porady: zapisywanie równoległej pętli ForEach ze zmiennymi lokalnymi wątku
W poniższym przykładzie pokazano, w jaki sposób napisać metodę <xref:System.Threading.Tasks.Parallel.ForEach%2A>, która używa zmiennych lokalnych wątku. Gdy wykonywana jest pętla <xref:System.Threading.Tasks.Parallel.ForEach%2A>, kolekcja źródłowa jest dzielona na wiele partycji. Każda partycja otrzyma własną kopię zmiennej „lokalnej wątku”. (Termin „lokalna wątku” jest nieprecyzyjny, ponieważ w niektórych przypadkach dwie partycje mogą działać w tym samym wątku).  
  
 Kod i parametry w przykładzie przypominają zbliżone w odpowiadającej metodzie <xref:System.Threading.Tasks.Parallel.For%2A>. Aby uzyskać więcej informacji, zobacz [porady: zapisywanie równoległej pętli for ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md).  
  
 Aby użyć zmiennej lokalnej wątku w <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli, należy wywołać jednego z przeciążeń metody, które przyjmuje dwa parametry typu. Pierwszy parametr typu `TSource`, określa typ elementu źródła, a drugi parametr typu `TLocal`, określa typ zmiennej lokalnej wątku.  
  
## <a name="example"></a>Przykład  
 Następujące przykładowe wywołania <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> przeciążenia do obliczenia sumy tablicę elementów milion. To przeciążenie ma cztery parametry:  
  
-   `source`, który jest źródłem danych. Musi on implementować <xref:System.Collections.Generic.IEnumerable%601>. Źródło danych w tym przykładzie jest elementem członkowskim milion `IEnumerable<Int32>` obiektu zwróconego przez <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> metody.  
  
-   `localInit`, lub funkcji, która inicjuje zmiennej lokalnej wątku. Ta funkcja jest wywoływana raz dla każdej partycji, w którym <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> wykonuje operację. Naszym przykładzie inicjuje zmiennej lokalnej wątku od zera.  
  
-   `body`, <xref:System.Func%604> który jest wywoływany przez równoległej pętli w każdej iteracji pętli. Podpis jest `Func\<TSource, ParallelLoopState, TLocal, TLocal>`. Podaj kod dla obiekt delegowany i przekazuje pętli w parametrach wejściowych, które są:  
  
    -   Bieżący element <xref:System.Collections.Generic.IEnumerable%601>.  
  
    -   A <xref:System.Threading.Tasks.ParallelLoopState> zmiennej, czy można użyć w kodzie pełnomocnika, aby sprawdzić stan pętli.  
  
    -   Zmiennej lokalnej wątku.  
  
     Pełnomocnika zwraca zmiennej lokalnej wątku, które są następnie przekazywane do następnej iteracji pętli, które wykonuje w tej określonej partycji. Każda partycja pętli przechowuje oddzielnego wystąpienia tej zmiennej.  
  
     W tym przykładzie delegat dodaje wartość całkowitą każdej zmiennej lokalnej wątku, co umożliwia utrzymywanie uruchomionej całkowitej wartości elementów całkowitą w tej partycji.  
  
-   `localFinally`, `Action<TLocal>` delegata, który <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> wywołuje po zakończeniu operacji pętli w każdej partycji. <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> Metoda przekazuje Twojej `Action<TLocal>` delegata końcowa wartość zmiennej lokalnej wątku dla tego wątku (lub pętli partycji), i podaj kod, który wykonuje działania wymagane do łączenia wynik tej partycji z wynikami z innych partycji. Delegat może być wywoływany współbieżnie przez wiele zadań. W związku z tym w przykładzie użyto <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> metody synchronizujący dostęp do `total` zmiennej. Ponieważ typ delegata to <xref:System.Action%601>, żadna wartość nie jest zwracana.  
  
 [!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
 [!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Porady: zapisywanie równoległej pętli for ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)  
 [Wyrażenia lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
