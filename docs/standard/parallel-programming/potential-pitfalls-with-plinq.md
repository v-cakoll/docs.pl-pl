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
ms.openlocfilehash: 44f40d6caad9187376a790f9a0ed09e22c861e37
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588601"
---
# <a name="potential-pitfalls-with-plinq"></a>Potencjalne pułapki z PLINQ

W wielu przypadkach PLINQ może zapewnić znaczną poprawę wydajności w porównaniu z sekwencyjnym LINQ do zapytań obiektów. Jednak praca równoległości wykonywania kwerendy wprowadza złożoność, która może prowadzić do problemów, które w kodzie sekwencyjnym nie są tak powszechne lub nie są w ogóle napotkane. W tym temacie wymieniono niektóre praktyki, których należy unikać podczas pisania zapytań PLINQ.

## <a name="dont-assume-that-parallel-is-always-faster"></a>Nie zakładaj, że równoległe jest zawsze szybsze

Równoległość czasami powoduje, że kwerenda PLINQ działać wolniej niż jego LINQ do obiektów równoważne. Podstawową zasadą jest to, że kwerendy, które mają kilka elementów źródłowych i szybkie delegatów użytkownika jest mało prawdopodobne, aby przyspieszyć znacznie. Jednak ponieważ wiele czynników są zaangażowane w wydajność, zaleca się zmierzyć rzeczywiste wyniki przed podjęciem decyzji, czy używać PLINQ. Aby uzyskać więcej informacji, zobacz [Opis przyspieszenia w PLINQ](understanding-speedup-in-plinq.md).

## <a name="avoid-writing-to-shared-memory-locations"></a>Unikaj pisania do lokalizacji pamięci współużytkowanej

W kodzie sekwencyjnym nie jest rzadkością odczytywanie lub zapisywanie zmiennych statycznych lub pól klasy. Jednak za każdym razem, gdy wiele wątków uzyskuje dostęp do takich zmiennych jednocześnie, istnieje duży potencjał dla warunków wyścigu. Mimo że można użyć blokad do synchronizacji dostępu do zmiennej, koszt synchronizacji może zaszkodzić wydajności. W związku z tym zaleca się, aby uniknąć lub przynajmniej ograniczyć dostęp do stanu udostępnionego w kwerendzie PLINQ jak najwięcej.

## <a name="avoid-over-parallelization"></a>Unikanie nadmiernej równoległości

Za pomocą `AsParallel` metody, należy ponieść koszty ogólne partycjonowania kolekcji źródłowej i synchronizacji wątków procesu roboczego. Korzyści z równoległości są dodatkowo ograniczone przez liczbę procesorów na komputerze. Nie ma żadnych przyspieszeń, które można uzyskać, uruchamiając wiele wątków związanych z obliczeniami na jednym procesorze. W związku z tym należy uważać, aby nie nadmiernie zrównoleglić kwerendy.

Najbardziej typowym scenariuszem, w którym może wystąpić nadmierna równoległość, jest zagnieżdżone kwerendy, jak pokazano w poniższym urywek.

[!code-csharp[PLINQ#20](~/samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

W takim przypadku najlepiej jest zrównoleglić tylko zewnętrzne źródło danych (klienci), chyba że stosuje się co najmniej jeden z następujących warunków:

- Wewnętrzne źródło danych (cust. zamówień) jest znany jako bardzo długi.

- Wykonujesz kosztowne obliczenia na każdym zamówieniu. (Operacja pokazana w przykładzie nie jest kosztowna).

- Wiadomo, że system docelowy ma wystarczającą liczbę procesorów do obsługi liczby wątków, które będą produkowane przez równoległość kwerendy na `cust.Orders`.

We wszystkich przypadkach najlepszym sposobem określenia optymalnego kształtu zapytania jest testowanie i mierzenie. Aby uzyskać więcej informacji, zobacz [Jak: Pomiar wydajności kwerendy PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).

## <a name="avoid-calls-to-non-thread-safe-methods"></a>Unikaj wezwań do metod niebezwiązanych z wątkami

Zapisywanie do metod wystąpienia niebezwłasników z zapytania PLINQ może prowadzić do uszkodzenia danych, które mogą lub nie mogą pozostać niewykryte w programie. Może to również prowadzić do wyjątków. W poniższym przykładzie wiele wątków będzie `FileStream.Write` próbować wywołać metodę jednocześnie, która nie jest obsługiwana przez klasę.

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a>Ograniczanie połączeń do metod bezpiecznych dla wątków

Większość metod statycznych w .NET Framework są bezpieczne dla wątków i mogą być wywoływane z wielu wątków jednocześnie. Jednak nawet w takich przypadkach synchronizacji zaangażowanych może prowadzić do znacznego spowolnienia w kwerendzie.

> [!NOTE]
> Możesz przetestować to samodzielnie, wstawiając niektóre wywołania <xref:System.Console.WriteLine%2A> w zapytaniach. Mimo że ta metoda jest używana w przykładach dokumentacji do celów demonstracyjnych, nie należy jej używać w zapytaniach PLINQ.

## <a name="avoid-unnecessary-ordering-operations"></a>Unikaj niepotrzebnych operacji zamawiania

Gdy PLINQ wykonuje kwerendę równolegle, dzieli sekwencję źródłową na partycje, które mogą być obsługiwane jednocześnie na wielu wątkach. Domyślnie kolejność przetwarzania partycji i dostarczania wyników nie jest przewidywalna (z wyjątkiem `OrderBy`operatorów, takich jak ). Można poinstruować PLINQ, aby zachować kolejność sekwencji źródłowej, ale ma to negatywny wpływ na wydajność. Najlepszym rozwiązaniem, gdy jest to możliwe, jest struktury kwerend, tak aby nie polegać na zachowaniu kolejności. Aby uzyskać więcej informacji, zobacz [Zachowanie porządku w PLINQ](order-preservation-in-plinq.md).

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>Preferuj ForAll do ForEach, gdy jest to możliwe

Chociaż PLINQ wykonuje kwerendę na wiele wątków, jeśli `foreach` zużywają wyniki w pętli (w`For Each` języku Visual Basic), a następnie wyniki kwerendy muszą być scalone z powrotem do jednego wątku i dostęp szeregowo przez moduł wyliczający. W niektórych przypadkach jest to nieuniknione; jednak, gdy jest to `ForAll` możliwe, użyj metody, aby umożliwić każdemu wątkowi wyprowadzanie własnych wyników, na przykład przez zapisywanie do kolekcji bezpiecznej dla wątków, takiej jak <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.

Ten sam problem <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>dotyczy . Innymi słowy, `source.AsParallel().Where().ForAll(...)` powinny być `Parallel.ForEach(source.AsParallel().Where(), ...)`zdecydowanie preferowane .

## <a name="be-aware-of-thread-affinity-issues"></a>Należy pamiętać o problemach z koligacjami wątków

Niektóre technologie, na przykład współdziałanie COM dla składników jednowątkowych apartamentów (STA), Windows Forms i Windows Presentation Foundation (WPF), nakładają ograniczenia koligacji wątku, które wymagają uruchomienia kodu w określonym wątku. Na przykład w formularzach systemu Windows i WPF WPF formantu można uzyskać tylko w wątku, w którym został utworzony. Jeśli spróbujesz uzyskać dostęp do udostępnionego stanu formantu Windows Forms w kwerendzie PLINQ, wyjątek jest wywoływany, jeśli jest uruchomiony w debugerze. (To ustawienie można wyłączyć). Jednak jeśli kwerenda jest zużywana w wątku interfejsu użytkownika, `foreach` następnie można uzyskać dostęp do formantu z pętli, która wylicza wyniki kwerendy, ponieważ ten kod jest wykonywany tylko w jednym wątku.

## <a name="dont-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nie zakładaj, że iteracje ForEach, For i ForAll zawsze są wykonywane równolegle

Ważne jest, aby pamiętać, że poszczególne <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>iteracje w , <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, lub <xref:System.Linq.ParallelEnumerable.ForAll%2A> pętli może, ale nie muszą wykonywać równolegle. W związku z tym należy unikać pisania kodu, który zależy od poprawności na równoległe wykonywanie iteracji lub na wykonywanie iteracji w określonej kolejności.

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

W tym przykładzie jedna iteracja ustawia zdarzenie, a wszystkie inne iteracje czekają na zdarzenie. Żadna z iteracji oczekiwania można wykonać, dopóki iteracja ustawienia zdarzenia nie zostanie ukończona. Jednak jest możliwe, że oczekiwanie iteracji bloku wszystkie wątki, które są używane do wykonywania pętli równoległej, przed iteracji ustawienia zdarzenia miał szansę wykonać. Powoduje to zakleszczenie — iteracja ustawienia zdarzeń nigdy nie zostanie wykonana, a iteracje oczekiwania nigdy nie zostaną wybudzeni.

W szczególności jedna iteracja pętli równoległej nigdy nie należy czekać na inną iterację pętli, aby poczynić postępy. Jeśli pętla równoległa zdecyduje się zaplanować iteracje sekwencyjnie, ale w odwrotnej kolejności wystąpi zakleszczenie.

## <a name="see-also"></a>Zobacz też

- [Równoległe LINQ (PLINQ)](introduction-to-plinq.md)
