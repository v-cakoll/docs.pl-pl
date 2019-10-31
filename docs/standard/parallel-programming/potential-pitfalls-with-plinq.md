---
title: Potencjalne pułapki związane z PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
ms.openlocfilehash: 85098a0d10b4c05de52cd33d30ec5c4f4bbc594d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140005"
---
# <a name="potential-pitfalls-with-plinq"></a>Potencjalne pułapki związane z PLINQ

W wielu przypadkach PLINQ może zapewnić znaczną poprawę wydajności w stosunku do sekwencyjnych zapytań LINQ to Objects. Jednak w pracy przekształcają wykonywania zapytania wprowadzono złożoność, która może prowadzić do problemów, które w sekwencyjnym kodzie nie są zgodne lub nie są w ogóle obsługiwane. Ten temat zawiera wskazówki, które należy unikać podczas pisania zapytań PLINQ.

## <a name="do-not-assume-that-parallel-is-always-faster"></a>Nie zakładaj, że równoległy jest zawsze szybszy

Przetwarzanie równoległe czasami powoduje spowolnienie działania zapytania PLINQ niż jego odpowiednik LINQ to Objects. Podstawowa zasada kciuka polega na tym, że zapytania, które mają kilka elementów źródłowych i szybkich delegatów użytkowników, prawdopodobnie nie przyspieszenie dużo. Jednak ze względu na to, że wiele czynników jest związanych z wydajnością, zalecamy zmierzenie rzeczywistych wyników przed podjęciem decyzji o tym, czy używać PLINQ. Aby uzyskać więcej informacji, zobacz temat [Omówienie przyspieszenie w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

## <a name="avoid-writing-to-shared-memory-locations"></a>Unikaj zapisywania w lokalizacjach pamięci współdzielonej

W sekwencyjnym kodzie nie jest mało typowe odczytywanie z lub zapisywanie do zmiennych statycznych lub pól klas. Jeśli jednak wiele wątków uzyskuje dostęp do takich zmiennych jednocześnie, istnieje duże prawdopodobieństwo dla warunków wyścigu. Mimo że można użyć blokad do synchronizowania dostępu do zmiennej, koszt synchronizacji może obniżyć wydajność. W związku z tym zalecamy uniknięcie lub ograniczenie dostępu do udostępnionego stanu w kwerendzie PLINQ.

## <a name="avoid-over-parallelization"></a>Unikaj nadmiernego przetwarzanie równoległe

Korzystając z operatora `AsParallel`, naliczane są koszty narzutu dotyczące partycjonowania kolekcji źródłowej i synchronizowania wątków roboczych. Zalety przetwarzanie równoległe są bardziej ograniczone przez liczbę procesorów na komputerze. Nie ma przyspieszenie do uzyskania, uruchamiając wiele wątków powiązanych z obliczeniami tylko na jednym procesorze. W związku z tym należy zachować ostrożność, aby nie zrównoleglanie zapytania.

Najbardziej typowym scenariuszem, w którym może wystąpić zbyt przetwarzanie równoległe, jest zapytanie zagnieżdżone, jak pokazano w poniższym fragmencie kodu.

[!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

W takim przypadku najlepiej zrównoleglanie tylko zewnętrzne źródło danych (klienci), chyba że zostanie spełniony co najmniej jeden z następujących warunków:

- Wewnętrzne źródło danych (odbiorcy. Zamówienia) są znane jako bardzo długie.

- Wykonujesz kosztowne obliczenia dla każdego zamówienia. (Operacja pokazana w przykładzie nie jest kosztowna).

- System docelowy ma wystarczającą ilość procesorów do obsługi liczby wątków, które zostaną utworzone przez przekształcają zapytania na `cust.Orders`.

We wszystkich przypadkach najlepszym sposobem określenia optymalnego kształtu zapytania jest przetestowanie i pomiar. Aby uzyskać więcej informacji, zobacz [How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).

## <a name="avoid-calls-to-non-thread-safe-methods"></a>Unikaj wywołań metod niebezpiecznych dla wątków

Zapis w metodach wystąpienia niebezpiecznego dla wątków z zapytania PLINQ może prowadzić do uszkodzenia danych, które mogą lub nie zostać wykryte w programie. Może to również prowadzić do wyjątków. W poniższym przykładzie wiele wątków próbuje wywołać metodę `FileStream.Write` jednocześnie, która nie jest obsługiwana przez klasę.

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a>Ogranicz wywołania metod bezpiecznych dla wątków

Większość metod statycznych w .NET Framework są bezpieczne dla wątków i może być wywoływana z wielu wątków jednocześnie. Jednak nawet w takich przypadkach Synchronizacja może prowadzić do znacznego spowolnienia w zapytaniu.

> [!NOTE]
> Można to sprawdzić za pomocą wstawiania niektórych wywołań do <xref:System.Console.WriteLine%2A> w zapytaniach. Mimo że ta metoda jest używana w przykładach dokumentacji w celach demonstracyjnych, nie należy używać jej w zapytaniach PLINQ.

## <a name="avoid-unnecessary-ordering-operations"></a>Unikaj niepotrzebnych operacji porządkowania

Gdy PLINQ wykonuje zapytanie równolegle, dzieli sekwencję źródłową na partycje, które mogą być wykonywane współbieżnie na wielu wątkach. Domyślnie kolejność, w której są przetwarzane partycje, a wyniki są dostarczane nie jest przewidywalna (z wyjątkiem operatorów takich jak `OrderBy`). Można polecić PLINQ, aby zachować kolejność każdej sekwencji źródłowej, ale ma negatywny wpływ na wydajność. Najlepszym rozwiązaniem, jeśli jest to możliwe, jest struktura zapytań, dzięki czemu nie są one zależne od zachowywania kolejności. Aby uzyskać więcej informacji, zobacz temat [porządkowania zamówień w PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>Preferuj ForAll do ForEach, gdy jest to możliwe

Mimo że PLINQ wykonuje zapytanie na wielu wątkach, jeśli wyniki są używane w pętli `foreach` (`For Each` w Visual Basic), wyniki zapytania muszą zostać scalone z powrotem do jednego wątku i dostępne w szeregach przez moduł wyliczający. W niektórych przypadkach jest to nieuniknione. jednak zawsze, gdy jest to możliwe, należy użyć metody `ForAll`, aby umożliwić każdemu wątkowi wyprowadzanie własnych wyników, na przykład przez zapis do kolekcji bezpiecznej dla wątków, takiej jak <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.

Ten sam problem odnosi się do <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> innymi słowy, `source.AsParallel().Where().ForAll(...)` powinien być silnie preferowany

`Parallel.ForEach(source.AsParallel().Where(), ...)`.,

## <a name="be-aware-of-thread-affinity-issues"></a>Należy pamiętać o problemach z koligacją wątków

Niektóre technologie, na przykład współdziałanie modelu COM dla składników Single-Threading Apartment (STA), Windows Forms i Windows Presentation Foundation (WPF), nakładają ograniczenia koligacji wątku, które wymagają kodu do uruchomienia w określonym wątku. Na przykład zarówno w Windows Forms, jak i WPF, dostęp do formantu można uzyskać tylko w wątku, w którym został utworzony. Jeśli spróbujesz uzyskać dostęp do udostępnionego stanu formantu Windows Forms w zapytaniu PLINQ, zostanie zgłoszony wyjątek w przypadku uruchamiania programu w debugerze. (To ustawienie może być wyłączone). Jeśli jednak zapytanie jest używane w wątku interfejsu użytkownika, można uzyskać dostęp do formantu z pętli `foreach`, która wylicza wyniki zapytania, ponieważ ten kod jest wykonywany tylko w jednym wątku.

## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nie zakładaj, że iteracje ForEach, for i ForAll są zawsze wykonywane równolegle

Należy pamiętać, że poszczególne iteracje w pętli <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> lub <xref:System.Linq.ParallelEnumerable.ForAll%2A> mogą, ale nie muszą być wykonywane równolegle. W związku z tym należy unikać pisania kodu, który zależy do poprawnego wykonywania iteracji lub wykonywania iteracji w określonej kolejności.

Na przykład ten kod może być zakleszczony:

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

W tym przykładzie Jedna iteracja ustawia zdarzenie, a wszystkie inne iteracje oczekują na zdarzenie. Żadna z oczekujących iteracji nie może zostać zakończona do momentu zakończenia iteracji ustawienia zdarzenia. Jednak istnieje możliwość, że oczekujące iteracje blokują wszystkie wątki, które są używane do wykonywania pętli równoległej, przed wykonaniem iteracji ustawienia zdarzenia. Powoduje to zakleszczenie — iteracja ustawienia zdarzenia nigdy nie zostanie wykonana, a oczekujące iteracje nigdy nie zostaną wznowione.

W szczególności jedna iteracja pętli równoległej nigdy nie powinna czekać na kolejną iterację pętli, aby wykonać postęp. Jeśli pętla równoległa zdecyduje się na sekwencyjne planowanie iteracji, ale w kolejności odwrotnej, nastąpi zakleszczenie.

## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
