---
title: "Tworzenie łańcuchów zadań przy użyciu zadań kontynuacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, continuations
ms.assetid: 0b45e9a2-de28-46ce-8212-1817280ed42d
caps.latest.revision: "30"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7037e0c91ee6ae83b70d6a26e72b87095456063b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="chaining-tasks-by-using-continuation-tasks"></a>Tworzenie łańcuchów zadań przy użyciu zadań kontynuacji
W programowanie asynchroniczne jest często stosowane w jednej operacji asynchronicznej, po zakończeniu, aby wywołać operację drugi i przekazywania danych do niej. Tradycyjnie to przeprowadzono przy użyciu metody wywołania zwrotnego. W bibliotece równoległych zadań podał funkcji *zadań kontynuacji*. Zadania kontynuacji (nazywanego także po prostu utrzymania) jest zadanie asynchroniczne, które jest wywoływane przez inne zadanie, znany jako *antecedent*, po zakończeniu antecedent.  
  
 Kontynuacje są stosunkowo łatwa w użyciu, ale mimo to bardzo wydajny i elastyczny. Możesz na przykład:  
  
-   Przekazywanie danych z antecedent do kontynuacji.  
  
-   Określ dokładne warunki, w których kontynuacji będzie wywoływane lub nie został wywołany.  
  
-   Anuluj utrzymania przed rozpoczęciem lub wspólnie ponieważ jest on uruchomiony.  
  
-   Zawierają wskazówki dotyczące sposobu powinny zostać zaplanowane kontynuacji.  
  
-   Wywołanie wielu kontynuacje z tym samym antecedent.  
  
-   Po ukończeniu całości lub jedną z wielu antecedents, należy wywołać kontynuacji jeden.  
  
-   Powiązane kontynuacje jeden po drugim żadnych dowolnej długości.  
  
-   Umożliwia Obsługa wyjątków zgłaszanych przez antecedent utrzymania.  
  
## <a name="about-continuations"></a>O kontynuacje  
 Kontynuacja to zadanie, które jest tworzony w <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation> stanu. Jest aktywowane automatycznie po ukończeniu jego poprzedzających zadania lub zadania. Wywoływanie <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType> na kontynuację w kodzie użytkownika zgłasza <xref:System.InvalidOperationException?displayProperty=nameWithType> wyjątku.  
  
 Jest to kontynuacja <xref:System.Threading.Tasks.Task> i nie są blokowane w wątku, na którym jest uruchomiona. Wywołanie <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodę, aby zablokować zakończenie zadania kontynuacji.  
  
## <a name="creating-a-continuation-for-a-single-antecedent"></a>Tworzenie kontynuacji dla pojedynczego antecedent  
 Utwórz utrzymania wykonującą po zakończeniu jego antecedent przez wywołanie metody <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metody. W poniższym przykładzie przedstawiono podstawowe wzorzec, (dla uzyskania przejrzystości, obsługa wyjątków został pominięty). Wykonywania poprzedzających zadań `taskA`, która zwraca <xref:System.DayOfWeek> obiekt, który wskazuje nazwę bieżącego dnia tygodnia. Po zakończeniu antecedent zadania kontynuacji `taskB`, jest przekazywany antecedent i wyświetla ciąg, który zawiera jego wynik.  
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## <a name="creating-a-continuation-for-multiple-antecedents"></a>Tworzenie kontynuacji dla wielu antecedents  
 Można również utworzyć kontynuacji, które zostanie uruchomione po ukończeniu niektóre lub wszystkie z grupy zadań. Kontynuacja należy wykonać po zakończeniu wykonywania wszystkich zadań poprzedzających, należy wywołać statycznych (`Shared` w języku Visual Basic) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metody lub wystąpienie <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> metody. Kontynuacja należy wykonać po zakończeniu poprzedzających zadań, należy wywołać statycznych (`Shared` w języku Visual Basic) <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metody lub wystąpienie <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> metody.  
  
 Należy pamiętać, że wywołań <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> przeciążenia nie blokują wątek wywołujący.  Jednak zwykle wywołują wszystkie elementy oprócz <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType> metody do pobierania zwróconego <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwość, która zablokować wywołania wątku.  
  
 Następujące przykładowe wywołania <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> metodę w celu utworzenia zadania kontynuacji odzwierciedlający wyniki dziesięć poprzedzających zadań. Każde zadanie poprzedzających kwadraty wartość indeksu, która w zakresie od 1 do 10. Jeśli antecedents zakończy się pomyślnie (ich <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> właściwość jest <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>), <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwości kontynuacji jest tablicą <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> wartości zwracanych przez każdego antecedent. Przykład dodaje je do obliczenia sumę kwadratów liczb wszystkich między 1 a 10.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## <a name="continuation-options"></a>Opcje kontynuacji  
 Podczas tworzenia kontynuacji jednego zadania, można użyć <xref:System.Threading.Tasks.Task.ContinueWith%2A> przeciążenia, które przyjmuje <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> wartość wyliczenia do określenia warunków, w jakich uruchamia kontynuacji. Na przykład można określić, że kontynuowanie jest uruchomienie tylko wtedy, gdy antecedent zakończy się pomyślnie, lub tylko wtedy, gdy ukończy stan. Jeśli warunek nie zostanie spełniony, gdy antecedent jest gotowe do kontynuacji wywołania, kontynuacji bezpośrednio do przejścia <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stanu i nie można uruchomić po tym.  
  
 Wiele metod kontynuacji wielu zadań, takich jak przeciążeń <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> metody również obejmować <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> parametru. Tylko podzestaw wszystkie <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> elementy członkowskie wyliczenia są prawidłowe, jednak. Można określić <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> wartości, które mają odpowiednikowi w <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType> wyliczenia, takich jak <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType>, i <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType>. Jeśli określisz żadnego z `NotOn` lub `OnlyOn` opcje w przypadku kontynuacji wielu zadań, <xref:System.ArgumentOutOfRangeException> zostanie wygenerowany wyjątek w czasie wykonywania.  
  
 Aby uzyskać więcej informacji na temat zadań kontynuacji opcji, zobacz <xref:System.Threading.Tasks.TaskContinuationOptions> tematu.  
  
## <a name="passing-data-to-a-continuation"></a>Przekazywanie danych do kontynuacji  
 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> Metoda przekazuje odwołanie do antecedent do delegata użytkownika o kontynuację jako argument. Jeśli jest antecedent <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> obiektu, a zadanie uruchomione dopóki została ukończona, mogą uzyskiwać dostęp do kontynuacji, a następnie <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwości zadania.  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> Właściwość blokuje dopiero po ukończeniu zadania. Jednak jeśli zadanie zostało anulowane lub wystąpił błąd, próbuje uzyskać dostęp do <xref:System.Threading.Tasks.Task%601.Result%2A> zgłasza właściwości <xref:System.AggregateException> wyjątku. Można uniknąć tego problemu za pomocą <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion> opcji, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Jeśli chcesz kontynuacji do uruchomienia, nawet jeśli antecedent nie zostało uruchomione na pomyślne zakończenie, należy zabezpieczyć się przed wyjątek. Jednym z podejść jest przetestowanie <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> właściwość poprzedzających i tylko próba uzyskania dostępu do <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość, o ile nie jest w stanie <xref:System.Threading.Tasks.TaskStatus.Faulted> lub <xref:System.Threading.Tasks.TaskStatus.Canceled>. Można również sprawdzić <xref:System.Threading.Tasks.Task.Exception%2A> właściwość antecedent. Aby uzyskać więcej informacji, zobacz [obsługi wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md). Poniższy przykład modyfikuje poprzedniego przykładu do dostępu antecedent <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwość tylko wtedy, gdy jego stan jest <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## <a name="canceling-a-continuation"></a>Anulowanie utrzymania  
 <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> Ma ustawioną właściwość utrzymania <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> w następujących sytuacjach:  
  
-   Zgłasza <xref:System.OperationCanceledException> wyjątek w odpowiedzi na żądanie anulowania. Podobnie jak wszystkie zadania, jeśli wyjątek zawiera ten sam token, który został przekazany do kontynuacji, będzie traktowane jako potwierdzenie wspólne anulowanie.  
  
-   Kontynuacja jest przekazywany <xref:System.Threading.CancellationToken?displayProperty=nameWithType> których <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> jest właściwość `true`. W takim przypadku nie można uruchomić kontynuacji, a przechodzi on w <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stanu.  
  
-   Utrzymanie nigdy nie działa, ponieważ warunek ustawiony jego <xref:System.Threading.Tasks.TaskContinuationOptions> argument nie została spełniona. Na przykład, jeśli antecedent przechodzi w stan <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> stanu, jego kontynuację, który został przekazany <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> opcja nie będzie działać, ale spowoduje przejście do <xref:System.Threading.Tasks.TaskStatus.Canceled> stanu.  
  
 Jeśli zadania i jego kontynuacji reprezentować dwie części tej samej operacji logicznych, można przekazać ten sam token anulowania do obu zadań, jak pokazano w poniższym przykładzie. Składa się z antecedent, który generuje listę liczb całkowitych, które są podzielna przez 33 przekazaniem do kontynuacji. Kontynuacja z kolei umożliwia wyświetlenie listy. Antecedent jak również kontynuacji wstrzymać regularnie dla losowych odstępach czasu. Ponadto <xref:System.Threading.Timer?displayProperty=nameWithType> obiektu służy do wykonywania `Elapsed` metody po upływie czasu pięciu sekund limitu czasu. Powoduje to wywołanie <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metodę, która powoduje wywołanie aktualnie wykonywanego zadania <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType> metody. Czy <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metoda jest wywoływana podczas wykonywania jest antecedent lub jego kontynuacji zależy od czas trwania pauzy losowo wygenerowany. Jeśli antecedent zostało anulowane, kontynuacji nie zostanie uruchomiona. Jeśli antecedent nie została anulowana, token nadal można anulować kontynuacji.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Możesz również uniemożliwić kontynuacji wykonania, jeśli jego antecedent zostało anulowane bez podawania kontynuacji token anulowania, określając <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> podczas tworzenia kontynuacji. Poniżej przedstawiono prosty przykład.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 Po kontynuacji przechodzi w stan <xref:System.Threading.Tasks.TaskStatus.Canceled> stan może mieć wpływ na kontynuacje, które należy wykonać, w zależności od <xref:System.Threading.Tasks.TaskContinuationOptions> dla tych kontynuacje określono.  
  
 Nie można uruchomić kontynuacje, które zostały usunięte.  
  
## <a name="continuations-and-child-tasks"></a>Kontynuacje i zadania podrzędne  
 Kontynuacja nie działa do momentu antecedent i wszystkie jego zadań podrzędnych dołączonych została ukończona. Kontynuacji bez oczekiwania na zakończenie zadań podrzędnych odłączony. Dwa poniższe przykłady przedstawiają zadań podrzędnych dołączonych do i odłączyć od antecedent, która tworzy utrzymania. W poniższym przykładzie kontynuacji uruchamia dopiero po zakończeniu wykonywania wszystkich zadań podrzędnych i identyczne systemem generuje wiele razy w przykładzie danych wyjściowych zawsze. Należy pamiętać, że przykładzie uruchamia antecedent wywołując <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody, ponieważ domyślnie <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metoda tworzy zadaniem nadrzędnym, którego domyślna opcja tworzenia zadań jest <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Jeśli zadania podrzędne są odłączone od antecedent, jednak kontynuacji działa jak antecedent został zakończony, bez względu na stan zadania podrzędne. W związku z tym wiele przebiegów w poniższym przykładzie można utworzyć zmiennej danych wyjściowych, która zależy od sposobu harmonogram zadań obsługi każdego zadania podrzędnego.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 Stan końcowy poprzedzających zadania zależy od żadnych zadań podrzędnych dołączonych stan końcowy. Stan zadania podrzędne odłączony nie ma wpływu na element nadrzędny. Aby uzyskać więcej informacji, zobacz [dołączonego i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="associating-state-with-continuations"></a>Kojarzenie z Kontynuacje stanu  
 Stan dowolnego można skojarzyć z kontynuacji zadań. <xref:System.Threading.Tasks.Task.ContinueWith%2A> Metoda zapewnia przeciążone wersje każdego podjęcia <xref:System.Object> wartość, która reprezentuje stan kontynuacji. Ten obiekt stanu może później dostęp przy użyciu <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> właściwości. Ten obiekt stanu jest `null` , jeśli nie zostanie określona wartość.  
  
 Stan kontynuacji jest przydatne, jeśli Konwertuj istniejący kod, który używa [asynchronicznego programowania modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) do użycia TPL. Zwykle w APM, można zapewnić stan obiektu w  **rozpocząć*metody*** — metoda i nowszym dostępu, który stanu przy użyciu <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType> właściwości. Za pomocą <xref:System.Threading.Tasks.Task.ContinueWith%2A> metody, można zachować ten stan podczas konwertowania kod, który używa APM do użycia TPL.  
  
 Stan kontynuacji również może być przydatna podczas pracy z <xref:System.Threading.Tasks.Task> obiekty w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugera. Na przykład w **zadań równoległych** okna, **zadań** kolumny Wyświetla reprezentację ciągu obiektu stanu dla każdego zadania. Aby uzyskać więcej informacji na temat **zadań równoległych** okna, zobacz [korzystanie z okna zadań](/visualstudio/debugger/using-the-tasks-window).  
  
 Poniższy przykład przedstawia użycie stan kontynuacji. Tworzy łańcuch zadań kontynuacji. Każde zadanie zawiera bieżący czas <xref:System.DateTime> obiektu, dla `state` parametr <xref:System.Threading.Tasks.Task.ContinueWith%2A> metody. Każdy <xref:System.DateTime> obiekt reprezentuje czas, o której została utworzona zadania kontynuacji. Każde zadanie tworzy jako wynik drugi <xref:System.DateTime> obiekt, który reprezentuje czas, w którym kończy zadanie. Po zakończeniu wszystkich zadań, w tym przykładzie wyświetla czas tworzenia i czasu, w którym każdy kontynuacji kończy zadanie.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## <a name="handling-exceptions-thrown-from-continuations"></a>Obsługa wyjątków zgłaszanych przez Kontynuacje  
 Relacja kontynuacji antecedent nie jest w relacji nadrzędny podrzędny. Wyjątki generowane przez kontynuacje nie są propagowane do antecedent. W związku z tym obsługa wyjątków zgłaszanych przez kontynuacje, jak będzie je obsłużyć w następujący sposób w innych zadań:  
  
-   Można użyć <xref:System.Threading.Tasks.Task.Wait%2A>, <xref:System.Threading.Tasks.Task.WaitAll%2A>, lub <xref:System.Threading.Tasks.Task.WaitAny%2A> metody lub jego ogólny odpowiednik, oczekiwanie na kontynuowanie. Poczekaj antecedent i jego kontynuacje w tym samym `try` instrukcji, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
-   Można obserwować drugi kontynuacji <xref:System.Threading.Tasks.Task.Exception%2A> właściwości pierwszy kontynuacji. W poniższym przykładzie zadanie próbuje odczytać z pliku nie istnieje. Następnie kontynuacji Wyświetla informacje o wyjątku w poprzedzających zadań.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     Ponieważ zostało uruchomione z <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType> opcji kontynuacji wykonuje tylko w przypadku wystąpienia wyjątku w antecedent i dlatego jego można założyć, że antecedent <xref:System.Threading.Tasks.Task.Exception%2A> właściwość nie jest `null`. Jeśli kontynuacji wykonuje, czy wyjątek w antecedent, będą musiały być Sprawdź, czy antecedent <xref:System.Threading.Tasks.Task.Exception%2A> właściwość nie jest `null` przed podjęciem próby obsłużyć wyjątek, jako poniższy fragment kodu przedstawia.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Aby uzyskać więcej informacji, zobacz [obsługi wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md) i [NIB: porady: obsługa wyjątków zgłaszanych przez zadania](http://msdn.microsoft.com/en-us/d6c47ec8-9de9-4880-beb3-ff19ae51565d).  
  
-   Jeśli kontynuacji jest zadania podrzędnego dołączone, który został utworzony przy użyciu <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType> opcji jego wyjątki będą przekazywane przez nadrzędny powrót do wywoływania wątku, jak w przypadku innych podrzędnych dołączonych. Aby uzyskać więcej informacji, zobacz [dołączonego i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
