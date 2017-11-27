---
title: Wprowadzenie do PLINQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PLINQ queries, introduction to
ms.assetid: eaa720d8-8999-4eb7-8df5-3c19ca61cad0
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db9c3e16d4a8073fbce636f37490f719dbd93e4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-plinq"></a>Wprowadzenie do PLINQ
## <a name="what-is-a-parallel-query"></a>Co to jest równoległe zapytania?  
 Zapytanie języku zintegrowanym (LINQ) została wprowadzona w systemie [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].  Zawiera funkcje ujednoliconego modelu do wykonywania zapytań w dowolnej <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> źródła danych w sposób bezpieczny. LINQ do obiektów jest nazwą zapytań LINQ, które są uruchamiane przed kolekcje w pamięci, takich jak <xref:System.Collections.Generic.List%601> i tablic. W tym artykule założono, że podstawowa Omówienie programu LINQ. Aby uzyskać więcej informacji, zobacz [LINQ (zapytania język Language-Integrated)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 Równoległe LINQ (PLINQ) jest równoległe implementacji wzorca LINQ. Zapytania PLINQ pod wieloma względami podobny nie są równoległe zapytania składnika LINQ to obiekty. Zapytania dotyczące technologii PLINQ, podobnie jak sekwencyjnych [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)] zapytań, działać na dowolnym w pamięci <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> danych źródła i mają odłożone wykonywania, co oznacza nie rozpocząć wykonywania, dopóki wyliczeniu zapytania. Podstawowa różnica polega na tym, że PLINQ próbuje wykorzystać wszystkie procesory w systemie. Robi to partycjonowania źródła danych na segmenty, a następnie wykonywania zapytania w każdym segmencie na oddzielnych wątków równolegle na wiele procesorów. W wielu przypadkach wykonywanie równoległe oznacza, że wykonywania kwerendy znacznie szybciej.  
  
 Za pomocą wykonywanie równoległe PLINQ można osiągnąć znaczną poprawę wydajności za pośrednictwem starszego kodu dla niektórych typów kwerend często tylko przez dodanie <xref:System.Linq.ParallelEnumerable.AsParallel%2A> operacji ze źródłem danych zapytania. Jednak równoległości można wprowadzić własny skomplikowane, a nie wszystkie operacje kwerend szybsze w PLINQ. W rzeczywistości paralelizacja faktycznie spowalnia niektórych zapytań. W związku z tym należy zrozumieć, wpływ zapytania równoległe problemy, takie jak porządkowania. Aby uzyskać więcej informacji, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
> [!NOTE]
>  Ta dokumentacja używa wyrażenia lambda, aby zdefiniować delegatów w PLINQ. Jeśli nie masz doświadczenia z wyrażenia lambda w języku C# lub Visual Basic, zobacz [wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 W dalszej części tego artykułu powinien zawierać omówienie głównych klas PLINQ i opisano, jak tworzyć zapytania dotyczące technologii PLINQ. Każda sekcja zawiera łącza do bardziej szczegółowych informacji i kod przykłady.  
  
## <a name="the-parallelenumerable-class"></a>Klasa ParallelEnumerable  
 <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> Klasa przedstawia prawie wszystkie funkcje w PLINQ.  Go i pozostałe <xref:System.Linq?displayProperty=nameWithType> przestrzeni nazw typów są kompilowane do zestawu System.Core.dll. Domyślne projektów C# i Visual Basic w programie Visual Studio odwoływać się do zestawu i zaimportować przestrzeni nazw.  
  
 <xref:System.Linq.ParallelEnumerable>obejmuje implementacje wszystkich standardowych operatorów zapytań LINQ do obiektów obsługiwanych przez program, chociaż nie próbuje parallelize każdej z nich. Jeśli nie masz doświadczenia z [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)], zobacz [wprowadzenie do LINQ](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e).  
  
 Oprócz standardowych operatorów zapytań <xref:System.Linq.ParallelEnumerable> klasa zawiera zestaw metod umożliwiających zachowania specyficzne dla przetwarzania równoległego. Te metody specyficzne dla PLINQ są wymienione w poniższej tabeli.  
  
|ParallelEnumerable Operator|Opis|  
|---------------------------------|-----------------|  
|<xref:System.Linq.ParallelEnumerable.AsParallel%2A>|Punkt wejścia dla PLINQ. Określa, że pozostała część zapytania należy zarządzana przetwarzaniem, jeśli jest to możliwe.|  
|<xref:System.Linq.ParallelEnumerable.AsSequential%2A>|Określa, że resztą zapytania mają być uruchamiane sekwencyjnie, kwerenda LINQ nie są równoległe.|  
|<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>|Określa PLINQ należy zachować, kolejność sekwencji źródłowej dla pozostałej zapytania lub do momentu kolejność została zmieniona, na przykład przy użyciu klauzuli orderby (Order By w Vlsual Basic).|  
|<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>|Określa, czy PLINQ w pozostałej części zapytania nie jest wymagane w celu zachowania kolejności sekwencji źródłowej.|  
|<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>|Określa, że PLINQ należy okresowo monitorować stan token anulowania podanego i anulowania wykonywania, jeśli żądanie.|  
|<xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>|Określa maksymalną liczbę procesorów, które mają zostać użyte do parallelize zapytania PLINQ.|  
|<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>|Podpowiada o jak PLINQ powinien, jeśli jest to możliwe, wyniki równoległych scalania do tylko jednej sekwencji w wątku odbierającą.|  
|<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>|Określa, czy PLINQ powinien parallelize zapytanie, nawet wtedy, gdy jest to domyślne zachowanie byłoby uruchomić go po kolei.|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Metoda wielowątkowe wyliczenie umożliwiającą, w odróżnieniu od Iterowanie po wyniki zapytania, wyniki do przetworzenia równoległego bez pierwszy scalania do wątku konsumenta.|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>przeciążenia|Przeciążenie, które jest unikatowa dla PLINQ i umożliwia agregację pośredniego za pośrednictwem lokalnej wątku partycje, a także końcowego agregacji połączyć wyniki wszystkich partycji.|  
  
## <a name="the-opt-in-model"></a>Model opcjonalnych  
 Podczas pisania kwerendy korzystania z PLINQ wywołując <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> — metoda rozszerzenia w źródle danych, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[PLINQ#1](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#1)]
 [!code-vb[PLINQ#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#1)]  
  
 <xref:System.Linq.ParallelEnumerable.AsParallel%2A> — Metoda rozszerzenia wiąże operatory kolejne zapytania w tym przypadku `where` i `select`, do <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> implementacji.  
  
## <a name="execution-modes"></a>Tryby wykonywania  
 Domyślnie PLINQ jest zachowawcze. W czasie wykonywania infrastruktury PLINQ analizuje ogólną strukturę zapytania. Jeśli zapytanie jest prawdopodobnie umożliwiające uzyskanie speedups przez paralelizacja, PLINQ partycje sekwencji źródłowej do zadań, które można uruchamiać jednocześnie. Jeśli nie jest bezpieczne parallelize kwerendy, PLINQ tylko uruchamia zapytanie po kolei. Jeśli PLINQ wybór między potencjalnie kosztowne algorytm równoległe lub niedrogich algorytm sekwencyjnych, wybiera algorytm sekwencyjnych domyślnie. Można użyć <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> — metoda i <xref:System.Linq.ParallelExecutionMode?displayProperty=nameWithType> wyliczenie nakazać programowi PLINQ, aby wybrać algorytm równoległych. Jest to przydatne, gdy wiesz, testowania i pomiarów wykonujący określonego zapytania szybciej równolegle. Aby uzyskać więcej informacji, zobacz [porady: Określanie trybu wykonywania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
## <a name="degree-of-parallelism"></a>Stopień równoległości  
 Domyślnie PLINQ używa wszystkich procesorów na hoście. Możesz wydać PLINQ do użycia w nie więcej niż określona liczba procesorów za pomocą <xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A> metody. Jest to przydatne, jeśli chcesz upewnić się, że innych procesów uruchomionych na komputerze otrzymywać określoną ilość czasu procesora CPU. Poniższy fragment ogranicza kwerendę do wykorzystania maksymalnie dwa procesory.  
  
 [!code-csharp[PLINQ#5](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#5)]
 [!code-vb[PLINQ#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#5)]  
  
 W przypadkach, gdy zapytanie wykonuje znaczną część pracy z systemem innym niż granica obliczeń takich jak We/Wy plików może być przydatne do określenia stopień równoległości większa liczba rdzeni na maszynie.  
  
## <a name="ordered-versus-unordered-parallel-queries"></a>Uporządkowane i nieuporządkowaną zapytania równoległe  
 W niektórych kwerend operator zapytania musi mieć wyniki, które zachowują kolejność sekwencji źródłowej. Udostępnia PLINQ <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operatora w tym celu. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>różni się od <xref:System.Linq.ParallelEnumerable.AsSequential%2A>. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> Sekwencji jest nadal przetwarzane równolegle, ale jego wyniki są buforowane oraz sortowane. Ponieważ zachowanie porządku zwykle wymaga dodatkowej pracy <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> sekwencji mogą być przetwarzane wolniej niż domyślne <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> sekwencji. Czy określonej operacji równoległych uporządkowanej szybciej niż kolejnych wersji operacji zależy od wielu czynników.  
  
 Poniższy przykład kodu pokazuje, jak się porządku.  
  
 [!code-csharp[PLINQ#3](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#3)]
 [!code-vb[PLINQ#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#3)]  
  
 Aby uzyskać więcej informacji, zobacz [zamawianie zachowywania w PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
## <a name="parallel-vs-sequential-queries"></a>Równoległe vs. Sekwencyjnych zapytań  
 Niektóre operacje wymagają, że źródło danych mają być dostarczane sekwencyjnie. <xref:System.Linq.ParallelEnumerable> Zapytania operatory powraca do trybu sekwencyjnych automatycznie, kiedy to wymagane. Operatory zdefiniowane przez użytkownika zapytań i obiektów delegowanych użytkownika, które wymagają wykonania kolejnych zapewnia PLINQ <xref:System.Linq.ParallelEnumerable.AsSequential%2A> metody. Jeśli używasz <xref:System.Linq.ParallelEnumerable.AsSequential%2A>, wszystkie kolejne operatory w zapytaniu są wykonywane sekwencyjnie do <xref:System.Linq.ParallelEnumerable.AsParallel%2A> nie zostanie ponownie wywołany. Aby uzyskać więcej informacji, zobacz [porady: łączenie równoległych i sekwencyjnych zapytań LINQ](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md).  
  
## <a name="options-for-merging-query-results"></a>Opcje scalania wyników zapytania  
 Podczas zapytania PLINQ równolegle, jego wyniki każdego wątku roboczego muszą zostać połączone powrotem do wątku głównego wykorzystania przez `foreach` pętli (`For Each` w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), lub wstawienia go do listy lub tablicy. W niektórych przypadkach może być przydatne do określenia określonego rodzaju operację scalania, na przykład, aby rozpocząć szybsze tworzenie wyników. W tym celu obsługuje PLINQ <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> metody i <xref:System.Linq.ParallelMergeOptions> wyliczenia. Aby uzyskać więcej informacji, zobacz [opcje scalania w PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
## <a name="the-forall-operator"></a>ForAll — Operator  
 W kolejnych [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)] zapytań, wykonywania została odroczona dopóki wyliczeniu zapytania w `foreach` (`For Each` w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) w pętli lub poprzez wywoływanie metody takie jak <xref:System.Linq.ParallelEnumerable.ToList%2A> , <xref:System.Linq.ParallelEnumerable.ToArray%2A> , lub <xref:System.Linq.ParallelEnumerable.ToDictionary%2A>. W PLINQ, można również użyć `foreach` do wykonania zapytania i iterację w wynikach. Jednak `foreach` się nie uruchomić równolegle i w związku z tym wymaga ona, czy dane wyjściowe z wszystkich zadań równoległych być scalone wątku, na którym działa pętli. W PLINQ, można użyć `foreach` po muszą zachować ostateczna kolejność wyników zapytania, a także po każdej zmianie przetwarzanego wyniki w sposób szeregowych, na przykład podczas wywoływania `Console.WriteLine` dla każdego elementu. Szybsze wykonywanie zapytania, gdy porządku nie jest wymagany i podczas przetwarzania wyników może sam być zarządzana z przetwarzaniem, używać <xref:System.Linq.ParallelEnumerable.ForAll%2A> metodę wykonywanie zapytań PLINQ. <xref:System.Linq.ParallelEnumerable.ForAll%2A>nie wykonuje tego kroku końcowego scalania. Poniższy przykładowy kod przedstawia sposób użycia <xref:System.Linq.ParallelEnumerable.ForAll%2A> metody. <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>jest używany w tym miejscu, ponieważ jest zoptymalizowany do wiele wątków jednocześnie dodając próby usunięcia żadnych elementów.  
  
 [!code-csharp[PLINQ#4](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#4)]
 [!code-vb[PLINQ#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#4)]  
  
 Na poniższej ilustracji przedstawiono różnice między `foreach` i <xref:System.Linq.ParallelEnumerable.ForAll%2A> w odniesieniu do wykonywania zapytań.  
  
 ![ForAll — vs. Instrukcja ForEach](../../../docs/standard/parallel-programming/media/vs-isvnt-allvseach.png "VS_ISVNT_ALLvsEACH")  
  
## <a name="cancellation"></a>Anulowanie  
 PLINQ jest zintegrowany z typami anulowania w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. (Aby uzyskać więcej informacji, zobacz [anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md).) W związku z tym w przeciwieństwie do sekwencyjnego LINQ do obiektów zapytań, zapytania dotyczące technologii PLINQ mogą zostać anulowane. Aby utworzyć kwerendę PLINQ można anulować, użyj <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> operator w zapytaniu i podaj <xref:System.Threading.CancellationToken> wystąpienie jako argument. Gdy <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwości w tokenie ustawiono wartość true, PLINQ będzie zauważyć go, Zatrzymaj przetwarzanie na wszystkie wątki i zgłosić <xref:System.OperationCanceledException>.  
  
 Istnieje możliwość zapytań PLINQ może kontynuować przetwarzania niektóre elementy po ustawieniu token anulowania.  
  
 Aby uzyskać większą elastyczność można odpowiedzieć żądań anulowania w delegatach użytkownika długotrwałe. Aby uzyskać więcej informacji, zobacz [porady: Anulowanie zapytania PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="exceptions"></a>Wyjątki  
 Po wykonaniu zapytania PLINQ, wiele wyjątków może zostać zgłoszone z różnych wątków jednocześnie. Ponadto kod, aby obsłużyć wyjątek może być w innym wątku niż kod, który zgłosił wyjątek. Używa PLINQ <xref:System.AggregateException> typu Hermetyzowanie wszystkie wyjątki, które zostały zgłoszone przez zapytanie i kierować te wyjątki powrót do wywoływania wątku. W wątku wywołującym wymagane jest tylko jeden blok try-catch. Jednak można wykonać iterację wszystkie wyjątki, które znajdują się w <xref:System.AggregateException> i które można bezpiecznie odzyskanie catch. W rzadkich przypadkach, niektóre wyjątki może zostać zgłoszony, które nie są ujęte w <xref:System.AggregateException>, i <xref:System.Threading.ThreadAbortException>s są również nie opakowana.  
  
 Jest wywoływane, gdy wyjątki mogą bąbelkowy się wstecz do łącząca wątku, możliwe zapytania mogą nadal przetwarzania niektórych elementów po wyjątku jest.  
  
 Aby uzyskać więcej informacji, zobacz [porady: obsługa wyjątków w zapytaniu PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="custom-partitioners"></a>Niestandardowe Partycjonery  
 W niektórych przypadkach może poprawić wydajność zapytań, tworząc niestandardowe partycjonerem, który wykorzystuje pewne cechy w źródła danych. W zapytaniu niestandardowy obiekt partitioner sam jest obiekt wyliczalny, który jest poddawany kwerendzie.  
  
 [!code-csharp[PLINQ#2](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#2)]
 [!code-vb[PLINQ#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq3.vb#2)]  
  
 PLINQ obsługuje stała liczba partycji (chociaż dane mogą być dynamicznie przypisane do te partycje w czasie wykonywania w programie Równoważenie obciążenia.). <xref:System.Threading.Tasks.Parallel.For%2A>i <xref:System.Threading.Tasks.Parallel.ForEach%2A> obsługuje tylko dynamiczne partycjonowanie, co oznacza, że liczba partycji zmian w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [niestandardowe Partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="measuring-plinq-performance"></a>Pomiaru wydajności PLINQ  
 W wielu przypadkach zapytanie może być zarządzana z przetwarzaniem, ale korzyści wydajności zebranych przeważa nad koszty konfigurowania zapytania równoległe. Jeśli zapytanie nie wykonuje wiele obliczeń lub jeśli źródło danych jest mały, zapytania PLINQ może być mniejsza niż sekwencyjnych LINQ do obiektów zapytania. Równoległe Analizator wydajności w programie Visual Studio Team Server umożliwia porównanie wydajności różne zapytania do lokalizowania przetwarzania wąskich gardeł i ustalić, czy zapytanie działa równolegle lub sekwencyjnie. Aby uzyskać więcej informacji, zobacz [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer) i [porady: wydajności zapytań PLINQ miary](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)
