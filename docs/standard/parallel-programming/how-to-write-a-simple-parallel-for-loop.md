---
title: 'Instrukcje: Zapisywanie prostej pętli Parallel.For'
description: Dowiedz się, jak pisać równolegle. pętle w programie .NET, w których nie trzeba anulować pętli, przerwać iteracje pętli lub zachować dowolny stan wątku — lokalnie.
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
ms.openlocfilehash: 8307f2205653fbd213d824acffc405ee97580166
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662696"
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Instrukcje: Zapisywanie prostej pętli Parallel.For

Ten temat zawiera dwa przykłady ilustrujące <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metodę. Pierwszy używa <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> przeciążenia metody, a drugi używa <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType> przeciążenia, dwa najprostsze przeciążenia <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody. Można użyć tych dwóch przeciążeń <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody, gdy nie trzeba anulować pętli, przerwać iteracji pętli lub zachować dowolnego stanu wątku.

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).

Pierwszy przykład oblicza rozmiar plików w jednym katalogu. Drugi Oblicza iloczyn dwóch macierzy.

## <a name="directory-size-example"></a>Przykład rozmiaru katalogu

Ten przykład to proste narzędzie wiersza polecenia, które oblicza łączny rozmiar plików w katalogu. Oczekuje ona pojedynczej ścieżki katalogu jako argumentu i raportuje liczbę i łączny rozmiar plików w tym katalogu. Po sprawdzeniu, czy katalog istnieje, używa <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody do wyliczania plików w katalogu i określania rozmiarów plików. Każdy rozmiar pliku jest następnie dodawany do `totalSize` zmiennej. Należy zauważyć, że dodanie jest wykonywane przez wywołanie metody, <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> Aby dodanie zostało wykonane jako operacja niepodzielna. W przeciwnym razie wiele zadań może próbować jednocześnie zaktualizować `totalSize` zmienną.

[!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
[!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]

## <a name="matrix-and-stopwatch-example"></a>Przykład macierzy i stopera

Ten przykład używa <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody do obliczenia iloczynu dwóch macierzy. Pokazano również, jak używać <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> klasy do porównywania wydajności pętli równoległej z pętlą nierównoległą. Należy pamiętać, że ponieważ może on generować dużą ilość danych wyjściowych, przykład umożliwia przekierowywanie danych wyjściowych do pliku.

[!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
[!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]

W przypadku przekształcają dowolnego kodu, w tym pętle, jeden istotny cel polega na tym, że procesor jest możliwie największej ilości bez przekształcają do momentu, w którym obciążenie przetwarzaniem równoległym wyklucza wszelkie korzyści z wydajności. W tym konkretnym przykładzie tylko pętla zewnętrzna jest równoległa, ponieważ nie ma zbyt dużej ilości pracy wykonanej w wewnętrznej pętli. Połączenie niewielkiej ilości pracy i niepożądanych efektów pamięci podręcznej może spowodować spadek wydajności zagnieżdżonych pętli równoległych. W związku z tym przekształcają pętlę zewnętrzną to najlepszy sposób, aby zmaksymalizować zalety współbieżności w większości systemów.

## <a name="the-delegate"></a>Obiekt delegowany

Trzeci parametr tego przeciążenia <xref:System.Threading.Tasks.Parallel.For%2A> jest delegatem typu `Action<int>` w języku C# lub `Action(Of Integer)` w Visual Basic. `Action`Delegat, bez względu na to, czy ma zero, jeden lub szesnast parametry typu, zawsze zwraca wartość void. W Visual Basic zachowanie `Action` jest zdefiniowane za pomocą `Sub` . W przykładzie jest stosowane wyrażenie lambda do utworzenia delegata, ale można również utworzyć delegata w inny sposób. Aby uzyskać więcej informacji, zobacz [wyrażenia lambda w PLINQ i TPL](lambda-expressions-in-plinq-and-tpl.md).

## <a name="the-iteration-value"></a>Wartość iteracji

Delegat przyjmuje jeden parametr wejściowy, którego wartością jest bieżąca iteracja. Ta wartość iteracji jest dostarczana przez środowisko uruchomieniowe i jej wartość początkowa jest indeksem pierwszego elementu w segmencie (partycji) źródła, które jest przetwarzane w bieżącym wątku.

Jeśli potrzebujesz większej kontroli nad poziomem współbieżności, użyj jednego z przeciążeń, które pobiera <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType> parametr wejściowy, na przykład: <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType> .

## <a name="return-value-and-exception-handling"></a>Wartość zwracana i obsługa wyjątków

<xref:System.Threading.Tasks.Parallel.For%2A>zwraca <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType> obiekt po zakończeniu wszystkich wątków. Ta wartość zwracana jest przydatna podczas ręcznego zatrzymywania lub przerywania iteracji pętli, ponieważ <xref:System.Threading.Tasks.ParallelLoopResult> zawiera informacje, takie jak Ostatnia iteracja, która została uruchomiona. Jeśli co najmniej jeden wyjątek występuje w jednym z wątków, <xref:System.AggregateException?displayProperty=nameWithType> zostanie zgłoszony.

W kodzie w tym przykładzie zwracana wartość <xref:System.Threading.Tasks.Parallel.For%2A> nie jest używana.

## <a name="analysis-and-performance"></a>Analiza i wydajność

Aby wyświetlić użycie procesora CPU na komputerze, można użyć Kreatora wydajności. W ramach eksperymentu Zwiększ liczbę kolumn i wierszy w macierzach. Im większa macierz, tym większa różnica wydajności między równoległymi i sekwencyjnymi wersjami obliczeń. Gdy macierz jest mała, wersja sekwencyjna będzie działać szybciej ze względu na obciążenie podczas konfigurowania pętli równoległej.

Wywołania synchroniczne do udostępnionych zasobów, takie jak konsola lub system plików, znacząco obniżą wydajność pętli równoległej. Podczas mierzenia wydajności spróbuj uniknąć wywołań takich jak <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> w pętli.

## <a name="compile-the-code"></a>Kompiluj kod

Skopiuj i wklej ten kod do projektu programu Visual Studio.

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Tasks.Parallel.For%2A>
- <xref:System.Threading.Tasks.Parallel.ForEach%2A>
- [Równoległość danych](data-parallelism-task-parallel-library.md)
- [Programowanie równoległe](index.md)
