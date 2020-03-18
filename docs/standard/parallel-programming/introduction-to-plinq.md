---
title: Wprowadzenie do PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, introduction to
ms.assetid: eaa720d8-8999-4eb7-8df5-3c19ca61cad0
ms.openlocfilehash: ed1b2df57c118a0ebb6b5ffa4326b3e2eac81dec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75632366"
---
# <a name="introduction-to-plinq"></a>Wprowadzenie do PLINQ

## <a name="what-is-a-parallel-query"></a>Co to jest kwerenda równoległa?

Zapytanie zintegrowane z językiem (LINQ) zostało wprowadzone w programie .NET Framework 3.5. Posiada ujednolicony model <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> do wykonywania zapytań dowolnego lub źródła danych w sposób bezpieczny dla typu. LINQ do obiektów jest nazwą dla kwerend LINQ, które <xref:System.Collections.Generic.List%601> są uruchamiane względem kolekcji w pamięci, takich jak i tablice. W tym artykule założono, że masz podstawową wiedzę na temat LINQ. Aby uzyskać więcej informacji, zobacz [Language-Integrated Query (LINQ) — C#](../../csharp/programming-guide/concepts/linq/index.md) lub [Language-Integrated Query (LINQ) — Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).

Parallel LINQ (PLINQ) jest równoległą implementacją wzorca LINQ. Kwerenda PLINQ na wiele sposobów przypomina nierównoległe LINQ do objects kwerendy. Zapytania PLINQ, podobnie jak sekwencyjne zapytania LINQ, <xref:System.Collections.IEnumerable> działają <xref:System.Collections.Generic.IEnumerable%601> na dowolnym źródle w pamięci lub danych i odroczyły wykonanie, co oznacza, że nie rozpoczynają wykonywania, dopóki kwerenda nie zostanie wyliczona. Podstawową różnicą jest to, że PLINQ próbuje w pełni wykorzystać wszystkie procesory w systemie. Czyni to przez partycjonowanie źródła danych w segmentach, a następnie wykonywanie kwerendy w każdym segmencie na oddzielnych wątków roboczych równolegle na wielu procesorów. W wielu przypadkach wykonanie równoległe oznacza, że kwerenda jest uruchamiana znacznie szybciej.

Poprzez wykonanie równoległe PLINQ może osiągnąć znaczne ulepszenia wydajności w stosunku <xref:System.Linq.ParallelEnumerable.AsParallel%2A> do starszego kodu dla niektórych rodzajów zapytań, często po prostu przez dodanie operacji kwerendy do źródła danych. Jednak równoległość może wprowadzić własne złożoności, a nie wszystkie operacje kwerendy działają szybciej w PLINQ. W rzeczywistości równoległość faktycznie spowalnia niektóre zapytania. W związku z tym należy zrozumieć, jak problemy, takie jak kolejność wpływają na zapytania równoległe. Aby uzyskać więcej informacji, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

W dalszej części tego artykułu przedstawiono omówienie głównych klas PLINQ i omówiono sposób tworzenia zapytań PLINQ. Każda sekcja zawiera łącza do bardziej szczegółowych informacji i przykłady kodu.

## <a name="the-parallelenumerable-class"></a>Klasa równoległa

Klasa <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> udostępnia prawie wszystkie funkcje PLINQ. To i pozostałe <xref:System.Linq?displayProperty=nameWithType> typy przestrzeni nazw są kompilowane do zestawu System.Core.dll. Domyślne projekty języka C# i Visual Basic w programie Visual Studio odwołują się do zestawu i importują obszar nazw.

<xref:System.Linq.ParallelEnumerable>zawiera implementacje wszystkich standardowych operatorów zapytań, które LINQ do obiektów obsługuje, mimo że nie próbuje zrównoleglić każdego z nich. Jeśli nie znasz LINQ, zobacz [Wprowadzenie do LINQ (C#)](../../csharp/programming-guide/concepts/linq/index.md) i [Wprowadzenie do LINQ (Visual Basic).](../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)

Oprócz standardowych operatorów zapytań <xref:System.Linq.ParallelEnumerable> klasa zawiera zestaw metod, które umożliwiają zachowania specyficzne dla wykonywania równoległego. Te metody specyficzne dla PLINQ są wymienione w poniższej tabeli.

|Operator równoległy|Opis|
|---------------------------------|-----------------|
|<xref:System.Linq.ParallelEnumerable.AsParallel%2A>|Punkt wejścia dla PLINQ. Określa, że pozostała część kwerendy powinna być równoległa, jeśli jest to możliwe.|
|<xref:System.Linq.ParallelEnumerable.AsSequential%2A>|Określa, że pozostała część kwerendy powinna być uruchamiana sekwencyjnie jako kwerenda LINQ nierównoległa.|
|<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>|Określa, że PLINQ należy zachować kolejność sekwencji źródłowej dla pozostałej części kwerendy lub do momentu zmiany kolejności, na przykład przez użycie orderby (Order By in Visual Basic) klauzuli.|
|<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>|Określa, że funkcja PLINQ dla pozostałej części kwerendy nie jest wymagana do zachowania kolejności sekwencji źródłowej.|
|<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>|Określa, że funkcja PLINQ powinna okresowo monitorować stan dostarczonego tokenu anulowania i anulować wykonanie, jeśli jest wymagane.|
|<xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>|Określa maksymalną liczbę procesorów, które plinq należy używać do równoległości kwerendy.|
|<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>|Zawiera wskazówkę, jak PLINQ powinien, jeśli jest to możliwe, scalić wyniki równoległe z powrotem do jednej sekwencji w wątku zużywa.|
|<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>|Określa, czy funkcja PLINQ powinna równoległo kwerendę, nawet jeśli domyślnym zachowaniem byłoby uruchamianie jej sekwencyjnie.|
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Wielowątkowa metoda wyliczenia, która w przeciwieństwie do iteracji wyników kwerendy umożliwia równoległe przetwarzanie wyników bez uprzedniego scalania z powrotem do wątku konsumenta.|
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>Przeciążenie|Przeciążenie, które jest unikatowe dla PLINQ i umożliwia agregację pośrednią za partycjami lokalnymi wątku, a także funkcję agregacji końcowej, aby połączyć wyniki wszystkich partycji.|

## <a name="the-opt-in-model"></a>The Opt-in Model

Podczas pisania kwerendy, zdecydować się <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> na PLINQ, wywołując metodę rozszerzenia w źródle danych, jak pokazano w poniższym przykładzie.

[!code-csharp[PLINQ#1](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#1)]
[!code-vb[PLINQ#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#1)]

Metoda <xref:System.Linq.ParallelEnumerable.AsParallel%2A> rozszerzenia wiąże kolejnych operatorów zapytań, `where` w `select`tym <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> przypadku i , do implementacji.

## <a name="execution-modes"></a>Tryby wykonywania

Domyślnie funkcja PLINQ jest zachowawcza. W czasie wykonywania infrastruktury PLINQ analizuje ogólną strukturę kwerendy. Jeśli kwerenda może przynieść przyspieszenie przez równoległość, PLINQ dzieli sekwencję źródłową na zadania, które można uruchomić jednocześnie. Jeśli nie jest bezpieczne do równoległości kwerendy, PLINQ po prostu uruchamia kwerendę sekwencyjnie. Jeśli PLINQ ma wybór między potencjalnie drogim algorytmem równoległym lub niedrogim algorytmem sekwencyjnym, domyślnie wybiera algorytm sekwencyjne. Można użyć <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metody i <xref:System.Linq.ParallelExecutionMode?displayProperty=nameWithType> wyliczenia polecić PLINQ, aby wybrać algorytm równoległy. Jest to przydatne, gdy wiadomo, testując i pomiaru, że określonej kwerendy wykonuje szybciej równolegle. Aby uzyskać więcej informacji, zobacz [Jak: Określić tryb wykonywania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).

## <a name="degree-of-parallelism"></a>Stopień równoległości

Domyślnie funkcja PLINQ używa wszystkich procesorów na komputerze-hoście. Można poinstruować PLINQ, aby używał nie więcej niż określonej <xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A> liczby procesorów przy użyciu tej metody. Jest to przydatne, gdy chcesz upewnić się, że inne procesy uruchomione na komputerze otrzymują pewną ilość czasu procesora CPU. Poniższy fragment kodu ogranicza kwerendę do korzystania z maksymalnie dwóch procesorów.

[!code-csharp[PLINQ#5](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#5)]
[!code-vb[PLINQ#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#5)]

W przypadkach, gdy kwerenda wykonuje znaczną ilość pracy niezwiązanej z obliczeniami, takich jak we/wy pliku, może być korzystne określenie stopnia równoległości większej niż liczba rdzeni na komputerze.

## <a name="ordered-versus-unordered-parallel-queries"></a>Uporządkowane a nieuporządkowane zapytania równoległe

W niektórych kwerendach operator kwerendy musi dawać wyniki, które zachowują kolejność sekwencji źródłowej. PLINQ zapewnia <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operatorowi w tym celu. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>różni się <xref:System.Linq.ParallelEnumerable.AsSequential%2A>od . Sekwencja <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> jest nadal przetwarzana równolegle, ale jej wyniki są buforowane i sortowane. Ponieważ zachowanie kolejności zazwyczaj wymaga <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> dodatkowej pracy, sekwencja może <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> być przetwarzana wolniej niż sekwencja domyślna. To, czy określona uporządkowana operacja równoległa jest szybsza niż sekwencyjna wersja operacji, zależy od wielu czynników.

W poniższym przykładzie kodu pokazano, jak zdecydować się na zachowanie kolejności.

[!code-csharp[PLINQ#3](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#3)]
[!code-vb[PLINQ#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#3)]

Aby uzyskać więcej informacji, zobacz [Zachowanie zamówień w PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).

## <a name="parallel-vs-sequential-queries"></a>Zapytania równoległe i sekwencyjne

Niektóre operacje wymagają, aby dane źródłowe były dostarczane w sposób sekwencyjny. Operatory <xref:System.Linq.ParallelEnumerable> kwerend automatycznie powracają do trybu sekwencyjnego, gdy jest to wymagane. Dla operatorów zapytań zdefiniowanych przez użytkownika i delegatów użytkownika, które <xref:System.Linq.ParallelEnumerable.AsSequential%2A> wymagają wykonania sekwencyjnego, PLINQ udostępnia metodę. Podczas korzystania <xref:System.Linq.ParallelEnumerable.AsSequential%2A>, wszystkie kolejne operatory w kwerendzie są <xref:System.Linq.ParallelEnumerable.AsParallel%2A> wykonywane sekwencyjnie, dopóki nie zostanie wywołana ponownie. Aby uzyskać więcej informacji, zobacz [Jak: Łączenie równoległych i sekwencyjnych zapytań LINQ](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md).

## <a name="options-for-merging-query-results"></a>Opcje scalania wyników kwerendy

Gdy kwerenda PLINQ jest wykonywana równolegle, jej wyniki z każdego wątku roboczego `foreach` muszą`For Each` zostać scalone z powrotem do głównego wątku do użycia przez pętlę (w języku Visual Basic) lub wstawianie do listy lub tablicy. W niektórych przypadkach może być korzystne określenie określonego rodzaju operacji scalania, na przykład, aby rozpocząć uzyskiwanie wyników szybciej. W tym celu PLINQ <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> obsługuje metodę <xref:System.Linq.ParallelMergeOptions> i wyliczenie. Aby uzyskać więcej informacji, zobacz [Opcje scalania w plinq](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).

## <a name="the-forall-operator"></a>The ForAll Operator

W kolejnych kwerendach LINQ wykonanie jest odroczone do momentu wyliczenia zapytania `foreach` `For Each` w pętli (w języku Visual Basic) <xref:System.Linq.ParallelEnumerable.ToArray%2A> lub <xref:System.Linq.ParallelEnumerable.ToDictionary%2A>przez wywołanie metody takiej jak <xref:System.Linq.ParallelEnumerable.ToList%2A> , , lub . W PLINQ, można `foreach` również użyć do wykonania kwerendy i iterate za pośrednictwem wyników. Jednak `foreach` sam nie działa równolegle i dlatego wymaga, aby dane wyjściowe ze wszystkich zadań równoległych zostały scalone z powrotem do wątku, na którym działa pętla. W PLINQ, można `foreach` użyć, gdy należy zachować ostateczną kolejność wyników kwerendy, a także za każdym razem, `Console.WriteLine` gdy przetwarzasz wyniki w sposób szeregowy, na przykład podczas wywoływania dla każdego elementu. Aby przyspieszyć wykonywanie zapytań, gdy zachowanie kolejności nie jest wymagane i gdy <xref:System.Linq.ParallelEnumerable.ForAll%2A> przetwarzanie wyników może być zrównoległe, należy użyć metody do wykonania kwerendy PLINQ. <xref:System.Linq.ParallelEnumerable.ForAll%2A>nie wykonuje tego ostatniego kroku scalania. W poniższym przykładzie kodu <xref:System.Linq.ParallelEnumerable.ForAll%2A> pokazano, jak korzystać z metody. <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>jest używany w tym miejscu, ponieważ jest zoptymalizowany dla wielu wątków dodawanie jednocześnie bez próby usunięcia żadnych elementów.

[!code-csharp[PLINQ#4](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#4)]
[!code-vb[PLINQ#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#4)]

Na poniższej ilustracji `foreach` <xref:System.Linq.ParallelEnumerable.ForAll%2A> przedstawiono różnicę między i w odniesieniu do wykonywania zapytań.

![ForAll kontra ForEach](../../../docs/standard/parallel-programming/media/vs-isvnt-allvseach.png "VS_ISVNT_ALLvsEACH")

## <a name="cancellation"></a>Anulowanie

FUNKCJA PLINQ jest zintegrowana z typami anulowania w .NET Framework 4. (Aby uzyskać więcej informacji, zobacz [Anulowanie w zarządzanych wątków](../../../docs/standard/threading/cancellation-in-managed-threads.md).) W związku z tym w przeciwieństwie do sekwencyjnych LINQ do obiektów zapytań, zapytania PLINQ można anulować. Aby utworzyć kwerendę PLINQ, <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> można anulować, użyj <xref:System.Threading.CancellationToken> operatora w kwerendzie i podaj wystąpienie jako argument. Gdy <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość na tokenjest ustawiona na true, PLINQ zauważy go, zatrzyma <xref:System.OperationCanceledException>przetwarzanie we wszystkich wątkach i wyrzuci plik .

Jest możliwe, że kwerenda PLINQ może kontynuować przetwarzanie niektórych elementów po ustawieniu tokenu anulowania.

Aby uzyskać większą szybkość reakcji, można również odpowiadać na żądania anulowania w długotrwałych delegatów użytkowników. Aby uzyskać więcej informacji, zobacz [Jak: Anulować kwerendę PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).

## <a name="exceptions"></a>Wyjątki

Po wykonaniu kwerendy PLINQ, wiele wyjątków może być generowanych z różnych wątków jednocześnie. Ponadto kod do obsługi wyjątku może być w innym wątku niż kod, który zgłosił wyjątek. PLINQ używa <xref:System.AggregateException> tego typu do hermetyzacji wszystkich wyjątków, które zostały wygenerowane przez kwerendę i zorganizować te wyjątki z powrotem do wątku wywołującego. W wątku wywołującego wymagany jest tylko jeden blok try-catch. Można jednak iterate przez wszystkie wyjątki, które są zamknięte <xref:System.AggregateException> w i złapać wszystkie, które można bezpiecznie odzyskać z. W rzadkich przypadkach mogą być generowane pewne wyjątki, które nie są zawinięte w <xref:System.AggregateException>, a <xref:System.Threading.ThreadAbortException>s również nie są owinięte.

Gdy wyjątki mogą bąbelkować z powrotem do wątku łączącego, jest możliwe, że kwerenda może kontynuować przetwarzanie niektórych elementów po wyłączeniu wyjątku.

Aby uzyskać więcej informacji, zobacz [Jak: Obsługiwać wyjątki w kwerendzie PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).

## <a name="custom-partitioners"></a>Niestandardowe partycjonery

W niektórych przypadkach można zwiększyć wydajność kwerendy, zapisując niestandardowy partycjoner, który wykorzystuje niektóre cechy danych źródłowych. W kwerendzie niestandardowy partycjonator sam jest wyliczalny obiekt, który jest przeszukiwany.

[!code-csharp[PLINQ#2](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#2)]
[!code-vb[PLINQ#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq3.vb#2)]

PLINQ obsługuje stałą liczbę partycji (chociaż dane mogą być dynamicznie przypisywane do tych partycji w czasie wykonywania dla równoważenia obciążenia.). <xref:System.Threading.Tasks.Parallel.For%2A>i <xref:System.Threading.Tasks.Parallel.ForEach%2A> obsługuje tylko partycjonowanie dynamiczne, co oznacza, że liczba partycji zmienia się w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Partycjonery niestandardowe dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).

## <a name="measuring-plinq-performance"></a>Pomiar wydajności PLINQ

W wielu przypadkach kwerenda może być równoległa, ale obciążenie dotyczące konfigurowania kwerendy równoległej przewyższa uzyskaną korzyść z wydajności. Jeśli kwerenda nie wykonuje wiele obliczeń lub źródło danych jest małe, kwerenda PLINQ może być wolniejsza niż sekwencyjne badanie LINQ do obiektów. Za pomocą równoległego analizatora wydajności w programie Visual Studio Team Server można porównać wydajność różnych zapytań, zlokalizować wąskie gardła przetwarzania i określić, czy kwerenda jest uruchomiona równolegle, czy sekwencyjnie. Aby uzyskać więcej informacji, zobacz [Wizualizacja współbieżności](/visualstudio/profiling/concurrency-visualizer) i [Jak: Mierzyć wydajność kwerendy PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).

## <a name="see-also"></a>Zobacz też

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)
