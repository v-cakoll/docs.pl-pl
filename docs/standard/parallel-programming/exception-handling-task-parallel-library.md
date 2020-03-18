---
title: Obsługa wyjątków (biblioteka równoległa zadań)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, exceptions
ms.assetid: beb51e50-9061-4d3d-908c-56a4f7c2e8c1
ms.openlocfilehash: 12777a5f34b8aadcc80977b8796fc2cd53c626a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134250"
---
# <a name="exception-handling-task-parallel-library"></a>Obsługa wyjątków (biblioteka równoległa zadań)

Nieobsługiwane wyjątki, które są generowane przez kod użytkownika, który jest uruchomiony wewnątrz zadania są propagowane z powrotem do wątku wywołującego, z wyjątkiem niektórych scenariuszy, które są opisane w dalszej części tego tematu. Wyjątki są propagowane podczas korzystania z <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> jednej z metod statycznych lub wystąpienia `try` / `catch` i obsługiwać je przez załączanie wywołania w instrukcji. Jeśli zadanie jest elementem nadrzędnym dołączonych zadań podrzędnych lub jeśli oczekujesz na wiele zadań, może zostać zgłoszonych wiele wyjątków.

Aby propagować wszystkie wyjątki z powrotem do wątku wywołującego, infrastruktura zadania owija je w wystąpieniu. <xref:System.AggregateException> Wyjątek <xref:System.AggregateException> ma <xref:System.AggregateException.InnerExceptions%2A> właściwość, która może być wyliczona do zbadania wszystkich oryginalnych wyjątków, które zostały wygenerowane i doobsługi (lub nie doobsługi) każdy z nich indywidualnie. Można również obsługiwać oryginalne wyjątki <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> za pomocą metody.

Nawet jeśli tylko jeden wyjątek jest generowany, <xref:System.AggregateException> nadal jest opakowany w wyjątek, jak pokazano w poniższym przykładzie.

[!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
[!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]

Można uniknąć nieobsługiwane wyjątek po prostu <xref:System.AggregateException> połowu i nie obserwując żadnego z wyjątków wewnętrznych. Jednak zaleca się, aby nie robić tego, ponieważ jest <xref:System.Exception> analogiczny do przechwytywania typu podstawowego w scenariuszach nierównoległych. Aby przechwycić wyjątek bez podejmowania określonych działań, aby odzyskać z niego może opuścić program w stanie nieokreślony.

Jeśli nie chcesz wywołać <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodę czekać na zakończenie zadania, można również <xref:System.AggregateException> pobrać wyjątek z <xref:System.Threading.Tasks.Task.Exception%2A> właściwości zadania, jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji, zobacz [obserwując wyjątki przy użyciu Task.Exception właściwości](#observing-exceptions-by-using-the-taskexception-property) sekcji w tym temacie.

[!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
[!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]

Jeśli nie czekać na zadanie, które propaguje <xref:System.Threading.Tasks.Task.Exception%2A> wyjątek lub dostęp do jego właściwości, wyjątek jest eskalowany zgodnie z zasadami wyjątków .NET, gdy zadanie jest zbierane bezużyteczno.

Gdy wyjątki mogą bąbelkować z powrotem do wątku łączącego, jest możliwe, że zadanie może kontynuować przetwarzanie niektórych elementów po wyłączeniu wyjątku.

> [!NOTE]
> Gdy opcja "Tylko mój kod" jest włączona, visual studio w niektórych przypadkach zostanie przerwana w wierszu, który zgłasza wyjątek i wyświetli komunikat o błędzie z komunikatem "wyjątek nie jest obsługiwany przez kod użytkownika". Ten błąd jest niegroźny. Można nacisnąć klawisz F5, aby kontynuować i zobaczyć zachowanie obsługi wyjątków, który został pokazany w tych przykładach. Aby zapobiec przerywaniu pierwszego błędu przez program Visual Studio, wystarczy odznaczyć pole wyboru **Włącz tylko mój kod** w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.

## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Dołączone zadania podrzędne i zagnieżdżone agregowane wyjątki

Jeśli zadanie ma dołączone zadanie podrzędne, które zgłasza wyjątek, <xref:System.AggregateException> ten wyjątek jest opakowany w, zanim zostanie <xref:System.AggregateException> rozpropagowany do zadania nadrzędnego, które otacza ten wyjątek samodzielnie, zanim propaguje go z powrotem do wątku wywołującego. W takich przypadkach <xref:System.AggregateException.InnerExceptions%2A> właściwość <xref:System.AggregateException> wyjątku, który <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>jest <xref:System.Threading.Tasks.Task.WaitAny%2A>przechwycony w , , lub <xref:System.Threading.Tasks.Task.WaitAll%2A> metoda zawiera jedno lub więcej <xref:System.AggregateException> wystąpień, a nie oryginalne wyjątki, które spowodowały błąd. Aby uniknąć konieczności iterate <xref:System.AggregateException> nad zagnieżdżonych wyjątków, można użyć <xref:System.AggregateException.Flatten%2A> metody, aby usunąć wszystkie wyjątki zagnieżdżone, <xref:System.AggregateException> tak aby <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> właściwość zawiera oryginalne wyjątki. W poniższym przykładzie <xref:System.AggregateException> zagnieżdżone wystąpienia są spłaszczane i obsługiwane w jednej pętli.

[!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
[!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]

Można również użyć <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> metody, aby ponownie zgłosić <xref:System.AggregateException> wyjątki wewnętrzne z wielu <xref:System.AggregateException> wystąpień generowanych przez wiele zadań w jednym wystąpieniu, jak pokazano w poniższym przykładzie.

[!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
[!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]

## <a name="exceptions-from-detached-child-tasks"></a>Wyjątki od odłączonych zadań podrzędnych

Domyślnie zadania podrzędne są tworzone jako odłączone. Wyjątki od odłączonych zadań muszą być obsługiwane lub rethrown w bezpośrednim zadanie nadrzędne; nie są propagowane z powrotem do wątku wywołującego w taki sam sposób, jak dołączone zadania podrzędne propagowane z powrotem. Najwyższej klasy nadrzędnego można ręcznie ponownie zgłosić wyjątek od odłączony <xref:System.AggregateException> element podrzędny, aby spowodować, że mają być zawinięte w i propagowane z powrotem do wątku wywołującego.

[!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
[!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]

Nawet jeśli używasz kontynuacji obserwować wyjątek w zadaniu podrzędnym, wyjątek nadal muszą być przestrzegane przez zadanie nadrzędne.

## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Wyjątki wskazujące na anulowanie współpracy

Gdy kod użytkownika w zadaniu odpowiada na żądanie anulowania, <xref:System.OperationCanceledException> prawidłową procedurą jest zgłoszenie przekazywania w tokenie anulowania, na którym zostało przekazane żądanie. Przed próbą propagacji wyjątku, wystąpienie zadania porównuje token w wyjątku do tego, który został przekazany do niego podczas jego tworzenia. Jeśli są takie same, zadanie <xref:System.Threading.Tasks.TaskCanceledException> propaguje <xref:System.AggregateException>zawinięte w , i może być widoczne, gdy wewnętrzne wyjątki są badane. Jednak jeśli wątek wywołujący nie oczekuje na zadanie, ten konkretny wyjątek nie będzie propagowany. Aby uzyskać więcej informacji, zobacz [Anulowanie zadań](../../../docs/standard/parallel-programming/task-cancellation.md).

[!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
[!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]

## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>Używanie metody obsługi do filtrowania wyjątków wewnętrznych

Można użyć <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metody do filtrowania wyjątków, które można traktować jako "obsługiwane" bez użycia dalszej logiki. W pełnomocnika użytkownika, który jest <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> dostarczany do metody, można <xref:System.Exception.Message%2A> sprawdzić typ wyjątku, jego właściwość lub wszelkie inne informacje o nim, które pozwolą Ci określić, czy jest niegroźny. Wszelkie wyjątki, dla których `false` delegat zwraca są <xref:System.AggregateException> rethrown <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> w nowym wystąpieniu natychmiast po zwraca metody.

Poniższy przykład jest funkcjonalnie odpowiednik pierwszego przykładu w tym temacie, <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> który sprawdza każdy wyjątek w kolekcji.  Zamiast tego ten program <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> obsługi wyjątków wywołuje obiekt metody dla każdego `CustomException` wyjątku i tylko ponownie zgłasza wyjątki, które nie są wystąpieniami.

[!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
[!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]

Poniżej przedstawiono bardziej kompletny przykład, <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> który używa metody, <xref:System.UnauthorizedAccessException> aby zapewnić specjalną obsługę dla wyjątku podczas wyliczania plików.

[!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
[!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]

## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Obserwowanie wyjątków przy użyciu Task.Exception właściwości

Jeśli zadanie zakończy się <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> w <xref:System.Threading.Tasks.Task.Exception%2A> stanie, jego właściwość można zbadać, aby odkryć, który określony wyjątek spowodował błąd. Dobrym sposobem obserwowania <xref:System.Threading.Tasks.Task.Exception%2A> właściwości jest użycie kontynuacji, która jest uruchamiana tylko wtedy, gdy błędy poprzedzającego zadania, jak pokazano w poniższym przykładzie.

[!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
[!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]

W rzeczywistej aplikacji delegat kontynuacji może rejestrować szczegółowe informacje o wyjątku i ewentualnie spawn nowych zadań, aby odzyskać z wyjątku.

## <a name="unobservedtaskexception-event"></a>Zdarzenie Nieobserwowane wyjątek zadania

W niektórych scenariuszach, takich jak podczas hostowania niezaufanych dodatków plug-in, niegroźne wyjątki mogą być typowe i może być zbyt trudne do ręcznego obserwowania ich wszystkich. W takich przypadkach można <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType> obsłużyć zdarzenie. Wystąpienie, <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType> które jest przekazywane do programu obsługi może służyć do zapobiegania nieobserwowanywyjątek jest propagowany z powrotem do wątku łączenia.

## <a name="see-also"></a>Zobacz też

- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
