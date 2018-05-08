---
title: Obsługa wyjątku (Biblioteka zadań równoległych)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, exceptions
ms.assetid: beb51e50-9061-4d3d-908c-56a4f7c2e8c1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16ab0b8967ac394540f201fcc9098024faaccaa7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="exception-handling-task-parallel-library"></a>Obsługa wyjątku (Biblioteka zadań równoległych)
Nieobsłużonych wyjątków, które są generowane przez kod użytkownika, który działa wewnątrz zadania są propagowane do wątek wywołujący, z wyjątkiem w niektórych scenariuszach, które zostały opisane w dalszej części tego tematu. Oczekiwania były propagowane, gdy używany jest jeden statycznych lub wystąpienia <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> lub <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` metod, a ich obsługę, umieszczając wywołanie `try` / `catch` instrukcji. Jeśli zadanie ma element nadrzędny zadania podrzędne dołączone lub oczekiwania na wielu zadań, może zostać zgłoszony wiele wyjątków.  
  
 Wszystkie wyjątki z powrotem do wątku wywołującym propagację, infrastruktury zadań opakowuje je w <xref:System.AggregateException> wystąpienia. <xref:System.AggregateException> Wyjątek ma <xref:System.AggregateException.InnerExceptions%2A> właściwości mogą być wyliczane do Badaj wszystkie wyjątki oryginalnego, które zostały zgłoszone, a obsługa (lub nie obsługują) każdej z nich osobno. Można również obsługiwać przy użyciu oryginalnego wyjątki <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metody.  
  
 Nawet wtedy, gdy tylko jeden wyjątek, nadal jest ujęte w <xref:System.AggregateException> wyjątek, jak przedstawiono na poniższym przykładzie.  
  
 [!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
 [!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]  
  
 Wystąpił nieobsługiwany wyjątek można uniknąć, po prostu Przechwytywanie <xref:System.AggregateException> i nie stosuje wewnętrzny wyjątki. Jednak zaleca się czy nie zrobisz, ponieważ jest ono odpowiednikiem Przechwytywanie bazie <xref:System.Exception> typu w scenariuszach z systemem innym niż równoległe. Aby przechwytywać wyjątku bez konieczności przełączania określonych czynności, aby odzyskać z niego można pozostawić program w stanie nieokreślonym.  
  
 Jeśli nie chcesz wywołać <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> lub <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` metody czekać na zakończenie zadania, można również pobrać <xref:System.AggregateException> wyjątku z zadania <xref:System.Threading.Tasks.Task.Exception%2A> właściwości, jak przedstawiono na poniższym przykładzie. Aby uzyskać więcej informacji, zobacz [obserwowania wyjątków przy użyciu właściwości Task.Exception](#ExceptionProp) w tym temacie.  
  
 [!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
 [!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]  
  
 Aby nie czekać na zadanie, które propaguje wyjątku lub dostępu do jego <xref:System.Threading.Tasks.Task.Exception%2A> właściwości, wyjątek eskalacji zgodnie z zasadami wyjątek .NET po ukończeniu zadania zbierane pamięci.  
  
 Wyjątki mogą bąbelkowy się wstecz, aby łącząca wątku, jest to możliwe, że zadania mogą w dalszym ciągu przetwarzania niektórych elementów po jest wyjątek.  
  
> [!NOTE]
>  Po włączeniu "Tylko mój kod" programu Visual Studio w niektórych przypadkach będzie podział wiersza, która zgłasza wyjątek i wyświetlony komunikat o błędzie stwierdzający "wyjątek nie obsłużony przez kod użytkownika." Ten błąd jest niegroźne. Naciśnij klawisz F5, aby kontynuować i zachowanie obsługi wyjątków, przedstawionej w tym przykładzie. Aby zapobiec dzieleniu pierwszego błędu w Visual Studio, po prostu usuń zaznaczenie pola wyboru **Włącz opcję tylko mój kod** wyboru **narzędzia, opcje, debugowanie, ogólne**.  
  
## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Zadania podrzędne dołączone i AggregateExceptions zagnieżdżonych  
 Jeśli zadanie ma zadanie podrzędne dołączone zgłasza wyjątek, ten wyjątek jest ujęte w <xref:System.AggregateException> zanim zostanie przekazane do zadania nadrzędnego, które zawijany ten wyjątek we własnym <xref:System.AggregateException> przed jego propaguje powrót do wywoływania wątku. W takich przypadkach <xref:System.AggregateException.InnerExceptions%2A> właściwość <xref:System.AggregateException> wyjątek, który zostanie przechwycony na <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> lub <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` lub <xref:System.Threading.Tasks.Task.WaitAny%2A> lub <xref:System.Threading.Tasks.Task.WaitAll%2A> metoda zawiera jeden lub więcej <xref:System.AggregateException> wystąpienia nie oryginalny wyjątki, które spowodowało błąd. Aby uniknąć konieczności iteracja zagnieżdżone <xref:System.AggregateException> wyjątków, można użyć <xref:System.AggregateException.Flatten%2A> metody, aby usunąć wszystkie zagnieżdżone <xref:System.AggregateException> wyjątki, aby <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> właściwość zawiera oryginalnego wyjątków. W poniższym przykładzie zagnieżdżone <xref:System.AggregateException> wystąpienia są spłaszczane i obsługiwane tylko jednej pętli.  
  
 [!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
 [!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]  
  
 Można również użyć <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> metody do ponownego zgłoszenia wyjątków wewnętrznych z wielu <xref:System.AggregateException> wystąpień zgłaszanych przez wielu zadań w pojedynczym <xref:System.AggregateException> wystąpienia, jak przedstawiono na poniższym przykładzie.  
  
 [!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
 [!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]  
  
## <a name="exceptions-from-detached-child-tasks"></a>Wyjątki od zadania podrzędne odłączona  
 Domyślnie zadania podrzędne są tworzone jako odłączona. Wyjątków zgłaszanych przez zadania odłączyć muszą być obsługiwane lub zgłoszony w zadaniem nadrzędnym natychmiastowego; nie są propagowane do wątku wywołującym sam sposób jak dołączone zadania podrzędne propagowane ponownie. Nadrzędnego najwyższego poziomu można ręcznie Ponowne zgłoszenie wyjątku odłączyć podrzędnej spowodować być ujęte w <xref:System.AggregateException> i propagowane wątek wywołujący.  
  
 [!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
 [!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]  
  
 Nawet jeśli używasz utrzymania obserwować wyjątek zadania podrzędnego wyjątek nadal muszą być spełnione przez zadaniem nadrzędnym.  
  
## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Wyjątki, które wskazują współpracy anulowania  
 Jeśli kod użytkownika zadania odpowiada na żądanie anulowania, poprawne procedura ma throw <xref:System.OperationCanceledException> przekazując token anulowania, na którym żądanie zostało przesłane. Zanim podejmie próbę propagowanie wyjątku, wystąpienie zadania porównuje token w wyjątek do tego, który został przekazany do niego, podczas jej tworzenia. Jeśli są one takie same, zadanie propaguje <xref:System.Threading.Tasks.TaskCanceledException> otoczona <xref:System.AggregateException>, i może być widoczny, gdy są sprawdzane wyjątków wewnętrznych. Jednak jeśli wątek wywołujący nie jest oczekiwanie na zadanie, ten wyjątek nie zostaną zastosowane. Aby uzyskać więcej informacji, zobacz [anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
 [!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
 [!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]  
  
## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>Przy użyciu metody dojścia do filtru wyjątków wewnętrznych  
 Można użyć <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metodę, aby odfiltrować wyjątki, które można traktować jako "obsługiwane" bez korzystania z żadnych dalszych logiki. W elemencie delegowanym użytkownika, który został dostarczony do <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> metody, typ wyjątku, można sprawdzić jego <xref:System.Exception.Message%2A> właściwości lub inne informacje o tym, które pozwalają określić, czy jest niegroźne. Wszelkie wyjątki, dla których zwraca delegata `false` są zgłoszony w nowym <xref:System.AggregateException> natychmiast po wystąpieniu <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> zwraca metody.  
  
 Poniższy przykład jest funkcjonalnym odpowiednikiem w tym temacie, który sprawdza, czy każdy wyjątek w pierwszym przykładzie <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> kolekcji.  Zamiast tego wywołuje ten program obsługi wyjątku <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> obiekt metody dla każdego wyjątku i tylko wyjątki ponownie zgłasza wyjątek, które nie są `CustomException` wystąpień.  
  
 [!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
 [!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]  
  
 Poniżej przedstawiono przykład bardziej szczegółowy, który używa <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metodę w celu zapewnienia obsługi specjalnej dla <xref:System.UnauthorizedAccessException> wyjątek podczas wyliczania plików.  
  
 [!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
 [!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]  
  
<a name="ExceptionProp"></a>   
## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Obserwowania wyjątków przy użyciu właściwości Task.Exception  
 Po zakończeniu zadania w <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> stanu, jego <xref:System.Threading.Tasks.Task.Exception%2A> właściwości można zbadać, aby dowiedzieć się, które określony wyjątek spowodował. Dobrym sposobem obserwować <xref:System.Threading.Tasks.Task.Exception%2A> właściwości jest użycie kontynuację, w którym działa tylko wtedy, gdy zadanie poprzedzających błędów, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
 [!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]  
  
 W rzeczywistej aplikacji delegata kontynuacji można rejestrować szczegółowe informacje o wyjątku i prawdopodobnie zduplikować nowe zadania, aby odzyskać z wyjątkiem.  
  
## <a name="unobservedtaskexception-event"></a>Zdarzenie UnobservedTaskException  
 W niektórych scenariuszach takich jak odnośnie do hostowania niezaufanych dodatków plug-in, wyjątki niegroźne może być wspólne, i może być zbyt trudne do ręcznie obserwować je wszystkie. W takich przypadkach można obsługiwać <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType> zdarzeń. <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType> Wystąpienie, które jest przekazywane do programu obsługi można zapobiec niezaobserwowany wyjątek propagowanie do łącząca wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
