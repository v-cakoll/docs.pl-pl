---
title: Potencjalne pułapki z PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
ms.openlocfilehash: 3ddc0c013335e6a7b4708a5dd8be0b2247b2f60c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74716255"
---
# <a name="potential-pitfalls-with-plinq"></a>Potencjalne pułapki z PLINQ

W wielu przypadkach PLINQ może zapewnić znaczną poprawę wydajności w stosunku do sekwencyjnego LINQ do obiektów zapytań. Jednak praca z równoległości wykonanie kwerendy wprowadza złożoność, która może prowadzić do problemów, które w kodzie sekwencyjnym, nie są tak powszechne lub nie występują w ogóle. W tym temacie wymieniono niektóre praktyki, których należy unikać podczas pisania zapytań PLINQ.

## <a name="dont-assume-that-parallel-is-always-faster"></a>Nie zakładaj, że równolegle jest zawsze szybszy

Równoległość czasami powoduje, że kwerenda PLINQ działa wolniej niż jego linq do obiektów równoważne. Podstawową zasadą jest, że zapytania, które mają kilka elementów źródłowych i delegatów szybkiego użytkownika jest mało prawdopodobne, aby przyspieszyć znacznie. Jednak ponieważ wiele czynników jest zaangażowanych w wydajność, zaleca się pomiar rzeczywistych wyników przed podjęciem decyzji, czy używać PLINQ. Aby uzyskać więcej informacji, zobacz [Opis przyspieszenia w PLINQ](understanding-speedup-in-plinq.md).

## <a name="avoid-writing-to-shared-memory-locations"></a>Unikaj zapisywania w lokalizacjach pamięci współużytkowanej

W kodzie sekwencyjnym nie jest rzadkością odczytywanie lub zapisywanie do zmiennych statycznych lub pól klas. Jednak zawsze, gdy wiele wątków uzyskuje dostęp do takich zmiennych jednocześnie, istnieje duży potencjał warunków wyścigu. Mimo że można użyć blokad do synchronizacji dostępu do zmiennej, koszt synchronizacji może zaszkodzić wydajności. W związku z tym zaleca się, aby uniknąć lub przynajmniej ograniczyć dostęp do stanu udostępnionego w kwerendzie PLINQ jak najwięcej.

## <a name="avoid-over-parallelization"></a>Unikaj nadmiernej równoległości

Za pomocą `AsParallel` metody, ponosi koszty ogólne partycjonowania kolekcji źródłowej i synchronizacji wątków roboczych. Korzyści z równoległości są dodatkowo ograniczone przez liczbę procesorów na komputerze. Nie ma żadnych przyspieszeń, które można uzyskać przez uruchomienie wielu wątków związanych z obliczeniami tylko na jednym procesorze. W związku z tym należy uważać, aby nie nadmiernie równoległości kwerendy.

Najbardziej typowym scenariuszem, w którym może wystąpić nadmierna równoległość, jest zagnieżdżona kwerenda, jak pokazano w poniższym fragmencie kodu.

[!code-csharp[PLINQ#20](~/samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

W takim przypadku najlepiej jest równoległość tylko zewnętrzne źródło danych (klientów), chyba że jeden lub więcej z następujących warunków stosuje się:

- Wewnętrzne źródło danych (cust. Zamówienia) jest znany jako bardzo długi.

- Wykonujesz kosztowne obliczenia na każdym zamówieniu. (Operacja pokazana w przykładzie nie jest kosztowna).

- Wiadomo, że system docelowy ma wystarczającą liczbę procesorów do obsługi liczby wątków, które zostaną wyprodukowane przez zleżenie kwerendy na `cust.Orders`.

We wszystkich przypadkach najlepszym sposobem określenia optymalnego kształtu zapytania jest testowanie i mierzenie. Aby uzyskać więcej informacji, zobacz [Jak: Mierzyć wydajność zapytań PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).

## <a name="avoid-calls-to-non-thread-safe-methods"></a>Unikaj wywołań metod innych niż bezpieczne dla wątków

Zapisywanie do metod wystąpienia innych niż wątki z kwerendy PLINQ może prowadzić do uszkodzenia danych, które mogą lub nie mogą pozostać niewykryte w programie. Może to również prowadzić do wyjątków. W poniższym przykładzie wiele wątków będzie próbować `FileStream.Write` wywołać metodę jednocześnie, który nie jest obsługiwany przez klasę.

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a>Ograniczanie wywołań do metod bezpiecznych dla wątków

Większość metod statycznych w .NET Framework są bezpieczne dla wątków i mogą być wywoływane z wielu wątków jednocześnie. Jednak nawet w takich przypadkach synchronizacja zaangażowanych może prowadzić do znacznego spowolnienia w kwerendzie.

> [!NOTE]
> Można przetestować <xref:System.Console.WriteLine%2A> to samodzielnie, wstawiając niektóre wywołania w kwerendach. Mimo że ta metoda jest używana w przykładach dokumentacji do celów demonstracyjnych, nie należy jej używać w kwerendach PLINQ.

## <a name="avoid-unnecessary-ordering-operations"></a>Unikaj niepotrzebnych operacji zamawiania

Gdy PLINQ wykonuje kwerendę równolegle, dzieli sekwencję źródłową na partycje, które mogą być obsługiwane jednocześnie na wielu wątkach. Domyślnie kolejność przetwarzania partycji i dostarczania wyników nie jest przewidywalna (z `OrderBy`wyjątkiem operatorów, takich jak ). Można poinstruować PLINQ, aby zachować kolejność dowolnej sekwencji źródłowej, ale ma to negatywny wpływ na wydajność. Najlepszym rozwiązaniem, gdy jest to możliwe, jest struktura zapytań, tak aby nie polegać na zachowanie porządku. Aby uzyskać więcej informacji, zobacz [Zachowanie zamówień w PLINQ](order-preservation-in-plinq.md).

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>Preferuj ForAll do ForEach, gdy jest to możliwe

Mimo że PLINQ wykonuje kwerendę na wiele wątków, `foreach` jeśli`For Each` zużywasz wyniki w pętli (w języku Visual Basic), a następnie wyniki kwerendy muszą być scalone z powrotem do jednego wątku i dostępne szeregowo przez moduł wyliczający. W niektórych przypadkach jest to nieuniknione; jednak w miarę możliwości `ForAll` należy użyć metody, aby umożliwić każdemu wątkowi do danych własnych <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>wyników, na przykład zapisując do kolekcji bezpieczne dla wątków, takich jak .

Ten sam problem <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>dotyczy . Innymi słowy, `source.AsParallel().Where().ForAll(...)` powinny być `Parallel.ForEach(source.AsParallel().Where(), ...)`zdecydowanie preferowane .

## <a name="be-aware-of-thread-affinity-issues"></a>Należy pamiętać o problemach z koligacji wątku

Niektóre technologie, na przykład współdziałanie modelu COM dla składników jednowątkowych apartamentów (STA), formularzy systemu Windows i podstawy prezentacji systemu Windows (WPF), nakładają ograniczenia koligacji wątków, które wymagają kodu do uruchomienia w określonym wątku. Na przykład w obu formularzach systemu Windows i WPF formant uzyskuje się tylko w wątku, w którym został utworzony. Jeśli spróbujesz uzyskać dostęp do stanu udostępnionego formantu Formularze systemu Windows w kwerendzie PLINQ, wyjątek jest wywoływany, jeśli używasz debugera. (To ustawienie można wyłączyć). Jednak jeśli kwerenda jest zużywana w wątku interfejsu użytkownika, `foreach` a następnie można uzyskać dostęp do formantu z pętli, która wylicza wyniki kwerendy, ponieważ kod jest wykonywany tylko na jednym wątku.

## <a name="dont-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nie zakładaj, że iteracje ForEach, For i ForAll zawsze są wykonywane równolegle

Ważne jest, aby pamiętać, że poszczególne <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>iteracje w , <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>lub <xref:System.Linq.ParallelEnumerable.ForAll%2A> pętli może, ale nie muszą wykonywać równolegle. W związku z tym należy unikać pisania kodu, który zależy od poprawności na równoległe wykonywanie iteracji lub na wykonanie iteracji w określonej kolejności.

Na przykład ten kod może zakleszczenie:

```vb
Dim mre = New ManualResetEventSlim()
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll(Sub(j)
   If j = Environment.ProcessorCount Then
       Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Set()
   Else
       Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Wait()
   End If
End Sub) ' deadlocks
```

```csharp
ManualResetEventSlim mre = new ManualResetEventSlim();
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll((j) =>
{
    if (j == Environment.ProcessorCount)
    {
        Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Set();
    }
    else
    {
        Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Wait();
    }
}); //deadlocks
```

W tym przykładzie jedna iteracja ustawia zdarzenie, a wszystkie inne iteracje czekają na zdarzenie. Żadna z iteracji oczekiwania nie może zakończyć się, dopóki iteracji ustawiania zdarzeń nie zostanie ukończona. Jednak jest możliwe, że iteracje oczekiwania zablokować wszystkie wątki, które są używane do wykonywania pętli równoległej, zanim iteracji ustawiania zdarzeń miał szansę wykonać. Powoduje to zakleszczenie — iteracji ustawiania zdarzeń nigdy nie zostanie wykonana, a iteracje oczekiwania nigdy nie obudzi.

W szczególności jedna iteracja pętli równoległej nigdy nie powinna czekać na inną iterację pętli, aby poczynić postępy. Jeśli pętla równoległa zdecyduje się zaplanować iteracje sekwencyjnie, ale w odwrotnej kolejności, nastąpi zakleszczenie.

## <a name="see-also"></a>Zobacz też

- [Równoległe LINQ (PLINQ)](parallel-linq-plinq.md)
