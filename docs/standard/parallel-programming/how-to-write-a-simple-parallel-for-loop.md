---
title: 'Porady: zapisywanie prostej równoległej pętli For'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Parallel.For, How to Write
- for loop, parallel construction in .NET
- parallel for loops, how to use
ms.assetid: 9029ba7f-a9d1-4526-8c84-c88716dba5d4
ms.openlocfilehash: 78f07a4f0118c6bce7a043f111988281ddd6add0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139655"
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Porady: zapisywanie prostej równoległej pętli For

Ten temat zawiera dwa przykłady ilustrujące <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody. Pierwszy używa przeciążenia metody <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType>, a drugi używa przeciążenia <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType>, dwóch najprostszych overloads metody <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>. Można użyć tych dwóch przeciążeń metody <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, gdy nie trzeba anulować pętli, przerwać iteracji pętli lub zachować dowolnego stanu wątku.

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie znasz wyrażeń lambda w C# lub Visual Basic, zobacz [wyrażenia lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

Pierwszy przykład oblicza rozmiar plików w jednym katalogu. Drugi Oblicza iloczyn dwóch macierzy.

## <a name="directory-size-example"></a>Przykład rozmiaru katalogu

Ten przykład to proste narzędzie wiersza polecenia, które oblicza łączny rozmiar plików w katalogu. Oczekuje ona pojedynczej ścieżki katalogu jako argumentu i raportuje liczbę i łączny rozmiar plików w tym katalogu. Po sprawdzeniu, czy katalog istnieje, używa metody <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, aby wyliczyć pliki w katalogu i określić ich rozmiary. Każdy rozmiar pliku jest następnie dodawany do zmiennej `totalSize`. Należy zauważyć, że dodanie jest wykonywane przez wywołanie <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType>, tak aby dodanie było wykonywane jako operacja niepodzielna. W przeciwnym razie wiele zadań może próbować jednocześnie zaktualizować zmienną `totalSize`.

[!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
[!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]

## <a name="matrix-and-stopwatch-example"></a>Przykład macierzy i stopera

W tym przykładzie zastosowano metodę <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, aby obliczyć iloczyn dwóch macierzy. Pokazano również, jak używać klasy <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> do porównania wydajności pętli równoległej z pętlą nierównoległą. Należy pamiętać, że ponieważ może on generować dużą ilość danych wyjściowych, przykład umożliwia przekierowywanie danych wyjściowych do pliku.

[!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
[!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]

W przypadku przekształcają dowolnego kodu, w tym pętle, jeden istotny cel polega na tym, że procesor jest możliwie największej ilości bez przekształcają do momentu, w którym obciążenie przetwarzaniem równoległym wyklucza wszelkie korzyści z wydajności. W tym konkretnym przykładzie tylko pętla zewnętrzna jest równoległa, ponieważ nie ma zbyt dużej ilości pracy wykonanej w wewnętrznej pętli. Połączenie niewielkiej ilości pracy i niepożądanych efektów pamięci podręcznej może spowodować spadek wydajności zagnieżdżonych pętli równoległych. W związku z tym przekształcają pętlę zewnętrzną to najlepszy sposób, aby zmaksymalizować zalety współbieżności w większości systemów.

## <a name="the-delegate"></a>Obiekt delegowany

Trzeci parametr tego przeciążenia <xref:System.Threading.Tasks.Parallel.For%2A> jest delegatem typu `Action<int>` w C# lub `Action(Of Integer)` w Visual Basic. Delegat `Action`, bez względu na to, czy ma zero, jeden lub szesnast parametry typu, zawsze zwraca wartość void. W Visual Basic zachowanie `Action` jest zdefiniowane przy użyciu `Sub`. W przykładzie jest stosowane wyrażenie lambda do utworzenia delegata, ale można również utworzyć delegata w inny sposób. Aby uzyskać więcej informacji, zobacz [wyrażenia lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="the-iteration-value"></a>Wartość iteracji

Delegat przyjmuje jeden parametr wejściowy, którego wartością jest bieżąca iteracja. Ta wartość iteracji jest dostarczana przez środowisko uruchomieniowe i jej wartość początkowa jest indeksem pierwszego elementu w segmencie (partycji) źródła, które jest przetwarzane w bieżącym wątku.

Jeśli potrzebujesz większej kontroli nad poziomem współbieżności, użyj jednego z przeciążeń, które pobiera <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType> parametr wejściowy, na przykład: <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType>.

## <a name="return-value-and-exception-handling"></a>Wartość zwracana i obsługa wyjątków

<xref:System.Threading.Tasks.Parallel.For%2A> zwraca obiekt <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType>, gdy wszystkie wątki zostały ukończone. Ta wartość zwracana jest przydatna podczas ręcznego zatrzymywania lub przerywania iteracji pętli, ponieważ <xref:System.Threading.Tasks.ParallelLoopResult> przechowuje informacje takie jak Ostatnia iteracja, która działała do ukończenia. Jeśli co najmniej jeden wyjątek występuje w jednym z wątków, zostanie wygenerowany <xref:System.AggregateException?displayProperty=nameWithType>.

W kodzie w tym przykładzie wartość zwracana <xref:System.Threading.Tasks.Parallel.For%2A> nie jest używana.

## <a name="analysis-and-performance"></a>Analiza i wydajność

Aby wyświetlić użycie procesora CPU na komputerze, można użyć Kreatora wydajności. W ramach eksperymentu Zwiększ liczbę kolumn i wierszy w macierzach. Im większa macierz, tym większa różnica wydajności między równoległymi i sekwencyjnymi wersjami obliczeń. Gdy macierz jest mała, wersja sekwencyjna będzie działać szybciej ze względu na obciążenie podczas konfigurowania pętli równoległej.

Wywołania synchroniczne do udostępnionych zasobów, takie jak konsola lub system plików, znacząco obniżą wydajność pętli równoległej. Podczas mierzenia wydajności spróbuj uniknąć wywołań takich jak <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> w pętli.

## <a name="compile-the-code"></a>Kompiluj kod

Skopiuj i wklej ten kod do projektu programu Visual Studio.

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Tasks.Parallel.For%2A>
- <xref:System.Threading.Tasks.Parallel.ForEach%2A>
- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
