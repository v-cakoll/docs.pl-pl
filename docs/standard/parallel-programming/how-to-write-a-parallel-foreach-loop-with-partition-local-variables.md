---
title: 'Instrukcje: zapisywanie pętli Parallel. ForEach ze zmiennymi lokalnymi partycji'
ms.date: 06/26/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to use local state
ms.assetid: 24b10041-b30b-45cb-aa65-66cf568ca76d
ms.openlocfilehash: cca48889670c3bd67366c879ccede94c89542c8d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139682"
---
# <a name="how-to-write-a-parallelforeach-loop-with-partition-local-variables"></a>Instrukcje: zapisywanie pętli Parallel. ForEach ze zmiennymi lokalnymi partycji

Poniższy przykład pokazuje, jak napisać metodę <xref:System.Threading.Tasks.Parallel.ForEach%2A>, która używa zmiennych lokalnych partycji. Gdy wykonywana jest pętla <xref:System.Threading.Tasks.Parallel.ForEach%2A>, kolekcja źródłowa jest dzielona na wiele partycji. Każda partycja ma własną kopię zmiennej lokalnej partycji. Zmienna lokalna partycji jest podobna do [zmiennej lokalnej wątku](xref:System.Threading.ThreadLocal%601), z tą różnicą, że wiele partycji może działać w jednym wątku.

Kod i parametry w przykładzie przypominają zbliżone w odpowiadającej metodzie <xref:System.Threading.Tasks.Parallel.For%2A>. Aby uzyskać więcej informacji, zobacz [jak: napisać pętlę Parallel. for ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md).

Aby użyć zmiennej lokalnej partycji w pętli <xref:System.Threading.Tasks.Parallel.ForEach%2A>, należy wywołać jedno z przeciążeń metody, które pobiera dwa parametry typu. Pierwszy parametr typu, `TSource`, określa typ elementu źródłowego, a drugi parametr typu, `TLocal`, określa typ zmiennej lokalnej partycji.

## <a name="example"></a>Przykład

Poniższy przykład wywołuje Przeciążenie <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType>, aby obliczyć sumę tablicy elementów 1 000 000. To Przeciążenie ma cztery parametry:

- `source`, który jest źródłem danych. Musi implementować <xref:System.Collections.Generic.IEnumerable%601>. Źródłem danych w naszym przykładzie jest element członkowski 1 000 000 `IEnumerable<Int32>` obiektu zwróconego przez metodę <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType>.

- `localInit`lub funkcja, która inicjuje zmienną lokalną partycji. Ta funkcja jest wywoływana raz dla każdej partycji, w której jest wykonywana operacja <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Nasz przykład inicjuje zmienną lokalną partycji na zero.

- `body`, <xref:System.Func%604>, który jest wywoływany przez pętlę równoległą dla każdej iteracji pętli. Jego podpis jest `Func\<TSource, ParallelLoopState, TLocal, TLocal>`. Podasz kod delegata, a pętla przechodzi w parametrach wejściowych, które są:

  - Bieżący element <xref:System.Collections.Generic.IEnumerable%601>.

  - Zmienna <xref:System.Threading.Tasks.ParallelLoopState>, której można użyć w kodzie delegata do sprawdzenia stanu pętli.

  - Zmienna lokalna partycji.

  Delegat zwraca zmienną lokalną partycji, która jest następnie przenoszona do następnej iteracji pętli, która jest wykonywana w danej partycji. Każda partycja pętli przechowuje oddzielne wystąpienie tej zmiennej.

  W tym przykładzie delegat dodaje wartość każdej liczby całkowitej do zmiennej lokalnej partycji, która zachowuje sumę całkowitą elementów liczby całkowitej w tej partycji.

- `localFinally`, `Action<TLocal>` delegat <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> wywoływany, gdy operacje zapętlenia w każdej partycji zakończyły się pomyślnie. Metoda <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> przekazuje `Action<TLocal>` delegowania wartości końcowej zmiennej lokalnej partycji dla tej partycji pętli, i podajesz kod, który wykonuje wymaganą akcję do łączenia wyniku z tej partycji z wynikami innych Partition. Delegat może być wywoływany współbieżnie przez wiele zadań. W związku z tym w przykładzie zastosowano metodę <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType>, aby zsynchronizować dostęp do zmiennej `total`. Ponieważ typ delegata to <xref:System.Action%601>, żadna wartość nie jest zwracana.

[!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
[!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]

## <a name="see-also"></a>Zobacz także

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Instrukcje: zapisywanie pętli Parallel.For ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
