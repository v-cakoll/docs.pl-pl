---
title: 'Porady: zapisywanie pętli Parallel.ForEach ze zmiennymi lokalnymi partycji'
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
ms.openlocfilehash: 357cc488705ec3dab66543fa4814dbe3e6a22777
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591000"
---
# <a name="how-to-write-a-parallelforeach-loop-with-partition-local-variables"></a>Porady: zapisywanie pętli Parallel.ForEach ze zmiennymi lokalnymi partycji
Poniższy przykład przedstawia sposób zapisania <xref:System.Threading.Tasks.Parallel.ForEach%2A> metodę, która używa zmiennych lokalnych partycji. Gdy wykonywana jest pętla <xref:System.Threading.Tasks.Parallel.ForEach%2A>, kolekcja źródłowa jest dzielona na wiele partycji. Każda partycja zawiera własną kopię zmiennej lokalnej partycji. Zmienna partycji lokalnej jest podobny do [zmienną lokalną wątku](xref:System.Threading.ThreadLocal%601), z tą różnicą, że wiele partycji można uruchomić w jednym wątku.
  
 Kod i parametry w przykładzie przypominają zbliżone w odpowiadającej metodzie <xref:System.Threading.Tasks.Parallel.For%2A>. Aby uzyskać więcej informacji, zobacz [porady: zapisywanie pętli Parallel.For ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md).  
  
 Aby użyć zmiennej lokalnej partycji w <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli, należy wywołać jedno z przeciążeń metody, która przyjmuje dwa parametry typu. Pierwszy parametr typu `TSource`, określa typ elementu źródłowego, a drugi parametr typu `TLocal`, określa typ zmiennej lokalnej partycji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wywołuje <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> przeciążenie, można obliczyć sumę tablicy elementów jeden milion. To przeciążenie ma cztery parametry:  
  
-   `source`, który jest źródłem danych. Musi on implementować <xref:System.Collections.Generic.IEnumerable%601>. Źródło danych, w tym przykładzie jest członkiem miliona `IEnumerable<Int32>` obiektu zwróconego przez <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> metody.  
  
-   `localInit`, lub funkcji, która inicjuje zmienną lokalnych partycji. Ta funkcja jest wywoływana jeden raz dla każdej partycji, w którym <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> wykonuje operację. Nasz przykład inicjuje zmienną partycji lokalnej do zera.  
  
-   `body`, <xref:System.Func%604> , wywoływany przez pętlę równoległą podczas każdej iteracji pętli. Jego podpis jest `Func\<TSource, ParallelLoopState, TLocal, TLocal>`. Dostarczasz kod dla delegata, a pętla przekazuje parametry wejściowe, które są:  
  
    -   Bieżący element <xref:System.Collections.Generic.IEnumerable%601>.
  
    -   A <xref:System.Threading.Tasks.ParallelLoopState> zmiennej, czy można użyć w kodzie w swoim delegacie, aby sprawdzić stan pętli.  
  
    -   Zmienna lokalnych partycji.  
  
     Swoim delegacie zwraca zmienną partycji lokalnej, która jest następnie przekazywany do następnej iteracji pętli, która jest wykonywana w określonej partycji. Każda partycja pętli zachowuje osobne wystąpienie tej zmiennej.  
  
     W tym przykładzie delegata dodaje wartość Każda liczba całkowita do zmiennej lokalnej partycji, która przechowuje działającego całkowitej wartości elementy całkowite w tej partycji.  
  
-   `localFinally`, `Action<TLocal>` delegowania, który <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> wywołuje po zakończeniu pętli operacji w poszczególnych partycjach. <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> Metoda przekazuje swoje `Action<TLocal>` delegować końcowa wartość zmiennej partycji lokalnej dla tej partycji pętli, a następnie podaj kod, który wykonuje czynność wymagane dla połączenia wyników danej partycji z wynikami innych partycji. Delegat może być wywoływany współbieżnie przez wiele zadań. W związku z tym w przykładzie użyto <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> metody do synchronizowania dostępu do `total` zmiennej. Ponieważ typ delegata to <xref:System.Action%601>, żadna wartość nie jest zwracana.  
  
 [!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
 [!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]  
  
## <a name="see-also"></a>Zobacz także

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [Instrukcje: zapisywanie pętli Parallel.For ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)  
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
