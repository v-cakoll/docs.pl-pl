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
ms.openlocfilehash: e9ef72c2691a4dbb9c68202b29e0f5c77dcdaa74
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588183"
---
# <a name="introduction-to-plinq"></a>Wprowadzenie do PLINQ

Parallel LINQ (PLINQ) jest równoległą implementacją wzorca [zapytania zintegrowanego z językiem (LINQ).](../../csharp/programming-guide/concepts/linq/index.md) PLINQ implementuje pełny zestaw operatorów zapytań standardowych <xref:System.Linq> LINQ jako metody rozszerzenia dla obszaru nazw i ma dodatkowe operatory dla operacji równoległych. PLINQ łączy prostotę i czytelność składni LINQ z mocą programowania równoległego.

> [!TIP]
> Jeśli nie jesteś zaznajomiony z LINQ, posiada ujednolicony model do wykonywania zapytań dowolnego źródła danych wyliczalne w sposób bezpieczny dla typu. LINQ do obiektów jest nazwą dla zapytań LINQ, które są <xref:System.Collections.Generic.List%601> uruchamiane względem kolekcji w pamięci, takich jak i tablice. W tym artykule przyjęto założenie, że masz podstawową wiedzę linq. Aby uzyskać więcej informacji, zobacz [Zapytanie zintegrowane z językiem (LINQ)](../../csharp/programming-guide/concepts/linq/index.md).

## <a name="what-is-a-parallel-query"></a>Co to jest kwerenda równoległa?

Kwerenda PLINQ pod wieloma względami przypomina niedlaka linq do kwerendy obiektów. Zapytania PLINQ, podobnie jak sekwencyjne zapytania LINQ, działają <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> na dowolnym źródle w pamięci lub źródła danych i mają odroczone wykonanie, co oznacza, że nie rozpoczynają wykonywania, dopóki kwerenda nie zostanie wyliczona. Podstawową różnicą jest to, że PLINQ próbuje w pełni wykorzystać wszystkie procesory w systemie. Robi to przez partycjonowanie źródła danych na segmenty, a następnie wykonywanie kwerendy w każdym segmencie na oddzielnych wątków roboczych równolegle na wielu procesorach. W wielu przypadkach wykonanie równoległe oznacza, że kwerenda działa znacznie szybciej.

Dzięki wykonaniu równoległemu PLINQ można osiągnąć znaczną poprawę wydajności w stosunku do <xref:System.Linq.ParallelEnumerable.AsParallel%2A> starszego kodu dla niektórych rodzajów zapytań, często po prostu dodając operację kwerendy do źródła danych. Jednak równoległość może wprowadzić własne złożoności i nie wszystkie operacje kwerendy działają szybciej w PLINQ. W rzeczywistości równoległości faktycznie spowalnia niektóre zapytania. W związku z tym należy zrozumieć, jak problemy, takie jak kolejność wpływają na zapytania równoległe. Aby uzyskać więcej informacji, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

Poniżej dalsza część artykułu Zawiera omówienie głównych klas PLINQ i omówiono sposób tworzenia zapytań PLINQ. Każda sekcja zawiera łącza do bardziej szczegółowych informacji i przykładów kodu.

## <a name="the-parallelenumerable-class"></a>Klasa ParallelEnumerable

Klasa <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> eksponuje prawie wszystkie funkcje PLINQ. On i pozostałe <xref:System.Linq?displayProperty=nameWithType> typy obszaru nazw są kompilowane do zestawu System.Core.dll. Domyślne projekty języka C# i Visual Basic w programie Visual Studio odwołują się do zestawu i importują obszar nazw.

<xref:System.Linq.ParallelEnumerable>zawiera implementacje wszystkich standardowych operatorów zapytań, które linq do obiektów obsługuje, chociaż nie próbuje zrównoleglić każdego z nich. Jeśli nie znasz linq, zobacz [Wprowadzenie do LINQ (C#)](../../csharp/programming-guide/concepts/linq/index.md) i [Wprowadzenie do LINQ (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md).

Oprócz standardowych operatorów zapytań <xref:System.Linq.ParallelEnumerable> klasa zawiera zestaw metod, które umożliwiają zachowania specyficzne dla wykonywania równoległego. Te metody specyficzne dla PLINQ są wymienione w poniższej tabeli.

|Operator równoległy|Opis|
|---------------------------------|-----------------|
|<xref:System.Linq.ParallelEnumerable.AsParallel%2A>|Punkt wejścia dla PLINQ. Określa, że reszta kwerendy powinna być równoległa, jeśli jest to możliwe.|
|<xref:System.Linq.ParallelEnumerable.AsSequential%2A>|Określa, że pozostała część kwerendy powinna być uruchamiana sekwencyjnie jako kwerenda linq niedościskuteczna.|
|<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>|Określa, że PLINQ należy zachować kolejność sekwencji źródłowej dla pozostałej części kwerendy lub do czasu zmiany kolejności, na przykład przez użycie orderby (Order By in Visual Basic) klauzuli.|
|<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>|Określa, że PLINQ dla pozostałej części kwerendy nie jest wymagane do zachowania kolejności sekwencji źródłowej.|
|<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>|Określa, że PLINQ należy okresowo monitorować stan tokenu anulowania pod warunkiem i anulować wykonanie, jeśli jest to wymagane.|
|<xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>|Określa maksymalną liczbę procesorów, których plinq powinien używać do równoległości kwerendy.|
|<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>|Zawiera wskazówkę na temat tego, jak PLINQ należy, jeśli jest to możliwe, scalić równoległe wyniki z powrotem do tylko jednej sekwencji na wątku zużywającym.|
|<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>|Określa, czy PLINQ należy zrównać kwerendę nawet wtedy, gdy domyślne zachowanie byłoby uruchomić go sekwencyjnie.|
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Metoda wyliczenia wielowątkowego, która w przeciwieństwie do iteracji nad wynikami kwerendy umożliwia równoległe przetwarzanie wyników bez uprzedniego scalania z powrotem do wątku konsumenta.|
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>Przeciążenie|Przeciążenie, które jest unikatowe dla PLINQ i umożliwia agregację pośrednią za pomocą partycji lokalnych wątków oraz końcową funkcję agregacji w celu łączenia wyników wszystkich partycji.|

## <a name="the-opt-in-model"></a>The Opt-in Model

Podczas pisania kwerendy, wybierz plinq, wywołując <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> metodę rozszerzenia w źródle danych, jak pokazano w poniższym przykładzie.

[!code-csharp[PLINQ#1](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#1)]
[!code-vb[PLINQ#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#1)]

Metoda <xref:System.Linq.ParallelEnumerable.AsParallel%2A> rozszerzenia wiąże kolejne operatory kwerend, `where` w `select`tym <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> przypadku i , do implementacji.

## <a name="execution-modes"></a>Tryby wykonywania

Domyślnie PLINQ jest konserwatywny. W czasie wykonywania infrastruktury PLINQ analizuje ogólną strukturę kwerendy. Jeśli kwerenda może przynieść przyspieszenia przez równoległość, PLINQ partycje sekwencji źródłowej do zadań, które mogą być uruchamiane jednocześnie. Jeśli nie jest bezpieczne do równoległości kwerendy, PLINQ po prostu uruchamia kwerendę sekwencyjnie. Jeśli PLINQ ma wybór między algorytmem równoległym potencjalnie drogie lub niedrogi algorytm sekwencyjny, wybiera algorytm sekwencyjny domyślnie. Można użyć <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metody i <xref:System.Linq.ParallelExecutionMode?displayProperty=nameWithType> wyliczenia, aby poinstruować PLINQ, aby wybrać algorytm równoległy. Jest to przydatne, gdy wiesz, testując i miara, że określone zapytanie wykonuje szybciej równolegle. Aby uzyskać więcej informacji, zobacz [Jak: Określanie trybu wykonywania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).

## <a name="degree-of-parallelism"></a>Stopień równoległości

Domyślnie PLINQ używa wszystkich procesorów na komputerze-hoście. Za pomocą <xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A> tej metody można poinstruować PLINQ, aby używała nie więcej niż określonej liczby procesorów. Jest to przydatne, gdy chcesz upewnić się, że inne procesy uruchomione na komputerze otrzymują określoną ilość czasu procesora CPU. Poniższy fragment kodu ogranicza kwerendę do wykorzystania maksymalnie dwóch procesorów.

[!code-csharp[PLINQ#5](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#5)]
[!code-vb[PLINQ#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#5)]

W przypadkach, gdy kwerenda wykonuje znaczną ilość pracy związanej z obliczeniami, takich jak we/wy pliku, może być korzystne określenie stopnia równoległości większej niż liczba rdzeni na komputerze.

## <a name="ordered-versus-unordered-parallel-queries"></a>Uporządkowane kwerendy równoległe w porównaniu z nieuiarszowanymi zapytaniami równoległymi

W niektórych kwerendach operator kwerendy musi uzyskać wyniki, które zachowują kolejność sekwencji źródłowej. PLINQ zapewnia <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operatorowi w tym celu. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>różni się <xref:System.Linq.ParallelEnumerable.AsSequential%2A>od . Sekwencja <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> jest nadal przetwarzane równolegle, ale jej wyniki są buforowane i sortowane. Ponieważ zachowanie zamówienia zazwyczaj obejmuje dodatkową <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> pracę, sekwencja może być <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> przetwarzana wolniej niż domyślna sekwencja. To, czy określona operacja równoległa uporządkowana jest szybsza niż sekwencyjna wersja operacji, zależy od wielu czynników.

Poniższy przykład kodu pokazuje, jak zdecydować się na zachowanie kolejności.

[!code-csharp[PLINQ#3](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#3)]
[!code-vb[PLINQ#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#3)]

Aby uzyskać więcej informacji, zobacz [Zachowanie porządku w PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).

## <a name="parallel-vs-sequential-queries"></a>Zapytania równoległe a sekwencyjne

Niektóre operacje wymagają, aby dane źródłowe były dostarczane w sposób sekwencyjny. Operatory <xref:System.Linq.ParallelEnumerable> kwerend automatycznie powracają do trybu sekwencyjnego, gdy jest to wymagane. Dla operatorów zapytań zdefiniowanych przez użytkownika i delegatów użytkownika, <xref:System.Linq.ParallelEnumerable.AsSequential%2A> które wymagają wykonywania sekwencyjnego, PLINQ udostępnia metodę. Podczas korzystania <xref:System.Linq.ParallelEnumerable.AsSequential%2A>wszystkie kolejne operatory w kwerendzie są <xref:System.Linq.ParallelEnumerable.AsParallel%2A> wykonywane sekwencyjnie, dopóki nie zostanie wywołana ponownie. Aby uzyskać więcej informacji, zobacz [Jak: Łączenie równoległych i sekwencyjnych zapytań LINQ](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md).

## <a name="options-for-merging-query-results"></a>Opcje scalania wyników kwerendy

Gdy kwerenda PLINQ wykonuje równolegle, jej wyniki z każdego wątku roboczego muszą `foreach` być`For Each` scalone z powrotem do wątku głównego do użycia przez pętlę (w języku Visual Basic) lub wstawiania do listy lub tablicy. W niektórych przypadkach może być korzystne określenie określonego rodzaju operacji scalania, na przykład, aby szybciej rozpocząć tworzenie wyników. W tym celu PLINQ <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> obsługuje metodę <xref:System.Linq.ParallelMergeOptions> i wyliczenie. Aby uzyskać więcej informacji, zobacz [Opcje scalania w PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).

## <a name="the-forall-operator"></a>The ForAll Operator

W kolejnych kwerendach LINQ wykonanie jest odroczone, dopóki kwerenda nie `foreach` zostanie`For Each` wyliczona w pętli (w <xref:System.Linq.ParallelEnumerable.ToList%2A> języku <xref:System.Linq.ParallelEnumerable.ToArray%2A> Visual <xref:System.Linq.ParallelEnumerable.ToDictionary%2A>Basic) lub wywołanie metody, takiej jak , lub . W PLINQ, można `foreach` również użyć do wykonania kwerendy i iteracji za pośrednictwem wyników. Jednak `foreach` sama nie działa równolegle i dlatego wymaga, aby dane wyjściowe ze wszystkich równoległych zadań zostały scalone z powrotem do wątku, na którym jest uruchomiona pętla. W PLINQ, można `foreach` użyć, gdy należy zachować ostateczną kolejność wyników kwerendy, a także za każdym razem, `Console.WriteLine` gdy są przetwarzane wyniki w sposób szeregowy, na przykład, gdy wywołujesz dla każdego elementu. Aby przyspieszyć wykonywanie zapytań, gdy zachowanie zleceń nie jest wymagane i gdy <xref:System.Linq.ParallelEnumerable.ForAll%2A> przetwarzanie wyników może być równoległe, użyj metody do wykonania kwerendy PLINQ. <xref:System.Linq.ParallelEnumerable.ForAll%2A>nie wykonuje tego ostatniego kroku scalania. Poniższy przykład kodu pokazuje, <xref:System.Linq.ParallelEnumerable.ForAll%2A> jak używać metody. <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>jest w tym miejscu używany, ponieważ jest zoptymalizowany pod kątem wielu wątków dodawanie jednocześnie bez próby usunięcia żadnych elementów.

[!code-csharp[PLINQ#4](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#4)]
[!code-vb[PLINQ#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#4)]

Na poniższej ilustracji `foreach` <xref:System.Linq.ParallelEnumerable.ForAll%2A> przedstawiono różnicę między i w odniesieniu do wykonywania kwerend.

![ForAll kontra ForEach](../../../docs/standard/parallel-programming/media/vs-isvnt-allvseach.png "VS_ISVNT_ALLvsEACH")

## <a name="cancellation"></a>Anulowanie

PLINQ jest zintegrowany z typami anulowania w .NET Framework 4. (Aby uzyskać więcej informacji, zobacz [Anulowanie w wątkach zarządzanych](../../../docs/standard/threading/cancellation-in-managed-threads.md).) W związku z tym, w przeciwieństwie do sekwencyjneGO LINQ do kwerend obiektów, zapytania PLINQ można anulować. Aby utworzyć kwerendę PLINQ, <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> której można anulować, <xref:System.Threading.CancellationToken> użyj operatora w kwerendzie i podaj wystąpienie jako argument. Gdy <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość na tokenie jest ustawiona na true, PLINQ zauważy to, zatrzyma przetwarzanie na wszystkich wątkach i wrzuć <xref:System.OperationCanceledException>.

Jest możliwe, że zapytanie PLINQ może nadal przetwarzać niektóre elementy po ustawieniu tokenu anulowania.

Aby uzyskać większą szybkość reakcji, można również odpowiadać na żądania anulowania w długotrwałych delegatów użytkowników. Aby uzyskać więcej informacji, zobacz [Jak: Anulowanie zapytania PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).

## <a name="exceptions"></a>Wyjątki

Podczas wykonywania kwerendy PLINQ, wiele wyjątków może być zgłaszanych z różnych wątków jednocześnie. Ponadto kod do obsługi wyjątku może być w innym wątku niż kod, który zgłosił wyjątek. PLINQ używa <xref:System.AggregateException> tego typu do hermetyzacji wszystkich wyjątków, które zostały odrzucone przez kwerendę i marshal te wyjątki z powrotem do wątku wywołującego. W wątku wywołującym wymagany jest tylko jeden blok try-catch. Można jednak iterować przez wszystkie wyjątki, które są hermetyzowane w <xref:System.AggregateException> i złapać dowolne, które można bezpiecznie odzyskać z. W rzadkich przypadkach niektóre wyjątki mogą być <xref:System.AggregateException>generowane, <xref:System.Threading.ThreadAbortException>które nie są zawinięte w , i s również nie są zawijane.

Gdy wyjątki są dozwolone do bańki z powrotem do wątku łączącego, a następnie jest możliwe, że kwerenda może kontynuować przetwarzanie niektórych elementów po wyjątek jest wywoływany.

Aby uzyskać więcej informacji, zobacz [Jak: Obsługa wyjątków w kwerendzie PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).

## <a name="custom-partitioners"></a>Niestandardowe partycjonowania

W niektórych przypadkach można zwiększyć wydajność kwerendy, pisząc niestandardowy partycjoner, który korzysta z niektórych cech danych źródłowych. W kwerendzie sam partycjonowanie niestandardowe jest obiektem wyliczalnym, który jest wyszukiwany.

[!code-csharp[PLINQ#2](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#2)]
[!code-vb[PLINQ#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq3.vb#2)]

PLINQ obsługuje stałą liczbę partycji (chociaż dane mogą być dynamicznie ponownie przypisane do tych partycji w czasie wykonywania dla równoważenia obciążenia.). <xref:System.Threading.Tasks.Parallel.For%2A>i <xref:System.Threading.Tasks.Parallel.ForEach%2A> obsługuje tylko dynamiczne partycjonowanie, co oznacza, że liczba partycji zmienia się w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Niestandardowe partitionery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).

## <a name="measuring-plinq-performance"></a>Pomiar wydajności PLINQ

W wielu przypadkach kwerendy można zrównoleglić, ale obciążenie związane z konfigurowaniem zapytania równoległego przeważa nad uzyskanymi korzyściami z wydajności. Jeśli kwerenda nie wykonuje wiele obliczeń lub jeśli źródło danych jest małe, kwerenda PLINQ może być wolniejsza niż sekwencyjne zapytanie LINQ do obiektów. Analizator wydajności równoległej w programie Visual Studio Team Server służy do porównywania wydajności różnych zapytań, lokalizowania wąskich gardeł przetwarzania i określania, czy kwerenda jest uruchomiona równolegle, czy sekwencyjnie. Aby uzyskać więcej informacji, zobacz [Wizualizator współbieżności](/visualstudio/profiling/concurrency-visualizer) i [jak: Pomiar wydajności kwerendy PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).

## <a name="see-also"></a>Zobacz też

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
- [Ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)
