---
title: Tworzenie łańcuchów zadań przy użyciu zadań kontynuacji
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, continuations
ms.assetid: 0b45e9a2-de28-46ce-8212-1817280ed42d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 308b834a133798104dcc47a16f8adc068ed937ec
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44188348"
---
# <a name="chaining-tasks-by-using-continuation-tasks"></a>Tworzenie łańcuchów zadań przy użyciu zadań kontynuacji
W programowaniu asynchronicznych jest częste jedna operacja asynchroniczna po zakończeniu wywołuje drugą operację i przekazuje dane do niej. Tradycyjnie zostało to zrobione za pomocą metody wywołania zwrotnego. W bibliotece zadań równoległych taką samą funkcjonalność świadczą *zadań kontynuacji*. Zadanie kontynuacji (znane również jako kontynuacja) to asynchroniczne zadanie, które jest wywoływane przez inne zadanie, który jest znany jako *zadania poprzedzającego*, po jego zakończeniu.  
  
 Kontynuacje są stosunkowo łatwe w użyciu, ale mimo to bardzo wydajne i elastyczne. Możesz na przykład:  
  
-   Przekazywanie danych od zadania poprzedzającego do kontynuacji.  
  
-   Określ dokładne warunki, na jakich kontynuacja będzie się lub nie jest wywoływana.  
  
-   Anuluj kontynuację albo przed jej rozpoczęciem albo w trakcie jest uruchomiona.  
  
-   Dostarczanie wskazówek na temat jak kontynuacja powinna zostać zaplanowana.  
  
-   Wywoływanie wielu kontynuacji z tego samego zadania poprzedzającego.  
  
-   Wywołanie jednej kontynuacji po ukończeniu wszystkich lub dowolnego jednego z wielu zadań poprzedzających.  
  
-   Kontynuacje łańcucha kolejno do każdej dowolnej długości.  
  
-   Użyj kontynuacji, aby obsłużyć wyjątki wyrzucane przez element poprzedzający.  
  
## <a name="about-continuations"></a>Temat kontynuacji  
 Kontynuacja jest zadaniem, który jest tworzony w <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation> stanu. Zostanie aktywowana automatycznie po ukończeniu jego zadania poprzedzającego lub zadania. Wywoływanie <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType> na kontynuację w kodzie użytkownika zgłasza <xref:System.InvalidOperationException?displayProperty=nameWithType> wyjątku.  
  
 Kontynuacja sama jest <xref:System.Threading.Tasks.Task> i nie jest blokowana w wątku, na którym jest uruchomiona. Wywołaj <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodę, aby zapewnić blokowanie do zakończenia zadania kontynuacji.  
  
## <a name="creating-a-continuation-for-a-single-antecedent"></a>Tworzenie kontynuacji dla pojedynczego zadania poprzedzającego  
 Utworzyć kontynuację, która wykonuje, gdy jej poprzednik zakończy się przez wywołanie metody <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metody. Poniższy przykład przedstawia podstawowy wzorzec (dla jasności pominięto obsługę wyjątków). Wykonuje zadania poprzedzającego `taskA`, która zwraca <xref:System.DayOfWeek> obiekt, który wskazuje nazwę bieżącego dnia tygodnia. Po zakończeniu zadania poprzedzającego, zadanie kontynuacji `continuation`, jest przekazywany do zadania poprzedzającego i wyświetla ciąg, który zawiera wynik.  
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## <a name="creating-a-continuation-for-multiple-antecedents"></a>Tworzenie kontynuacji dla wielu zadań poprzedzających  
 Można również utworzyć kontynuację, która będzie uruchamiana po zakończeniu dowolne lub wszystkie grupy zadań. Do wykonywania kontynuację, po zakończeniu wszystkie zadania poprzedzającego, wywołaj statyczną (`Shared` w języku Visual Basic) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metody lub wystąpienie <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> metody. Do wykonywania kontynuację, po zakończeniu dowolnego zadania poprzedzającego, wywołaj statyczną (`Shared` w języku Visual Basic) <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metody lub wystąpienie <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> metody.  
  
 Należy zauważyć, że wywołania <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> przeciążenia nie blokują wątek wywołujący.  Jednak zwykle wywołują wszystkie elementy oprócz <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType> metody pobierania zwracanego <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwość, która zablokowanie wątku wywołującego.  
  
 Poniższy przykład wywołuje <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> metodę, aby utworzyć zadanie kontynuacji, które odzwierciedla wyniki jego dziesięć zadania poprzedzającego. Każdego zadania poprzedzającego squares wartość indeksu z zakresu od 1 do 10. Jeśli poprzedników zakończy się pomyślnie (ich <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> właściwość <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>), <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwość kontynuacji jest tablicą <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> wartości zwróconych z każdego zadania poprzedzającego. Przykład dodaje je do obliczenia suma kwadratów dla wszystkich numerów między 1 a 10.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## <a name="continuation-options"></a>Opcje kontynuacji  
 Podczas tworzenia kontynuacji, można użyć <xref:System.Threading.Tasks.Task.ContinueWith%2A> przeciążenia przyjmującego <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> wartości wyliczenia można określić warunki, na jakich kontynuacja rozpoczyna się. Na przykład można określić, że kontynuacja ma być uruchamiane tylko wtedy, gdy zadanie poprzedzające zakończy się pomyślnie, lub tylko w przypadku, jeśli zakończy się w nieprawidłowym stanie. Jeśli warunek nie zostanie spełniony, gdy zadanie poprzedzające jest gotowe do wywołania kontynuacji, kontynuacja przechodzi bezpośrednio do <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stan i nie może zostać uruchomiona po tym.  
  
 Liczba metod wielozadaniową, takich jak przeciążenia <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> metody również obejmować <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> parametru. Tylko podzbiór wszystkich <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> elementów członkowskich wyliczenia są prawidłowe, jednak. Można określić <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> wartości, które mają odpowiedniki w <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType> wyliczenia, takich jak <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType>, i <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType>. Jeśli określisz dowolną z `NotOn` lub `OnlyOn` opcji wielozadaniową, <xref:System.ArgumentOutOfRangeException> zostanie zgłoszony wyjątek w czasie wykonywania.  
  
 Aby uzyskać więcej informacji na temat opcji kontynuacji zadań, zobacz <xref:System.Threading.Tasks.TaskContinuationOptions> tematu.  
  
## <a name="passing-data-to-a-continuation"></a>Przekazywanie danych do kontynuacji  
 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> Metoda przekazuje odwołanie do obiektu poprzedzającego do pełnomocnika użytkownika kontynuacji jako argument. Jeśli zadanie poprzedzające jest <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> obiektu, a zadanie działał do momentu zostało ukończone, a następnie kontynuacji mogą uzyskiwać dostęp do <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwości zadania.  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> Właściwość blokuje, dopóki zadanie zostało ukończone. Jednakże, jeśli zadanie zostało anulowane lub wystąpił błąd, próby uzyskania dostępu do <xref:System.Threading.Tasks.Task%601.Result%2A> zgłasza właściwości <xref:System.AggregateException> wyjątku. Można uniknąć tego problemu, przy użyciu <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion> opcji, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Jeśli chcesz kontynuację uruchamiać nawet wtedy, gdy zadanie poprzedzające nie zostało uruchomione pomyślnie ukończone, należy chronić się przed wyjątkiem. Jedno z podejść jest przetestowanie <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> właściwość poprzedzającego i tylko próba uzyskania dostępu do <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość, jeśli nie jest w stanie <xref:System.Threading.Tasks.TaskStatus.Faulted> lub <xref:System.Threading.Tasks.TaskStatus.Canceled>. Można również sprawdzić <xref:System.Threading.Tasks.Task.Exception%2A> właściwości zadania poprzedzającego. Aby uzyskać więcej informacji, zobacz [wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md). Poniższy przykład modyfikuje poprzedni przykład do poprzedzającego dostępu <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwości tylko wtedy, gdy jego stan to <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## <a name="canceling-a-continuation"></a>Anulowanie kontynuacji  
 <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> Utrzymania zostaje ustalona <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> w następujących sytuacjach:  
  
-   Wyniku weryfikacji zgłasza wyjątek <xref:System.OperationCanceledException> wyjątek w odpowiedzi na żądanie anulowania. Podobnie jak w przypadku dowolnego zadania, jeśli wyjątek zawiera ten sam token, który został przekazany do kontynuacji, jest ona traktowana jako potwierdzenie wspólnego anulowania.  
  
-   Kontynuacja jest przekazywany <xref:System.Threading.CancellationToken?displayProperty=nameWithType> którego <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość `true`. W takim przypadku kontynuacja nie uruchamia się i przechodzi do <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stanu.  
  
-   Kontynuacja nigdy nie działa, ponieważ warunek ustawiony jego <xref:System.Threading.Tasks.TaskContinuationOptions> argumentu nie zostało spełnione. Na przykład, jeśli zadanie poprzedzające przechodzi w stan <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> stanu, jego kontynuacja, która została przekazana <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> opcja nie będzie działać, ale zostanie zastąpiona usługą <xref:System.Threading.Tasks.TaskStatus.Canceled> stanu.  
  
 Jeśli zadania i jego kontynuacja reprezentują dwie pierwsze części z tej samej operacji logicznej, można przekazać ten sam token odwołania do obu zadań, jak pokazano w poniższym przykładzie. Składa się z zadania poprzedzającego, która generuje listę liczb całkowitych, które są podzielna przez 33, która przekazuje do kontynuacji. Kontynuacja z kolei umożliwia wyświetlenie listy. Zadania poprzedzającego i kontynuacja Wstrzymanie aktualizacji regularnie losowych odstępach czasu. Ponadto <xref:System.Threading.Timer?displayProperty=nameWithType> obiektu jest używana do wykonywania `Elapsed` metoda po upływie 5 sekundowy limit czasu. Powoduje to wywołanie <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metody, która powoduje, że aktualnie wykonywane zadanie wywołać <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType> metody. Czy <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metoda jest wywoływana, gdy zadanie poprzedzające lub jego kontynuacja jest wykonywany jest zależna od czasu trwania pauzy generowany losowo. Jeśli zadanie poprzedzające jest anulowane, kontynuacja nie zostanie uruchomiona. Jeśli zadanie poprzedzające nie zostało anulowane, tokenu nadal można do anulowania kontynuacji.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Warto również zapobiegać kontynuacji wykonywanie, jeśli poprzednik został anulowany bez podawania kontynuacja token anulowania, określając <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> podczas tworzenia kontynuacji. Poniżej przedstawiono prosty przykład.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 Po kontynuacji przechodzi do <xref:System.Threading.Tasks.TaskStatus.Canceled> stanu, który może wpływać na kontynuacje, które należy wykonać, w zależności od <xref:System.Threading.Tasks.TaskContinuationOptions> które zostały określone dla tych kontynuacji.  
  
 Usuniętych kontynuacji nie zostanie uruchomiona.  
  
## <a name="continuations-and-child-tasks"></a>Kontynuacje i zadania podrzędne  
 Kontynuacja nie uruchamia się przed zakończeniem poprzedniego i wszystkich dołączonych zadań podrzędnych została ukończona. Kontynuacja nie czeka na odłączonych zadań podrzędnych do zakończenia. Dwa poniższe przykłady ilustrują zadań podrzędnych, które są dołączone do odłączona od zadania poprzedzającego, który tworzy kontynuację. W poniższym przykładzie kontynuacja działa tylko po ukończeniu wszystkich zadań podrzędnych oraz identyczne uruchomieniem przykładu wielokrotnie generuje dane wyjściowe każdorazowo. Należy pamiętać, że przykład uruchamia zadania poprzedzającego, wywołując <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody, ponieważ domyślnie <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metoda tworzy zadanie nadrzędne, w których domyślnej opcji tworzenia zadań jest <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Jeśli zadania podrzędne są odłączone od zadania poprzedzającego, jednak kontynuacja działa tak szybko, jak długo zadanie poprzedzające zostało zakończone, bez względu na stan zadań podrzędnych. Co w efekcie wiele przebiegów poniższy przykład służy do tworzenia zmiennych danych wyjściowych, który zależy od sposobu harmonogram zadań obsługi każdego zadania podrzędnego.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 Końcowy stan zadania poprzedzającego zależy od stanu końcowego jakiegokolwiek dołączonego zadania podrzędnego. Stan odłączonych zadań podrzędnych nie wpływa na element nadrzędny. Aby uzyskać więcej informacji, zobacz [dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="associating-state-with-continuations"></a>Kojarzenie stanu z Kontynuacjami  
 Można skojarzyć z dowolny stan z kontynuacją zadania. <xref:System.Threading.Tasks.Task.ContinueWith%2A> Metoda zapewnia przeciążone wersje, każda <xref:System.Object> wartość, która reprezentuje stan kontynuacji. Obiekt stanu można później dostęp, za pomocą <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> właściwości. Obiekt stanu to `null` Jeśli nie zostanie określona wartość.  
  
 Stanu kontynuacji jest przydatny, gdy konwertujesz istniejący kod, który używa [modelu programowania asynchronicznego (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) Aby wykorzystać TPL. W modelu programowania Asynchronicznego zazwyczaj podaje się stan obiektu w **rozpocząć *** metoda* i później przechodzi do tego stanu przy użyciu <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType> właściwości. Za pomocą <xref:System.Threading.Tasks.Task.ContinueWith%2A> metody, można zachować ten stan podczas konwertowania kodu, który używa APM, aby wykorzystać TPL.  
  
 Stan kontynuacji może być także przydatny podczas pracy z <xref:System.Threading.Tasks.Task> obiektów w debugerze programu Visual Studio. Na przykład w **zadań równoległych** oknie **zadań** kolumna wyświetla ciąg reprezentujący obiekt stanu dla każdego zadania. Aby uzyskać więcej informacji na temat **zadań równoległych** okna, zobacz [korzystanie z okna zadań](/visualstudio/debugger/using-the-tasks-window).  
  
 Poniższy przykład przedstawia sposób używania stanu kontynuacji. Tworzy łańcuch połączonych zadań. Każde zadanie zawiera bieżącą godzinę <xref:System.DateTime> obiektu, dla `state` parametru <xref:System.Threading.Tasks.Task.ContinueWith%2A> metody. Każdy <xref:System.DateTime> obiekt reprezentuje czas, w którym utworzono zadanie kontynuacji. Każde zadanie tworzy jako wynik drugi <xref:System.DateTime> obiekt, który reprezentuje czas, w którym zadanie się nie zakończy. Po zakończeniu wszystkich zadań w tym przykładzie wyświetla czas tworzenia i czas, w której każdy kontynuacji zakończeniem zadania.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## <a name="handling-exceptions-thrown-from-continuations"></a>Obsługa wyjątków zgłaszanych z kontynuacji  
 Relacja kontynuacji poprzednika nie jest relacją nadrzędny podrzędny. Wyjątki generowane przez kontynuacje nie są propagowane do zadania poprzedzającego. W związku z tym obsłużyć wyjątki wyrzucane przez kontynuacja, jak możesz być je obsługiwał w dowolnym innym zadaniu, w następujący sposób:  
  
-   Możesz użyć <xref:System.Threading.Tasks.Task.Wait%2A>, <xref:System.Threading.Tasks.Task.WaitAll%2A>, lub <xref:System.Threading.Tasks.Task.WaitAny%2A> metody lub jego odpowiednika rodzajowego, aby czekać na kontynuację. Możesz poczekać na poprzednik i jego kontynuacje w tej samej `try` instrukcji, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
-   Można użyć drugiej kontynuacji, aby obserwować <xref:System.Threading.Tasks.Task.Exception%2A> właściwości pierwszej kontynuacji. W poniższym przykładzie zadanie próbuje odczytać z pliku nie istnieje. Kontynuacja następnie wyświetla informacje o wyjątku w zadania poprzedzającego.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     Ponieważ zostało uruchomione z <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType> opcji kontynuacja wykonuje tylko wtedy, gdy wystąpi wyjątek w zadania poprzedzającego, i w związku z tym go można założyć, że zadania poprzedzającego <xref:System.Threading.Tasks.Task.Exception%2A> właściwość nie jest `null`. Jeśli kontynuacja wykonuje informację określającą, czy wyjątek jest zgłaszany poprzednika, będą musiały być Sprawdź, czy zadania poprzedzającego <xref:System.Threading.Tasks.Task.Exception%2A> właściwość nie jest `null` przed podjęciem próby wykonania do obsługi wyjątków, jak poniższy fragment kodu przedstawia.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Aby uzyskać więcej informacji, zobacz [wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
-   Jeśli kontynuacja jest dołączone zadanie podrzędne, który został utworzony przy użyciu <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType> opcji, jej wyjątki będą propagowane przez nadrzędne z powrotem do wywołanego wątku, jak w przypadku innych dołączonych zadań podrzędnych. Aby uzyskać więcej informacji, zobacz [dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
