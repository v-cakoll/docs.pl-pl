---
title: Implementacja wzorca asynchronicznego opartego na zadaniach
description: W tym artykule wyjaśniono, jak zaimplementować wzorzec asynchroniczny oparty na zadaniach. Służy do implementowania operacji asynchronicznych powiązanych z obliczeniami i we/wy.
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
ms.openlocfilehash: 1f2f44b6b92f66f95816778c6dc8e893f1291abe
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289369"
---
# <a name="implementing-the-task-based-asynchronous-pattern"></a>Implementacja wzorca asynchronicznego opartego na zadaniach
Wzorzec asynchroniczny oparty na zadaniach (TAP) można zaimplementować na trzy sposoby: za pomocą kompilatorów C# i Visual Basic w programie Visual Studio, ręcznie lub za pomocą kombinacji kompilatora i metod ręcznych. W poniższych sekcjach szczegółowo omówiono każdą metodę. Możesz użyć wzorca TAP, aby zaimplementować operacje asynchroniczne powiązane z obliczaniem i we/wy. W sekcji [obciążenia](#workloads) omówiono każdy typ operacji.

## <a name="generating-tap-methods"></a>Generowanie metod TAP

### <a name="using-the-compilers"></a>Korzystanie z kompilatorów
Począwszy od .NET Framework 4,5, każda metoda, która jest przypisana za pomocą `async` słowa kluczowego ( `Async` w Visual Basic) jest uznawana za metodę asynchroniczną, a kompilatory C# i Visual Basic wykonują wymagane przekształcenia w celu asynchronicznego zaimplementowania metody przy użyciu narzędzia TAP. Metoda asynchroniczna powinna zwracać albo <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> obiekt. Dla tej ostatniej, treść funkcji powinna zwracać `TResult` i kompilator zapewnia, że wynik jest udostępniany przez wynikowy obiekt zadania. Podobnie wszystkie wyjątki, które nie są obsługiwane w treści metody są przekazywane do zadania wyjściowego i powodują, że wynikowe zadanie zakończy się w <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> stanie. Wyjątkiem od tej reguły jest <xref:System.OperationCanceledException> nieobsłużony (lub typ pochodny), w którym przypadku wyniki zadania kończą się w <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stanie.

### <a name="generating-tap-methods-manually"></a>Ręczne generowanie metod TAP
Wzorzec TAP można zaimplementować ręcznie w celu zapewnienia lepszej kontroli nad implementacją. Kompilator opiera się na obszarze powierzchni publicznej uwidocznionej z <xref:System.Threading.Tasks?displayProperty=nameWithType> przestrzeni nazw i typów pomocniczych w <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw. Aby zaimplementować samodzielne wybieranie, należy utworzyć <xref:System.Threading.Tasks.TaskCompletionSource%601> obiekt, wykonać operację asynchroniczną i po jego zakończeniu wywołać <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A> <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A> metodę,, lub <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> lub `Try` wersję jednej z tych metod. W przypadku ręcznego zaimplementowania metody TAP należy wykonać zadanie podrzędne, gdy zostanie ukończona operacja asynchroniczna. Na przykład:

[!code-csharp[Conceptual.TAP_Patterns#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#1)]
[!code-vb[Conceptual.TAP_Patterns#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#1)]

### <a name="hybrid-approach"></a>Podejście hybrydowe
 Przydatne może okazać się ręczne wdrożenie wzorca TAP, ale w celu delegowania podstawowej logiki implementacji do kompilatora. Na przykład możesz chcieć użyć podejścia hybrydowego, gdy chcesz zweryfikować argumenty poza metodę asynchroniczną wygenerowaną przez kompilator, aby wyjątki mogły wyjść bezpośrednio do obiektu wywołującego metody, a nie ujawniać go za pośrednictwem <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> :

 [!code-csharp[Conceptual.TAP_Patterns#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#2)]
 [!code-vb[Conceptual.TAP_Patterns#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#2)]

 Innym przypadkiem, gdy takie delegowanie jest przydatne, jest wdrożenie szybkiej optymalizacji ścieżki i zwrócenie zadania w pamięci podręcznej.

## <a name="workloads"></a>Obciążenia
Można zaimplementować operacje asynchroniczne powiązane z obliczeniami i we/wy jako metody TAP. Mimo że metody TAP są ujawniane publicznie z biblioteki, powinny być dostarczane tylko w przypadku obciążeń obejmujących operacje we/wy (mogą także dotyczyć obliczeń, ale nie powinny być czyste). Jeśli metoda ma charakter wyłącznie obliczeniowy, powinno być uwidoczniona tylko jako implementacja synchroniczna. Kod, który go zużywa, może następnie zdecydować, czy należy otoczyć wywołanie tej metody synchronicznej do zadania w celu odciążenia pracy do innego wątku lub osiągnięcia równoległości. A jeśli metoda jest powiązana we/wy, powinna być udostępniona tylko jako implementacja asynchroniczna.

### <a name="compute-bound-tasks"></a>Zadania związane z obliczeniami
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>Klasa doskonale nadaje się do reprezentowania operacji intensywnie korzystających z obliczeń. Domyślnie wykorzystuje ona specjalną pomoc techniczną w ramach <xref:System.Threading.ThreadPool> klasy w celu zapewnienia wydajnego wykonania i zapewnia znaczącą kontrolę nad tym, gdzie i jak są wykonywane asynchroniczne obliczenia.

Zadania związane z obliczeniami można generować w następujący sposób:

- W .NET Framework 4 Użyj <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody, która akceptuje obiekt delegowany (zwykle <xref:System.Action%601> lub a), który <xref:System.Func%601> ma być wykonywany asynchronicznie. W przypadku podania <xref:System.Action%601> delegata Metoda zwraca <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiekt, który reprezentuje asynchroniczne wykonywanie tego delegata. W przypadku podania <xref:System.Func%601> delegata Metoda zwraca <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> obiekt. Przeciążenia <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metody akceptują token anulowania ( <xref:System.Threading.CancellationToken> ), opcje tworzenia zadań ( <xref:System.Threading.Tasks.TaskCreationOptions> ) i harmonogram zadań ( <xref:System.Threading.Tasks.TaskScheduler> ), które zapewniają szczegółową kontrolę nad planowaniem i wykonywaniem zadania. Wystąpienie fabryki, które jest celem bieżącego harmonogramu zadań, jest dostępne jako właściwość statyczna ( <xref:System.Threading.Tasks.Task.Factory%2A> ) <xref:System.Threading.Tasks.Task> klasy; na przykład: `Task.Factory.StartNew(…)` .

- W .NET Framework 4,5 i nowszych wersjach (w tym .NET Core i .NET Standard) Użyj metody statycznej <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> jako skrótu do <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> . Można użyć, <xref:System.Threading.Tasks.Task.Run%2A> Aby łatwo uruchomić zadanie powiązane z obliczeniami, które jest przeznaczone dla puli wątków. W .NET Framework 4,5 i nowszych wersjach jest to preferowany mechanizm uruchamiania zadania związanego z obliczaniem. Używaj `StartNew` bezpośrednio tylko wtedy, gdy potrzebujesz bardziej precyzyjnej kontroli nad zadaniem.

- Użyj konstruktorów `Task` typu lub `Start` metody, jeśli chcesz generować i planować zadanie osobno. Metody publiczne muszą zwracać tylko zadania, które zostały już uruchomione.

- Użyj przeciążenia <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metody. Ta metoda tworzy nowe zadanie zaplanowane po zakończeniu innego zadania. Niektóre <xref:System.Threading.Tasks.Task.ContinueWith%2A> przeciążenia akceptują token anulowania, opcje kontynuacji i harmonogram zadań, aby zapewnić lepszą kontrolę nad planowaniem i wykonywaniem zadania kontynuacji.

- Użyj <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> metod i <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> . Te metody tworzą nowe zadanie zaplanowane po zakończeniu wszystkich lub dowolnego dostarczonego zestawu zadań. Te metody zapewniają również przeciążenia umożliwiające sterowanie planowaniem i wykonywaniem tych zadań.

W zadaniach związanych z obliczaniem, system może uniemożliwić wykonanie zaplanowanego zadania, Jeśli odbierze żądanie anulowania przed uruchomieniem zadania. W związku z tym, jeśli podajesz token anulowania ( <xref:System.Threading.CancellationToken> Object), możesz przekazać ten token do kodu asynchronicznego, który monitoruje token. Możesz również podać token dla jednej z wymienionych wcześniej metod, takich jak lub, `StartNew` Aby `Run` `Task` środowisko uruchomieniowe mogło również monitorować token.

Rozważmy na przykład metodę asynchroniczną, która renderuje obraz. Treść zadania może sondować token anulowania, dzięki czemu kod może zakończyć się wczesne w przypadku odebrania żądania anulowania podczas renderowania. Ponadto, jeśli żądanie anulowania dociera przed rozpoczęciem renderowania, należy zapobiec operacji renderowania:

[!code-csharp[Conceptual.TAP_Patterns#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#3)]
[!code-vb[Conceptual.TAP_Patterns#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#3)]

Zadania powiązane z obliczeniami kończą się w <xref:System.Threading.Tasks.TaskStatus.Canceled> stanie, jeśli co najmniej jeden z następujących warunków jest spełniony:

- Żądanie anulowania dociera do <xref:System.Threading.CancellationToken> obiektu, który jest dostarczany jako argument metody tworzenia (na przykład `StartNew` lub `Run` ) przed przejściem do <xref:System.Threading.Tasks.TaskStatus.Running> stanu zadania.

- <xref:System.OperationCanceledException>Wyjątek nie jest obsługiwany w treści tego zadania, ten wyjątek zawiera te same dane, <xref:System.Threading.CancellationToken> które są przesyłane do zadania, a ten token pokazuje, że żądanie anulowania jest wymagane.

Jeśli inny wyjątek nie jest obsługiwany w treści zadania, zadanie zakończy się w <xref:System.Threading.Tasks.TaskStatus.Faulted> stanie, a wszystkie próby oczekiwania na zadanie lub uzyskania dostępu do wyniku spowodują wystąpienie wyjątku.

### <a name="io-bound-tasks"></a>Operacje we/wy — powiązane zadania
Aby utworzyć zadanie, które nie powinno być bezpośrednio wykonywane przez wątek dla całości jego wykonywania, użyj <xref:System.Threading.Tasks.TaskCompletionSource%601> typu. Ten typ uwidacznia <xref:System.Threading.Tasks.TaskCompletionSource%601.Task%2A> Właściwość, która zwraca skojarzone <xref:System.Threading.Tasks.Task%601> wystąpienie. Cykl życia tego zadania jest kontrolowany przy użyciu <xref:System.Threading.Tasks.TaskCompletionSource%601> metod takich jak <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A> ,, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A> <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> i ich `TrySet` wariantów.

Załóżmy, że chcesz utworzyć zadanie, które zostanie ukończone po upływie określonego czasu. Na przykład możesz chcieć opóźnić działanie w interfejsie użytkownika. <xref:System.Threading.Timer?displayProperty=nameWithType>Klasa umożliwia już Asynchroniczne wywoływanie delegata po określonym czasie, a przy użyciu <xref:System.Threading.Tasks.TaskCompletionSource%601> można umieścić <xref:System.Threading.Tasks.Task%601> na nim przód, na przykład:

[!code-csharp[Conceptual.TAP_Patterns#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#4)]
[!code-vb[Conceptual.TAP_Patterns#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#4)]

Począwszy od .NET Framework 4,5, <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Metoda jest dostępna do tego celu i można jej użyć w innej metodzie asynchronicznej, na przykład w celu zaimplementowania asynchronicznej pętli sondowania:

[!code-csharp[Conceptual.TAP_Patterns#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#5)]
[!code-vb[Conceptual.TAP_Patterns#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#5)]

<xref:System.Threading.Tasks.TaskCompletionSource%601>Klasa nie ma nieogólnego odpowiednika. Jednak <xref:System.Threading.Tasks.Task%601> pochodzi z <xref:System.Threading.Tasks.Task> , więc można użyć obiektu generycznego <xref:System.Threading.Tasks.TaskCompletionSource%601> dla metod powiązanych we/wy, które po prostu zwracają zadanie. W tym celu można użyć źródła z manekinem `TResult` ( <xref:System.Boolean> jest to dobry wybór domyślny, ale jeśli użytkownik ma informacje o użytkowniku <xref:System.Threading.Tasks.Task> rzutowanie go do <xref:System.Threading.Tasks.Task%601> , `TResult` zamiast tego można użyć typu prywatnego). Na przykład `Delay` Metoda w poprzednim przykładzie zwraca bieżący czas wraz z wynikowym przesunięciem ( `Task<DateTimeOffset>` ). Jeśli taka wartość wynikowa jest niezbędna, Metoda może być zakodowana w następujący sposób (należy zwrócić uwagę na zmianę typu zwracanego i zmianę argumentu na <xref:System.Threading.Tasks.TaskCompletionSource%601.TrySetResult%2A> ):

[!code-csharp[Conceptual.TAP_Patterns#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#6)]
[!code-vb[Conceptual.TAP_Patterns#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#6)]

### <a name="mixed-compute-bound-and-io-bound-tasks"></a>Mieszane zadania powiązane z obliczeniami i operacje we/wy
Metody asynchroniczne nie są ograniczone do operacji tylko powiązanych z obliczeniami lub we/wy, ale mogą reprezentować kombinację dwóch. W rzeczywistości wiele operacji asynchronicznych często są łączone w większe operacje mieszane. Na przykład `RenderAsync` Metoda w poprzednim przykładzie wykonała operację obliczeniową intensywnie, aby renderować obraz na podstawie niektórych danych wejściowych `imageData` . `imageData`Może to być z usługi sieci Web, do której masz dostęp asynchroniczny:

[!code-csharp[Conceptual.TAP_Patterns#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#7)]
[!code-vb[Conceptual.TAP_Patterns#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#7)]

W tym przykładzie pokazano również, jak pojedynczy token anulowania może być wielowątkowy przez wiele operacji asynchronicznych. Aby uzyskać więcej informacji, zobacz sekcję użycie anulowania w temacie [Używanie wzorca asynchronicznego opartego na zadaniach](consuming-the-task-based-asynchronous-pattern.md).

## <a name="see-also"></a>Zobacz także

- [Wzorzec asynchroniczny oparty na zadaniach (TAP)](task-based-asynchronous-pattern-tap.md)
- [Wykorzystywanie wzorca asynchronicznego opartego na zadaniach](consuming-the-task-based-asynchronous-pattern.md)
- [Współdziałanie z innymi wzorcami asynchronicznymi i typami](interop-with-other-asynchronous-patterns-and-types.md)
