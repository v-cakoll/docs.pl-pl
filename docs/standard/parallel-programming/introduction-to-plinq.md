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
ms.openlocfilehash: e50b2bf15d9a627f70ff01616bf2c72c70d7ff33
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290684"
---
# <a name="introduction-to-plinq"></a>Wprowadzenie do PLINQ

Parallel LINQ (PLINQ) jest równoległą implementacją wzorca [języka CLR](../../csharp/programming-guide/concepts/linq/index.md) . PLINQ implementuje pełen zestaw standardowych operatorów zapytań LINQ jako metody rozszerzenia dla <xref:System.Linq> przestrzeni nazw i ma dodatkowe operatory dla operacji równoległych. PLINQ łączy prostotę i czytelność składni LINQ z możliwością programowania równoległego.

> [!TIP]
> Jeśli nie znasz programu LINQ, oferuje on jednolity model służący do wykonywania zapytań dotyczących dowolnego wyliczalnego źródła danych w sposób bezpieczny dla tego typu. LINQ to Objects to nazwa zapytań LINQ, które są uruchamiane względem kolekcji w pamięci, takich jak <xref:System.Collections.Generic.List%601> tablice. W tym artykule przyjęto założenie, że masz podstawową wiedzę na temat LINQ. Aby uzyskać więcej informacji, zobacz temat [Language-Integrated Query (LINQ)](../../csharp/programming-guide/concepts/linq/index.md).

## <a name="what-is-a-parallel-query"></a>Co to jest zapytanie równoległe?

Zapytanie PLINQ na wiele sposobów przypomina nierównoległe zapytanie LINQ to Objects. PLINQ zapytania, podobnie jak zapytania sekwencyjne LINQ, działają na dowolnym z pamięci <xref:System.Collections.IEnumerable> lub w <xref:System.Collections.Generic.IEnumerable%601> źródle danych i mają odroczone wykonanie, co oznacza, że nie są uruchamiane, dopóki zapytanie nie zostanie wyliczone. Podstawowa różnica polega na tym, że PLINQ próbuje w pełni korzystać ze wszystkich procesorów w systemie. Robi to przez partycjonowanie źródła danych do segmentów, a następnie wykonywanie zapytania dla każdego segmentu w oddzielnych wątkach roboczych równolegle na wielu procesorach. W wielu przypadkach wykonywanie równoległe oznacza, że zapytanie działa znacznie szybciej.

Za pośrednictwem wykonywania równoległego PLINQ może osiągnąć znaczną poprawę wydajności w przypadku niektórych rodzajów zapytań, często tylko przez dodanie <xref:System.Linq.ParallelEnumerable.AsParallel%2A> operacji zapytania do źródła danych. Równoległość może jednak wprowadzać własne złożoności, a nie wszystkie operacje zapytań są wykonywane szybciej w PLINQ. W rzeczywistości przetwarzanie równoległe w rzeczywistości spowalnia niektóre zapytania. W związku z tym należy zrozumieć, jak problemy, takie jak porządkowanie, wpływają na zapytania równoległe. Aby uzyskać więcej informacji, zobacz temat [Omówienie przyspieszenie w PLINQ](understanding-speedup-in-plinq.md).

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).

Pozostała część tego artykułu zawiera omówienie głównych klas PLINQ i omawia sposób tworzenia zapytań PLINQ. Każda sekcja zawiera linki do bardziej szczegółowych informacji i przykładów kodu.

## <a name="the-parallelenumerable-class"></a>Klasa ParallelEnumerable

<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>Klasa uwidacznia prawie wszystkie funkcje PLINQ. A pozostałe <xref:System.Linq?displayProperty=nameWithType> typy przestrzeni nazw są kompilowane do zestawu System. Core. dll. Domyślne projekty C# i Visual Basic w programie Visual Studio odwołują się do zestawu i importują przestrzeń nazw.

<xref:System.Linq.ParallelEnumerable>zawiera implementacje wszystkich standardowych operatorów zapytań, które są obsługiwane przez LINQ to Objects, chociaż nie podejmuje próby zrównoleglanie każdego z nich. Jeśli nie znasz programu LINQ, zobacz [Introduction to LINQ (C#)](../../csharp/programming-guide/concepts/linq/index.md) i [Introduction to LINQ (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md).

Oprócz standardowych operatorów zapytań <xref:System.Linq.ParallelEnumerable> Klasa zawiera zestaw metod, które umożliwiają zachowanie specyficzne dla wykonywania równoległego. Te metody specyficzne dla PLINQ są wymienione w poniższej tabeli.

|Operator ParallelEnumerable|Opis|
|---------------------------------|-----------------|
|<xref:System.Linq.ParallelEnumerable.AsParallel%2A>|Punkt wejścia dla PLINQ. Określa, że pozostała część zapytania powinna być równoległa, jeśli jest to możliwe.|
|<xref:System.Linq.ParallelEnumerable.AsSequential%2A>|Określa, że pozostała część zapytania powinna być uruchamiana sekwencyjnie, jako nierównoległe zapytanie LINQ.|
|<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>|Określa, że PLINQ powinna zachować kolejność sekwencji źródłowej pozostałej części zapytania lub do czasu zmiany kolejności, na przykład za pomocą klauzuli OrderBy (order by w Visual Basic).|
|<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>|Określa, że PLINQ dla pozostałej części zapytania nie jest wymagana do zachowania kolejności sekwencji źródłowej.|
|<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>|Określa, że PLINQ powinien okresowo monitorować stan podanego tokenu anulowania i anulować wykonywanie, jeśli jest to wymagane.|
|<xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>|Określa maksymalną liczbę procesorów, które PLINQ powinny być używane do zrównoleglanie zapytania.|
|<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>|Zawiera wskazówkę dotyczącą sposobu, w jaki PLINQ powinna, jeśli jest to możliwe, scalanie równoległych wyników z powrotem do jednej sekwencji w wątku zużywanym.|
|<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>|Określa, czy PLINQ ma zrównoleglanie zapytanie, nawet gdy domyślne zachowanie będzie uruchamiane sekwencyjnie.|
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Metoda wyliczania wielowątkowego, która, w przeciwieństwie do iteracji wyników zapytania, umożliwia równoległe przetwarzanie wyników bez wcześniejszego scalania z powrotem do wątku odbiorcy.|
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>występują|Przeciążenie, które jest unikatowe dla PLINQ i włącza agregację pośrednią względem partycji lokalnych wątków, oraz ostateczną funkcję agregacji, aby połączyć wyniki wszystkich partycji.|

## <a name="the-opt-in-model"></a>Model zgody

Po zapisaniu zapytania należy zadecydować, aby PLINQ przez wywołanie <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> metody rozszerzenia źródła danych, jak pokazano w poniższym przykładzie.

[!code-csharp[PLINQ#1](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#1)]
[!code-vb[PLINQ#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#1)]

<xref:System.Linq.ParallelEnumerable.AsParallel%2A>Metoda rozszerzenia wiąże kolejne operatory zapytań, w tym przypadku `where` i `select` , do <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> implementacji.

## <a name="execution-modes"></a>Tryby wykonywania

Domyślnie PLINQ jest ostrożność. W czasie wykonywania infrastruktura PLINQ analizuje ogólną strukturę zapytania. Jeśli zapytanie może dać przyspieszenia przez przetwarzanie równoległe, PLINQ podzieli sekwencję źródłową z zadaniami, które mogą być uruchamiane współbieżnie. Jeśli zrównoleglanie zapytania nie jest bezpieczne, PLINQ po prostu uruchamia kwerendę sekwencyjnie. Jeśli PLINQ ma wybór między potencjalnie kosztownym algorytmem równoległym lub niedrogim algorytmem sekwencyjnym, wybiera algorytm sekwencyjny domyślnie. Możesz użyć <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metody i <xref:System.Linq.ParallelExecutionMode?displayProperty=nameWithType> wyliczenia, aby polecić PLINQ, aby wybrać algorytm równoległy. Jest to przydatne, gdy wiadomo, że testy i pomiary są wykonywane szybciej przez określone zapytanie. Aby uzyskać więcej informacji, zobacz [How to: Określanie trybu wykonywania w PLINQ](how-to-specify-the-execution-mode-in-plinq.md).

## <a name="degree-of-parallelism"></a>Stopień równoległości

Domyślnie PLINQ używa wszystkich procesorów na komputerze-hoście. Można wydać PLINQ do użycia nie więcej niż określoną liczbę procesorów przy użyciu <xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A> metody. Jest to przydatne, jeśli chcesz upewnić się, że inne procesy uruchomione na komputerze otrzymują określoną ilość czasu procesora CPU. Poniższy fragment kodu ogranicza zapytanie do wykorzystania maksymalnie dwóch procesorów.

[!code-csharp[PLINQ#5](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#5)]
[!code-vb[PLINQ#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#5)]

W przypadkach, gdy zapytanie wykonuje znaczną ilość pracy niezwiązanej z obliczeniami, taką jak pliki we/wy, warto określić stopień równoległości większy niż liczba rdzeni na komputerze.

## <a name="ordered-versus-unordered-parallel-queries"></a>Uporządkowane i nieuporządkowane zapytania równoległe

W niektórych zapytaniach operator zapytania musi generować wyniki, które zachowują kolejność sekwencji źródłowej. PLINQ zapewnia <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operator do tego celu. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>różni się od <xref:System.Linq.ParallelEnumerable.AsSequential%2A> . <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>Sekwencja jest nadal przetwarzana równolegle, ale jej wyniki są buforowane i sortowane. Ponieważ zachowanie kolejności zwykle wymaga dodatkowej pracy, <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> sekwencja może być przetwarzana wolniej niż domyślna <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> . Czy określona uporządkowana operacja równoległa jest szybsza niż sekwencyjna wersja operacji, zależy od wielu czynników.

Poniższy przykład kodu pokazuje, jak zrezygnować z zachowania porządku.

[!code-csharp[PLINQ#3](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#3)]
[!code-vb[PLINQ#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#3)]

Aby uzyskać więcej informacji, zobacz temat [porządkowania zamówień w PLINQ](order-preservation-in-plinq.md).

## <a name="parallel-vs-sequential-queries"></a>Zapytania równoległe a sekwencyjne

Niektóre operacje wymagają, aby dane źródłowe były dostarczane w sposób sekwencyjny. <xref:System.Linq.ParallelEnumerable>Operatory zapytań powracają do trybu sekwencyjnego automatycznie, gdy jest to wymagane. W przypadku operatorów zapytań zdefiniowanych przez użytkownika i delegatów użytkowników, którzy wymagają wykonania sekwencyjnego, PLINQ udostępnia <xref:System.Linq.ParallelEnumerable.AsSequential%2A> metodę. Gdy używasz <xref:System.Linq.ParallelEnumerable.AsSequential%2A> , wszystkie kolejne operatory w zapytaniu są wykonywane sekwencyjnie do momentu, gdy <xref:System.Linq.ParallelEnumerable.AsParallel%2A> zostanie wywołane ponownie. Aby uzyskać więcej informacji, zobacz [How to: łączenie równoległych i sekwencyjnych zapytań LINQ](how-to-combine-parallel-and-sequential-linq-queries.md).

## <a name="options-for-merging-query-results"></a>Opcje scalania wyników zapytania

Gdy zapytania PLINQ są wykonywane równolegle, jego wyniki z każdego wątku roboczego muszą zostać scalone z powrotem do głównego wątku w celu użycia przez `foreach` pętlę ( `For Each` w Visual Basic) lub wstawić do listy lub tablicy. W niektórych przypadkach może być korzystne określenie określonego rodzaju operacji scalania, na przykład w celu szybszego tworzenia wyników. W tym celu PLINQ obsługuje <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> metodę i <xref:System.Linq.ParallelMergeOptions> Wyliczenie. Aby uzyskać więcej informacji, zobacz [Opcje scalania w PLINQ](merge-options-in-plinq.md).

## <a name="the-forall-operator"></a>Operator ForAll

W sekwencyjnych zapytaniach LINQ wykonywanie jest odroczone do momentu wyliczenia zapytania w `foreach` `For Each` pętli (w Visual Basic) lub przez wywołanie metody takiej jak <xref:System.Linq.ParallelEnumerable.ToList%2A> , <xref:System.Linq.ParallelEnumerable.ToArray%2A> lub <xref:System.Linq.ParallelEnumerable.ToDictionary%2A> . W programie PLINQ można także użyć `foreach` do wykonania zapytania i iteracji przez wyniki. Jednak `foreach` samo nie działa równolegle i dlatego wymaga, aby dane wyjściowe ze wszystkich zadań równoległych były scalane z powrotem do wątku, w którym jest uruchomiona pętla. W programie PLINQ można użyć, `foreach` gdy należy zachować ostateczne porządkowanie wyników zapytania, a także za każdym razem, gdy przetwarzasz wyniki w sposób szeregowy, na przykład w przypadku wywoływania `Console.WriteLine` dla każdego elementu. Aby przyspieszyć wykonywanie zapytań, gdy zachowywanie kolejności nie jest wymagane i gdy przetwarzanie wyników może być równoległe, użyj metody, <xref:System.Linq.ParallelEnumerable.ForAll%2A> Aby wykonać zapytanie PLINQ. <xref:System.Linq.ParallelEnumerable.ForAll%2A>nie wykonuje tego końcowego kroku scalania. Poniższy przykład kodu pokazuje, jak używać <xref:System.Linq.ParallelEnumerable.ForAll%2A> metody. <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>jest używany w tym miejscu, ponieważ jest zoptymalizowany pod kątem wielu wątków, które dodają współbieżność bez próby usunięcia jakichkolwiek elementów.

[!code-csharp[PLINQ#4](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#4)]
[!code-vb[PLINQ#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#4)]

Na poniższej ilustracji przedstawiono różnicę między `foreach` i <xref:System.Linq.ParallelEnumerable.ForAll%2A> w odniesieniu do wykonywania zapytań.

![ForAll a ForEach](media/vs-isvnt-allvseach.png "VS_ISVNT_ALLvsEACH")

## <a name="cancellation"></a>Anulowanie

PLINQ jest zintegrowany z typami anulowania w .NET Framework 4. (Aby uzyskać więcej informacji, zobacz [Anulowanie w zarządzanych wątkach](../threading/cancellation-in-managed-threads.md).) W związku z tym, w przeciwieństwie do sekwencyjnych zapytań LINQ to Objects, można anulować zapytania PLINQ. Aby utworzyć zapytanie PLINQ z możliwością anulowania, użyj <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> operatora w zapytaniu i podaj <xref:System.Threading.CancellationToken> wystąpienie jako argument. Gdy <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> Właściwość w tokenie ma wartość true, PLINQ będzie zauważyć, Zatrzymaj przetwarzanie we wszystkich wątkach i zgłosić <xref:System.OperationCanceledException> .

Istnieje możliwość, że zapytanie PLINQ może nadal przetwarzać niektóre elementy po ustawieniu tokenu anulowania.

Aby zwiększyć czas odpowiedzi, można także odpowiedzieć na żądania anulowania w długotrwałych delegatach użytkowników. Aby uzyskać więcej informacji, zobacz [How to: Cancel a PLINQ Query](how-to-cancel-a-plinq-query.md).

## <a name="exceptions"></a>Wyjątki

Gdy wykonywane jest zapytanie PLINQ, wiele wyjątków może być generowanych z różnych wątków jednocześnie. Ponadto kod obsługujący wyjątek może znajdować się w innym wątku niż kod, który wywołał wyjątek. PLINQ używa <xref:System.AggregateException> typu do hermetyzacji wszystkich wyjątków zgłoszonych przez zapytanie i przekierować te wyjątki z powrotem do wątku wywołującego. W wątku wywołującym wymagany jest tylko jeden blok try-catch. Można jednak wykonać iterację we wszystkich wyjątkach, które są hermetyzowane w <xref:System.AggregateException> i przechwytywać dowolne z nich, z których można bezpiecznie odzyskać. W rzadkich przypadkach mogą zostać zgłoszone pewne wyjątki, które nie są opakowane w <xref:System.AggregateException> , a <xref:System.Threading.ThreadAbortException> s nie są również opakowane.

Gdy wyjątki mogą być rzutowane z powrotem do wątku sprzęgania, istnieje możliwość, że zapytanie może nadal przetwarzać niektóre elementy po wystąpieniu wyjątku.

Aby uzyskać więcej informacji, zobacz [How to: obsługa wyjątków w zapytaniu PLINQ](how-to-handle-exceptions-in-a-plinq-query.md).

## <a name="custom-partitioners"></a>Niestandardowe partycje

W niektórych przypadkach można poprawić wydajność zapytań, pisząc niestandardowy program do partycjonowania, który wykorzystuje pewną charakterystykę danych źródłowych. W zapytaniu jest to obiekt, który jest wyliczalny.

[!code-csharp[PLINQ#2](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#2)]
[!code-vb[PLINQ#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq3.vb#2)]

PLINQ obsługuje stałą liczbę partycji (mimo że dane mogą być dynamicznie przypisywane do tych partycji w czasie wykonywania równoważenia obciążenia). <xref:System.Threading.Tasks.Parallel.For%2A>i <xref:System.Threading.Tasks.Parallel.ForEach%2A> obsługują tylko partycjonowanie dynamiczne, co oznacza, że liczba partycji zmienia się w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [niestandardowe partycje dla PLINQ i TPL](custom-partitioners-for-plinq-and-tpl.md).

## <a name="measuring-plinq-performance"></a>Mierzenie wydajności PLINQ

W wielu przypadkach zapytanie może być równoległe, ale obciążenie związane z konfigurowaniem zapytania równoległego przewyższa uzyskane korzyści z wydajności. Jeśli zapytanie nie wykonuje dużo obliczeń lub źródło danych jest małe, zapytanie PLINQ może być wolniejsze niż sekwencyjne zapytanie LINQ to Objects. Można użyć analizatora wydajności równoległej w programie Visual Studio Team Server do porównania wydajności różnych zapytań, lokalizowania wąskich gardeł przetwarzania oraz określania, czy zapytanie działa równolegle, czy sekwencyjnie. Aby uzyskać więcej informacji, zobacz temat [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer) i [instrukcje: mierzenie wydajności zapytań PLINQ](how-to-measure-plinq-query-performance.md).

## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](introduction-to-plinq.md)
- [Ogólne informacje o przyspieszeniach w PLINQ](understanding-speedup-in-plinq.md)
