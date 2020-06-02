---
title: Obsługa wyjątków (Biblioteka zadań równoległych)
ms.date: 04/20/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, exceptions
ms.assetid: beb51e50-9061-4d3d-908c-56a4f7c2e8c1
ms.openlocfilehash: 674abcfe4477e14295f131e766a48422779391de
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290048"
---
# <a name="exception-handling-task-parallel-library"></a>Obsługa wyjątków (Biblioteka zadań równoległych)

Nieobsłużone wyjątki, które są generowane przez kod użytkownika, który działa wewnątrz zadania są propagowane z powrotem do wątku wywołującego, z wyjątkiem określonych scenariuszy opisanych w dalszej części tego tematu. Wyjątki są propagowane w przypadku używania jednej z metod statycznych lub wystąpień <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> i są obsługiwane przez załączanie wywołania w `try` / `catch` instrukcji. Jeśli zadanie jest elementem nadrzędnym dołączonych zadań podrzędnych lub jeśli oczekujesz na wiele zadań, może zostać zgłoszonych wiele wyjątków.

Aby propagować wszystkie wyjątki z powrotem do wątku wywołującego, infrastruktura zadań zawija je w <xref:System.AggregateException> wystąpieniu. <xref:System.AggregateException>Wyjątek ma <xref:System.AggregateException.InnerExceptions%2A> Właściwość, którą można wyliczyć, aby przeanalizować wszystkie pierwotne wyjątki, które zostały zgłoszone, i dojście (lub nie obsłuży) osobno dla każdego z nich. Można także obsłużyć pierwotne wyjątki przy użyciu <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metody.

Nawet w przypadku zgłoszenia tylko jednego wyjątku jest on nadal opakowany w <xref:System.AggregateException> wyjątek, jak pokazano w poniższym przykładzie.

[!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
[!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]

Można uniknąć nieobsłużonego wyjątku poprzez jedynie przechwycenie <xref:System.AggregateException> i nieprzestrzeganie któregokolwiek z wyjątków wewnętrznych. Nie zaleca się jednak, aby to zrobić, ponieważ jest to analogiczne do przechwytywania <xref:System.Exception> typu podstawowego w scenariuszach nierównoległych. Aby przechwytywać wyjątek bez podejmowania określonych działań do odzyskania z niego, może to spowodować nieokreślony stan programu.

Jeśli nie chcesz wywoływać <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metody w celu oczekiwania na ukończenie zadania, możesz również pobrać <xref:System.AggregateException> wyjątek z <xref:System.Threading.Tasks.Task.Exception%2A> właściwości zadania, jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji, zobacz sekcję [obserwowanie wyjątków za pomocą właściwości Task. Exception](#observing-exceptions-by-using-the-taskexception-property) w tym temacie.

[!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
[!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]

Jeśli użytkownik nie czeka na zadanie, które propaguje wyjątek lub uzyskuje dostęp do jego <xref:System.Threading.Tasks.Task.Exception%2A> właściwości, wyjątek zostanie przekazany zgodnie z zasadami wyjątku platformy .NET, gdy zadanie jest zbierane jako elementy bezużyteczne.

Gdy wyjątki mogą być rzutowane z powrotem do wątku sprzęgania, istnieje możliwość, że zadanie może nadal przetwarzać niektóre elementy po wystąpieniu wyjątku.

> [!NOTE]
> Po włączeniu "Tylko mój kod" program Visual Studio będzie przerywał pracę w wierszu, który zgłosi wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika". Ten błąd jest niegroźny. Możesz nacisnąć klawisz F5, aby kontynuować i zobaczyć zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach. Aby zapobiec utracie przez program Visual Studio pierwszego błędu, po prostu usuń zaznaczenie pola wyboru **włącz tylko mój kod** w obszarze **Narzędzia, opcje, debugowanie, ogólne**.

## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Dołączone zadania podrzędne i zagnieżdżone AggregateExceptions

Jeśli zadanie ma dołączone zadanie podrzędne, które zgłasza wyjątek, ten wyjątek jest opakowany <xref:System.AggregateException> przed propagacją do zadania nadrzędnego, co spowoduje, że ten wyjątek jest zawijany przed <xref:System.AggregateException> propagacją z powrotem do wątku wywołującego. W takich przypadkach <xref:System.AggregateException.InnerExceptions%2A> Właściwość <xref:System.AggregateException> wyjątku, która jest przechwytywana w <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> , <xref:System.Threading.Tasks.Task.WaitAny%2A> , lub, <xref:System.Threading.Tasks.Task.WaitAll%2A> zawiera co najmniej jedno <xref:System.AggregateException> wystąpienie, a nie oryginalne wyjątki, które spowodowały błąd. Aby uniknąć konieczności iteracji w przypadku wyjątków zagnieżdżonych <xref:System.AggregateException> , można użyć <xref:System.AggregateException.Flatten%2A> metody do usunięcia wszystkich zagnieżdżonych <xref:System.AggregateException> wyjątków, aby <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> Właściwość zawierała oryginalne wyjątki. W poniższym przykładzie zagnieżdżone <xref:System.AggregateException> wystąpienia są spłaszczone i obsługiwane w zaledwie jednej pętli.

[!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
[!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]

Można również użyć metody, <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> Aby ponownie zgłosić wewnętrzne wyjątki z wielu <xref:System.AggregateException> wystąpień zgłoszonych przez wiele zadań w pojedynczym <xref:System.AggregateException> wystąpieniu, jak pokazano w poniższym przykładzie.

[!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
[!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]

## <a name="exceptions-from-detached-child-tasks"></a>Wyjątki z odłączonych zadań podrzędnych

Domyślnie zadania podrzędne są tworzone jako odłączone. Wyjątki zgłoszone z odłączonych zadań muszą być obsłużone lub ponownie zgłoszone w bezpośrednim zadaniu nadrzędnym. nie są one propagowane z powrotem do wywołującego wątku w taki sam sposób jak dołączone zadania podrzędne propagowane z powrotem. Element nadrzędny najwyższego poziomu może ręcznie ponownie zgłosić wyjątek z odłączonego elementu podrzędnego, aby spowodować jego zawinięcie <xref:System.AggregateException> i propagację z powrotem do wątku wywołującego.

[!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
[!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]

Nawet w przypadku używania kontynuacji do obserwowania wyjątku w zadaniu podrzędnym wyjątek nadal musi być zaobserwowany przez zadanie nadrzędne.

## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Wyjątki wskazujące na odwołanie do spółdzielni

Jeśli kod użytkownika w zadaniu odpowiada na żądanie anulowania, poprawna procedura polega na wyrzucaniu <xref:System.OperationCanceledException> w tokenie anulowania, na którym żądanie zostało przekazane. Przed próbą propagowania wyjątku wystąpienie zadania porównuje token w wyjątku z tym, który został przesłany do niego podczas jego tworzenia. Jeśli są takie same, zadanie propaguje <xref:System.Threading.Tasks.TaskCanceledException> opakowane w <xref:System.AggregateException> i może być widoczne po zbadaniu wewnętrznych wyjątków. Jeśli jednak wątek wywołujący nie oczekuje na zadanie, ten konkretny wyjątek nie zostanie propagowany. Aby uzyskać więcej informacji, zobacz [Anulowanie zadania](task-cancellation.md).

[!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
[!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]

## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>Używanie metody obsługi do filtrowania wyjątków wewnętrznych

Możesz użyć metody, <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> Aby odfiltrować wyjątki, które można traktować jako "obsłużone" bez użycia żadnej dalszej logiki. W delegatze użytkownika, który jest dostarczany do <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> metody, można sprawdzić typ wyjątku, jego <xref:System.Exception.Message%2A> Właściwość lub inne informacje o nim, które pozwolą określić, czy jest to niegroźne. Wszelkie wyjątki, dla których zwracane są zwroty delegatów, `false` są ponownie zgłaszane w nowym <xref:System.AggregateException> wystąpieniu natychmiast po <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> powrocie metody.

Poniższy przykład jest funkcjonalnie odpowiednikiem pierwszego przykładu w tym temacie, który bada każdy wyjątek w <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> kolekcji.  Zamiast tego ten program obsługi wyjątków wywołuje <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> obiekt metody dla każdego wyjątku i ponownie generuje wyjątki, które nie są `CustomException` wystąpieniami.

[!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
[!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]

Poniżej przedstawiono bardziej kompletny przykład wykorzystujący <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metodę w celu zapewnienia specjalnej obsługi <xref:System.UnauthorizedAccessException> wyjątku podczas wyliczania plików.

[!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
[!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]

## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Obserwowanie wyjątków przy użyciu właściwości Task. Exception

Jeśli zadanie zostanie ukończone w <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> stanie, jego <xref:System.Threading.Tasks.Task.Exception%2A> Właściwość może zostać zbadana w celu odnalezienia, który konkretny wyjątek spowodował błąd. Dobrym sposobem obserwowania <xref:System.Threading.Tasks.Task.Exception%2A> właściwości jest użycie kontynuacji, która jest uruchamiana tylko wtedy, gdy błędy zadań poprzedzających, jak pokazano w poniższym przykładzie.

[!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
[!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]

W zrozumiałej aplikacji delegat kontynuacji może rejestrować szczegółowe informacje o wyjątku i ewentualnie zduplikować nowe zadania w celu odzyskania z tego wyjątku. Jeśli wystąpią błędy zadań, następujące wyrażenia zwracają wyjątek:

- `await task`
- `task.Wait()`
- `task.Result`
- `task.GetAwaiter().GetResult()`

Użyj [`try-catch`](../../csharp/language-reference/keywords/try-catch.md) instrukcji, aby obsłużyć i obserwować zgłoszone wyjątki. Alternatywnie, zaobserwuj wyjątek, uzyskując dostęp do <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> właściwości.

## <a name="unobservedtaskexception-event"></a>Zdarzenie UnobservedTaskException

W niektórych scenariuszach, takich jak w przypadku hostowania niezaufanych wtyczek, niegroźne wyjątki mogą być często używane, a ich ręczne obserwowanie może być utrudnione. W takich przypadkach można obsłużyć <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType> zdarzenie. <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType>Wystąpienie przekazane do procedury obsługi może służyć do uniemożliwienia propagowania niezauważalnego wyjątku z powrotem do wątku przyłączania.

## <a name="see-also"></a>Zobacz także

- [Biblioteka zadań równoległych (TPL)](task-parallel-library-tpl.md)
