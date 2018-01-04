---
title: Implementacja wzorca asynchronicznego opartego na zadaniach
ms.date: 06/14/2017
ms.prod: .net
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: fab6bd41-91bd-44ad-86f9-d8319988aa78
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 238f164fec78fe5e6dae9e7880fabc0a386bf399
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-the-task-based-asynchronous-pattern"></a>Implementacja wzorca asynchronicznego opartego na zadaniach
Oparty na zadaniach asynchronicznej wzorca (TAP) można wdrożyć na trzy sposoby: za pomocą Kompilatory języka C# i Visual Basic w programie Visual Studio, ręcznie lub za pomocą kombinacji metod kompilatora i ręcznie. W poniższych sekcjach omówiono każdej metody szczegółowo. Wzorzec NACIŚNIJ umożliwia implementować zarówno powiązane z obliczeń, jak i I/E-powiązane z operacji asynchronicznych. [Obciążeń](#workloads) sekcji omówiono każdego typu działania.

## <a name="generating-tap-methods"></a>Generowanie wybranie metody

### <a name="using-the-compilers"></a>Przy użyciu kompilatory
Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], dowolnej metody, która ma atrybut `async` — słowo kluczowe (`Async` w języku Visual Basic) jest uznawany za metody asynchronicznej i Kompilatory języka C# i Visual Basic wykonać transformacje niezbędne do wdrożenia metody asynchroniczne, używając NACIŚNIJ. Metody asynchronicznej powinien zwrócić albo <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> lub <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> obiektu. W przypadku drugiego nagłówka, powinien zwrócić treści funkcji `TResult`, i kompilator zapewnia wynik jest udostępnione za pośrednictwem wynikowego obiektu zadania. Podobnie, wszelkie wyjątki, które go nieobsługiwany w treści metody są przekazywane do danych wyjściowych zadania i spowodować wynikowy zadania kończyć się <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> stanu. Wyjątek stanowi, kiedy <xref:System.OperationCanceledException> (lub typu pochodnego) nieobsługiwany umieszczane, w którym to przypadku zadaniu wynikowym kończy się <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stanu.

### <a name="generating-tap-methods-manually"></a>Generowanie metody NACIŚNIJ ręcznie
Może wdrożyć wzorcem NACIŚNIJ ręcznie lepszą kontrolę nad implementacji. Kompilator zależy od uwidaczniać jej w publicznej powierzchni <xref:System.Threading.Tasks?displayProperty=nameWithType> przestrzeni nazw i obsługi typów w <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw. Aby zaimplementować PRZYŁOŻENIU samodzielnie, należy utworzyć <xref:System.Threading.Tasks.TaskCompletionSource%601> obiektu, wykonaj operację asynchroniczną i po jego ukończeniu, należy wywołać <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>, lub <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> metody, lub `Try` wersji jednej z tych metod. Gdy ręcznie zaimplementować metodę NACIŚNIJ zadaniu wynikowym należy wykonać po zakończeniu operacji asynchronicznej reprezentowanego. Na przykład:

[!code-csharp[Conceptual.TAP_Patterns#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#1)]
[!code-vb[Conceptual.TAP_Patterns#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#1)]

### <a name="hybrid-approach"></a>Podejście hybrydowego
 Mogą być przydatne, aby ręcznie zaimplementować wzorzec NACIŚNIJ, ale aby delegować logiki core do wykonania w kompilatorze. Na przykład można użyć metody hybrydowych, gdy chcesz zweryfikować argumenty poza generowane przez kompilator metody asynchronicznej, dzięki czemu można escape wyjątki, aby metody bezpośredniego wywołującego, a nie są dostępne za pośrednictwem <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiektu:

 [!code-csharp[Conceptual.TAP_Patterns#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#2)]
 [!code-vb[Conceptual.TAP_Patterns#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#2)]

 Jest innym przypadku, gdy taki delegowania jest przydatne w przypadku jest implementacja optymalizacji fast-path i chcesz zwracać buforowane zadania.

## <a name="workloads"></a>Obciążeń
Zarówno powiązane z obliczeń, jak i I/E-powiązane z operacji asynchronicznych może wdrożyć jako wybranie metody. Jednak gdy wybranie metody są udostępniane publicznie z biblioteki, powinny one dostępne tylko dla obciążeń, które obejmują operacje I/E-granica (one mogą również obejmować obliczeń, ale nie może być całkowicie obliczeniową). Jeśli metoda jest wyłącznie obliczeń wiązaniem, powinny zostać ujawnione tylko jako synchroniczne implementacji. Kod, który wykorzystuje ona może następnie wybrać, czy powodującą otoczenie wywołania tej metody synchroniczne zadanie odciążania pracy do innego wątku lub osiągnięcie równoległości. A jeśli metoda jest związany z we/wy, powinny zostać ujawnione tylko jako implementacja asynchronicznego.

### <a name="compute-bound-tasks"></a>Zadania powiązane z obliczeń
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Klasy doskonale nadaje się do reprezentujący praktyce intensywne operacje. Domyślnie, jego zalet specjalną obsługę w <xref:System.Threading.ThreadPool> klasy aby zapewnić efektywne wykonanie, a także zapewnia znaczną kontrolę nad tym, kiedy, jak i gdzie wykonywanie obliczeń asynchronicznych.

Może wygenerować zadań powiązanych z obliczeń w następujący sposób:

- W .NET Framework 4, użyj <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metodę, która akceptuje delegata (zazwyczaj <xref:System.Action%601> lub <xref:System.Func%601>) ma być wykonywana w sposób asynchroniczny. Jeśli podasz <xref:System.Action%601> delegować, metoda zwraca <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiekt, który reprezentuje asynchroniczne wykonywanie tego delegata. Jeśli podasz <xref:System.Func%601> delegować, metoda zwraca <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> obiektu. Overloads z <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metoda akceptuje token anulowania (<xref:System.Threading.CancellationToken>), opcje tworzenia zadań (<xref:System.Threading.Tasks.TaskCreationOptions>) i harmonogram zadań (<xref:System.Threading.Tasks.TaskScheduler>), które zapewniają precyzyjną kontrolę nad planowania i wykonywania zadania. Wystąpienia fabryki, przeznaczonego dla bieżącego harmonogramu zadań jest dostępna jako właściwość statyczna (<xref:System.Threading.Tasks.Task.Factory%2A>) z <xref:System.Threading.Tasks.Task> klasy; na przykład: `Task.Factory.StartNew(…)`.

- W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i nowszych wersjach (w tym oprogramowanie .NET Core i .NET Standard), użyj statycznych <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metody w celu szybkiego <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>. Możesz użyć <xref:System.Threading.Tasks.Task.Run%2A> można łatwo uruchomić zadań powiązanych z obliczeń, przeznaczonego dla puli wątków. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i nowszych wersjach, jest to preferowany sposób uruchamiania zadań powiązanych z obliczeń. Użyj `StartNew` bezpośrednio tylko jeśli chcesz bardziej precyzyjną kontrolę nad zadania.

- Użyj konstruktorów `Task` typu lub `Start` metodę, jeśli chcesz wygenerować i Zaplanuj zadanie oddzielnie. Metody publiczne musi zwracać tylko zadania, które zostało już rozpoczęte.

- Użyj przeciążeń <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metody. Ta metoda tworzy nowe zadanie, które jest zaplanowane po zakończeniu inne zadanie. Niektóre <xref:System.Threading.Tasks.Task.ContinueWith%2A> przeciążenia zaakceptować token anulowania, opcje kontynuacji i harmonogram zadań, aby uzyskać lepszą kontrolę nad planowania i wykonywania zadania kontynuacji.

- Użyj <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> metody. Te metody utworzyć nowe zadanie, które jest zaplanowane po zakończeniu wszystkie lub niektóre podane zestaw zadań. Te metody Podaj także przeciążenia do kontrolowania, planowania i wykonywania tych zadań.

W zadań powiązanych z obliczeń system można uniemożliwić uruchomienia zaplanowanego zadania, jeśli odbiera żądanie anulowania, przed rozpoczęciem wykonywania zadania. Działa w taki sposób, jeśli podasz token anulowania (<xref:System.Threading.CancellationToken> obiektu), można przekazać tokenu do asynchronicznego kod, który monitoruje tokenu. Można też podać token do jednej z metod opisanych powyżej takich jak `StartNew` lub `Run` , aby `Task` środowiska uruchomieniowego może także monitorować tokenu.

Rozważmy na przykład metoda asynchroniczna, który renderuje obraz. Treść zadania można sondować token anulowania, dzięki czemu kod może zakończyć wcześniej, jeśli żądanie anulowania podczas renderowania. Ponadto jeśli żądanie anulowania przed rozpoczęciem renderowania, należy operacja renderowania:

[!code-csharp[Conceptual.TAP_Patterns#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#3)]
[!code-vb[Conceptual.TAP_Patterns#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#3)]

Zadań powiązanych z obliczeń kończyć się <xref:System.Threading.Tasks.TaskStatus.Canceled> stan, jeśli wartość true, jest co najmniej jeden z następujących warunków:

- Żądanie anulowania dociera do <xref:System.Threading.CancellationToken> obiektu, który jest dostarczany jako argument do metody tworzenia (na przykład `StartNew` lub `Run`) przed przejścia zadań do <xref:System.Threading.Tasks.TaskStatus.Running> stanu.

- <xref:System.OperationCanceledException> Wyjątków przechodzi nieobsługiwany w treści takie zadania, czy wyjątek zawiera takie same <xref:System.Threading.CancellationToken> przekazanego do zadania, a token zawiera zażądano anulowania.

Jeśli nie jest nieobsługiwany w treści zadania kolejny wyjątek, zadanie kończy się <xref:System.Threading.Tasks.TaskStatus.Faulted> stanu i wszelkie próby oczekiwanie na zadanie lub zostać zgłoszony wyjątek powoduje jego wynik dostępu.

### <a name="io-bound-tasks"></a>Zadania I/E-granica
Aby utworzyć zadanie, które nie powinny być bezpośrednio kopii przez wątek dla całości jego wykonywania, użyj <xref:System.Threading.Tasks.TaskCompletionSource%601> typu. Ten typ przedstawia <xref:System.Threading.Tasks.TaskCompletionSource%601.Task%2A> właściwości, która zwraca skojarzony <xref:System.Threading.Tasks.Task%601> wystąpienia. Cykl życia to zadanie jest kontrolowany przez <xref:System.Threading.Tasks.TaskCompletionSource%601> metod, takich jak <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A>i ich `TrySet` wariantów.

Załóżmy, że chcesz utworzyć zadanie, które zostanie ukończona po upływie określonego czasu. Na przykład można opóźnić działanie w interfejsie użytkownika. <xref:System.Threading.Timer?displayProperty=nameWithType> Klasy już umożliwia asynchroniczne wywołanie delegata po upływie określonego czasu i za pomocą <xref:System.Threading.Tasks.TaskCompletionSource%601> można umieścić <xref:System.Threading.Tasks.Task%601> FrontPage na zegarze, na przykład:

[!code-csharp[Conceptual.TAP_Patterns#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#4)]
[!code-vb[Conceptual.TAP_Patterns#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#4)]

Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> metoda znajduje się w tym celu i umożliwia wewnątrz innej metody asynchroniczne, na przykład do zaimplementowania pętli asynchroniczne sondowania:

[!code-csharp[Conceptual.TAP_Patterns#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#5)]
[!code-vb[Conceptual.TAP_Patterns#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#5)]

<xref:System.Threading.Tasks.TaskCompletionSource%601> Klasa nie ma odpowiednika nierodzajową. Jednak <xref:System.Threading.Tasks.Task%601> pochodną <xref:System.Threading.Tasks.Task>, dzięki czemu można używać ogólnych <xref:System.Threading.Tasks.TaskCompletionSource%601> obiektu dla metody I/E-granica, po prostu zwracające zadania. Aby to zrobić, można używać źródła z manekina `TResult` (<xref:System.Boolean> jest wybór domyślny dobry, ale jeśli masz obawy użytkownik <xref:System.Threading.Tasks.Task> rzutowanie w dół go do <xref:System.Threading.Tasks.Task%601>, można użyć prywatnych `TResult` zamiast tego wpisz). Na przykład `Delay` metoda w poprzednim przykładzie zwraca bieżącą godzinę wraz z powstałe w ten sposób przesunięcia (`Task<DateTimeOffset>`). Jeśli wartość wyniku nie jest konieczne, metoda może być zamiast tego kodowane w następujący sposób (zmiany zwracanego typu i zmiana argumentu <xref:System.Threading.Tasks.TaskCompletionSource%601.TrySetResult%2A>):

[!code-csharp[Conceptual.TAP_Patterns#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#6)]
[!code-vb[Conceptual.TAP_Patterns#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#6)]

### <a name="mixed-compute-bound-and-io-bound-tasks"></a>Mieszane zadań powiązanych z obliczeń i I/E-powiązane z
Nie są ograniczone do operacji tylko powiązane z obliczeń lub I/E-powiązane z metod asynchronicznych, ale może reprezentować kombinację dwa. W rzeczywistości wiele operacji asynchronicznych często są łączone w większych mieszanych operacji. Na przykład `RenderAsync` praktyce intensywna operacja by renderować obraz oparty na niektórych danych wejściowych wykonywane w poprzednim przykładzie metody `imageData`. To `imageData` może pochodzić z usługi sieci web, do którego dostęp asynchronicznie:

[!code-csharp[Conceptual.TAP_Patterns#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#7)]
[!code-vb[Conceptual.TAP_Patterns#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#7)]

Również w tym przykładzie pokazano, jak token anulowania pojedynczego może wątków za pomocą wielu operacji asynchronicznych. Aby uzyskać więcej informacji, zobacz sekcję użycia anulowania w [wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

## <a name="see-also"></a>Zobacz także
 [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [Wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)  
 [Współdziałanie z innymi wzorcami asynchronicznymi i typami](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)  
