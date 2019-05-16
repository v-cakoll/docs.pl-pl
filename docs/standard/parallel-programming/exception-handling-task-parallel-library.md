---
title: Obsługa wyjątków (Biblioteka zadań równoległych)
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
ms.openlocfilehash: a3e602057bfd2dea15887daee9058b12f26992f2
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639044"
---
# <a name="exception-handling-task-parallel-library"></a>Obsługa wyjątków (Biblioteka zadań równoległych)

Nieobsługiwane wyjątki wyrzucane przez kod użytkownika, który działa wewnątrz zadaniem jest propagowany z powrotem do wywołanego wątku, z wyjątkiem w niektórych scenariuszach, które są opisane w dalszej części tego tematu. Wyjątki są propagowane podczas korzystania z jednego statycznego lub wystąpienie <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metody i można je obsłużyć, umieszczając wywołanie `try` / `catch` instrukcji. Czy zadanie jest elementem nadrzędnym dołączonych zadań podrzędnych, czy użytkownik czeka na wiele zadań, wiele wyjątków może zostać wygenerowany.

Propagacja wszystkie wyjątki z powrotem do wątku wywołującego, infrastruktury zadań opakowywanie ich w <xref:System.AggregateException> wystąpienia. <xref:System.AggregateException> Wyjątek <xref:System.AggregateException.InnerExceptions%2A> właściwości, które mogą być wyliczane zbadanie wszystkich oryginalnego wyjątki, które zostały zgłoszone i obsługiwać (lub nie obsługiwać) każdej z nich osobno. Może również obsługiwać wyjątki, oryginalnym przy użyciu <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metody.

Nawet wtedy, gdy tylko jeden wyjątek, nadal jest opakowana w <xref:System.AggregateException> wyjątku, co ilustruje poniższy przykład.

[!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
[!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]

Wystąpił nieobsługiwany wyjątek można uniknąć, po prostu Przechwytywanie <xref:System.AggregateException> i nie obserwowania wszystkich wyjątków wewnętrznych. Firma Microsoft zaleca jednak nie tej czynności, ponieważ jest ono odpowiednikiem przechwytywanie, podstawą <xref:System.Exception> typu w scenariuszach nierównoległy. Aby przechwytywać wyjątek, bez konieczności przełączania konkretne akcje, aby odzyskać z niego można pozostawić program w stanie nieokreślonym.

Jeśli nie chcesz wywołać <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodę, aby czekać na ukończenie zadania podrzędnego, możesz również pobrać <xref:System.AggregateException> wyjątek z zadania podrzędnego <xref:System.Threading.Tasks.Task.Exception%2A> właściwości, co ilustruje poniższy przykład. Aby uzyskać więcej informacji, zobacz [monitorowanie wyjątków za pomocą właściwości Task.Exception](#observing-exceptions-by-using-the-taskexception-property) w tym temacie.

[!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
[!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]

Jeśli użytkownik nie zaczeka na zadania, które propaguje wyjątek lub dostęp do jego <xref:System.Threading.Tasks.Task.Exception%2A> eskalacji właściwości wyjątku zgodnie z zasadami wyjątek .NET, gdy zadanie będzie jesdnostką zbierającą śmieci.

Wyjątki mogą pojawiać się z powrotem w sąsiednim wątku, jest to możliwe, że zadanie będzie kontynuować przetwarzanie niektórych elementy po jest wyjątek.

> [!NOTE]
> Po włączeniu "Tylko mój kod" Visual Studio, w niektórych przypadkach przerwania w wierszu, który zgłasza wyjątek i wyświetlić komunikat o błędzie informujący, że "wyjątek nie obsłużony przez kod użytkownika." Ten błąd jest nieszkodliwe. Można nacisnąć klawisz F5, aby kontynuować, a także sprawdzić sposób obsługi wyjątków, przedstawionej w tych przykładach. Aby zapobiec istotne w przypadku pierwszego błędu programu Visual Studio, po prostu usuń zaznaczenie pola wyboru **Włącz tylko mój kod** pole wyboru w obszarze **narzędzia, opcje, debugowanie, ogólne**.

## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Dołączonych zadań podrzędnych i AggregateExceptions zagnieżdżonych

Jeśli zadanie ma zadanie dołączonych zadań podrzędnych, które zgłasza wyjątek, ten wyjątek jest opakowana w <xref:System.AggregateException> przed jest propagowany do zadania nadrzędnego, który otacza tego wyjątku w ramach ich własnej <xref:System.AggregateException> przed propaguje je do wątku wywołującego. W takich przypadkach <xref:System.AggregateException.InnerExceptions%2A> właściwość <xref:System.AggregateException> wyjątek, który zostanie przechwycony na <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAny%2A>, lub <xref:System.Threading.Tasks.Task.WaitAll%2A> metody zawiera jeden lub więcej <xref:System.AggregateException> wystąpień nie oryginalnego wyjątki, które spowodowały błąd. Aby uniknąć konieczności iteracja zagnieżdżone <xref:System.AggregateException> wyjątki, można użyć <xref:System.AggregateException.Flatten%2A> metodę, aby usunąć wszystkie zagnieżdżonego <xref:System.AggregateException> wyjątki, tak, aby <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> właściwość zawiera oryginalny wyjątków. W poniższym przykładzie zagnieżdżone <xref:System.AggregateException> wystąpienia są spłaszczone i obsługiwane w tylko jednej pętli.

[!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
[!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]

Można również użyć <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> metody, aby można było ponownie wewnętrznych wyjątków z wielu <xref:System.AggregateException> wystąpień zgłoszony przez wiele zadań w ramach pojedynczej <xref:System.AggregateException> wystąpienia, co ilustruje poniższy przykład.

[!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
[!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]

## <a name="exceptions-from-detached-child-tasks"></a>Wyjątki od odłączonych zadań podrzędnych

Domyślnie zadania podrzędne są tworzone jako odłączona. Wyjątków zgłaszanych przez odłączonych zadań, które muszą być obsługiwane lub zgłaszany ponownie w zadania nadrzędnym natychmiastowe; nie są propagowane do wątku wywołującego w ten sam sposób jak dołączonych zadań podrzędnych propagowany z powrotem. Najwyższego poziomu nadrzędny można ręcznie wyjątki z odłączony podrzędnych, aby spowodować, że otoczona <xref:System.AggregateException> i propagowany z powrotem do wątku wywołującego.

[!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
[!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]

Nawet wtedy, gdy Użyj kontynuacji, aby obserwować wyjątek zadania podrzędnego, wyjątek nadal muszą być spełnione przez zadanie nadrzędne.

## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Wyjątki, które wskazują kooperatywne anulowanie

Gdy kod użytkownika w zadaniu odpowie na żądanie anulowania, ma poprawne procedura throw <xref:System.OperationCanceledException> przekazując token anulowania, na którym żądanie zostało przekazane. Zanim próbuje propagowanie wyjątku wystąpienia zadania porównuje token wyjątku do tego, który został przekazany do niego podczas jej tworzenia. Jeśli są takie same zadania propaguje <xref:System.Threading.Tasks.TaskCanceledException> otoczona <xref:System.AggregateException>, i może być widoczny, gdy są sprawdzane wyjątków wewnętrznych. Jednak jeśli wątek wywołujący nie oczekuje na zadanie, ten wyjątek nie zostaną zastosowane. Aby uzyskać więcej informacji, zobacz [anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md).

[!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
[!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]

## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>Za pomocą metody dojścia do filtrowania wewnętrznych wyjątków

Możesz użyć <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metodę, aby filtrować bez przy użyciu dowolnej logiki dalsze wyjątki, które można traktować jako "obsługiwane". W delegacie użytkownika, która jest dostarczana do <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> metoda, typ wyjątku, można sprawdzić jego <xref:System.Exception.Message%2A> właściwości lub inne informacje na jego temat, które pozwalają określić, czy jest nieszkodliwe. Wszelkie wyjątki, które zwraca delegata `false` jest zgłaszany ponownie w nowym <xref:System.AggregateException> natychmiast po wystąpieniu <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metoda zwraca.

Poniższy przykład jest funkcjonalnie równoważny programowi pierwszego przykładu w tym temacie, który sprawdza, czy każdy wyjątek w <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> kolekcji.  Zamiast tego wywołuje program obsługi tego wyjątku <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> obiekt metody dla każdego wyjątku i jedyne ponownie zgłasza wyjątki, które nie są `CustomException` wystąpień.

[!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
[!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]

Poniżej przedstawiono bardziej szczegółowy przykład, który używa <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metody w celu zapewnienia specjalna obsługa <xref:System.UnauthorizedAccessException> wyjątek podczas wyliczania plików.

[!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
[!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]

## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Monitorowanie wyjątków za pomocą właściwości Task.Exception

Jeśli zadanie zakończy się w <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> stanu, jego <xref:System.Threading.Tasks.Task.Exception%2A> właściwości można zbadać, aby dowiedzieć się, które określony wyjątek spowodował. Dobrym sposobem, aby obserwować <xref:System.Threading.Tasks.Task.Exception%2A> właściwość ma na celu to kontynuacja, która jest uruchamiana tylko wtedy, gdy zadanie poprzedzające błędów, jak pokazano w poniższym przykładzie.

[!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
[!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]

W rzeczywistej aplikacji delegata kontynuacji może rejestrować szczegółowe informacje o wyjątku i prawdopodobnie zduplikować nowe zadania, aby odzyskać z wyjątkiem.

## <a name="unobservedtaskexception-event"></a>Zdarzenie UnobservedTaskException

W niektórych scenariuszach takich jak hostując niezaufanych dodatków plug-in niegroźne wyjątki mogą być wspólne i może być zbyt trudne do ręcznie Sprawdź je wszystkie. W takich przypadkach można obsługiwać <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType> zdarzeń. <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType> Wystąpienie, które są przekazywane do programu obsługi może służyć do uniemożliwić niewidocznego wyjątek propagowanie powrotem w sąsiednim wątku.

## <a name="see-also"></a>Zobacz także

- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
