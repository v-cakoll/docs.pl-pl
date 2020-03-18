---
title: Implementacja wzorca asynchronicznego opartego na zadaniach
ms.date: 06/14/2017
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
ms.openlocfilehash: 6218aa1a7b813601e9b718abf862e20a7cbcd313
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124303"
---
# <a name="implementing-the-task-based-asynchronous-pattern"></a>Implementacja wzorca asynchronicznego opartego na zadaniach
Wzorca asynchronicznego opartego na zadaniach (TAP) można zaimplementować na trzy sposoby: przy użyciu kompilatorów Języka C# i Visual Basic w programie Visual Studio, ręcznie lub za pomocą kombinacji kompilatora i metod ręcznych. W poniższych sekcjach szczegółowo omówiono każdą metodę. Wzorca TAP służy do implementowania operacji asynchronicznych związanych z obliczeniami i operacji asynchronicznych związanych z we/wy. [Obciążenia](#workloads) sekcji omówiono każdy typ operacji.

## <a name="generating-tap-methods"></a>Generowanie metod TAP

### <a name="using-the-compilers"></a>Korzystanie z kompilatorów
Począwszy od .NET Framework 4.5, każda `async` metoda,`Async` która jest przypisana za pomocą słowa kluczowego (w języku Visual Basic) jest uważany za metodę asynchroniczną, a kompilatory Języka C# i Visual Basic wykonują niezbędne przekształcenia, aby zaimplementować metodę asynchronicznie za pomocą tap. Metoda asynchroniczna powinna <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> zwracać <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> a lub obiekt. Dla tego ostatniego treść funkcji powinien `TResult`zwrócić , a kompilator zapewnia, że ten wynik jest udostępniona za pośrednictwem wynikowego obiektu zadania. Podobnie wszelkie wyjątki, które go nieobsługiwane w treści metody są organizowane do zadania wyjściowego i <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> spowodować wynikowe zadanie do końca w stanie. Wyjątkiem jest, <xref:System.OperationCanceledException> gdy (lub typu pochodnego) idzie nieobsługiwane, w którym <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> to przypadku wynikowe zadanie kończy się w stanie.

### <a name="generating-tap-methods-manually"></a>Ręczne generowanie metod TAP
Można zaimplementować wzorzec TAP ręcznie dla lepszej kontroli nad implementacją. Kompilator opiera się na publicznym <xref:System.Threading.Tasks?displayProperty=nameWithType> obszarze powierzchni uwyponionym z obszaru nazw i typów pomocniczych w obszarze <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> nazw. Aby samodzielnie zaimplementować <xref:System.Threading.Tasks.TaskCompletionSource%601> tap, należy utworzyć obiekt, wykonać operację asynchroniczną, a po jego zakończeniu wywołać <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>lub <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> metody lub `Try` wersji jednej z tych metod. Podczas ręcznego implementowania metody TAP należy wykonać wynikowe zadanie po zakończeniu reprezentowanej operacji asynchronicznej. Przykład:

[!code-csharp[Conceptual.TAP_Patterns#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#1)]
[!code-vb[Conceptual.TAP_Patterns#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#1)]

### <a name="hybrid-approach"></a>Podejście hybrydowe
 Może się okazać, że warto zaimplementować wzorzec TAP ręcznie, ale delegować logikę rdzenia dla implementacji do kompilatora. Na przykład można użyć podejścia hybrydowego, gdy chcesz zweryfikować argumenty poza metodą asynchroniczną wygenerowaną przez kompilator, aby wyjątki <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> mogły uciec do bezpośredniego obiektu wywołującego metody, a nie uwidaczniania negedyfikatora za pośrednictwem obiektu:

 [!code-csharp[Conceptual.TAP_Patterns#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#2)]
 [!code-vb[Conceptual.TAP_Patterns#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#2)]

 Innym przypadkiem, w którym takie delegowanie jest przydatne jest podczas implementowania optymalizacji szybkiej ścieżki i chcesz zwrócić zadanie buforowane.

## <a name="workloads"></a>Obciążenia
Operacje asynchroniczne związane z obliczeniami i we/wy można zaimplementować jako metody TAP. Jednak gdy metody TAP są udostępniane publicznie z biblioteki, powinny być dostarczane tylko dla obciążeń, które obejmują operacje związane we/wy (mogą również obejmować obliczenia, ale nie powinny być czysto obliczeniowe). Jeśli metoda jest czysto obliczeniowa, powinna być uwidaczniana tylko jako implementacja synchroniczna. Kod, który zużywa może następnie wybrać, czy zawijać wywołanie tej metody synchronicznej do zadania, aby odciążyć pracę do innego wątku lub osiągnąć równoległości. A jeśli metoda jest powiązana we/wy, powinna być uwidaczniana tylko jako implementacja asynchroniczna.

### <a name="compute-bound-tasks"></a>Zadania obliczeniowe
Klasa <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> idealnie nadaje się do reprezentowania operacji intensywnie korzystających z obliczeń. Domyślnie korzysta ze specjalnej obsługi <xref:System.Threading.ThreadPool> w ramach klasy, aby zapewnić efektywne wykonanie, a także zapewnia znaczną kontrolę nad kiedy, gdzie i jak obliczenia asynchroniczne wykonać.

Zadania związane z obliczeniami można generować w następujący sposób:

- W .NET Framework 4 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> użyj metody, która akceptuje delegata <xref:System.Action%601> (zazwyczaj <xref:System.Func%601>lub ) do wykonania asynchronicznie. Jeśli podasz <xref:System.Action%601> pełnomocnika, metoda <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> zwraca obiekt, który reprezentuje asynchroniczne wykonanie tego delegata. Jeśli podasz <xref:System.Func%601> pełnomocnika, metoda <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> zwraca obiekt. Przeciążenia <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metody akceptują token<xref:System.Threading.CancellationToken>anulowania ( ),<xref:System.Threading.Tasks.TaskCreationOptions>opcje tworzenia zadań<xref:System.Threading.Tasks.TaskScheduler>( i harmonogram zadań ( ), z których wszystkie zapewniają precyzyjną kontrolę nad planowaniem i wykonywaniem zadania. Wystąpienie fabryki, które jest przeznaczony mego harmonogramu bieżącego zadania jest dostępna jako właściwość statyczna (<xref:System.Threading.Tasks.Task.Factory%2A>) <xref:System.Threading.Tasks.Task> klasy; na przykład: `Task.Factory.StartNew(…)`.

- W wersji .NET Framework 4.5 i nowszej (w tym <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> .NET Core <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>i .NET Standard) użyj metody statycznej jako skrótu do . Można użyć <xref:System.Threading.Tasks.Task.Run%2A> do łatwego uruchamiania zadania obliczeniowego, które jest przeznaczony dla puli wątków. W .NET Framework 4.5 i nowszych wersjach jest to preferowany mechanizm uruchamiania zadania obliczeniowego. Należy `StartNew` używać bezpośrednio tylko wtedy, gdy chcesz uzyskać bardziej precyzyjną kontrolę nad zadaniem.

- Użyj konstruktorów `Task` typu lub `Start` metody, jeśli chcesz wygenerować i zaplanować zadanie oddzielnie. Metody publiczne muszą zwracać tylko zadania, które zostały już uruchomione.

- Użyj przeciążenia <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metody. Ta metoda tworzy nowe zadanie, które jest zaplanowane po zakończeniu innego zadania. Niektóre <xref:System.Threading.Tasks.Task.ContinueWith%2A> przeciążenia akceptują token anulowania, opcje kontynuacji i harmonogram zadań dla lepszej kontroli nad planowaniem i wykonywaniem zadania kontynuacji.

- Użyj <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> metod. Metody te tworzą nowe zadanie, które jest zaplanowane po zakończeniu wszystkich lub dowolnych z dostarczonego zestawu zadań. Metody te zapewniają również przeciążenia do kontrolowania planowania i wykonywania tych zadań.

W zadaniach obliczeniowych system może uniemożliwić wykonanie zaplanowanego zadania, jeśli otrzyma żądanie anulowania przed rozpoczęciem uruchamiania zadania. W związku z tym, jeśli<xref:System.Threading.CancellationToken> podasz token anulowania (obiekt), można przekazać ten token do kodu asynchronicznego, który monitoruje token. Można również podać token do jednej z wcześniej wymienionych `Run` metod, `Task` takich jak `StartNew` lub tak, że czas wykonywania może również monitorować token.

Rozważmy na przykład metodę asynchroniczną, która renderuje obraz. Treść zadania można sondować token anulowania, tak aby kod może zakończyć się wcześniej, jeśli żądanie anulowania przybywa podczas renderowania. Ponadto jeśli żądanie anulowania pojawi się przed rozpoczęciem renderowania, należy uniemożliwić operację renderowania:

[!code-csharp[Conceptual.TAP_Patterns#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#3)]
[!code-vb[Conceptual.TAP_Patterns#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#3)]

Zadania związane z obliczeniami <xref:System.Threading.Tasks.TaskStatus.Canceled> kończą się w stanie, jeśli spełniony jest co najmniej jeden z następujących warunków:

- Żądanie anulowania dociera za <xref:System.Threading.CancellationToken> pośrednictwem obiektu, który jest dostarczany jako argument `StartNew` `Run`metody tworzenia (na przykład <xref:System.Threading.Tasks.TaskStatus.Running> lub ) przed przejściem zadania do stanu.

- Wyjątek <xref:System.OperationCanceledException> nie jest obsługiwany w treści takiego zadania, ten <xref:System.Threading.CancellationToken> wyjątek zawiera to samo, które jest przekazywane do zadania, a token ten pokazuje, że wymagane jest anulowanie.

Jeśli inny wyjątek nie zostanie obsłużony w treści zadania, zadanie kończy się w <xref:System.Threading.Tasks.TaskStatus.Faulted> stanie, a wszelkie próby oczekiwania na zadanie lub uzyskania dostępu do jego wyniku powoduje wyjątek wyjątku.

### <a name="io-bound-tasks"></a>Zadania związane z we/wy
Aby utworzyć zadanie, które nie powinny być bezpośrednio wspierane przez wątek dla <xref:System.Threading.Tasks.TaskCompletionSource%601> całego jego wykonania, należy użyć tego typu. Ten typ udostępnia <xref:System.Threading.Tasks.TaskCompletionSource%601.Task%2A> właściwość, która <xref:System.Threading.Tasks.Task%601> zwraca skojarzone wystąpienie. Cykl życia tego zadania jest <xref:System.Threading.Tasks.TaskCompletionSource%601> kontrolowany za <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>pomocą <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A> <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A>metod, `TrySet` takich jak , , i ich warianty.

Załóżmy, że chcesz utworzyć zadanie, które zostanie ukończone po upływie określonego czasu. Na przykład można opóźnić działanie w interfejsie użytkownika. Klasa <xref:System.Threading.Timer?displayProperty=nameWithType> już zapewnia możliwość asynchronicznie wywołać delegata po upływie określonego czasu <xref:System.Threading.Tasks.TaskCompletionSource%601> i za <xref:System.Threading.Tasks.Task%601> pomocą można umieścić przodu na czasomierze, na przykład:

[!code-csharp[Conceptual.TAP_Patterns#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#4)]
[!code-vb[Conceptual.TAP_Patterns#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#4)]

Począwszy od .NET Framework 4.5, <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> metoda jest dostępna w tym celu i można go używać wewnątrz innej metody asynchronicznej, na przykład do zaimplementowania asynchronicznej pętli sondowania:

[!code-csharp[Conceptual.TAP_Patterns#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#5)]
[!code-vb[Conceptual.TAP_Patterns#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#5)]

Klasa <xref:System.Threading.Tasks.TaskCompletionSource%601> nie ma odpowiednika nierodzajowego. Jednak <xref:System.Threading.Tasks.Task%601> pochodzi z <xref:System.Threading.Tasks.Task>, dzięki czemu <xref:System.Threading.Tasks.TaskCompletionSource%601> można użyć obiektu ogólnego dla metod związanych we/wy, które po prostu zwracają zadanie. Aby to zrobić, można użyć źródła `TResult` z<xref:System.Boolean> manekinem (jest dobrym domyślnym wyborem, <xref:System.Threading.Tasks.Task> ale jeśli martwisz się o użytkownika downcasting go do <xref:System.Threading.Tasks.Task%601>, można użyć typu prywatnego `TResult` zamiast). Na przykład `Delay` metoda w poprzednim przykładzie zwraca bieżący czas wraz`Task<DateTimeOffset>`z wynikowe przesunięcie ( ). Jeśli taka wartość wyniku jest zbędna, zamiast tego metoda może być kodowana w następujący <xref:System.Threading.Tasks.TaskCompletionSource%601.TrySetResult%2A>sposób (zwróć uwagę na zmianę typu zwracanego i zmianę argumentu na):

[!code-csharp[Conceptual.TAP_Patterns#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#6)]
[!code-vb[Conceptual.TAP_Patterns#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#6)]

### <a name="mixed-compute-bound-and-io-bound-tasks"></a>Zadania powiązane z obliczeniami mieszanymi i we/wy
Metody asynchroniczne nie są ograniczone tylko do operacji związanych z obliczeniami lub operacji związanych z we/wy, ale mogą reprezentować mieszaninę tych dwóch. W rzeczywistości wiele operacji asynchronicznych są często łączone w większych operacji mieszanych. Na przykład `RenderAsync` metoda w poprzednim przykładzie wykonała operację intensywnie korzystającą z obliczeń `imageData`w celu renderowania obrazu na podstawie niektórych danych wejściowych . Może `imageData` to pochodzić z usługi sieci web, do której dostęp jest asynchroniczny:

[!code-csharp[Conceptual.TAP_Patterns#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#7)]
[!code-vb[Conceptual.TAP_Patterns#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#7)]

W tym przykładzie pokazano również, jak pojedynczy token anulowania mogą być wątków za pośrednictwem wielu operacji asynchronicznych. Aby uzyskać więcej informacji, zobacz sekcję użycia anulowania w [Sekcji Korzystanie z wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

## <a name="see-also"></a>Zobacz też

- [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
- [Współdziałanie z innymi wzorcami asynchronicznymi i typami](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
