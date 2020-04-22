---
title: Obsługa wyjątków (biblioteka równoległa zadań)
ms.date: 04/20/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, exceptions
ms.assetid: beb51e50-9061-4d3d-908c-56a4f7c2e8c1
ms.openlocfilehash: aa6d4b706eb11921ffd419402bcf4cf059a29b11
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021512"
---
# <a name="exception-handling-task-parallel-library"></a>Obsługa wyjątków (biblioteka równoległa zadań)

Nieobsługiwały wyjątki, które są generowane przez kod użytkownika, który jest uruchomiony wewnątrz zadania są propagowane z powrotem do wątku wywołującego, z wyjątkiem niektórych scenariuszy, które są opisane w dalszej części tego tematu. Wyjątki są propagowane podczas korzystania z jednej <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> z metod statycznych lub instancji i `try` / `catch` obsługiwać je przez załączenie wywołania w instrukcji. Jeśli zadanie jest elementem nadrzędnym dołączonych zadań podrzędnych lub jeśli czekasz na wiele zadań, można zrzucić wiele wyjątków.

Aby propagować wszystkie wyjątki z powrotem do wątku wywołującego, Task infrastruktury zawija je w wystąpieniu. <xref:System.AggregateException> Wyjątek <xref:System.AggregateException> ma <xref:System.AggregateException.InnerExceptions%2A> właściwość, która może być wyliczona do zbadania wszystkich oryginalnych wyjątków, które zostały odrzucone i obsługi (lub nie obsługiwać) każdy z nich indywidualnie. Można również obsługiwać oryginalne wyjątki <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> przy użyciu metody.

Nawet jeśli tylko jeden wyjątek jest zgłaszany, nadal jest zawijany w wyjątku, jak pokazano w poniższym <xref:System.AggregateException> przykładzie.

[!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
[!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]

Można uniknąć nieobsługiwał wyjątek <xref:System.AggregateException> po prostu połowu i nie obserwując żadnego z wewnętrznych wyjątków. Jednak zaleca się, aby nie robić tego, ponieważ jest <xref:System.Exception> analogiczne do połowu typu podstawowego w scenariuszach innych niż równoległe. Aby złapać wyjątek bez podejmowania określonych działań, aby odzyskać z niego można pozostawić program w stanie nieokreślonym.

Jeśli nie chcesz wywołać <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodę czekać na ukończenie zadania, można również <xref:System.AggregateException> pobrać wyjątek <xref:System.Threading.Tasks.Task.Exception%2A> z właściwości zadania, jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji, zobacz [obserwowanie wyjątków przy użyciu Task.Exception sekcji właściwości](#observing-exceptions-by-using-the-taskexception-property) w tym temacie.

[!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
[!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]

Jeśli nie czekasz na zadanie, które propaguje wyjątek lub uzyskać dostęp do jego <xref:System.Threading.Tasks.Task.Exception%2A> właściwości, wyjątek jest eskalowany zgodnie z zasadami wyjątków .NET, gdy zadanie jest zbierane z odpadami.

Gdy wyjątki są dozwolone do bańki z powrotem do wątku łączącego, jest możliwe, że zadanie może kontynuować przetwarzanie niektórych elementów po wyjątek jest wywoływana.

> [!NOTE]
> Gdy "Tylko mój kod" jest włączona, Visual Studio w niektórych przypadkach zostanie przerwane w wierszu, który zgłasza wyjątek i wyświetlić komunikat o błędzie, który mówi "wyjątek nie obsługiwane przez kod użytkownika." Ten błąd jest łagodny. Można nacisnąć klawisz F5, aby kontynuować i wyświetlić zachowanie obsługi wyjątków, które jest pokazane w tych przykładach. Aby zapobiec przerywaniu pierwszego błędu w programie Visual Studio, po prostu wyczyść **zaznaczenie** pola wyboru Włącz tylko mój kod w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.

## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Dołączone zadania podrzędne i zagnieżdżone zagregowane zagregowane wyjątkowe

Jeśli zadanie ma dołączone zadanie podrzędne, które zgłasza wyjątek, <xref:System.AggregateException> ten wyjątek jest zawijany w przed jest propagowany do zadania nadrzędnego, który zawija ten wyjątek w swoim własnym, <xref:System.AggregateException> zanim propaguje go z powrotem do wątku wywołującego. W takich przypadkach <xref:System.AggregateException.InnerExceptions%2A> właściwość <xref:System.AggregateException> wyjątku, który <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WaitAny%2A>jest <xref:System.Threading.Tasks.Task.WaitAll%2A> złowionych w <xref:System.AggregateException> , lub metoda zawiera jedno lub więcej wystąpień, a nie oryginalne wyjątki, które spowodowały błąd. Aby uniknąć konieczności iteracji <xref:System.AggregateException> za pomocą wyjątków <xref:System.AggregateException.Flatten%2A> zagnieżdżonych, <xref:System.AggregateException> można użyć metody, aby usunąć wszystkie zagnieżdżone wyjątki, tak aby <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> właściwość zawiera oryginalne wyjątki. W poniższym przykładzie <xref:System.AggregateException> zagnieżdżone wystąpienia są spłaszczone i obsługiwane w jednej pętli.

[!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
[!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]

Można również użyć <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> metody, aby ponownie wywrzeć wewnętrzne wyjątki z wielu <xref:System.AggregateException> wystąpień generowanych przez wiele zadań w jednym <xref:System.AggregateException> wystąpieniu, jak pokazano w poniższym przykładzie.

[!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
[!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]

## <a name="exceptions-from-detached-child-tasks"></a>Wyjątki od odłączonych zadań podrzędnych

Domyślnie zadania podrzędne są tworzone jako odłączone. Wyjątki zgłaszane z odłączonych zadań muszą być obsługiwane lub rethrown w bezpośrednim zadaniu nadrzędnym; nie są one propagowane z powrotem do wątku wywołującego w taki sam sposób, jak dołączone zadania podrzędne propagowane z powrotem. Najwyższy nadrzędny można ręcznie ponownie wyzwolić wyjątek od odłączonego <xref:System.AggregateException> dziecka, aby spowodować, że mają być zawinięte w i propagowane z powrotem do wątku wywołującego.

[!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
[!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]

Nawet jeśli używasz kontynuacji do obserwowania wyjątku w zadaniu podrzędnym, wyjątek nadal musi być przestrzegany przez zadanie nadrzędne.

## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Wyjątki wskazujące na anulowanie współpracy

Gdy kod użytkownika w zadaniu odpowiada na żądanie anulowania, <xref:System.OperationCanceledException> prawidłową procedurą jest zgłaszanie przekazywania w tokenie anulowania, na którym zostało przekazane żądanie. Przed próbą propagacji wyjątku, wystąpienie zadania porównuje token w wyjątku do tego, który został przekazany do niego podczas jego tworzenia. Jeśli są one takie same, zadanie <xref:System.Threading.Tasks.TaskCanceledException> propaguje <xref:System.AggregateException>zawinięte w , i można go zobaczyć, gdy wewnętrzne wyjątki są badane. Jednak jeśli wątek wywołujący nie czeka na zadanie, ten konkretny wyjątek nie będzie propagowany. Aby uzyskać więcej informacji, zobacz [Anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md).

[!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
[!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]

## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>Używanie metody dojścia do filtrowania wyjątków wewnętrznych

Można użyć <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metody, aby odfiltrować wyjątki, które można traktować jako "obsługiwane" bez użycia dalszej logiki. W delegatu użytkownika, który <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> jest dostarczany do metody, <xref:System.Exception.Message%2A> można sprawdzić typ wyjątku, jego właściwości lub inne informacje na jego temat, które pozwolą określić, czy jest łagodny. Wszelkie wyjątki, dla `false` których zwraca delegata są <xref:System.AggregateException> rethrown w nowym wystąpieniu <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> natychmiast po zwraca metodę.

Poniższy przykład jest funkcjonalnie równoważne pierwszy przykład w tym <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> temacie, który bada każdy wyjątek w kolekcji.  Zamiast tego ten program <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> obsługi wyjątków wywołuje obiekt metody dla każdego wyjątku `CustomException` i tylko ponownie wydnieje wyjątki, które nie są wystąpieniami.

[!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
[!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]

Poniżej przedstawiono bardziej kompletny przykład, który używa <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metody, aby zapewnić specjalną obsługę <xref:System.UnauthorizedAccessException> wyjątku podczas wyliczania plików.

[!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
[!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]

## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Przestrzeganie wyjątków przy użyciu właściwości Task.Exception

Jeśli zadanie zostanie ukończone <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> w <xref:System.Threading.Tasks.Task.Exception%2A> stanie, jego właściwość można zbadać, aby odkryć, który wyjątek spowodował błąd. Dobrym sposobem, aby <xref:System.Threading.Tasks.Task.Exception%2A> obserwować właściwość jest użycie kontynuacji, która jest uruchamiana tylko wtedy, gdy błędy zadania poprzedza, jak pokazano w poniższym przykładzie.

[!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
[!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]

W znaczącej aplikacji delegat kontynuacji można rejestrować szczegółowe informacje o wyjątku i ewentualnie spawn nowych zadań do odzyskania od wyjątku. Jeśli zadanie zakaże, następujące wyrażenia zgłaszają wyjątek:

- `await task`
- `task.Wait()`
- `task.Result`
- `task.GetAwaiter().GetResult()`

Użyj [`try-catch`](../../csharp/language-reference/keywords/try-catch.md) instrukcji do obsługi i obserwować wyjątki zgłoszonych. Alternatywnie należy przestrzegać wyjątku, <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> uzyskując dostęp do właściwości.

## <a name="unobservedtaskexception-event"></a>Zdarzenie UnobservedTaskException

W niektórych scenariuszach, takich jak podczas hostowania niezaufanych wtyczek, łagodne wyjątki mogą być typowe i może być zbyt trudne do ręcznego obserwowania ich wszystkich. W takich przypadkach można <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType> obsłużyć zdarzenie. Wystąpienie, <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType> które jest przekazywane do programu obsługi może służyć do zapobiegania niezaobserwowany wyjątek z propagacji z powrotem do wątku łączącego.

## <a name="see-also"></a>Zobacz też

- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
