---
title: Potencjalne pułapki związane z równoległością danych i zadań
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel programming, pitfalls
ms.assetid: 1e357177-e699-4b8f-9e49-56d3513ed128
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ee939096ef4e24397d03aa8a64405d66c740580
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946331"
---
# <a name="potential-pitfalls-in-data-and-task-parallelism"></a>Potencjalne pułapki związane z równoległością danych i zadań
W wielu przypadkach <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> może zapewnić znaczną poprawę wydajności w porównaniu z zwykłymi pętlami sekwencyjnymi. Jednak prace przekształcają pętlą wprowadzają złożoność, która może prowadzić do problemów, które w sekwencyjnym kodzie nie są zgodne lub nie są w ogóle obsługiwane. Ten temat zawiera wskazówki, które należy unikać podczas pisania pętli równoległych.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Nie zakładaj, że równoległy jest zawsze szybszy  
 W niektórych przypadkach pętla równoległa może działać wolniej niż jej odpowiednik sekwencyjny. Podstawowa zasada kciuka polega na tym, że pętle równoległe, które mają kilka iteracji i szybki delegatów użytkowników, prawdopodobnie nie przyspieszenie dużo. Jednak ze względu na to, że wiele czynników jest związanych z wydajnością, zaleca się, aby zawsze mierzyć rzeczywiste wyniki.  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Unikaj zapisywania w lokalizacjach pamięci współdzielonej  
 W sekwencyjnym kodzie nie jest mało typowe odczytywanie z lub zapisywanie do zmiennych statycznych lub pól klas. Jeśli jednak wiele wątków uzyskuje dostęp do takich zmiennych jednocześnie, istnieje duże prawdopodobieństwo dla warunków wyścigu. Mimo że można użyć blokad do synchronizowania dostępu do zmiennej, koszt synchronizacji może obniżyć wydajność. W związku z tym zalecamy uniknięcie lub ograniczenie dostępu do udostępnionego stanu w pętli równoległej tak długo, jak to możliwe. Najlepszym sposobem jest użycie przeciążeń <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> , które używają <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> zmiennej do przechowywania stanu wątku — lokalnego podczas wykonywania pętli. Aby uzyskać więcej informacji, zobacz [jak: Napisz Parallel. for — pętla ze zmiennymi](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) lokalnymi wątku i [instrukcje: Napisz równoległą pętlę. ForEach ze zmiennymi](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)lokalnymi partycji.  
  
## <a name="avoid-over-parallelization"></a>Unikaj nadmiernego przetwarzanie równoległe  
 Korzystając z pętli równoległych, naliczane są koszty narzutu partycjonowania źródłowej kolekcji i synchronizowania wątków roboczych. Zalety przetwarzanie równoległe są bardziej ograniczone przez liczbę procesorów na komputerze. Nie ma przyspieszenie do uzyskania, uruchamiając wiele wątków powiązanych z obliczeniami tylko na jednym procesorze. W związku z tym należy zachować ostrożność, aby nie zrównoleglanie pętli.  
  
 Najbardziej typowym scenariuszem, w którym może wystąpić zbyt przetwarzanie równoległe, jest pętla zagnieżdżona. W większości przypadków najlepiej zrównoleglanie tylko pętlę zewnętrzną, chyba że spełnione są co najmniej jeden z następujących warunków:  
  
- Pętla wewnętrzna jest znana jako bardzo długa.  
  
- Wykonujesz kosztowne obliczenia dla każdego zamówienia. (Operacja pokazana w przykładzie nie jest kosztowna).  
  
- System docelowy ma wystarczającą ilość procesorów do obsługi liczby wątków, które zostaną utworzone przez przekształcają zapytania `cust.Orders`.  
  
 We wszystkich przypadkach najlepszym sposobem określenia optymalnego kształtu zapytania jest przetestowanie i pomiar.  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Unikaj wywołań metod niebezpiecznych dla wątków  
 Zapisywanie w metodach wystąpienia niebezpiecznego dla wątków z pętli równoległej może prowadzić do uszkodzenia danych, które mogą lub nie zostać wykryte w programie. Może to również prowadzić do wyjątków. W poniższym przykładzie wiele wątków próbuje wywołać <xref:System.IO.FileStream.WriteByte%2A?displayProperty=nameWithType> metodę jednocześnie, co nie jest obsługiwane przez klasę.  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Ogranicz wywołania metod bezpiecznych dla wątków  
 Większość metod statycznych w .NET Framework są bezpieczne dla wątków i może być wywoływana z wielu wątków jednocześnie. Jednak nawet w takich przypadkach Synchronizacja może prowadzić do znacznego spowolnienia w zapytaniu.  
  
> [!NOTE]
> Możesz przetestować ten sposób, wstawiając kilka wywołań do <xref:System.Console.WriteLine%2A> zapytania. Chociaż ta metoda jest używana w przykładach dokumentacji w celach demonstracyjnych, nie należy używać jej w pętlach równoległych, chyba że jest to konieczne.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Należy pamiętać o problemach z koligacją wątków  
 Niektóre technologie, na przykład współdziałanie modelu COM dla składników Single-Threading Apartment (STA), Windows Forms i Windows Presentation Foundation (WPF), nakładają ograniczenia koligacji wątku, które wymagają kodu do uruchomienia w określonym wątku. Na przykład zarówno w Windows Forms, jak i WPF, dostęp do formantu można uzyskać tylko w wątku, w którym został utworzony. Oznacza to, na przykład, że nie można zaktualizować formantu listy z pętli równoległej, chyba że zostanie skonfigurowany harmonogram wątków w celu zaplanowania pracy tylko w wątku interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [określanie kontekstu synchronizacji](xref:System.Threading.Tasks.TaskScheduler#specifying-a-synchronization-context).  
  
## <a name="use-caution-when-waiting-in-delegates-that-are-called-by-parallelinvoke"></a>Należy zachować ostrożność podczas oczekiwania w delegatach, które są wywoływane przez Parallel. Invoke  
 W pewnych okolicznościach Biblioteka zadań równoległych wykona zadanie podrzędne, co oznacza, że jest uruchamiane na zadaniu w aktualnie wykonywanym wątku. (Aby uzyskać więcej informacji, zobacz [Task](xref:System.Threading.Tasks.TaskScheduler)Schedulers). Ta optymalizacja wydajności może prowadzić do zakleszczenia w niektórych przypadkach. Na przykład dwa zadania mogą uruchomić ten sam kod delegata, który sygnalizuje czas wystąpienia zdarzenia, a następnie czeka na inne zadanie. Jeśli drugie zadanie jest umieszczane w tym samym wątku co pierwszy, a pierwszy przechodzi w stan oczekiwania, drugie zadanie nigdy nie będzie mogło sygnalizować zdarzenia. Aby uniknąć takiego wystąpienia, można określić limit czasu dla operacji oczekiwania lub użyć jawnych konstruktorów wątków, aby zapewnić, że jedno zadanie nie może zablokować drugiego.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nie zakładaj, że iteracje ForEach, for i ForAll są zawsze wykonywane równolegle  
 Należy pamiętać, że poszczególne iteracje w <xref:System.Threading.Tasks.Parallel.For%2A> <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli lub <xref:System.Linq.ParallelEnumerable.ForAll%2A> mogą nie być wykonywane równolegle. W związku z tym należy unikać pisania kodu, który zależy do poprawnego wykonywania iteracji lub wykonywania iteracji w określonej kolejności. Na przykład ten kod może być zakleszczony:  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 W tym przykładzie Jedna iteracja ustawia zdarzenie, a wszystkie inne iteracje oczekują na zdarzenie. Żadna z oczekujących iteracji nie może zostać zakończona do momentu zakończenia iteracji ustawienia zdarzenia. Jednak istnieje możliwość, że oczekujące iteracje blokują wszystkie wątki, które są używane do wykonywania pętli równoległej, przed wykonaniem iteracji ustawienia zdarzenia. Powoduje to zakleszczenie — iteracja ustawienia zdarzenia nigdy nie zostanie wykonana, a oczekujące iteracje nigdy nie zostaną wznowione.  
  
 W szczególności jedna iteracja pętli równoległej nigdy nie powinna czekać na kolejną iterację pętli, aby wykonać postęp. Jeśli pętla równoległa zdecyduje się na sekwencyjne planowanie iteracji, ale w kolejności odwrotnej, nastąpi zakleszczenie.  
  
## <a name="avoid-executing-parallel-loops-on-the-ui-thread"></a>Unikaj wykonywania pętli równoległych w wątku interfejsu użytkownika  
 Ważne jest, aby zachować odpowiedzi interfejsu użytkownika aplikacji. Jeśli operacja zawiera wystarczającą ilość pracy do uznania przetwarzanie równoległe, prawdopodobnie nie należy uruchamiać tej operacji w wątku interfejsu użytkownika.  Zamiast tego należy odciążyć tę operację do uruchomienia w wątku w tle. Na przykład jeśli chcesz użyć pętli równoległej do obliczenia niektórych danych, które powinny być następnie renderowane do kontrolki interfejsu użytkownika, należy rozważyć wykonanie pętli w ramach wystąpienia zadania, a nie bezpośrednio w programie obsługi zdarzeń interfejsu użytkownika.  Tylko wtedy, gdy podstawowe obliczenie zostało zakończone, należy następnie zorganizować aktualizację interfejsu użytkownika z powrotem do wątku interfejsu użytkownika.  
  
 Jeśli uruchamiasz pętle równoległe w wątku interfejsu użytkownika, należy zachować ostrożność, aby uniknąć aktualizowania formantów interfejsu użytkownika z poziomu pętli. Próba zaktualizowania formantów interfejsu użytkownika z poziomu pętli równoległej wykonywanej w wątku interfejsu użytkownika może prowadzić do uszkodzenia stanu, wyjątków, opóźnionych aktualizacji i nawet zakleszczeń, w zależności od sposobu wywołania aktualizacji interfejsu użytkownika. W poniższym przykładzie pętla równoległa blokuje wątek interfejsu użytkownika, na którym jest wykonywany do momentu ukończenia wszystkich iteracji. Jeśli jednak iteracja pętli jest uruchomiona w wątku w tle (jak to <xref:System.Threading.Tasks.Parallel.For%2A> możliwe), wywołanie metody Invoke powoduje wysłanie komunikatu do wątku interfejsu użytkownika i bloków oczekujących na przetworzenie tego komunikatu. Ponieważ wątek interfejsu użytkownika jest blokowany w <xref:System.Threading.Tasks.Parallel.For%2A>systemie, komunikat nigdy nie może zostać przetworzony, a wątek interfejsu użytkownika jest zakleszczony.  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 Poniższy przykład pokazuje, jak uniknąć zakleszczenia, uruchamiając pętlę wewnątrz wystąpienia zadania. Wątek interfejsu użytkownika nie jest blokowany przez pętlę i można go przetworzyć.  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Potencjalne pułapki związane z PLINQ](../../../docs/standard/parallel-programming/potential-pitfalls-with-plinq.md)
- [Wzorce programowania równoległego: Zrozumienie i stosowanie równoległych wzorców z .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222)
