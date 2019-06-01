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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d41a88b7a9197a19a131cbda078297a96acdabfb
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457489"
---
# <a name="introduction-to-plinq"></a>Wprowadzenie do PLINQ

## <a name="what-is-a-parallel-query"></a>Co to jest zapytanie równoległe?

Language-Integrated Query (LINQ) została wprowadzona w [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]. Zawiera funkcje zunifikowany model przeznaczony do wykonywania zapytań o dowolne <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> źródła danych w sposób bezpieczny dla typu. LINQ to Objects do nazwa zapytania LINQ, które są uruchamiane na kolekcjach w pamięci, takich jak <xref:System.Collections.Generic.List%601> i tablice. W tym artykule założono, że masz podstawową wiedzę na temat LINQ. Aby uzyskać więcej informacji, zobacz [Language-Integrated Query (LINQ) - C# ](../../csharp/programming-guide/concepts/linq/index.md) lub [Language-Integrated Query (LINQ) - Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).

Równoległe LINQ (PLINQ) to implementacja przetwarzania równoległego wzorzec LINQ. Zapytanie PLINQ pod wieloma względami przypomina nierównoległy LINQ do kwerendy obiekty. Zapytania PLINQ, podobnie jak w przypadku sekwencyjnych [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)] zapytań, działają na wszystkie w pamięci <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> danych źródła i mają wstrzymane wykonanie, co oznacza, że nie rozpocząć wykonywanie aż do wyliczenia zapytania. Podstawowa różnica polega na tym, że PLINQ próbuje w pełni wykorzystać wszystkie procesory w systemie. Odbywa się to poprzez podział źródła danych na segmenty i następnie wykonywanie zapytań w każdym segmencie na oddzielnych wątkach roboczych równolegle na wielu procesorach. W wielu przypadkach wykonywanie równoległe oznacza, że zapytanie działa znacznie szybciej.

Za pomocą przetwarzania równoległego, PLINQ może osiągnąć znaczne ulepszenia wydajności w porównaniu ze starszym kodem dla niektórych rodzajów zapytań, często po prostu przez dodanie <xref:System.Linq.ParallelEnumerable.AsParallel%2A> operację do źródła danych zapytania. Jednakże równoległość może wprowadzać własne złożoności, a nie wszystkie operacje na zapytaniach działają szybciej w programie PLINQ. W rzeczywistości przetwarzanie równoległe faktycznie spowalnia niektóre zapytania. W związku z tym należy zrozumieć, jak problemy, takie jak zamawianie, wpływają na zapytania równolegle. Aby uzyskać więcej informacji, zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [wyrażeń Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

W dalszej części tego artykułu zawiera przegląd głównych klas PLINQ i w tym artykule omówiono sposób tworzenia zapytań PLINQ. Każda sekcja zawiera łącza do bardziej szczegółowych informacji i przykładów kodu.

## <a name="the-parallelenumerable-class"></a>Klasa ParallelEnumerable

<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> Klasy ujawnia prawie wszystkie funkcje w PLINQ. Ten i pozostałe z <xref:System.Linq?displayProperty=nameWithType> typy przestrzenie nazw są kompilowane do zestawu System.Core.dll. Domyślne projekty C# i Visual Basic w programie Visual Studio odwołują się do zestawu i importują przestrzeń nazw.

<xref:System.Linq.ParallelEnumerable> zawiera implementacje wszystkich standardowych operatorów zapytań, które obsługuje LINQ to Objects, ale go nie podejmuje próby zrównoleglenia. Jeśli nie jesteś zaznajomiony z [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)], zobacz [wprowadzenie do LINQ (C#)](../../csharp/programming-guide/concepts/linq/introduction-to-linq.md) i [wprowadzenie do LINQ (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md).

Oprócz standardowych operatorów zapytań <xref:System.Linq.ParallelEnumerable> klasa zawiera zestaw metod, które umożliwiają zachowania specyficzne dla wykonywania równoległego. Te metody specyficzne dla PLINQ są wymienione w poniższej tabeli.

|ParallelEnumerable Operator|Opis|
|---------------------------------|-----------------|
|<xref:System.Linq.ParallelEnumerable.AsParallel%2A>|Punkt wejścia dla PLINQ. Określa, że pozostała część zapytania powinna być przeprowadzana równolegle, jeśli jest to możliwe.|
|<xref:System.Linq.ParallelEnumerable.AsSequential%2A>|Określa, że pozostała część zapytania powinna być uruchamiana kolejno, jako nierównoległe zapytanie LINQ.|
|<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>|Określa, że PLINQ powinno zachować kolejność sekwencji źródłowej rest zapytania lub do momentu kolejność ulegnie zmianie, na przykład przy użyciu klauzuli orderby (Order By w języku Visual Basic).|
|<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>|Określa, że PLINQ dla pozostałej części zapytania nie jest wymagane dla zachowania kolejności sekwencji źródłowej.|
|<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>|Określa PLINQ powinno okresowo monitorować stan podanego tokenu anulowania i anulować wykonanie, jeśli żądanie.|
|<xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>|Określa maksymalną liczbę procesorów, których PLINQ powinien używać do zrównoleglenia zapytania.|
|<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>|Udostępnia wskazówkę o tym, jak program PLINQ powinien, jeśli jest to możliwe, scalać wyniki przetwarzania równoległego do tylko jednej sekwencji w zużywającym wątku.|
|<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>|Określa, czy PLINQ powinien zrównoleglić zapytanie, nawet wtedy, gdy zachowanie domyślne będzie uruchamiać jej sekwencyjnie.|
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Metoda wyliczania wielowątkowego, w której w przeciwieństwie do iteracji wyników kwerendy, umożliwia przetwarzanie równoległe bez scalania powrotnego do wątku konsumenta.|
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A> przeciążenie|Przeciążenia, które są unikatowe dla PLINQ i umożliwia agregacje pośrednie w partycji lokalnej wątku, a także funkcję agregacji końcowej w celu połączenia wyników wszystkich partycji.|

## <a name="the-opt-in-model"></a>Model Opt-in

Podczas pisywania zapytania zgadzaj się na PLINQ przez wywołanie <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> metody rozszerzenia dla źródła danych, jak pokazano w poniższym przykładzie.

[!code-csharp[PLINQ#1](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#1)]
[!code-vb[PLINQ#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#1)]

<xref:System.Linq.ParallelEnumerable.AsParallel%2A> — Metoda rozszerzenia wiąże operatory kolejnych zapytań, w tym przypadku `where` i `select`, <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> implementacji.

## <a name="execution-modes"></a>Tryby wykonywania

Domyślnie PLINQ jest Konserwatywny. W czasie wykonywania infrastruktura PLINQ analizuje ogólną strukturę kwerendy. Jeśli zapytanie jest prawdopodobne szybsze przez przetwarzanie równoległe, program PLINQ dzieli sekwencję źródłową na zadania, które mogą być uruchamiane równolegle. Jeśli nie jest bezpieczne równoległe przetwarzanie zapytania, program PLINQ po prostu wykonuje zapytanie sekwencyjnie. Jeśli narzędzie PLINQ ma wybór między potencjalnie kosztownym algorytmem równoległym lub niedrogim algorytmem sekwencyjnym, wybiera algorytm sekwencyjny domyślnie. Możesz użyć <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metody i <xref:System.Linq.ParallelExecutionMode?displayProperty=nameWithType> wyliczeniu, aby nakazać PLINQ wybrać algorytm równoległy. Jest to przydatne, gdy wiadomo, polegająca na przetestowaniu i miary, która określone zapytanie jest równolegle wykonywane szybciej. Aby uzyskać więcej informacji, zobacz [jak: Określanie trybu wykonywania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).

## <a name="degree-of-parallelism"></a>Stopień równoległości

Domyślnie PLINQ używa wszystkich procesorów na komputerze-hoście. Możesz nakazać PLINQ używać nie więcej niż określoną liczbę procesorów za pomocą <xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A> metody. Jest to przydatne, jeśli chcesz upewnić się, że inne procesy uruchomione na komputerze otrzymują określoną ilość czasu procesora CPU. Poniższy urywek ogranicza zapytanie do wykorzystywania maksymalnie dwóch procesorów.

[!code-csharp[PLINQ#5](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#5)]
[!code-vb[PLINQ#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#5)]

W przypadkach, gdzie zapytanie wykonuje znaczną ilość pracy bez powiązany obliczeniowych, takich jak We/Wy może być korzystne, aby określić stopień równoległości większy niż liczba rdzeni na maszynie.

## <a name="ordered-versus-unordered-parallel-queries"></a>Uporządkowane a nieuporządkowane zapytania równoległe

W niektórych zapytaniach operator zapytań musi generować wyniki, które zachowują kolejność sekwencji źródłowej. Program PLINQ zawiera <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operatora w tym celu. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> różni się od <xref:System.Linq.ParallelEnumerable.AsSequential%2A>. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> Sekwencji jest nadal przetwarzana równolegle, ale jego wyniki są buforowane i posortowane. Ponieważ zachowanie kolejności zazwyczaj wymaga dodatkowej pracy <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> sekwencji może być przetwarzana wolniej niż domyślna <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> sekwencji. Czy zamówiona operacja równoległa jest szybsza niż kolejna wersja operacji zależy od wielu czynników.

Poniższy przykład kodu pokazuje sposób korzystania z opcji dla zamówienia zachowania.

[!code-csharp[PLINQ#3](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#3)]
[!code-vb[PLINQ#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#3)]

Aby uzyskać więcej informacji, zobacz [zamawianie zachowywania w PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).

## <a name="parallel-vs-sequential-queries"></a>Równoległe programu vs. Zapytania sekwencyjne

Niektóre operacje wymagają, że dane źródłowe były dostarczane w sposób sekwencyjny. <xref:System.Linq.ParallelEnumerable> Zapytania, operatory powracają do trybu sekwencyjnego automatycznie, gdy jest to wymagane. Operatory zapytań zdefiniowanych przez użytkownika i delegatów użytkownika, które wymagają wykonywania sekwencyjnego, mechanizm PLINQ zawiera <xref:System.Linq.ParallelEnumerable.AsSequential%2A> metody. Kiedy używasz <xref:System.Linq.ParallelEnumerable.AsSequential%2A>, wszystkie kolejne operatory w zapytaniu są wykonywane sekwencyjnie aż do <xref:System.Linq.ParallelEnumerable.AsParallel%2A> wywoływana jest ponownie. Aby uzyskać więcej informacji, zobacz [jak: Łączenie równoległych i sekwencyjnych zapytań LINQ](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md).

## <a name="options-for-merging-query-results"></a>Opcje scalania wyników zapytań

Gdy zapytanie PLINQ jest wykonywane równolegle, jego wyniki z każdego wątku roboczego musi zostać połączony ponownie do głównego wątku, do spożycia przez `foreach` pętli (`For Each` w języku Visual Basic), lub wstawiania do listy lub tablicy. W niektórych przypadkach może być korzystne, aby określić określony rodzaj operacji scalania, na przykład, w celu generowania wyników znacznie szybciej. W tym celu narzędzie PLINQ obsługuje <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> metody i <xref:System.Linq.ParallelMergeOptions> wyliczenia. Aby uzyskać więcej informacji, zobacz [opcje scalania w PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).

## <a name="the-forall-operator"></a>ForAll Operator

W kolejnych [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)] zapytań, wykonanie jest odroczone do czasu wyliczenia zapytania albo w `foreach` (`For Each` w języku Visual Basic) w pętli lub poprzez wywoływanie metody, takie jak <xref:System.Linq.ParallelEnumerable.ToList%2A> , <xref:System.Linq.ParallelEnumerable.ToArray%2A> , lub <xref:System.Linq.ParallelEnumerable.ToDictionary%2A>. W programie PLINQ można również użyć `foreach` do wykonywania zapytania i iteracyjnego przeglądania wyników. Jednak `foreach` sam nie działa w sposób równoległy, a w związku z tym, wymaga on, że dane wyjściowe z wszystkich zadań równoległych jest scalana z powrotem do wątku, na którym działa pętla. W programie PLINQ można użyć `foreach` gdy należy zachować ostateczną kolejność wyników zapytania, a także gdy są przetwarzania wyniki w sposób szeregowy, na przykład gdy wywołujesz `Console.WriteLine` dla każdego elementu. Dla szybszego wykonywania zapytań, gdy porządku nie jest wymagane i podczas przetwarzania wyników może się odbywać się równolegle, użyj <xref:System.Linq.ParallelEnumerable.ForAll%2A> metodę, aby wykonać zapytanie PLINQ. <xref:System.Linq.ParallelEnumerable.ForAll%2A> nie wykonuje tego ostatniego kroku scalania. Poniższy przykład kodu pokazuje sposób użycia <xref:System.Linq.ParallelEnumerable.ForAll%2A> metody. <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> jest używana w tym miejscu, ponieważ jest zoptymalizowany dla wielu wątków dodawanych jednocześnie bez próby usuwania jakichkolwiek elementów.

[!code-csharp[PLINQ#4](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#4)]
[!code-vb[PLINQ#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#4)]

Poniższa ilustracja przedstawia różnicę między `foreach` i <xref:System.Linq.ParallelEnumerable.ForAll%2A> w odniesieniu do wykonywania zapytań.

![ForAll programu vs. ForEach](../../../docs/standard/parallel-programming/media/vs-isvnt-allvseach.png "VS_ISVNT_ALLvsEACH")

## <a name="cancellation"></a>Anulowanie

Program PLINQ jest zintegrowany z typami anulowania w .NET Framework 4. (Aby uzyskać więcej informacji, zobacz [anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md).) W związku z tym w przeciwieństwie do sekwencyjnego LINQ do zapytań obiekt, zapytania PLINQ może być anulowane. Aby utworzyć zapytanie PLINQ można anulować, użyj <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> operatora zapytania i podaj <xref:System.Threading.CancellationToken> wystąpienie jako argument. Gdy <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość token jest ustawiona na wartość true, PLINQ będzie zauważy, zatrzyma przetwarzanie na wszystkich wątkach i throw <xref:System.OperationCanceledException>.

Istnieje możliwość, że zapytanie PLINQ może kontynuować przetwarzanie niektóre elementy po ustawieniu tokenu odwołania.

Aby uzyskać szybsze odpowiedzi może również odpowiadać na żądania anulowania w długo wykonywanych delegatach użytkownika. Aby uzyskać więcej informacji, zobacz [jak: Anulowanie zapytania PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).

## <a name="exceptions"></a>Wyjątki

Po wykonaniu zapytania PLINQ, wiele wyjątków może być wyrzucanych z różnych wątków jednocześnie. Ponadto kod do obsługi wyjątków może być w innym wątku niż kod, który wygenerował wyjątek. Program PLINQ korzysta <xref:System.AggregateException> typ do hermetyzacji wszystkich wyjątków, które zostały zgłoszone przez zapytanie i kierowania tych wyjątków z powrotem do wątku wywołującego. Na wątku wywołującym wymagane jest tylko jedna blokada try-catch. Jednakże, można wykonać iterację przez wszystkie wyjątki, które są hermetyzowane w <xref:System.AggregateException> i przechwytywać tych, które możesz można bezpiecznie dokonać przywrócenia. W rzadkich przypadkach niektóre wyjątki mogą być generowane, które nie zostały zapakowane w <xref:System.AggregateException>, i <xref:System.Threading.ThreadAbortException>s nie również zostały zapakowane.

Kiedy wyjątki mogą się pojawiać z powrotem w sąsiednim wątku, jest możliwe, że zapytanie może w dalszym ciągu przetwarzać niektóre elementy po wyjątku jest zgłaszany.

Aby uzyskać więcej informacji, zobacz [jak: Obsługa wyjątków w zapytaniu PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).

## <a name="custom-partitioners"></a>Niestandardowe Partycjonery

W niektórych przypadkach może poprawić wydajność zapytań przez napisanie niestandardowego partycjonera, który wykorzystuje pewne cechy danych źródłowych. W zapytaniu sam niestandardowy partycjoner jest wyliczanym obiektem, którego dotyczy kwerenda.

[!code-csharp[PLINQ#2](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#2)]
[!code-vb[PLINQ#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq3.vb#2)]

Program PLINQ obsługuje stałą liczbę partycji (chociaż dane mogą być dynamicznie przypisane do tych partycji w czasie wykonywania dla równoważenia obciążenia.). <xref:System.Threading.Tasks.Parallel.For%2A> i <xref:System.Threading.Tasks.Parallel.ForEach%2A> obsługują tylko dynamiczne partycjonowanie, co oznacza, że liczba partycji zmienia w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [niestandardowe Partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).

## <a name="measuring-plinq-performance"></a>Mierzenie wydajności programu PLINQ

W wielu przypadkach zapytanie może odbywać się równolegle, ale obciążenie konfigurowania zapytania równoległego przewyższa uzyskane korzyści wydajności. Jeśli zapytanie nie wykonuje wielu obliczeń lub jeśli źródło danych jest małe, zapytanie PLINQ może być wolniejsze niż sekwencyjne zapytanie LINQ to Objects. Analizatora wydajności równoległej w Visual Studio Team Server umożliwia porównać wydajność różnych zapytań, zlokalizować wąskie gardła przetwarzania i aby określić, czy Twoje zapytanie działa równolegle czy w sekwencji. Aby uzyskać więcej informacji, zobacz [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer) i [jak: Mierzenie wydajności zapytań PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).

## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)
