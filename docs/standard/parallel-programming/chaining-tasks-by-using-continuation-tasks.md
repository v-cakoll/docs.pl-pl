---
title: Tworzenie łańcuchów zadań przy użyciu zadań kontynuacji
ms.date: 02/11/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, continuations
ms.assetid: 0b45e9a2-de28-46ce-8212-1817280ed42d
ms.openlocfilehash: 7de8c4e44e1866e3df36c666c9ecc210dc6a7d83
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159367"
---
# <a name="chaining-tasks-by-using-continuation-tasks"></a>Tworzenie łańcuchów zadań przy użyciu zadań kontynuacji
W programowaniu asynchronicznym, jest wspólne dla jednej operacji asynchronicznej po zakończeniu, aby wywołać drugą operację i przekazać do niej dane. Tradycyjnie, kontynuacje zostały wykonane przy użyciu metod wywołania zwrotnego. W bibliotece zadań równoległych te same funkcje są udostępniane przez *zadania kontynuacji*. Zadanie kontynuacji (znane również jako kontynuacja) to asynchroniczne zadanie, które jest wywoływane przez inne zadanie, znane jako *poprzedzające*, po zakończeniu poprzedzającego.  
  
 Kontynuacje są stosunkowo łatwe w użyciu, ale są jednak zaawansowane i elastyczne. Można na przykład:  
  
- Przekaż dane z Antecedent do kontynuacji.  
  
- Określ dokładne warunki, w których kontynuacja zostanie wywołana lub nie zostanie wywołana.  
  
- Anuluj kontynuację albo przed jej rozpoczęciem albo w trakcie jej działania.  
  
- Podaj wskazówki dotyczące sposobu, w jaki kontynuacja powinna zostać zaplanowana.  
  
- Wywoływanie wielu kontynuacji z tego samego poprzedzającego.  
  
- Wywołanie jednej kontynuacji po ukończeniu wszystkich lub dowolnego jednego z wielu poprzedników.  
  
- Łańcuch uzupełnia jeden po drugim do dowolnej dowolnej długości.  
  
- Użyj kontynuacji, aby obsłużyć wyjątki generowane przez poprzedzające.  
  
## <a name="about-continuations"></a>Informacje o kontynuacji  
 Kontynuacja to zadanie, które jest tworzone w stanie <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>. Jest uaktywniana automatycznie po ukończeniu zadania lub zadania poprzedzającego. Wywołanie <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType> na kontynuacji w kodzie użytkownika zgłasza wyjątek <xref:System.InvalidOperationException?displayProperty=nameWithType>.  
  
 Kontynuacja jest sama <xref:System.Threading.Tasks.Task> i nie blokuje wątku, w którym jest uruchomiona. Wywołaj metodę <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, aby zablokować do momentu zakończenia zadania kontynuacji.  
  
## <a name="creating-a-continuation-for-a-single-antecedent"></a>Tworzenie kontynuacji dla pojedynczego poprzedzającego  
 Należy utworzyć kontynuację, która jest wykonywana po zakończeniu poprzedzającego, wywołując metodę <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. W poniższym przykładzie pokazano wzorzec podstawowy (dla jasności, obsługa wyjątków jest pomijana). Wykonuje zadanie poprzedzające, `taskA`, które zwraca obiekt <xref:System.DayOfWeek>, który wskazuje nazwę bieżącego dnia tygodnia. Po zakończeniu poprzedzającego, zadanie kontynuacji, `continuation`, jest przenoszona poprzedzające i wyświetla ciąg, który zawiera jego wynik.

> [!NOTE]
> W C# przykładach w tym artykule użyto modyfikatora `async` na `Main` metodzie. Ta funkcja jest dostępna w C# 7,1 i nowszych. Poprzednie wersje generują [`CS5001`](../../csharp/misc/cs5001.md) podczas kompilowania tego przykładowego kodu. Należy ustawić wersję językową na C# 7,1 lub nowszą. Możesz dowiedzieć się, jak skonfigurować wersję języka w artykule dotyczącym [konfigurowania wersji językowej](../../csharp/language-reference/configure-language-version.md).
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## <a name="creating-a-continuation-for-multiple-antecedents"></a>Tworzenie kontynuacji dla wielu poprzedzających  
 Możesz również utworzyć kontynuację, która będzie uruchamiana po zakończeniu dowolnej lub wszystkich grup zadań. Aby wykonać kontynuację, gdy wszystkie zadania poprzedzające zostały ukończone, należy wywołać metodę "static" (`Shared` in Visual Basic) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> lub metodę <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> wystąpienia. Aby wykonać kontynuację, gdy którekolwiek z zadań poprzedzających zostało zakończone, należy wywołać metodę static (`Shared` in Visual Basic) <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> lub metodę <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> wystąpienia.  
  
 Należy zauważyć, że wywołania przeciążeń <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> nie blokują wątku wywołującego.  Jednak zazwyczaj wywołują wszystkie metody, ale <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType>, aby pobrać zwracaną Właściwość <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType>, która blokuje wątek wywołujący.  
  
 Poniższy przykład wywołuje metodę <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, aby utworzyć zadanie kontynuacji, które odzwierciedla wyniki jego 10 poprzedzających zadań. Każde zadanie poprzedzające ma wartość indeksu, która należy do zakresu od 1 do 10. Jeśli poprzedzające pomyślne ukończenie (ich <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> Właściwość to <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>), właściwość <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> kontynuacji jest tablicą wartości <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> zwracanych przez każde wystąpienie antecedent. Przykład dodaje je do obliczenia sumy kwadratów dla wszystkich liczb z zakresu od 1 do 10.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## <a name="continuation-options"></a>Opcje kontynuacji  
 Podczas tworzenia kontynuacji pojedynczego zadania można użyć przeciążenia <xref:System.Threading.Tasks.Task.ContinueWith%2A>, które przyjmuje <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> wartość wyliczenia, aby określić warunki, pod którymi rozpocznie się kontynuacja. Na przykład można określić, że kontynuacja ma być uruchamiana tylko wtedy, gdy poprzednik zostanie zakończony pomyślnie, lub tylko wtedy, gdy zostanie zakończony w stanie awarii. Jeśli warunek nie ma wartości true, gdy poprzednik jest gotowy do wywołania kontynuacji, kontynuacja przechodzi bezpośrednio do stanu <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> i nie można jej uruchomić.  
  
 Wiele metod kontynuacji wielu zadań, takich jak przeciążenia metody <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>, również zawiera parametr <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType>. Jednak tylko podzbiór wszystkich elementów członkowskich wyliczenia <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> są prawidłowe. Można określić <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> wartości, które mają odpowiedniki w <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType> wyliczenia, takie jak <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType>i <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType>. W przypadku określenia dowolnej opcji `NotOn` lub `OnlyOn` z kontynuacją wielozadania zostanie wygenerowany wyjątek <xref:System.ArgumentOutOfRangeException> w czasie wykonywania.  
  
 Więcej informacji o opcjach kontynuacji zadań znajduje się w temacie <xref:System.Threading.Tasks.TaskContinuationOptions>.  
  
## <a name="passing-data-to-a-continuation"></a>Przekazywanie danych do kontynuacji  
 Metoda <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> przekazuje odwołanie do odwołującego się do delegata użytkownika kontynuacji jako argumentu. Jeśli antecedent jest obiektem <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, a zadanie zostało uruchomione, dopóki nie zostało ukończone, kontynuacja może uzyskać dostęp do właściwości <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> zadania.  
  
 Właściwość <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> jest blokowana do momentu ukończenia zadania. Jeśli jednak zadanie zostało anulowane lub wystąpił błąd, próba uzyskania dostępu do właściwości <xref:System.Threading.Tasks.Task%601.Result%2A> zgłasza wyjątek <xref:System.AggregateException>. Możesz uniknąć tego problemu, korzystając z opcji <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion>, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Jeśli chcesz, aby kontynuacja była uruchamiana, nawet jeśli poprzednik nie został uruchomiony w celu pomyślnego ukończenia, należy zabezpieczyć wyjątek. Jednym z metod jest przetestowanie właściwości <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> antecedent i próba uzyskania dostępu do właściwości <xref:System.Threading.Tasks.Task%601.Result%2A>, jeśli stan nie jest <xref:System.Threading.Tasks.TaskStatus.Faulted> lub <xref:System.Threading.Tasks.TaskStatus.Canceled>. Możesz również przeanalizować Właściwość <xref:System.Threading.Tasks.Task.Exception%2A> poprzedzającego. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md). Poniższy przykład modyfikuje poprzedni przykład, aby uzyskać dostęp do właściwości <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> antecedent tylko wtedy, gdy jego stan jest <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## <a name="canceling-a-continuation"></a>Anulowanie kontynuacji  
 Właściwość <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> kontynuacji jest ustawiana na <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> w następujących sytuacjach:  
  
- Zgłasza wyjątek <xref:System.OperationCanceledException> w odpowiedzi na żądanie anulowania. Podobnie jak w przypadku każdego zadania, jeśli wyjątek zawiera ten sam token, który został przekazano do kontynuacji, jest traktowany jako potwierdzenie dla spółdzielni.  
  
- Kontynuacja jest przenoszona <xref:System.Threading.CancellationToken?displayProperty=nameWithType> którego właściwość <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> jest `true`. W takim przypadku kontynuacja nie zostanie uruchomiona i przechodzi do stanu <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType>.  
  
- Kontynuacja nigdy nie działa, ponieważ warunek ustawiony przez <xref:System.Threading.Tasks.TaskContinuationOptions> argument nie został spełniony. Na przykład jeśli poprzednika przejdzie do stanu <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType>, jego kontynuacja, która została przeniesiona <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> opcja nie zostanie uruchomiona, ale przejdzie do stanu <xref:System.Threading.Tasks.TaskStatus.Canceled>.  
  
 Jeśli zadanie i jego kontynuacja reprezentują dwie części tej samej operacji logicznej, można przekazać ten sam token anulowania do obu zadań, jak pokazano w poniższym przykładzie. Składa się z poprzedzającego, który generuje listę liczb całkowitych, które są podzielne przez 33, które przechodzi do kontynuacji. Kontynuacja z kolei wyświetla listę. Zarówno poprzednik, jak i kontynuacja są regularnie wstrzymywane w przypadku losowych interwałów. Ponadto obiekt <xref:System.Threading.Timer?displayProperty=nameWithType> jest używany do wykonywania metody `Elapsed` po upływie pięciu sekund interwału limitu czasu. Ten przykład wywołuje metodę <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType>, która powoduje wywołanie metody <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType> przez aktualnie wykonywane zadanie. Czy metoda <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> jest wywoływana, gdy jest wykonywane poprzedzające lub kontynuacja, zależy od czasu trwania losowo generowanych przerw. Jeśli poprzednik zostanie anulowany, kontynuacja nie zostanie uruchomiona. Jeśli poprzedzające nie zostało anulowane, token nadal może być używany do anulowania kontynuacji.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Można również uniemożliwić kontynuowanie wykonywania, jeśli jego poprzednik zostanie anulowany bez podawania kontynuacji tokenu anulowania przez określenie opcji <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> podczas tworzenia kontynuacji. Poniżej przedstawiono prosty przykład.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 Gdy kontynuacja przejdzie w stan <xref:System.Threading.Tasks.TaskStatus.Canceled>, może to wpłynąć na kontynuacje, które są następujące, w zależności od <xref:System.Threading.Tasks.TaskContinuationOptions> określonych dla tych kontynuacji.  
  
 Kontynuacje, które zostały zlikwidowane, nie zostaną uruchomione.  
  
## <a name="continuations-and-child-tasks"></a>Kontynuacje i zadania podrzędne  
 Kontynuacja nie działa do momentu ukończenia poprzedzających i wszystkich dołączonych zadań podrzędnych. Kontynuacja nie czeka na zakończenie odłączonych zadań podrzędnych. Poniższe dwa przykłady ilustrują zadania podrzędne, które są dołączone do i odłączane od poprzedzającego, który tworzy kontynuację. W poniższym przykładzie kontynuacja jest uruchamiana tylko po wykonaniu wszystkich zadań podrzędnych, a wielokrotne uruchomienie tego przykładu da identyczne dane wyjściowe. Przykład uruchamia poprzedzające wywołanie metody <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>, ponieważ domyślnie <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> Metoda tworzy zadanie nadrzędne, którego opcja tworzenia zadania domyślnego jest <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Jeśli zadania podrzędne są odłączone od poprzedzającego, jednak kontynuacja jest uruchamiana zaraz po zakończonym poprzedniku, niezależnie od stanu zadań podrzędnych. W związku z tym wiele przebiegów poniższego przykładu może generować zmienne dane wyjściowe, które są zależne od tego, jak harmonogram zadań obsłużył każde zadanie podrzędne.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 Końcowy stan zadania poprzedzającego zależy od końcowego stanu wszystkich dołączonych zadań podrzędnych. Stan odłączonych zadań podrzędnych nie ma wpływu na element nadrzędny. Aby uzyskać więcej informacji, zobacz [dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="associating-state-with-continuations"></a>Kojarzenie stanu z kontynuacjami  
 Możliwe jest skojarzenie dowolnego stanu z kontynuacją zadania. Metoda <xref:System.Threading.Tasks.Task.ContinueWith%2A> zapewnia przeciążone wersje, z których każda przyjmuje wartość <xref:System.Object>, która reprezentuje stan kontynuacji. Możesz później uzyskać dostęp do tego obiektu stanu przy użyciu właściwości <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType>. Ten obiekt stanu jest `null`, jeśli nie podasz wartości.  
  
 Stan kontynuacji jest przydatny podczas konwertowania istniejącego kodu, który używa [modelu programowania asynchronicznego (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) do korzystania z TPL. W programie APM zazwyczaj jest używany stan obiektu w metodzie **BEGIN** i później uzyskuje się dostęp do tego stanu przy użyciu właściwości <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType>. Za pomocą metody <xref:System.Threading.Tasks.Task.ContinueWith%2A> można zachować ten stan podczas konwertowania kodu, który używa APM do użycia TPL.  
  
 Stan kontynuacji może być również przydatny podczas pracy z obiektami <xref:System.Threading.Tasks.Task> w debugerze programu Visual Studio. Na przykład w oknie **zadania równoległe** w kolumnie **zadanie** jest wyświetlany ciąg reprezentujący obiekt stanu dla każdego zadania. Aby uzyskać więcej informacji o oknie **zadań równoległych** , zobacz [Korzystanie z okna zadań](/visualstudio/debugger/using-the-tasks-window).  
  
 Poniższy przykład pokazuje, jak używać stanu kontynuacji. Tworzy łańcuch zadań kontynuacji. Każde zadanie zawiera bieżący czas, <xref:System.DateTime> obiektu, dla `state` parametru metody <xref:System.Threading.Tasks.Task.ContinueWith%2A>. Każdy obiekt <xref:System.DateTime> reprezentuje godzinę utworzenia zadania kontynuacji. Każde zadanie powstaje jako wynik drugi <xref:System.DateTime> obiektu, który reprezentuje godzinę zakończenia zadania. Po zakończeniu wszystkich zadań ten przykład wyświetla czas utworzenia i godzinę zakończenia każdego zadania kontynuacji.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## <a name="handling-exceptions-thrown-from-continuations"></a>Obsługa wyjątków zgłoszonych przez kontynuacje  
 Relację kontynuacji poprzedzającej nie jest relacją nadrzędny-podrzędny. Wyjątki zgłoszone przez kontynuacje nie są propagowane do poprzedzającego. W związku z tym, obsługa wyjątków zgłaszanych przez kontynuacje w miarę obsłużenia ich w innych zadaniach w następujący sposób:  
  
- Aby czekać na kontynuację, można użyć metody <xref:System.Threading.Tasks.Task.Wait%2A>, <xref:System.Threading.Tasks.Task.WaitAll%2A>lub <xref:System.Threading.Tasks.Task.WaitAny%2A> lub jej ogólnego odpowiednika. Możesz poczekać na poprzedzające i jego kontynuacje w tej samej instrukcji `try`, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
- Możesz użyć drugiej kontynuacji, aby obserwować właściwość <xref:System.Threading.Tasks.Task.Exception%2A> pierwszej kontynuacji. W poniższym przykładzie zadanie próbuje odczytać z nieistniejącego pliku. Kontynuacja następnie wyświetla informacje o wyjątku w zadaniu poprzedzającym.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     Ponieważ został uruchomiony z opcją <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType>, kontynuacja jest wykonywana tylko wtedy, gdy wystąpi wyjątek w poprzedniku i w związku z tym może założyć, że właściwość <xref:System.Threading.Tasks.Task.Exception%2A> poprzedzająca nie jest `null`. Jeśli kontynuacja jest wykonywana niezależnie od tego, czy wyjątek jest zgłaszany w przypadku poprzedzającego, należy sprawdzić, czy właściwość <xref:System.Threading.Tasks.Task.Exception%2A> poprzedzający nie jest `null` przed podjęciem próby obsłużenia wyjątku, jak pokazano w poniższym fragmencie kodu.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
- Jeśli kontynuacja jest dołączonym zadaniem podrzędnym, które zostało utworzone przy użyciu opcji <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>, jego wyjątki będą propagowane przez nadrzędny z powrotem do wątku wywołującego, podobnie jak w przypadku dowolnego innego dołączonego elementu podrzędnego. Aby uzyskać więcej informacji, zobacz [dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="see-also"></a>Zobacz też

- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
