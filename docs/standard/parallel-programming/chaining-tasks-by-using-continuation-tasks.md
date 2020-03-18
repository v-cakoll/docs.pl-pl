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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159367"
---
# <a name="chaining-tasks-by-using-continuation-tasks"></a>Tworzenie łańcuchów zadań przy użyciu zadań kontynuacji
W programowaniu asynchronicznym jest wspólne dla jednej operacji asynchronicznej, po zakończeniu, wywołać drugą operację i przekazać dane do niej. Tradycyjnie kontynuacje zostały wykonane przy użyciu metod wywołania zwrotu. W bibliotece równoległej zadania te same funkcje są dostarczane przez *zadania kontynuacji*. Zadanie kontynuacji (znane również jako kontynuacja) jest zadaniem asynchronicznym wywoływanym przez inne zadanie, które jest znane jako *poprzednik*, po zakończeniu poprzednika.  
  
 Kontynuacje są stosunkowo łatwe w użyciu, ale mimo to są potężne i elastyczne. Można na przykład:  
  
- Przekazywanie danych z poprzednika do kontynuacji.  
  
- Określ dokładne warunki, w których kontynuacja będzie wywoływana lub nie wywoływana.  
  
- Anuluj kontynuację przed jej rozpoczęciem lub wspólnie, gdy jest uruchomiona.  
  
- Podaj wskazówki dotyczące sposobu planowania kontynuacji.  
  
- Wywołać wiele kontynuacji z tego samego poprzednika.  
  
- Wywołaj jedną kontynuację po zakończeniu wszystkich lub jednego z wielu poprzedników.  
  
- Łańcuch kontynuacje jeden po drugim do dowolnej długości.  
  
- Użyj kontynuacji do obsługi wyjątków zgłoszonych przez poprzednika.  
  
## <a name="about-continuations"></a>O kontynuacjach  
 Kontynuacja jest zadaniem, który <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation> jest tworzony w stanie. Jest on aktywowany automatycznie po zakończeniu jego poprzedzających zadań lub zadań. Wywołanie <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType> kontynuacji w kodzie <xref:System.InvalidOperationException?displayProperty=nameWithType> użytkownika zgłasza wyjątek.  
  
 Kontynuacja sama <xref:System.Threading.Tasks.Task> w sobie jest i nie blokuje wątku, na którym jest uruchamiany. Wywołaj <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodę, aby zablokować, dopóki nie zakończy się zadanie kontynuacji.  
  
## <a name="creating-a-continuation-for-a-single-antecedent"></a>Tworzenie kontynuacji dla jednego poprzednika  
 Tworzenie kontynuacji, która jest wykonywana po zakończeniu jego <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> poprzednika przez wywołanie metody. W poniższym przykładzie przedstawiono podstawowy wzorzec (dla jasności pominięto obsługę wyjątków). Wykonuje zadanie poprzednika, , `taskA`który zwraca <xref:System.DayOfWeek> obiekt, który wskazuje nazwę bieżącego dnia tygodnia. Po zakończeniu antecedent, zadanie kontynuacji, `continuation`, jest przekazywana antecedent i wyświetla ciąg, który zawiera jego wynik.

> [!NOTE]
> Przykłady Języka C# w tym `async` artykule korzystają `Main` z modyfikatora na metodę. Ta funkcja jest dostępna w języku C# 7.1 i nowszych. Poprzednie wersje generują [`CS5001`](../../csharp/misc/cs5001.md) podczas kompilowania tego przykładowego kodu. Musisz ustawić wersję językową na C# 7.1 lub nowszą. Możesz dowiedzieć się, jak skonfigurować wersję językową w artykule na [konfigurowanie wersji językowej](../../csharp/language-reference/configure-language-version.md).
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## <a name="creating-a-continuation-for-multiple-antecedents"></a>Tworzenie kontynuacji dla wielu poprzedników  
 Można również utworzyć kontynuację, która zostanie uruchamiana po zakończeniu dowolnej lub wszystkich grup zadań. Aby wykonać kontynuację po zakończeniu wszystkich poprzednich zadań,`Shared` należy wywołać <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metodę statyczną (w języku Visual Basic) lub metodę wystąpienia. <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> Aby wykonać kontynuację po zakończeniu dowolnych zadań poprzedników, należy`Shared` wywołać <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metodę statyczną (w języku Visual Basic) lub metodę wystąpienia. <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType>  
  
 Należy zauważyć, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> że <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> wywołania i przeciążenia nie blokują wątku wywołującego.  Jednak zazwyczaj wywołać wszystkie <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> oprócz <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType> i metody, aby <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> pobrać zwróconą właściwość, która blokuje wątek wywołujący.  
  
 Poniższy przykład wywołuje <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> metodę, aby utworzyć zadanie kontynuacji, który odzwierciedla wyniki jego 10 poprzednich zadań. Każde zadanie poprzednika kwadraty wartość indeksu, który waha się od jednego do 10. Jeśli poprzedników zakończyć pomyślnie (ich <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> właściwość <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>jest <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> ), właściwość kontynuacji jest <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> tablica wartości zwracanych przez każdego poprzednika. W przykładzie dodaje je do obliczenia sumy kwadratów dla wszystkich liczb z 1 do 10.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## <a name="continuation-options"></a>Opcje kontynuacji  
 Podczas tworzenia kontynuacji jednego zadania, można <xref:System.Threading.Tasks.Task.ContinueWith%2A> użyć przeciążenia, który przyjmuje wartość <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> wyliczenia, aby określić warunki, w których rozpoczyna się kontynuacja. Na przykład można określić, że kontynuacja ma być uruchamiana tylko wtedy, gdy poprzednik zakończy się pomyślnie lub tylko wtedy, gdy zakończy się w stanie błędnym. Jeśli warunek nie jest spełniony, gdy poprzednik jest gotowy do wywołania <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> kontynuacji, kontynuacja przechodzi bezpośrednio do stanu, a następnie nie można uruchomić.  
  
 Szereg wielozadaniowych metod kontynuacji, takich jak <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> przeciążenia metody, również parametr. <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> Jednak tylko podzbiór <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> wszystkich elementów członkowskich wyliczania jest prawidłowy. Można określić <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> wartości, które mają <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType> odpowiedniki w <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>wyliczeniu, takie jak , <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType>, i <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType>. Jeśli określisz `NotOn` `OnlyOn` dowolną z lub opcji <xref:System.ArgumentOutOfRangeException> z kontynuacją wielu zadań, wyjątek zostanie zgłoszony w czasie wykonywania.  
  
 Aby uzyskać więcej informacji na <xref:System.Threading.Tasks.TaskContinuationOptions> temat opcji kontynuacji zadań, zobacz temat.  
  
## <a name="passing-data-to-a-continuation"></a>Przekazywanie danych do kontynuacji  
 Metoda <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> przekazuje odwołanie do poprzednika do delegata użytkownika kontynuacji jako argument. Jeśli antecedent jest <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> obiektem, a zadanie zostało wykonane, dopóki nie <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> zostało ukończone, kontynuacja może uzyskać dostęp do właściwości zadania.  
  
 Właściwość <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> blokuje, dopóki zadanie nie zostanie zakończone. Jednak jeśli zadanie zostało anulowane lub błędy, próba <xref:System.Threading.Tasks.Task%601.Result%2A> uzyskania dostępu <xref:System.AggregateException> do właściwości zgłasza wyjątek. Ten problem można uniknąć, <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion> korzystając z opcji, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Jeśli chcesz, aby kontynuacja była uruchamiana, nawet jeśli poprzednik nie został uruchomiony do pomyślnego zakończenia, należy zabezpieczyć się przed wyjątkiem. Jednym z podejść <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> jest przetestowanie właściwości poprzednika i <xref:System.Threading.Tasks.Task%601.Result%2A> tylko próbować uzyskać <xref:System.Threading.Tasks.TaskStatus.Faulted> dostęp <xref:System.Threading.Tasks.TaskStatus.Canceled>do właściwości, jeśli stan nie jest lub . Można również sprawdzić <xref:System.Threading.Tasks.Task.Exception%2A> właściwość poprzednika. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md). Poniższy przykład modyfikuje poprzedni przykład, aby uzyskać <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> dostęp do właściwości <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>poprzednika tylko wtedy, gdy jego stan jest .  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## <a name="canceling-a-continuation"></a>Anulowanie kontynuacji  
 Właściwość <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> kontynuacji jest ustawiona <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> w następujących sytuacjach:  
  
- Zgłasza <xref:System.OperationCanceledException> wyjątek w odpowiedzi na żądanie anulowania. Podobnie jak w przypadku każdego zadania, jeśli wyjątek zawiera ten sam token, który został przekazany do kontynuacji, jest traktowany jako potwierdzenie anulowania współpracy.  
  
- Kontynuacja jest <xref:System.Threading.CancellationToken?displayProperty=nameWithType> przekazywana, której <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość jest `true`. W takim przypadku kontynuacja nie uruchamia się i <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> przechodzi do stanu.  
  
- Kontynuacja nigdy nie działa, <xref:System.Threading.Tasks.TaskContinuationOptions> ponieważ warunek ustawiony przez jego argument nie został spełniony. Na przykład jeśli poprzednik przechodzi w <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> stan, jego kontynuacja, która została <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> przekazana, <xref:System.Threading.Tasks.TaskStatus.Canceled> opcja nie zostanie uruchomiony, ale przejdzie do stanu.  
  
 Jeśli zadanie i jego kontynuacja reprezentują dwie części tej samej operacji logicznej, można przekazać ten sam token anulowania do obu zadań, jak pokazano w poniższym przykładzie. Składa się z poprzednika, który generuje listę liczb całkowitych, które są podzielne przez 33, który przechodzi do kontynuacji. Kontynuacja z kolei wyświetla listę. Zarówno poprzednik, jak i kontynuacja regularnie pauzują w losowych odstępach czasu. Ponadto <xref:System.Threading.Timer?displayProperty=nameWithType> obiekt jest używany do `Elapsed` wykonywania metody po pięciosekundowym przedziale czasu. W tym <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> przykładzie wywołuje metodę, co powoduje, <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType> że aktualnie wykonywane zadanie do wywołania metody. To, <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> czy metoda jest wywoływana podczas wykonywania poprzednika, czy jego kontynuacja, zależy od czasu trwania losowo generowanych pauz. Jeśli poprzednik zostanie anulowany, kontynuacja nie rozpocznie się. Jeśli poprzednik nie zostanie anulowany, token nadal może służyć do anulowania kontynuacji.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Można również zapobiec kontynuacji wykonywania, jeśli jego poprzednik jest anulowane bez podawania kontynuacji token anulowania, określając <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> opcję podczas tworzenia kontynuacji. Poniżej przedstawiono prosty przykład.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 Po kontynuacji przechodzi <xref:System.Threading.Tasks.TaskStatus.Canceled> do stanu, może mieć wpływ na <xref:System.Threading.Tasks.TaskContinuationOptions> kontynuacje, które następują, w zależności od, które zostały określone dla tych kontynuacji.  
  
 Kontynuacje, które są usuwane nie rozpocznie.  
  
## <a name="continuations-and-child-tasks"></a>Kontynuacje i zadania podrzędne  
 Kontynuacja nie jest uruchamiana, dopóki poprzednik i wszystkie związane z nim zadania podrzędne nie zostaną zakończone. Kontynuacja nie czeka na zakończenie zadań podrzędnych odłączonych. W poniższych dwóch przykładach przedstawiono zadania podrzędne, które są dołączone do i odłączone od poprzednika, który tworzy kontynuację. W poniższym przykładzie kontynuacja jest uruchamiana tylko po zakończeniu wszystkich zadań podrzędnych, a uruchamianie przykładu wiele razy powoduje uzyskanie identycznych danych wyjściowych za każdym razem. Przykład uruchamia poprzednika, wywołując <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metodę, ponieważ domyślnie <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metoda tworzy zadanie nadrzędne, <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>którego domyślną opcją tworzenia zadania jest .  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Jeśli zadania podrzędne są odłączone od poprzednika, jednak kontynuacja jest uruchamiana natychmiast po zakończeniu poprzednika, niezależnie od stanu zadań podrzędnych. W rezultacie wiele przebiegów w poniższym przykładzie może generować zmienne dane wyjściowe, które zależy od tego, jak harmonogram zadań obsługiwał każde zadanie podrzędne.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 Ostateczny stan zadania poprzednika zależy od ostatecznego stanu dołączonych zadań podrzędnych. Stan odłączonych zadań podrzędnych nie ma wpływu na element nadrzędny. Aby uzyskać więcej informacji, zobacz [Dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="associating-state-with-continuations"></a>Kojarzenie państwa z kontynuacjami  
 Można skojarzyć dowolny stan z kontynuacją zadania. Metoda <xref:System.Threading.Tasks.Task.ContinueWith%2A> zawiera przeciążone wersje, które każdy ma <xref:System.Object> wartość, która reprezentuje stan kontynuacji. Później można uzyskać dostęp do <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> tego obiektu stanu przy użyciu właściwości. Ten obiekt `null` stanu jest, jeśli nie podasz wartość.  
  
 Stan kontynuacji jest przydatne podczas konwertowania istniejącego kodu, który używa [asynchronicznego modelu programowania (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) do korzystania z TPL. W programie APM zazwyczaj podaje stos obiektu w **begin**_method_ metody <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType> i później dostęp do tego stanu przy użyciu właściwości. Za pomocą <xref:System.Threading.Tasks.Task.ContinueWith%2A> metody, można zachować ten stan podczas konwertowania kodu, który używa APM do korzystania z TPL.  
  
 Stan kontynuacji może być również <xref:System.Threading.Tasks.Task> przydatne podczas pracy z obiektami w debugerze programu Visual Studio. Na przykład w oknie **Zadania równoległe** kolumna **Zadanie** wyświetla reprezentację ciągu obiektu stanu dla każdego zadania. Aby uzyskać więcej informacji na temat okna **Zadania równoległe,** zobacz [Korzystanie z okna Zadania](/visualstudio/debugger/using-the-tasks-window).  
  
 W poniższym przykładzie pokazano, jak używać stanu kontynuacji. Tworzy łańcuch zadań kontynuacji. Każde zadanie zawiera bieżący <xref:System.DateTime> czas, obiekt, `state` dla <xref:System.Threading.Tasks.Task.ContinueWith%2A> parametru metody. Każdy <xref:System.DateTime> obiekt reprezentuje czas, w którym jest tworzone zadanie kontynuacji. Każde zadanie daje w wyniku <xref:System.DateTime> drugi obiekt, który reprezentuje czas, w którym kończy się zadanie. Po zakończeniu wszystkich zadań w tym przykładzie jest wyświetlany czas utworzenia i czas zakończenia każdego zadania kontynuacji.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## <a name="handling-exceptions-thrown-from-continuations"></a>Obsługa wyjątków generowanych z kontynuacji  
 Relacja antecedent-kontynuacja nie jest relacją nadrzędny podrzędny. Wyjątki generowane przez kontynuacje nie są propagowane do poprzednika. W związku z tym doobsługi wyjątków generowanych przez kontynuacje, jak można obsługiwać je w każdym innym zadaniu, w następujący sposób:  
  
- Można użyć <xref:System.Threading.Tasks.Task.Wait%2A>, <xref:System.Threading.Tasks.Task.WaitAll%2A>lub <xref:System.Threading.Tasks.Task.WaitAny%2A> metody lub jego odpowiednik rodzajowy, aby poczekać na kontynuację. Można czekać na poprzednika i jego kontynuacji `try` w tej samej instrukcji, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
- Można użyć drugiej kontynuacji <xref:System.Threading.Tasks.Task.Exception%2A> obserwować właściwość pierwszej kontynuacji. W poniższym przykładzie zadanie próbuje odczytać z pliku nieistniejącego. Następnie kontynuacja wyświetla informacje o wyjątku w zadaniu poprzednika.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     Ponieważ został uruchomiony <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType> z opcją, kontynuacja jest wykonywana tylko wtedy, gdy wystąpi wyjątek w poprzedniku, a zatem można założyć, że właściwość poprzednika <xref:System.Threading.Tasks.Task.Exception%2A> nie `null`jest . Jeśli kontynuacja wykonuje, czy wyjątek jest zgłaszany w poprzednik, musiałby sprawdzić, czy <xref:System.Threading.Tasks.Task.Exception%2A> właściwość antecedent nie `null` jest przed podjęciem próby obsługi wyjątku, jak pokazano w poniższym fragmencie kodu.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
- Jeśli kontynuacja jest dołączonym zadaniem podrzędnym, który został utworzony przy użyciu <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType> opcji, jego wyjątki będą propagowane przez element nadrzędny z powrotem do wątku wywołującego, jak to ma miejsce w każdym innym dołączonym podrzędnym. Aby uzyskać więcej informacji, zobacz [Dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="see-also"></a>Zobacz też

- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
