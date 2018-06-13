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
ms.openlocfilehash: 73ec2d2fb73ee95b39a15307d136c35542578c41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591719"
---
# <a name="potential-pitfalls-with-plinq"></a>Potencjalne pułapki związane z PLINQ
W wielu przypadkach PLINQ można zapewnia znaczną poprawę wydajności za pośrednictwem sekwencyjnych LINQ do obiektów zapytań. Jednak pracy parallelizing wykonywania zapytania wprowadza złożoności, który może prowadzić do problemów, które w kolejnych kodu nie są jako wspólne lub w ogóle nie wystąpi. W tym temacie wymieniono niektóre praktyki, których należy unikać podczas pisania zapytania dotyczące technologii PLINQ.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Nie przyjęto założenie, że równolegle jest zawsze szybsze  
 Czasami paralelizacja powoduje, że zapytania PLINQ działać wolniej niż jego LINQ do obiektów równoważne. Podstawowe zasadą to zapytań, które ma kilka elementy źródłowe i delegatów szybkiego użytkownika prawdopodobnie nie będzie przyspieszenie znacznie. Jednak ponieważ wydajności są związane z wielu czynników, zaleca się zmierzyć rzeczywiste wyniki, przed podjęciem decyzji o tym, czy używać PLINQ. Aby uzyskać więcej informacji, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Unikaj zapisywanie w lokalizacji pamięci współużytkowanej  
 W kolejnych kodu nie jest rzadko do odczytu lub zapisu zmienne statyczne lub pola klasy. Zawsze, gdy wiele wątków uzyskują dostęp do tych zmiennych współbieżnie, istnieje jednak możliwość big wyścigu. Mimo że używasz blokad synchronizujący dostęp do zmiennej, kosztów synchronizacji może pogarszać wydajność. Dlatego zalecamy można uniknąć, lub co najmniej ograniczyć dostęp do udostępniania stanu w zapytaniu PLINQ możliwie.  
  
## <a name="avoid-over-parallelization"></a>Unikaj nadmiernego Paralelizacja  
 Za pomocą `AsParallel` operatora ponoszenia kosztów partycjonowania kolekcji źródłowej i synchronizowanie wątków roboczych. Korzyści równoległości dalsze są ograniczone przez liczbę procesorów w komputerze. Nie ma żadnych przyspieszenie, które można uzyskać, uruchamiając wiele wątków wiązaniem obliczeń w tylko jednym procesorze. W związku z tym należy uważać, aby nie nadmiernie parallelize zapytania.  
  
 Najbardziej typowy scenariusz, w które nadmierne paralelizacja może wystąpić jest zapytania zagnieżdżone, jak pokazano w poniższy fragment kodu.  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 W takim przypadku warto parallelize tylko zewnętrzne źródło danych (klienci), chyba że zastosowanie co najmniej jeden z następujących warunków:  
  
-   Źródło danych wewnętrzny (odbiorcy. Zamówienia) jest uznany za długa.  
  
-   Kosztowna obliczenia są wykonywane na każdej kolejności. (Operacja pokazano w przykładzie nie jest kosztowna).  
  
-   System docelowy jest znana wystarczającą do obsługi liczby wątków, które zostaną utworzone przez parallelizing zapytanie na procesorów `cust.Orders`.  
  
 We wszystkich przypadkach najlepszy sposób, aby ustalić optymalne zapytania kształtu jest do testowania i miar. Aby uzyskać więcej informacji, zobacz [porady: wydajności zapytań PLINQ miary](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Unikaj wywołania metod innych niż wątkowo  
 Zapisywanie do metod innych niż wątkowo wystąpienia z PLINQ zapytanie może doprowadzić do uszkodzenia danych, które mogą lub nie mogą zostać wykryte w programie. Również może prowadzić do wyjątków. W poniższym przykładzie, wiele wątków czy próba wywołania `Filestream.Write` metody równocześnie, który nie jest obsługiwany przez klasę.  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Limit wywołania metod obsługujące wielowątkowość  
 Najbardziej statycznej metody w programie .NET Framework są wątkowo i może zostać wywołana z wiele wątków jednocześnie. Jednak nawet w takich przypadkach zaangażowanych synchronizacji może prowadzić do znaczne spowolnienie w zapytaniu.  
  
> [!NOTE]
>  Można przetestować tego samodzielnie przez wstawienie pewnych wywołań <xref:System.Console.WriteLine%2A> zapytania. Mimo że ta metoda jest używana w przykładach dokumentacji dla celów demonstracyjnych, nie należy go używać zapytania dotyczące technologii PLINQ i.  
  
## <a name="avoid-unnecessary-ordering-operations"></a>Unikaj niepotrzebnych operacji kolejności  
 Podczas PLINQ zapytania równolegle, dzieli sekwencji źródłowej na partycje, które może być obsługiwany przez jednocześnie na wielu wątków. Domyślnie nie jest przewidywalnej kolejności partycje są przetwarzane i wyniki są dostarczane (z wyjątkiem operatorów, takich jak `OrderBy`). Możesz wydać PLINQ w celu zachowania kolejności żadnych sekwencji źródłowej, ale ma negatywny wpływ na wydajność. Najlepszym rozwiązaniem, jeśli to możliwe, jest struktura zapytania tak, aby nie należy polegać na zachowanie porządku. Aby uzyskać więcej informacji, zobacz [zamawianie zachowywania w PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>ForAll — wolą ForEach, gdy jest to możliwe  
 Chociaż PLINQ wykonuje zapytanie na wiele wątków, jeśli korzystanie z powoduje `foreach` pętli (`For Each` w języku Visual Basic), a następnie wyniki zapytania musi być scalone jeden wątek i szeregowe używane przez moduł wyliczający. W niektórych przypadkach jest to nieuniknione; Jednak jeśli to możliwe, użyj `ForAll` metodę umożliwiającą włączenie każdy wątek do wyjściowego własną wyników, na przykład, wpisując je do kolekcji wątkowo takich jak <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.  
  
 Ten sam problem dotyczy <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> innymi słowy, `source.AsParallel().Where().ForAll(...)` powinny być silnie preferowana względem  
  
 `Parallel.ForEach(source.AsParallel().Where(), ...)`.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Należy pamiętać o problemy koligacji wątku  
 Niektóre technologie, na przykład współdziałanie COM dla składników Single-Threaded Apartment (STA), formularze systemu Windows i Windows Presentation Foundation (WPF), nakładają ograniczenia koligacji wątków, które wymagają kodu do uruchomienia na konkretnym wątkiem. Na przykład w formularzach systemu Windows i WPF formantu można uzyskać tylko w wątku, w którym został utworzony. Jeśli spróbujesz uzyskać dostępu do udostępnionych stan formantu formularzy systemu Windows w zapytaniu PLINQ jest zgłoszony wyjątek, jeśli używasz w debugerze. (To ustawienie można wyłączyć.) Jednak zapytania jest używany w wątku interfejsu użytkownika, następnie można przejść do formantu z `foreach` wyników pętli, które wylicza zapytania, ponieważ ten kod wykonywany tylko jednego wątku.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nie należy zakładać, że iteracji ForEach, dla i ForAll — zawsze wykonywanie równoległe  
 Należy pamiętać, że poszczególne iteracji w <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> lub <xref:System.Linq.ParallelEnumerable.ForAll%2A> pętla może, ale nie ma potrzeby wykonywania równolegle. W związku z tym należy unikać pisania kodu, który jest zależny pod kątem poprawności na wykonywanie równoległe iteracji lub wykonywania iteracji w określonej kolejności.  
  
 Na przykład ten kod prawdopodobnie zakleszczenie:  
  
```vb  
Dim mre = New ManualResetEventSlim()  
    Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll(Sub(j)   
  
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
            Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll((j) =>  
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
  
 W tym przykładzie iteracji jednego ustawia zdarzenie, a wszystkie inne iteracji oczekiwania na zdarzenie. Brak iteracji oczekiwania można wykonać dopiero po ukończeniu iteracji ustawienie zdarzenia. Jednak jest możliwe, że iteracji oczekiwania Blokuj wszystkie wątki, które są używane do wykonywania pętli równoległej, przed iteracji ustawienie zdarzenia miał możliwość wykonania. Powoduje to zakleszczenie — nigdy nie wykona iteracji ustawienie zdarzenia i nigdy nie wzbudzania iteracji oczekiwania.  
  
 W szczególności jeden iteracji pętli równoległej nigdy nie należy czekać na inny iteracji pętli postęp. Jeśli równoległej pętli decyduje się na Planowanie iteracji sekwencyjnie, ale w kolejności przeciwnej, nastąpi zakleszczenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
