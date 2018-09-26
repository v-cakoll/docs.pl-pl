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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e44fd3e6f806eef3805416dafd90a4855e79b3c7
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206414"
---
# <a name="potential-pitfalls-with-plinq"></a>Potencjalne pułapki związane z PLINQ
W wielu przypadkach PLINQ może zapewnić znaczne ulepszenia wydajności za pośrednictwem sekwencyjnego LINQ do kwerendy obiekty. Jednak pracy przekształcają wykonywania zapytania wprowadza złożoności, który może prowadzić do problemów, które sekwencyjnego kodu nie są jako wspólne lub nie zostaną napotkane w ogóle. W tym temacie wymieniono niektóre rozwiązania, aby uniknąć podczas pisania zapytań PLINQ.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Nie należy zakładać, że równoległa jest zawsze szybciej  
 Czasami przetwarzanie równoległe powoduje, że zapytanie PLINQ działać wolniej niż jego LINQ do obiekty równoważne. Podstawowa zasada mówi to kwerend, które mają kilka elementów źródła i delegatów użytkownika szybkie, prawdopodobnie nie będzie przyspieszenie znacznie. Ponieważ wiele czynników są zaangażowane w wydajności, firma Microsoft zaleca jednak pomiaru rzeczywiste wyniki, przed podjęciem decyzji o tym, czy ma być używany program PLINQ. Aby uzyskać więcej informacji, zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Należy unikać pisania do lokalizacji udostępnionej pamięci  
 W kodzie sekwencyjnych nie jest niczym niezwykłym, aby odczytać lub zapisać zmienne statyczne lub pola klasy. Zawsze, gdy wiele wątków uzyskują dostęp do takich zmiennych jednocześnie, istnieje jednak duże prawdopodobieństwo jednoczesnego wyścigu. Mimo że blokad służy do synchronizowania dostępu do zmiennej, koszt synchronizacji może obniżyć wydajność. Dlatego zaleca się że uniknąć, lub co najmniej ograniczyć, dostęp do udostępnionego stanu w możliwie zapytanie PLINQ.  
  
## <a name="avoid-over-parallelization"></a>Unikaj nadmiernego przetwarzania równoległego  
 Za pomocą `AsParallel` operatora ponosić kosztów ogólnych partycjonowania kolekcji źródłowej i synchronizacji wątków roboczych. Korzyści wynikające z przetwarzaniem równoległym dalsze są ograniczone przez liczbę procesorów w komputerze. Nie ma żadnych przyspieszenie, które można uzyskać, uruchamiając wiele wątków powiązany obliczeniowych w tylko jednym procesorze. W związku z tym należy uważać, aby nie nadmiernie równoległe przetwarzanie zapytania.  
  
 Najbardziej typowym scenariuszem, w których nadmiernego przetwarzania równoległego może wystąpić trwa zapytań zagnieżdżonej, jak pokazano w poniższym fragmencie kodu.  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 W takim przypadku najlepiej zrównoleglić tylko zewnętrznym źródle danych (klientów), chyba że zastosować co najmniej jeden z następujących warunków:  
  
-   Źródło danych wewnętrzny (odbiorcy. Zamówienia) jest uznany za długa.  
  
-   Kosztowne obliczenia są wykonywane na każde zamówienie. (Operacja pokazano w przykładzie nie jest kosztowna).  
  
-   System docelowy jest znana wystarczającej liczby procesorów, którą należy obsługiwać liczbę wątków, które zostaną wygenerowane przez zrównoleglić zapytanie na `cust.Orders`.  
  
 We wszystkich przypadkach najlepszym sposobem określenia kształtu optymalne zapytania jest do testowania i miar. Aby uzyskać więcej informacji, zobacz [jak: wydajności zapytań PLINQ miary](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Należy unikać wywołania metod innych niż wątkowo  
 Zapisywanie metod wystąpienia innych wątkowo z PLINQ zapytania może prowadzić do uszkodzenia danych, które mogą lub nie może być wykryte w programach. Może to również prowadzić do wyjątków. W poniższym przykładzie wielu wątków będzie próba wywołania `Filestream.Write` metoda równocześnie, które nie jest obsługiwane przez klasę.  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Ogranicz wywołania metod metodą o bezpiecznych wątkach  
 Najbardziej statycznych metod .NET Framework są odporne na wątki i może być wywoływana z wielu wątków jednocześnie. Jednak nawet w takich przypadkach zaangażowane synchronizacji może prowadzić do znaczne spowolnienie w zapytaniu.  
  
> [!NOTE]
>  Możesz sprawdzić to samodzielnie, wstawiając wywołania niektórych <xref:System.Console.WriteLine%2A> w zapytaniach. Chociaż ta metoda jest używana w przykładach dokumentacji w celach demonstracyjnych, nie należy używać go w zapytania PLINQ.  
  
## <a name="avoid-unnecessary-ordering-operations"></a>Unikaj niepotrzebnych operacji porządkowanie  
 Gdy PLINQ jest wykonywane zapytania równolegle, dzieli sekwencję źródłową na partycje, które mogą być stosowane jednocześnie w wielu wątkach. Domyślnie nie jest przewidywalne kolejności, w którym partycje są przetwarzane, a wyniki są dostarczane (z wyjątkiem operatorów, takich jak `OrderBy`). Możesz nakazać PLINQ dla zachowania kolejności sekwencji dowolnego źródła, ale ma negatywny wpływ na wydajność. Najlepszym rozwiązaniem jest zawsze, gdy jest to możliwe, jest struktura zapytania, aby nie należy polegać na porządku. Aby uzyskać więcej informacji, zobacz [zamawianie zachowywania w PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>Wolisz ForAll ForEach, gdy jest to możliwe  
 Mimo że PLINQ wykonuje zapytanie w wielu wątkach, jeśli wykorzystasz wyniki w `foreach` pętli (`For Each` w języku Visual Basic), a następnie wyniki zapytania musi być scalana z powrotem do jednego wątku i szeregowo uzyskiwał dostęp do modułu wyliczającego. W niektórych przypadkach jest nieuniknione; Jednak w miarę możliwości należy użyć `ForAll` metodę umożliwiającą włączenie każdy wątek w danych wyjściowych swój własny wyników, na przykład, przez napisanie kolekcji metodą o bezpiecznych wątkach, takich jak <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.  
  
 Ten sam problem dotyczy <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> innymi słowy, `source.AsParallel().Where().ForAll(...)` powinny być silnie preferowany dla wiadomości  
  
 `Parallel.ForEach(source.AsParallel().Where(), ...)`.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Należy pamiętać o problemów koligacji wątku  
 Niektóre technologie, na przykład współdziałanie COM dla składników Single-Threaded apartamentu (STA), Windows Forms i Windows Presentation Foundation (WPF), nakładają ograniczenia koligacji wątku, które wymagają kod wymagany do uruchomienia w określonym wątku. Na przykład w Windows Forms i WPF formant może zostać oceniony jedynie w wątku, na którym została utworzona. Jeśli zostanie podjęta próba dostępu do udostępnionego stanu formantu Windows Forms w zapytaniu PLINQ, zgłaszany jest wyjątek, jeśli są uruchomione w debugerze. (To ustawienie może być wyłączone.) Jednak jeśli zapytanie jest używany przez wątek interfejsu użytkownika, tak powstały formant z `foreach` wyników pętli, która wylicza zapytania, ponieważ ten kod jest wykonywany tylko jednego wątku.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nie należy zakładać, że iteracji ForEach, dla i równolegle uruchomić zawsze ForAll  
 Ważne jest, aby pamiętać, że poszczególnych iteracji w <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> lub <xref:System.Linq.ParallelEnumerable.ForAll%2A> pętli może, ale nie trzeba wykonywać równolegle. W związku z tym należy unikać pisania żadnego kodu, który zależy od pod kątem poprawności na równoległe wykonywanie iteracji lub wykonywania iteracji w określonej kolejności.  
  
 Na przykład ten kod jest prawdopodobnie zakleszczenie:  
  
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
  
 W tym przykładzie jednej iteracji ustawia zdarzenie, a wszystkie inne iteracje oczekiwania na zdarzenie. Brak iteracji oczekiwania można wykonać przed ukończeniem iteracji ustawienie zdarzenia. Jednak jest możliwe, że iteracji oczekujące blokuje wszystkie wątki, które są używane do wykonywania pętli równoległej, zanim iteracji ustawienie zdarzenia miała szansę, aby wykonać. Skutkuje to zakleszczenie — iteracji ustawienie zdarzenia nigdy nie zostanie wykonana i iteracje oczekiwania nigdy nie będzie wznawiania.  
  
 W szczególności jednej iteracji pętli równoległej nigdy nie należy czekać na innej iteracji pętli postępu. Jeśli pętli równoległej decyduje zaplanować iteracje kolejno, ale w kolejności przeciwnej, nastąpi zakleszczenia.  
  
## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
