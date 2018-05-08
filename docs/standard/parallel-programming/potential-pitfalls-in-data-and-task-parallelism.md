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
ms.openlocfilehash: da87531ff7f20181e1e5499acb8152d0fbadc8af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="potential-pitfalls-in-data-and-task-parallelism"></a>Potencjalne pułapki związane z równoległością danych i zadań
W wielu przypadkach <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> zapewnia znaczną poprawę wydajności za pośrednictwem zwykłego pętle sekwencyjnych. Jednak pracy parallelizing pętli wprowadza złożoności, który może prowadzić do problemów, które w kolejnych kodu nie są jako wspólne lub w ogóle nie wystąpi. W tym temacie wymieniono niektóre praktyki, których należy unikać podczas pisania pętle równoległe.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Nie przyjęto założenie, że równolegle jest zawsze szybsze  
 W niektórych przypadkach równoległej pętli może działać wolniej niż jego odpowiednik sekwencyjnych. Podstawowe zasadą to pętle równoległe wyposażonych w kilka iteracji i delegatów szybkiego użytkownika prawdopodobnie nie będzie przyspieszenie znacznie. Jednak ponieważ wydajności są związane z wielu czynników, zalecamy zawsze miar rzeczywiste wyniki.  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Unikaj zapisywanie w lokalizacji pamięci współużytkowanej  
 W kolejnych kodu nie jest rzadko do odczytu lub zapisu zmienne statyczne lub pola klasy. Zawsze, gdy wiele wątków uzyskują dostęp do tych zmiennych współbieżnie, istnieje jednak możliwość big wyścigu. Mimo że używasz blokad synchronizujący dostęp do zmiennej, kosztów synchronizacji może pogarszać wydajność. W związku z tym zalecamy można uniknąć, lub co najmniej ograniczyć dostęp do udostępniania stanu w możliwie równoległej pętli. Najlepszym sposobem, w tym celu jest Użyj przeciążeń <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> używające <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> zmienną do przechowywania stanu lokalnego wątku podczas wykonywania pętli. Aby uzyskać więcej informacji, zobacz [porady: zapisywanie równoległej pętli for ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) i [porady: zapisywanie równoległej pętli Foreach ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md).  
  
## <a name="avoid-over-parallelization"></a>Unikaj nadmiernego Paralelizacja  
 Za pomocą pętli równoległej ponosisz kosztów partycjonowania kolekcji źródłowej i synchronizowanie wątków roboczych. Korzyści równoległości dalsze są ograniczone przez liczbę procesorów w komputerze. Nie ma żadnych przyspieszenie, które można uzyskać, uruchamiając wiele wątków wiązaniem obliczeń w tylko jednym procesorze. W związku z tym należy uważać, aby nie nadmiernie parallelize pętli.  
  
 Najbardziej typowy scenariusz, w których nadmierne paralelizacja może wystąpić znajduje się w pętli zagnieżdżonych. W większości przypadków najlepiej parallelize zewnętrzne pętli, chyba że zastosowanie co najmniej jeden z następujących warunków:  
  
-   Fragment pętli jest znana trwać bardzo długo.  
  
-   Kosztowna obliczenia są wykonywane na każdej kolejności. (Operacja pokazano w przykładzie nie jest kosztowna).  
  
-   System docelowy jest znana wystarczającą do obsługi liczby wątków, które zostaną utworzone przez parallelizing zapytanie na procesorów `cust.Orders`.  
  
 We wszystkich przypadkach najlepszy sposób, aby ustalić optymalne zapytania kształtu jest do testowania i miar.  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Unikaj wywołania metod innych niż wątkowo  
 Zapisywanie metod innych niż wątkowo wystąpienia pętlę równoległą może doprowadzić do uszkodzenia danych, które mogą lub nie mogą zostać wykryte w programie. Również może prowadzić do wyjątków. W poniższym przykładzie, wiele wątków czy próba wywołania <xref:System.IO.FileStream.WriteByte%2A?displayProperty=nameWithType> metody równocześnie, który nie jest obsługiwany przez klasę.  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Limit wywołania metod obsługujące wielowątkowość  
 Najbardziej statycznej metody w programie .NET Framework są wątkowo i może zostać wywołana z wiele wątków jednocześnie. Jednak nawet w takich przypadkach zaangażowanych synchronizacji może prowadzić do znaczne spowolnienie w zapytaniu.  
  
> [!NOTE]
>  Można przetestować tego samodzielnie przez wstawienie pewnych wywołań <xref:System.Console.WriteLine%2A> zapytania. Mimo że ta metoda jest używana w przykładach dokumentacji dla celów demonstracyjnych, nie jest używana w pętlach równoległych o ile to konieczne.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Należy pamiętać o problemy koligacji wątku  
 Niektóre technologie, na przykład współdziałanie COM dla składników Single-Threaded Apartment (STA), formularze systemu Windows i Windows Presentation Foundation (WPF), nakładają ograniczenia koligacji wątków, które wymagają kodu do uruchomienia na konkretnym wątkiem. Na przykład w formularzach systemu Windows i WPF formantu można uzyskać tylko w wątku, w którym został utworzony. Oznacza to, na przykład nie można zaktualizować formant listy pętlę równoległą dopiero po skonfigurowaniu harmonogramu wątku do harmonogramu pracy tylko w wątku interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [porady: harmonogram pracy w wątku interfejsu użytkownika (UI)](http://msdn.microsoft.com/library/32a846a5-d628-4933-907b-4888ff72c663).  
  
## <a name="use-caution-when-waiting-in-delegates-that-are-called-by-parallelinvoke"></a>Należy zachować ostrożność podczas oczekiwania w Delegatach, które są wywoływane przez parallel_invoke podczas przeprowadzania  
 W pewnych okolicznościach Biblioteka zadań równoległych będzie wbudowane zadania, co oznacza, że jest ono uruchamiane w wątku aktualnie wykonywane zadania. (Aby uzyskać więcej informacji, zobacz [planiści zadań](http://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65).) Optymalizacja wydajności może doprowadzić do zakleszczenia w niektórych przypadkach. Na przykład dwa zadania może uruchomić tego samego obiektu delegowanego kodu, która sygnalizuje, gdy wystąpi zdarzenie, a następnie czeka na inne zadanie w celu zasygnalizowania. W przypadku drugiego zadań wbudowanego na tym samym wątku, co pierwszy i pierwszy przechodzi w stan oczekiwania, drugie zadanie nigdy nie będą mogli jej zdarzenia sygnalizują. Aby uniknąć wystąpienia zdarzenia, można określić limit czasu oczekiwania operacji lub użyj wątku jawnych konstruktorów ułatwić zapewnienie, że jedno zadanie nie można zablokować innych.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nie należy zakładać, że iteracji ForEach, dla i ForAll — zawsze wykonywanie równoległe  
 Należy pamiętać, że poszczególne iteracji w <xref:System.Threading.Tasks.Parallel.For%2A>, <xref:System.Threading.Tasks.Parallel.ForEach%2A> lub <xref:System.Linq.ParallelEnumerable.ForAll%2A> pętla może, ale nie ma potrzeby wykonywania równolegle. W związku z tym należy unikać pisania kodu, który jest zależny pod kątem poprawności na wykonywanie równoległe iteracji lub wykonywania iteracji w określonej kolejności. Na przykład ten kod prawdopodobnie zakleszczenie:  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 W tym przykładzie iteracji jednego ustawia zdarzenie, a wszystkie inne iteracji oczekiwania na zdarzenie. Brak iteracji oczekiwania można wykonać dopiero po ukończeniu iteracji ustawienie zdarzenia. Jednak jest możliwe, że iteracji oczekiwania Blokuj wszystkie wątki, które są używane do wykonywania pętli równoległej, przed iteracji ustawienie zdarzenia miał możliwość wykonania. Powoduje to zakleszczenie — nigdy nie wykona iteracji ustawienie zdarzenia i nigdy nie wzbudzania iteracji oczekiwania.  
  
 W szczególności jeden iteracji pętli równoległej nigdy nie należy czekać na inny iteracji pętli postęp. Jeśli równoległej pętli decyduje się na Planowanie iteracji sekwencyjnie, ale w kolejności przeciwnej, nastąpi zakleszczenie.  
  
## <a name="avoid-executing-parallel-loops-on-the-ui-thread"></a>Należy unikać wykonywania pętle równoległe w wątku interfejsu użytkownika  
 Należy zachować reakcji interfejsu użytkownika (UI). Jeśli operacja zawiera wystarczająco dużo pracy, aby zagwarantować paralelizacja, następnie go prawdopodobnie nie powinien być uruchamiany tej operacji w wątku interfejsu użytkownika.  Zamiast tego należy go odciążania tej operacji można uruchomić wątku w tle. Na przykład jeśli chcesz użyć równoległej pętli do obliczenia części danych, które mają być renderowane następnie do formantu interfejsu użytkownika, należy rozważyć wykonywania pętli w ramach wystąpienia zadania, a nie bezpośrednio w procedurze obsługi zdarzeń interfejsu użytkownika.  Tylko wtedy, gdy obliczenia core została ukończona powinien można następnie kierować aktualizacji interfejsu użytkownika do wątku interfejsu użytkownika.  
  
 Jeśli pętle równoległe uruchomić w wątku interfejsu użytkownika, należy zachować ostrożność uniknąć aktualizowanie formantów interfejsu użytkownika z w pętli. Podjęto próbę zaktualizowania interfejsu użytkownika formantów z wewnątrz równoległej pętli, które jest wykonywane w wątku interfejsu użytkownika może doprowadzić do uszkodzenia stanu, wyjątki opóźnione aktualizacje i nawet zakleszczenia, w zależności od tego, jak aktualizacja interfejsu użytkownika jest wywoływany. W poniższym przykładzie równoległej pętli blokuje wątku interfejsu użytkownika, na którym jest wykonywany do momentu zakończenia wszystkich iteracji. Jednak jeśli iteracji pętli jest uruchomiona w wątku tła (jako <xref:System.Threading.Tasks.Parallel.For%2A> może), wywołanie Invoke powoduje, że komunikat do przesłania do wątku interfejsu użytkownika i bloki oczekujących na przetworzenie tej wiadomości. Ponieważ wątku interfejsu użytkownika jest zablokowany, systemem <xref:System.Threading.Tasks.Parallel.For%2A>, nigdy nie można przetworzyć wiadomości i zakleszczenie wątku interfejsu użytkownika.  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 Poniższy przykład pokazuje, jak w celu uniknięcia zakleszczenia, uruchamiając pętli wewnątrz wystąpienia zadania. Wątku interfejsu użytkownika nie jest blokowany przez pętli i można przetwarzać komunikatu.  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
 [Potencjalne pułapki związane z PLINQ](../../../docs/standard/parallel-programming/potential-pitfalls-with-plinq.md)  
 [Wzorce programowania równoległego: opis i stosowanie równoległe wzorce za pomocą programu .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222)
