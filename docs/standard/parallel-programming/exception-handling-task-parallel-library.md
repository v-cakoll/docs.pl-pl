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
ms.openlocfilehash: 12777a5f34b8aadcc80977b8796fc2cd53c626a8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134250"
---
# <a name="exception-handling-task-parallel-library"></a>Obsługa wyjątków (Biblioteka zadań równoległych)

Nieobsłużone wyjątki, które są generowane przez kod użytkownika, który działa wewnątrz zadania są propagowane z powrotem do wątku wywołującego, z wyjątkiem określonych scenariuszy opisanych w dalszej części tego tematu. Wyjątki są propagowane w przypadku używania jednej z metod statycznych lub <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, a ich obsługa przez załączanie wywołania w instrukcji `try`/`catch`. Jeśli zadanie jest elementem nadrzędnym dołączonych zadań podrzędnych lub jeśli oczekujesz na wiele zadań, może zostać zgłoszonych wiele wyjątków.

Aby propagować wszystkie wyjątki z powrotem do wątku wywołującego, infrastruktura zadań zawija je w wystąpieniu <xref:System.AggregateException>. Wyjątek <xref:System.AggregateException> ma właściwość <xref:System.AggregateException.InnerExceptions%2A>, którą można wyliczyć, aby przeanalizować wszystkie pierwotne wyjątki, które zostały zgłoszone, i dojście (lub nieobsługiwane) osobno. Można także obsłużyć pierwotne wyjątki przy użyciu metody <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType>.

Nawet w przypadku zgłoszenia tylko jednego wyjątku jest on nadal opakowany w wyjątek <xref:System.AggregateException>, jak pokazano w poniższym przykładzie.

[!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
[!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]

Można uniknąć nieobsłużonego wyjątku przez przechwycenie <xref:System.AggregateException> i nieprzestrzeganie żadnego z wyjątków wewnętrznych. Nie zaleca się jednak, aby to zrobić, ponieważ jest to analogiczne do przechwytywania podstawowego typu <xref:System.Exception> w scenariuszach nierównoległych. Aby przechwytywać wyjątek bez podejmowania określonych działań do odzyskania z niego, może to spowodować nieokreślony stan programu.

Jeśli nie chcesz wywoływać metody <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, aby czekać na ukończenie zadania, możesz również pobrać wyjątek <xref:System.AggregateException> z właściwości <xref:System.Threading.Tasks.Task.Exception%2A> zadania, jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji, zobacz sekcję [obserwowanie wyjątków za pomocą właściwości Task. Exception](#observing-exceptions-by-using-the-taskexception-property) w tym temacie.

[!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
[!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]

Jeśli nie poczekasz na zadanie, które propaguje wyjątek, lub uzyskaj dostęp do jego właściwości <xref:System.Threading.Tasks.Task.Exception%2A>, wyjątek zostanie przekazany zgodnie z zasadami wyjątku platformy .NET, gdy zadanie jest zbierane jako elementy bezużyteczne.

Gdy wyjątki mogą być rzutowane z powrotem do wątku sprzęgania, istnieje możliwość, że zadanie może nadal przetwarzać niektóre elementy po wystąpieniu wyjątku.

> [!NOTE]
> Po włączeniu "Tylko mój kod" program Visual Studio będzie przerywał pracę w wierszu, który zgłosi wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika". Ten błąd jest niegroźny. Możesz nacisnąć klawisz F5, aby kontynuować i zobaczyć zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach. Aby zapobiec utracie przez program Visual Studio pierwszego błędu, po prostu usuń zaznaczenie pola wyboru **włącz tylko mój kod** w obszarze **Narzędzia, opcje, debugowanie, ogólne**.

## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Dołączone zadania podrzędne i zagnieżdżone AggregateExceptions

Jeśli zadanie ma dołączone zadanie podrzędne, które zgłasza wyjątek, ten wyjątek jest opakowany w <xref:System.AggregateException> przed propagacją do zadania nadrzędnego, które zawija ten wyjątek we własnym <xref:System.AggregateException> przed jego propagacją do wątku wywołującego. W takich przypadkach Właściwość <xref:System.AggregateException.InnerExceptions%2A> wyjątku <xref:System.AggregateException>, która jest przechwytywana w metodzie <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAny%2A>lub <xref:System.Threading.Tasks.Task.WaitAll%2A>, zawiera co najmniej jedno wystąpienie <xref:System.AggregateException>, a nie oryginalne wyjątki, które spowodowały błąd. Aby uniknąć konieczności iteracji w przypadku zagnieżdżonych wyjątków <xref:System.AggregateException>, można użyć metody <xref:System.AggregateException.Flatten%2A> do usunięcia wszystkich zagnieżdżonych wyjątków <xref:System.AggregateException>, dzięki czemu Właściwość <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> zawiera pierwotne wyjątki. W poniższym przykładzie zagnieżdżone wystąpienia <xref:System.AggregateException> są spłaszczone i obsługiwane w zaledwie jednej pętli.

[!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
[!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]

Można również użyć metody <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType>, aby ponownie zgłosić wewnętrzne wyjątki z wielu wystąpień <xref:System.AggregateException> zgłoszonych przez wiele zadań w jednym wystąpieniu <xref:System.AggregateException>, jak pokazano w poniższym przykładzie.

[!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
[!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]

## <a name="exceptions-from-detached-child-tasks"></a>Wyjątki z odłączonych zadań podrzędnych

Domyślnie zadania podrzędne są tworzone jako odłączone. Wyjątki zgłoszone z odłączonych zadań muszą być obsłużone lub ponownie zgłoszone w bezpośrednim zadaniu nadrzędnym. nie są one propagowane z powrotem do wywołującego wątku w taki sam sposób jak dołączone zadania podrzędne propagowane z powrotem. Element nadrzędny najwyższego poziomu może ręcznie ponownie zgłosić wyjątek z odłączonego elementu podrzędnego, aby spowodować jego zawinięcie do <xref:System.AggregateException> i propagację z powrotem do wątku wywołującego.

[!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
[!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]

Nawet w przypadku używania kontynuacji do obserwowania wyjątku w zadaniu podrzędnym wyjątek nadal musi być zaobserwowany przez zadanie nadrzędne.

## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Wyjątki wskazujące na odwołanie do spółdzielni

W przypadku, gdy kod użytkownika w zadaniu odpowiada na żądanie anulowania, poprawna procedura polega na wyrzucaniu <xref:System.OperationCanceledException> przekazywania w tokenie anulowania, na którym żądanie zostało przekazane. Przed próbą propagowania wyjątku wystąpienie zadania porównuje token w wyjątku z tym, który został przesłany do niego podczas jego tworzenia. Jeśli są one takie same, zadanie propaguje <xref:System.Threading.Tasks.TaskCanceledException> opakowane <xref:System.AggregateException>i może być widoczne po zbadaniu wyjątków wewnętrznych. Jeśli jednak wątek wywołujący nie oczekuje na zadanie, ten konkretny wyjątek nie zostanie propagowany. Aby uzyskać więcej informacji, zobacz [Anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md).

[!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
[!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]

## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>Używanie metody obsługi do filtrowania wyjątków wewnętrznych

Za pomocą metody <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> można odfiltrować wyjątki, które można traktować jako "obsłużone" bez użycia żadnej dalszej logiki. W odniesieniu do obiektu delegowanego użytkownika, który jest dostarczany do metody <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType>, można sprawdzić typ wyjątku, jego właściwość <xref:System.Exception.Message%2A> lub wszelkie inne informacje, które pozwolą określić, czy jest to niegroźne. Wszelkie wyjątki, dla których delegat zwraca `false` są ponownie zgłaszane w nowym wystąpieniu <xref:System.AggregateException> natychmiast po powrocie metody <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType>.

Poniższy przykład jest funkcjonalnie odpowiednikiem pierwszego przykładu w tym temacie, który bada każdy wyjątek w kolekcji <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType>.  Zamiast tego ten program obsługi wyjątków wywołuje obiekt metody <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> dla każdego wyjątku i ponownie generuje wyjątki, które nie są `CustomException` wystąpieniami.

[!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
[!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]

Poniżej przedstawiono bardziej kompletny przykład wykorzystujący metodę <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> do zapewnienia specjalnej obsługi wyjątku <xref:System.UnauthorizedAccessException> podczas wyliczania plików.

[!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
[!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]

## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Obserwowanie wyjątków przy użyciu właściwości Task. Exception

Jeśli zadanie zostanie ukończone w stanie <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType>, jego właściwość <xref:System.Threading.Tasks.Task.Exception%2A> może zostać zbadane w celu odnalezienia konkretnego wyjątku powodującego błąd. Dobrym sposobem obserwowania właściwości <xref:System.Threading.Tasks.Task.Exception%2A> jest użycie kontynuacji, która jest uruchamiana tylko wtedy, gdy błędy zadań poprzedzających, jak pokazano w poniższym przykładzie.

[!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
[!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]

W prawdziwej aplikacji delegat kontynuacji może rejestrować szczegółowe informacje o wyjątku i mogą zostać zduplikowane nowe zadania do odzyskania z powodu wyjątku.

## <a name="unobservedtaskexception-event"></a>Zdarzenie UnobservedTaskException

W niektórych scenariuszach, takich jak w przypadku hostowania niezaufanych wtyczek, niegroźne wyjątki mogą być często używane, a ich ręczne obserwowanie może być utrudnione. W takich przypadkach można obsłużyć zdarzenie <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType>. Wystąpienie <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType> przekazane do procedury obsługi może służyć do uniemożliwienia propagowania niezauważalnego wyjątku z powrotem do wątku przyłączania.

## <a name="see-also"></a>Zobacz także

- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
