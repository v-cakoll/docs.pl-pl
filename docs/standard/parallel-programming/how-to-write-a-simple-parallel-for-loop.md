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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139655"
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Porady: zapisywanie prostej równoległej pętli For

Ten temat zawiera dwa przykłady, które ilustrują <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metodę. Pierwszy używa <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> przeciążenia metody, a <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType> drugi używa przeciążenia, dwa <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> najprostsze przeciążenia metody. Można użyć tych dwóch przeciążeń <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody, gdy nie trzeba anulować pętli, wyrwać się z iteracji pętli lub zachować dowolny stan lokalny wątku.

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

Pierwszy przykład oblicza rozmiar plików w jednym katalogu. Drugi oblicza iloczyn dwóch matryc.

## <a name="directory-size-example"></a>Przykład rozmiaru katalogu

W tym przykładzie jest to proste narzędzie wiersza polecenia, które oblicza całkowity rozmiar plików w katalogu. Oczekuje pojedynczej ścieżki katalogu jako argumentu i raportuje liczbę i całkowity rozmiar plików w tym katalogu. Po sprawdzeniu, czy katalog <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> istnieje, używa metody do wyliczania plików w katalogu i określania ich rozmiarów plików. Każdy rozmiar pliku jest `totalSize` następnie dodawany do zmiennej. Należy zauważyć, że dodanie jest <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> wykonywane przez wywołanie tak, aby dodanie jest wykonywane jako operacji atomowej. W przeciwnym razie wiele zadań `totalSize` może próbować zaktualizować zmienną jednocześnie.

[!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
[!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]

## <a name="matrix-and-stopwatch-example"></a>Przykład matrycy i stopera

W tym <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> przykładzie użyto metody do obliczenia produktu dwóch macierzy. Pokazuje również, jak <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> użyć klasy do porównania wydajności pętli równoległej z pętli nierównoległej. Należy zauważyć, że ponieważ może generować dużą ilość danych wyjściowych, przykład umożliwia dane wyjściowe, które mają być przekierowywane do pliku.

[!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
[!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]

Podczas paralelowania dowolnego kodu, w tym pętli, jednym ważnym celem jest wykorzystanie procesorów w jak największym stopniu bez nadmiernego równoległości do punktu, w którym obciążenie dla przetwarzania równoległego neguje wszelkie korzyści wydajności. W tym konkretnym przykładzie tylko zewnętrzna pętla jest równoległa, ponieważ nie ma zbyt wiele pracy wykonywanej w pętli wewnętrznej. Połączenie niewielkiej ilości pracy i niepożądanych efektów pamięci podręcznej może spowodować spadek wydajności w zagnieżdżonych pętlach równoległych. W związku z tym równoległość tylko pętli zewnętrznej jest najlepszym sposobem, aby zmaksymalizować korzyści współbieżności w większości systemów.

## <a name="the-delegate"></a>Pełnomocnik

Trzeci parametr tego przeciążenia <xref:System.Threading.Tasks.Parallel.For%2A> jest delegatem `Action<int>` typu w `Action(Of Integer)` języku C# lub w języku Visual Basic. Pełnomocnik, `Action` niezależnie od tego, czy ma zero, jeden lub szesnaście parametrów typu, zawsze zwraca void. W języku Visual Basic `Action` zachowanie jest `Sub`zdefiniowany za pomocą . W przykładzie użyto wyrażenia lambda do utworzenia pełnomocnika, ale można utworzyć pełnomocnika w inny sposób, jak również. Aby uzyskać więcej informacji, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="the-iteration-value"></a>Wartość iteracji

Delegat przyjmuje pojedynczy parametr wejściowy, którego wartość jest bieżącą iteracją. Ta wartość iteracji jest dostarczana przez program runtime, a jego wartość początkowa jest indeksem pierwszego elementu w segmencie (partycji) źródła, który jest przetwarzany w bieżącym wątku.

Jeśli potrzebujesz większej kontroli nad poziomem współbieżności, należy <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType> użyć jednego z <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType>przeciążeń, który przyjmuje parametr wejściowy, takich jak: .

## <a name="return-value-and-exception-handling"></a>Zwracawartość i obsługa wyjątków

<xref:System.Threading.Tasks.Parallel.For%2A>zwraca <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType> obiekt po zakończeniu wszystkich wątków. Ta wartość zwracana jest przydatna podczas ręcznego zatrzymywania <xref:System.Threading.Tasks.ParallelLoopResult> lub przerywania iteracji pętli, ponieważ przechowuje informacje, takie jak ostatnia iteracja, która została uruchomiona do zakończenia. Jeśli jeden lub więcej wyjątków występuje w <xref:System.AggregateException?displayProperty=nameWithType> jednym z wątków, zostanie wygenerowany.

W kodzie w tym przykładzie <xref:System.Threading.Tasks.Parallel.For%2A> wartość zwracana nie jest używana.

## <a name="analysis-and-performance"></a>Analiza i wydajność

Za pomocą Kreatora wydajności można wyświetlać użycie procesora na komputerze. Jako eksperyment zwiększ liczbę kolumn i wierszy w matrycych. Im większe macierze, tym większa różnica wydajności między równoległymi i sekwencyjnymi wersjami obliczeń. Gdy macierz jest mała, wersja sekwencyjna będzie działać szybciej ze względu na obciążenie podczas konfigurowania pętli równoległej.

Synchroniczne wywołania zasobów udostępnionych, takich jak Konsola lub System plików, znacznie obniżą wydajność pętli równoległej. Podczas pomiaru wydajności należy unikać <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> wywołań, takich jak w pętli.

## <a name="compile-the-code"></a>Skompiluj kod

Skopiuj i wklej ten kod do projektu programu Visual Studio.

## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Tasks.Parallel.For%2A>
- <xref:System.Threading.Tasks.Parallel.ForEach%2A>
- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
