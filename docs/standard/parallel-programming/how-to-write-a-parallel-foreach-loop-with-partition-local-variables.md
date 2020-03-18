---
title: 'Jak: Napisz Parallel.ForEach pętli ze zmiennymi partycji lokalnych'
ms.date: 06/26/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to use local state
ms.assetid: 24b10041-b30b-45cb-aa65-66cf568ca76d
ms.openlocfilehash: cca48889670c3bd67366c879ccede94c89542c8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139682"
---
# <a name="how-to-write-a-parallelforeach-loop-with-partition-local-variables"></a>Jak: Napisz Parallel.ForEach pętli ze zmiennymi partycji lokalnych

W poniższym przykładzie pokazano, jak napisać <xref:System.Threading.Tasks.Parallel.ForEach%2A> metodę, która używa zmiennych lokalnych partycji. Gdy wykonywana jest pętla <xref:System.Threading.Tasks.Parallel.ForEach%2A>, kolekcja źródłowa jest dzielona na wiele partycji. Każda partycja ma własną kopię zmiennej lokalnej partycji. Zmienna lokalna partycji jest podobna do [zmiennej lokalnej dla wątku,](xref:System.Threading.ThreadLocal%601)z tą różnicą, że wiele partycji można uruchomić w jednym wątku.

Kod i parametry w przykładzie przypominają zbliżone w odpowiadającej metodzie <xref:System.Threading.Tasks.Parallel.For%2A>. Aby uzyskać więcej informacji, zobacz [Jak: Napisać Parallel.For pętli ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md).

Aby użyć zmiennej lokalnej <xref:System.Threading.Tasks.Parallel.ForEach%2A> partycji w pętli, należy wywołać jeden z przeciążeń metody, który przyjmuje dwa parametry typu. Pierwszy parametr typu `TSource`, określa typ elementu źródłowego, a drugi `TLocal`parametr typu , określa typ zmiennej lokalnej partycji.

## <a name="example"></a>Przykład

Poniższy przykład wywołuje <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> przeciążenie, aby obliczyć sumę tablicy miliona elementów. Przeciążenie to ma cztery parametry:

- `source`, który jest źródłem danych. Musi wdrożyć <xref:System.Collections.Generic.IEnumerable%601>. Źródło danych w naszym przykładzie jest `IEnumerable<Int32>` milion obiektu <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> członkowskiego zwrócone przez metodę.

- `localInit`lub funkcja, która inicjuje zmienną lokalną partycji. Ta funkcja jest wywoływana raz <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> dla każdej partycji, w której wykonuje operację. Nasz przykład inicjuje zmienną lokalną partycji do zera.

- `body`, <xref:System.Func%604> a, który jest wywoływany przez pętlę równoległą na każdej iteracji pętli. Jego podpis `Func\<TSource, ParallelLoopState, TLocal, TLocal>`jest . Należy podać kod dla delegata, a pętla przekazuje w parametrach wejściowych, które są:

  - Bieżący element pliku <xref:System.Collections.Generic.IEnumerable%601>.

  - Zmienna, <xref:System.Threading.Tasks.ParallelLoopState> której można użyć w kodzie pełnomocnika, aby zbadać stan pętli.

  - Zmienna lokalna partycji.

  Pełnomocnik zwraca zmienną lokalną partycji, która jest następnie przekazywana do następnej iteracji pętli, która jest wykonywana w tej określonej partycji. Każda partycja pętli zachowuje oddzielne wystąpienie tej zmiennej.

  W tym przykładzie pełnomocnik dodaje wartość każdej liczby całkowitej do zmiennej lokalnej partycji, która utrzymuje bieżącą sumę wartości elementów całkowitych w tej partycji.

- `localFinally`, `Action<TLocal>` pełnomocnika, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> który wywołuje po zakończeniu operacji pętli w każdej partycji. Metoda <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> przekazuje `Action<TLocal>` delegata wartość końcową zmiennej lokalnej partycji dla tej partycji pętli i podać kod, który wykonuje wymaganą akcję do łączenia wyniku z tej partycji z wynikami z innych partycji. Delegat może być wywoływany współbieżnie przez wiele zadań. W związku z tym <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> w przykładzie używa metody `total` do synchronizacji dostępu do zmiennej. Ponieważ typ delegata to <xref:System.Action%601>, żadna wartość nie jest zwracana.

[!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
[!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]

## <a name="see-also"></a>Zobacz też

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Porady: zapisywanie równoległej pętli For ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
