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
ms.openlocfilehash: f6910dfba0889b4eaf601960d13dfe87a3b8c2fa
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44214124"
---
# <a name="potential-pitfalls-in-data-and-task-parallelism"></a>Potencjalne pułapki związane z równoległością danych i zadań
W wielu przypadkach <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> może zapewnić znaczne ulepszenia wydajności za pośrednictwem zwykłych sekwencyjne pętli. Jednak pracy zrównoleglić pętlę wprowadza złożoności, który może prowadzić do problemów, które sekwencyjnego kodu nie są jako wspólne lub nie zostaną napotkane w ogóle. W tym temacie wymieniono niektóre rozwiązania, aby uniknąć podczas pisania pętli równoległych.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Nie należy zakładać, że równoległa jest zawsze szybciej  
 W niektórych przypadkach pętlę równoległą może działać wolniej niż równoważnik sekwencyjne. Podstawowa zasada mówi jest możliwość równoległego pętli, które mają kilka iteracji i delegatów użytkownika szybkie, prawdopodobnie nie będzie przyspieszenie znacznie. Ponieważ wiele czynników są zaangażowane w wydajności, firma Microsoft zaleca jednak zawsze pomiaru rzeczywiste wyniki.  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Należy unikać pisania do lokalizacji udostępnionej pamięci  
 W kodzie sekwencyjnych nie jest niczym niezwykłym, aby odczytać lub zapisać zmienne statyczne lub pola klasy. Zawsze, gdy wiele wątków uzyskują dostęp do takich zmiennych jednocześnie, istnieje jednak duże prawdopodobieństwo jednoczesnego wyścigu. Mimo że blokad służy do synchronizowania dostępu do zmiennej, koszt synchronizacji może obniżyć wydajność. Dlatego zaleca się że uniknąć, lub co najmniej ograniczyć, dostęp do udostępnionego stanu w miarę możliwości pętli równoległej. Najlepszym sposobem, w tym celu jest użycie przeciążenia <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> używające <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> zmienną do przechowywania stanu lokalnej wątku podczas wykonywania pętli. Aby uzyskać więcej informacji, zobacz [porady: zapisywanie pętli Parallel.For ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) i [porady: zapisywanie pętli Parallel.ForEach ze zmiennymi lokalnymi partycji](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="avoid-over-parallelization"></a>Unikaj nadmiernego przetwarzania równoległego  
 Za pomocą pętli równoległej wiąże się z kosztów ogólnych partycjonowania kolekcji źródłowej i synchronizacji wątków roboczych. Korzyści wynikające z przetwarzaniem równoległym dalsze są ograniczone przez liczbę procesorów w komputerze. Nie ma żadnych przyspieszenie, które można uzyskać, uruchamiając wiele wątków powiązany obliczeniowych w tylko jednym procesorze. W związku z tym należy uważać, aby nie nadmiernie zrównoleglić pętlę.  
  
 Najbardziej typowym scenariuszem, w których nadmiernego przetwarzania równoległego może wystąpić znajduje się w pętli zagnieżdżonych. W większości przypadków najlepiej jest równoległe przetwarzanie tylko zewnętrzna pętla, chyba że zastosować co najmniej jeden z następujących warunków:  
  
-   Wiadomo, że wewnętrzną pętlę być bardzo długie.  
  
-   Kosztowne obliczenia są wykonywane na każde zamówienie. (Operacja pokazano w przykładzie nie jest kosztowna).  
  
-   System docelowy jest znana wystarczającej liczby procesorów, którą należy obsługiwać liczbę wątków, które zostaną wygenerowane przez zrównoleglić zapytanie na `cust.Orders`.  
  
 We wszystkich przypadkach najlepszym sposobem określenia kształtu optymalne zapytania jest do testowania i miar.  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Należy unikać wywołania metod innych niż wątkowo  
 Zapisywanie metod wystąpienia innych wątkowo pętlę równoległą może prowadzić do uszkodzenia danych, które mogą lub nie może być wykryte w programach. Może to również prowadzić do wyjątków. W poniższym przykładzie wielu wątków będzie próba wywołania <xref:System.IO.FileStream.WriteByte%2A?displayProperty=nameWithType> metoda równocześnie, które nie jest obsługiwane przez klasę.  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Ogranicz wywołania metod metodą o bezpiecznych wątkach  
 Najbardziej statycznych metod .NET Framework są odporne na wątki i może być wywoływana z wielu wątków jednocześnie. Jednak nawet w takich przypadkach zaangażowane synchronizacji może prowadzić do znaczne spowolnienie w zapytaniu.  
  
> [!NOTE]
>  Możesz sprawdzić to samodzielnie, wstawiając wywołania niektórych <xref:System.Console.WriteLine%2A> w zapytaniach. Chociaż ta metoda jest używana w przykładach dokumentacji w celach demonstracyjnych, nie należy używać go w pętlach równoległych Jeśli to konieczne.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Należy pamiętać o problemów koligacji wątku  
 Niektóre technologie, na przykład współdziałanie COM dla składników Single-Threaded apartamentu (STA), Windows Forms i Windows Presentation Foundation (WPF), nakładają ograniczenia koligacji wątku, które wymagają kod wymagany do uruchomienia w określonym wątku. Na przykład w Windows Forms i WPF formant może zostać oceniony jedynie w wątku, na którym została utworzona. Oznacza to, na przykład nie można zaktualizować formantu listy z równoległą pętlą o ile nie skonfigurowano harmonogramu wątków do zaplanowania pracy tylko w wątku interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [jak: harmonogram pracy w wątku interfejsu użytkownika (UI)](https://msdn.microsoft.com/library/32a846a5-d628-4933-907b-4888ff72c663).  
  
## <a name="use-caution-when-waiting-in-delegates-that-are-called-by-parallelinvoke"></a>Należy zachować ostrożność podczas oczekiwania w delegatów, które są wywoływane przez elementu Parallel.Invoke  
 W pewnych okolicznościach Biblioteka zadań równoległych będą wbudowane zadanie, co oznacza, że jest ono uruchamiane zadanie na aktualnie wykonywany wątek. (Aby uzyskać więcej informacji, zobacz [harmonogramów zadań](https://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65).) Tego rodzaju optymalizacji wydajności może prowadzić do zakleszczenia w niektórych przypadkach. Na przykład dwa zadania może uruchomić tego samego obiektu delegowanego kodu, które sygnalizują, gdy wystąpi zdarzenie, a następnie czeka na innych zadań w celu sygnalizowania, że. Jeśli drugie zadanie jest śródwierszowa, w tym samym wątku, który jako pierwszy, a pierwszy przechodzi w stan oczekiwania, drugie zadanie nigdy nie będą mogli sygnalizują jego zdarzenia. Aby uniknąć wystąpienia zdarzenia, można określić limit czasu operacji oczekiwania, lub użyj wątku jawne konstruktory ułatwiające, upewnij się, że jedno zadanie nie można zablokować, drugi.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nie należy zakładać, że iteracji ForEach, dla i równolegle uruchomić zawsze ForAll  
 Ważne jest, aby pamiętać, że poszczególnych iteracji w <xref:System.Threading.Tasks.Parallel.For%2A>, <xref:System.Threading.Tasks.Parallel.ForEach%2A> lub <xref:System.Linq.ParallelEnumerable.ForAll%2A> pętli może, ale nie trzeba wykonywać równolegle. W związku z tym należy unikać pisania żadnego kodu, który zależy od pod kątem poprawności na równoległe wykonywanie iteracji lub wykonywania iteracji w określonej kolejności. Na przykład ten kod jest prawdopodobnie zakleszczenie:  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 W tym przykładzie jednej iteracji ustawia zdarzenie, a wszystkie inne iteracje oczekiwania na zdarzenie. Brak iteracji oczekiwania można wykonać przed ukończeniem iteracji ustawienie zdarzenia. Jednak jest możliwe, że iteracji oczekujące blokuje wszystkie wątki, które są używane do wykonywania pętli równoległej, zanim iteracji ustawienie zdarzenia miała szansę, aby wykonać. Skutkuje to zakleszczenie — iteracji ustawienie zdarzenia nigdy nie zostanie wykonana i iteracje oczekiwania nigdy nie będzie wznawiania.  
  
 W szczególności jednej iteracji pętli równoległej nigdy nie należy czekać na innej iteracji pętli postępu. Jeśli pętli równoległej decyduje zaplanować iteracje kolejno, ale w kolejności przeciwnej, nastąpi zakleszczenia.  
  
## <a name="avoid-executing-parallel-loops-on-the-ui-thread"></a>Należy unikać wykonywania pętli równoległych w wątku interfejsu użytkownika  
 Należy zachować elastyczny interfejs użytkownika (UI). Jeśli operacja zawiera wystarczająco dużo pracy, aby gwarantowało przetwarzania równoległego, następnie go prawdopodobnie nie powinna być uruchamiana tej operacji w wątku interfejsu użytkownika.  Powinien on zamiast tego należy obciążyć tej operacji należy uruchomić na wątku w tle. Na przykład jeśli chcesz użyć pętli równoległej do obliczenia części danych, które następnie powinna być renderowana na kontrolkę interfejsu użytkownika, należy rozważyć wykonywanie pętli w ramach wystąpienie zadania, a nie bezpośrednio na program obsługi zdarzeń w interfejsie użytkownika.  Tylko wtedy, gdy obliczenie core została zakończona powinien można następnie kierować aktualizacji interfejsu użytkownika do wątku interfejsu użytkownika.  
  
 Po uruchomieniu pętli równoległych w wątku interfejsu użytkownika, należy zachować ostrożność uniknąć aktualizowanie formantów interfejsu użytkownika z w ramach pętli. Podjęto próbę zaktualizowania interfejsu użytkownika kontrolki z w ramach pętli równoległej, które jest wykonywane w wątku interfejsu użytkownika może spowodować uszkodzenie stanu, wyjątki, opóźnione aktualizacje i nawet zakleszczenia, w zależności od tego, jak jest wywoływany aktualizacji interfejsu użytkownika. W poniższym przykładzie pętli równoległej blokuje wątek interfejsu użytkownika, na którym jest wykonywany, dopiero po zakończeniu wszystkich iteracji. Jednak jeśli iteracji pętli jest uruchomiona w wątku tła (jako <xref:System.Threading.Tasks.Parallel.For%2A> może wykonać), wiadomości do wysłania do wątku interfejsu użytkownika i bloków oczekiwanie na przetworzenie tego komunikatu powoduje, że wywołanie metody Invoke. Ponieważ wątku interfejsu użytkownika jest zablokowane, uruchamianie <xref:System.Threading.Tasks.Parallel.For%2A>, nigdy nie można przetworzyć wiadomości, a zakleszczenia wątku interfejsu użytkownika.  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 Poniższy przykład pokazuje, jak w celu uniknięcia zakleszczenia, uruchamiając pętli wewnątrz wystąpienia zadania. Wątek interfejsu użytkownika nie jest blokowany przez pętli, a wiadomości, które mogą być przetwarzane.  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
- [Potencjalne pułapki związane z PLINQ](../../../docs/standard/parallel-programming/potential-pitfalls-with-plinq.md)  
- [Wzorce programowania równoległego: rozumienie i stosowanie równoległych wzorców z programu .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222)
