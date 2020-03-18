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
ms.openlocfilehash: ff6ac9e8c41ee203ae72e1b28c088f462ddf6a54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140022"
---
# <a name="potential-pitfalls-in-data-and-task-parallelism"></a>Potencjalne pułapki związane z równoległością danych i zadań
W wielu <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> przypadkach <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> i może zapewnić znaczną poprawę wydajności w zwykłych pętli sekwencyjnych. Jednak praca z równoległości pętli wprowadza złożoność, która może prowadzić do problemów, które w kodzie sekwencyjnym, nie są tak powszechne lub nie występują w ogóle. W tym temacie wymieniono niektóre praktyki, których należy unikać podczas pisania pętli równoległych.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Nie zakładaj, że parallel jest zawsze szybszy  
 W niektórych przypadkach pętla równoległa może działać wolniej niż jej odpowiednik sekwencyjnego. Podstawową zasadą jest to, że równoległe pętle, które mają niewiele iteracji i szybkich delegatów użytkownika jest mało prawdopodobne, aby znacznie przyspieszyć. Jednak ponieważ wiele czynników są zaangażowane w wydajność, zaleca się zawsze zmierzyć rzeczywiste wyniki.  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Unikaj zapisywania w lokalizacjach pamięci współużytkowanej  
 W kodzie sekwencyjnym nie jest rzadkością odczytywanie lub zapisywanie do zmiennych statycznych lub pól klas. Jednak zawsze, gdy wiele wątków uzyskuje dostęp do takich zmiennych jednocześnie, istnieje duży potencjał warunków wyścigu. Mimo że można użyć blokad do synchronizacji dostępu do zmiennej, koszt synchronizacji może zaszkodzić wydajności. W związku z tym zaleca się, aby uniknąć lub przynajmniej ograniczyć dostęp do stanu udostępnionego w pętli równoległej, jak to możliwe. Najlepszym sposobem, aby to zrobić jest <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> użycie <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> przeciążenia i które używają zmiennej <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> do przechowywania stanu lokalnego wątku podczas wykonywania pętli. Aby uzyskać więcej informacji, zobacz [Jak: Napisać Parallel.For pętli ze zmiennymi wątku lokalnych](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) i [Jak: Napisz Parallel.ForEach pętli ze zmiennymi partycji lokalnych](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="avoid-over-parallelization"></a>Unikaj nadmiernej równoległości  
 Za pomocą pętli równoległych ponosi koszty ogólne partycjonowania kolekcji źródłowej i synchronizacji wątków roboczych. Korzyści z równoległości są dodatkowo ograniczone przez liczbę procesorów na komputerze. Nie ma żadnych przyspieszeń, które można uzyskać przez uruchomienie wielu wątków związanych z obliczeniami tylko na jednym procesorze. W związku z tym należy uważać, aby nie nadmiernie równoległości pętli.  
  
 Najbardziej typowyscenariusz, w którym może wystąpić nadmierna równoległość, znajduje się w pętlach zagnieżdżonych. W większości przypadków najlepiej jest równoległość tylko zewnętrznej pętli, chyba że stosuje się jeden lub więcej z następujących warunków:  
  
- Wewnętrzna pętla jest znana jako bardzo długa.  
  
- Wykonujesz kosztowne obliczenia na każdym zamówieniu. (Operacja pokazana w przykładzie nie jest kosztowna).  
  
- Wiadomo, że system docelowy ma wystarczającą liczbę procesorów do obsługi liczby wątków, które zostaną wyprodukowane przez zleżenie kwerendy na `cust.Orders`.  
  
 We wszystkich przypadkach najlepszym sposobem określenia optymalnego kształtu zapytania jest testowanie i mierzenie.  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Unikaj wywołań metod innych niż bezpieczne dla wątków  
 Zapisywanie do metod wystąpienia innych niż wątki z pętli równoległej może prowadzić do uszkodzenia danych, które mogą lub nie mogą pozostać niewykryte w programie. Może to również prowadzić do wyjątków. W poniższym przykładzie wiele wątków będzie próbować <xref:System.IO.FileStream.WriteByte%2A?displayProperty=nameWithType> wywołać metodę jednocześnie, który nie jest obsługiwany przez klasę.  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Ogranicz wywołania do metod bezpiecznych dla wątków  
 Większość metod statycznych w .NET Framework są bezpieczne dla wątków i mogą być wywoływane z wielu wątków jednocześnie. Jednak nawet w takich przypadkach synchronizacja zaangażowanych może prowadzić do znacznego spowolnienia w kwerendzie.  
  
> [!NOTE]
> Można przetestować <xref:System.Console.WriteLine%2A> to samodzielnie, wstawiając niektóre wywołania w kwerendach. Mimo że ta metoda jest używana w przykładach dokumentacji do celów demonstracyjnych, nie należy jej używać w pętli równoległych, chyba że jest to konieczne.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Należy pamiętać o problemach z koligacji wątku  
 Niektóre technologie, na przykład współdziałanie modelu COM dla składników jednowątkowych apartamentów (STA), formularzy systemu Windows i podstawy prezentacji systemu Windows (WPF), nakładają ograniczenia koligacji wątków, które wymagają kodu do uruchomienia w określonym wątku. Na przykład w obu formularzach systemu Windows i WPF formant uzyskuje się tylko w wątku, w którym został utworzony. Oznacza to na przykład, że nie można zaktualizować formantlisty z pętli równoległej, chyba że skonfigurujesz harmonogram wątków do planowania pracy tylko w wątku interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Określanie kontekstu synchronizacji](xref:System.Threading.Tasks.TaskScheduler#specifying-a-synchronization-context).  
  
## <a name="use-caution-when-waiting-in-delegates-that-are-called-by-parallelinvoke"></a>Należy zachować ostrożność podczas oczekiwania w delegatów, które są wywoływane przez Parallel.Invoke  
 W pewnych okolicznościach biblioteka równoległa zadania będzie wbudowany zadanie, co oznacza, że działa na zadanie w wątku aktualnie wykonywane. (Aby uzyskać więcej informacji, zobacz [Harmonogramy zadań](xref:System.Threading.Tasks.TaskScheduler).) Ta optymalizacja wydajności może prowadzić do zakleszczenia w niektórych przypadkach. Na przykład dwa zadania mogą działać ten sam kod delegata, który sygnalizuje, gdy wystąpi zdarzenie, a następnie czeka na inne zadanie do sygnału. Jeśli drugie zadanie jest wbudowane w tym samym wątku jako pierwszy, a pierwszy przechodzi w Wait stanu, drugie zadanie nigdy nie będzie w stanie zasygnalizować jego zdarzenia. Aby uniknąć takiego wystąpienia, można określić timeout na Wait operacji lub użyć jawne konstruktory wątku, aby upewnić się, że jedno zadanie nie może zablokować inne.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nie zakładaj, że iteracje ForEach, For i ForAll zawsze wykonać równolegle  
 Ważne jest, aby pamiętać, że poszczególne <xref:System.Threading.Tasks.Parallel.For%2A>iteracje w , <xref:System.Threading.Tasks.Parallel.ForEach%2A> lub <xref:System.Linq.ParallelEnumerable.ForAll%2A> pętli może, ale nie muszą wykonywać równolegle. W związku z tym należy unikać pisania kodu, który zależy od poprawności na równoległe wykonywanie iteracji lub na wykonanie iteracji w określonej kolejności. Na przykład ten kod może zakleszczenie:  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 W tym przykładzie jedna iteracja ustawia zdarzenie, a wszystkie inne iteracje czekają na zdarzenie. Żadna z iteracji oczekiwania nie może zakończyć się, dopóki iteracji ustawiania zdarzeń nie zostanie ukończona. Jednak jest możliwe, że iteracje oczekiwania zablokować wszystkie wątki, które są używane do wykonywania pętli równoległej, zanim iteracji ustawiania zdarzeń miał szansę wykonać. Powoduje to zakleszczenie — iteracji ustawiania zdarzeń nigdy nie zostanie wykonana, a iteracje oczekiwania nigdy nie obudzi.  
  
 W szczególności jedna iteracja pętli równoległej nigdy nie powinna czekać na inną iterację pętli, aby poczynić postępy. Jeśli pętla równoległa zdecyduje się zaplanować iteracje sekwencyjnie, ale w odwrotnej kolejności, nastąpi zakleszczenie.  
  
## <a name="avoid-executing-parallel-loops-on-the-ui-thread"></a>Unikaj wykonywania pętli równoległych w wątku interfejsu użytkownika  
 Ważne jest, aby interfejs użytkownika aplikacji był responsywny. Jeśli operacja zawiera wystarczającą ilość pracy, aby uzasadnić równoległość, prawdopodobnie nie należy uruchamiać tej operacji w wątku interfejsu użytkownika.  Zamiast tego należy odciążyć tej operacji do uruchomienia w wątku w tle. Na przykład jeśli chcesz użyć pętli równoległej do obliczania niektórych danych, które następnie powinny być renderowane do formantu interfejsu użytkownika, należy rozważyć wykonanie pętli w wystąpieniu zadania, a nie bezpośrednio w programie obsługi zdarzeń interfejsu użytkownika.  Tylko po zakończeniu obliczeń podstawowych należy następnie zorganizować aktualizację interfejsu użytkownika z powrotem do wątku interfejsu użytkownika.  
  
 Jeśli uruchomisz równoległe pętle w wątku interfejsu użytkownika, należy zachować ostrożność, aby uniknąć aktualizowania formantów interfejsu użytkownika z poziomu pętli. Próba zaktualizowania formantów interfejsu użytkownika z poziomu pętli równoległej, która jest wykonywana w wątku interfejsu użytkownika, może prowadzić do uszkodzenia stanu, wyjątków, opóźnionych aktualizacji, a nawet zakleszczeń, w zależności od tego, jak jest wywoływana aktualizacja interfejsu użytkownika. W poniższym przykładzie pętli równoległej blokuje wątek interfejsu użytkownika, na którym jest wykonywany, dopóki wszystkie iteracje są kompletne. Jednak jeśli iteracji pętli jest uruchomiona w wątku w tle (jak <xref:System.Threading.Tasks.Parallel.For%2A> może zrobić), wywołanie Wywołać powoduje, że komunikat, który ma zostać przesłany do wątku interfejsu użytkownika i bloki oczekujące na tę wiadomość do przetworzenia. Ponieważ wątek interfejsu użytkownika jest <xref:System.Threading.Tasks.Parallel.For%2A>zablokowany, uruchamianie , komunikat nigdy nie może być przetwarzany, a wątek interfejsu użytkownika zakleszczenia.  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 W poniższym przykładzie pokazano, jak uniknąć zakleszczenia, uruchamiając pętlę wewnątrz wystąpienia zadania. Wątek interfejsu użytkownika nie jest blokowany przez pętlę, a komunikat może być przetwarzany.  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Potencjalne pułapki związane z PLINQ](../../../docs/standard/parallel-programming/potential-pitfalls-with-plinq.md)
- [Wzorce programowania równoległego: opis i stosowanie wzorców równoległych z .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222)
