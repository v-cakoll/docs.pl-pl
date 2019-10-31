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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124303"
---
# <a name="implementing-the-task-based-asynchronous-pattern"></a>Implementacja wzorca asynchronicznego opartego na zadaniach
Wzorzec asynchroniczny oparty na zadaniach (TAP) można zaimplementować na trzy sposoby: za pomocą kompilatorów C# i Visual Basic w programie Visual Studio, ręcznie lub za pomocą kombinacji kompilatora i metod ręcznych. W poniższych sekcjach szczegółowo omówiono każdą metodę. Możesz użyć wzorca TAP, aby zaimplementować operacje asynchroniczne powiązane z obliczaniem i we/wy. W sekcji [obciążenia](#workloads) omówiono każdy typ operacji.

## <a name="generating-tap-methods"></a>Generowanie metod TAP

### <a name="using-the-compilers"></a>Korzystanie z kompilatorów
Począwszy od .NET Framework 4,5, każda metoda, która jest przypisana za pomocą słowa kluczowego `async` (`Async` w Visual Basic) jest uznawana za metodę C# asynchroniczną, a kompilatory i Visual Basic wykonują wymagane przekształcenia w celu zaimplementowania Metoda asynchronicznie przy użyciu narzędzia TAP. Metoda asynchroniczna powinna zwracać obiekt <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> lub <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Dla tej ostatniej, treść funkcji powinna zwracać `TResult`i kompilator zapewnia, że ten wynik jest udostępniany przez wynikowy obiekt zadania. Podobnie wszystkie wyjątki, które nie są obsługiwane w treści metody są przekazywane do zadania wyjściowego i powodują, że wynikowe zadanie zakończy się w stanie <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType>. Wyjątek polega na tym, że <xref:System.OperationCanceledException> (lub typ pochodny) nie jest obsługiwany, w takim przypadku wyniki zadania kończą się w stanie <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType>.

### <a name="generating-tap-methods-manually"></a>Ręczne generowanie metod TAP
Wzorzec TAP można zaimplementować ręcznie w celu zapewnienia lepszej kontroli nad implementacją. Kompilator opiera się na obszarze publicznej powierzchni uwidocznionej z przestrzeni nazw <xref:System.Threading.Tasks?displayProperty=nameWithType> i typów pomocniczych w przestrzeni nazw <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>. Aby zaimplementować samodzielnie NACIŚNIĘCIe, należy utworzyć obiekt <xref:System.Threading.Tasks.TaskCompletionSource%601>, wykonać operację asynchroniczną i po jej zakończeniu wywołać metodę <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>lub <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> lub wersję `Try` jednej z tych metod. W przypadku ręcznego zaimplementowania metody TAP należy wykonać zadanie podrzędne, gdy zostanie ukończona operacja asynchroniczna. Na przykład:

[!code-csharp[Conceptual.TAP_Patterns#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#1)]
[!code-vb[Conceptual.TAP_Patterns#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#1)]

### <a name="hybrid-approach"></a>Podejście hybrydowe
 Przydatne może okazać się ręczne wdrożenie wzorca TAP, ale w celu delegowania podstawowej logiki implementacji do kompilatora. Na przykład możesz chcieć użyć podejścia hybrydowego, gdy chcesz zweryfikować argumenty poza metodę asynchroniczną wygenerowaną przez kompilator, aby wyjątki mogły wyjść bezpośrednio do obiektu wywołującego metody, a nie ujawniać go za pośrednictwem <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>go:

 [!code-csharp[Conceptual.TAP_Patterns#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#2)]
 [!code-vb[Conceptual.TAP_Patterns#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#2)]

 Innym przypadkiem, gdy takie delegowanie jest przydatne, jest wdrożenie szybkiej optymalizacji ścieżki i zwrócenie zadania w pamięci podręcznej.

## <a name="workloads"></a>Pakiety robocze
Można zaimplementować operacje asynchroniczne powiązane z obliczeniami i we/wy jako metody TAP. Mimo że metody TAP są ujawniane publicznie z biblioteki, powinny być dostarczane tylko w przypadku obciążeń obejmujących operacje we/wy (mogą także dotyczyć obliczeń, ale nie powinny być czyste). Jeśli metoda ma charakter wyłącznie obliczeniowy, powinno być uwidoczniona tylko jako implementacja synchroniczna. Kod, który go zużywa, może następnie zdecydować, czy należy otoczyć wywołanie tej metody synchronicznej do zadania w celu odciążenia pracy do innego wątku lub osiągnięcia równoległości. A jeśli metoda jest powiązana we/wy, powinna być udostępniona tylko jako implementacja asynchroniczna.

### <a name="compute-bound-tasks"></a>Zadania związane z obliczeniami
Klasa <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> idealnie nadaje się do reprezentowania operacji intensywnie korzystających z obliczeń. Domyślnie wykorzystuje ona specjalną pomoc techniczną w ramach klasy <xref:System.Threading.ThreadPool> w celu zapewnienia wydajnego wykonania i zapewnia znaczącą kontrolę nad tym, gdzie i jak są wykonywane asynchroniczne obliczenia.

Zadania związane z obliczeniami można generować w następujący sposób:

- W .NET Framework 4 Użyj metody <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>, która akceptuje obiekt delegowany (zazwyczaj <xref:System.Action%601> lub <xref:System.Func%601>) do wykonania asynchronicznie. Jeśli podano delegata <xref:System.Action%601>, metoda zwraca obiekt <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, który reprezentuje asynchroniczne wykonywanie tego delegata. Jeśli podano delegata <xref:System.Func%601>, metoda zwróci obiekt <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Przeciążenia metody <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> akceptują token anulowania (<xref:System.Threading.CancellationToken>), opcje tworzenia zadań (<xref:System.Threading.Tasks.TaskCreationOptions>) i harmonogram zadań (<xref:System.Threading.Tasks.TaskScheduler>), które zapewniają szczegółową kontrolę nad planowaniem i wykonywaniem zadania. Wystąpienie fabryki, które jest celem bieżącego harmonogramu zadań, jest dostępne jako właściwość statyczna (<xref:System.Threading.Tasks.Task.Factory%2A>) klasy <xref:System.Threading.Tasks.Task>; na przykład: `Task.Factory.StartNew(…)`.

- W .NET Framework 4,5 i nowszych wersjach (w tym .NET Core i .NET Standard) Użyj statycznej metody <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> jako skrótu do <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>. Za pomocą <xref:System.Threading.Tasks.Task.Run%2A> można łatwo uruchomić zadanie powiązane z obliczaniem, które jest przeznaczone dla puli wątków. W .NET Framework 4,5 i nowszych wersjach jest to preferowany mechanizm uruchamiania zadania związanego z obliczaniem. Używaj `StartNew` bezpośrednio tylko wtedy, gdy potrzebujesz bardziej szczegółowej kontroli nad zadaniem.

- Użyj konstruktorów typu `Task` lub metody `Start`, jeśli chcesz generować i planować zadanie osobno. Metody publiczne muszą zwracać tylko zadania, które zostały już uruchomione.

- Użyj przeciążenia metody <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. Ta metoda tworzy nowe zadanie zaplanowane po zakończeniu innego zadania. Niektóre z przeciążeń <xref:System.Threading.Tasks.Task.ContinueWith%2A> akceptują token anulowania, opcje kontynuacji i harmonogram zadań, aby zapewnić lepszą kontrolę nad planowaniem i wykonywaniem zadania kontynuacji.

- Użyj metod <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType>. Te metody tworzą nowe zadanie zaplanowane po zakończeniu wszystkich lub dowolnego dostarczonego zestawu zadań. Te metody zapewniają również przeciążenia umożliwiające sterowanie planowaniem i wykonywaniem tych zadań.

W zadaniach związanych z obliczaniem, system może uniemożliwić wykonanie zaplanowanego zadania, Jeśli odbierze żądanie anulowania przed uruchomieniem zadania. W związku z tym, jeśli podajesz token anulowania (<xref:System.Threading.CancellationToken> Object), możesz przekazać ten token do kodu asynchronicznego, który monitoruje token. Możesz również podać token do jednej z wymienionych wcześniej metod, takich jak `StartNew` lub `Run`, aby środowisko uruchomieniowe `Task` mogło również monitorować token.

Rozważmy na przykład metodę asynchroniczną, która renderuje obraz. Treść zadania może sondować token anulowania, dzięki czemu kod może zakończyć się wczesne w przypadku odebrania żądania anulowania podczas renderowania. Ponadto, jeśli żądanie anulowania dociera przed rozpoczęciem renderowania, należy zapobiec operacji renderowania:

[!code-csharp[Conceptual.TAP_Patterns#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#3)]
[!code-vb[Conceptual.TAP_Patterns#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#3)]

Zadania powiązane z obliczeniami kończą się w stanie <xref:System.Threading.Tasks.TaskStatus.Canceled>, jeśli co najmniej jeden z następujących warunków jest spełniony:

- Żądanie anulowania dociera do obiektu <xref:System.Threading.CancellationToken>, który jest dostarczany jako argument metody tworzenia (na przykład `StartNew` lub `Run`) przed przejściem do stanu <xref:System.Threading.Tasks.TaskStatus.Running>.

- Wyjątek <xref:System.OperationCanceledException> nie jest obsługiwany w treści tego zadania, ten wyjątek zawiera ten sam <xref:System.Threading.CancellationToken>, który jest przekazywany do zadania, a ten token pokazuje, że żądanie anulowania jest wymagane.

Jeśli inny wyjątek nie jest obsługiwany w treści zadania, zadanie kończy się w stanie <xref:System.Threading.Tasks.TaskStatus.Faulted> i wszystkie próby oczekiwania na zadanie lub uzyskania dostępu do wyniku spowodują wystąpienie wyjątku.

### <a name="io-bound-tasks"></a>Operacje we/wy — powiązane zadania
Aby utworzyć zadanie, które nie powinno być bezpośrednio obsługiwane przez wątek dla całości jego wykonywania, użyj typu <xref:System.Threading.Tasks.TaskCompletionSource%601>. Ten typ uwidacznia Właściwość <xref:System.Threading.Tasks.TaskCompletionSource%601.Task%2A>, która zwraca skojarzone wystąpienie <xref:System.Threading.Tasks.Task%601>. Cykl życia tego zadania jest kontrolowany przez <xref:System.Threading.Tasks.TaskCompletionSource%601> metody, takie jak <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A>i ich `TrySet` wariantów.

Załóżmy, że chcesz utworzyć zadanie, które zostanie ukończone po upływie określonego czasu. Na przykład możesz chcieć opóźnić działanie w interfejsie użytkownika. Klasa <xref:System.Threading.Timer?displayProperty=nameWithType> już umożliwia Asynchroniczne wywoływanie delegata po upływie określonego czasu, a za pomocą <xref:System.Threading.Tasks.TaskCompletionSource%601> można umieścić <xref:System.Threading.Tasks.Task%601> przed upływem czasomierza, na przykład:

[!code-csharp[Conceptual.TAP_Patterns#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#4)]
[!code-vb[Conceptual.TAP_Patterns#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#4)]

Począwszy od .NET Framework 4,5, Metoda <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> jest dostępna do tego celu i można jej użyć w innej metodzie asynchronicznej, na przykład w celu zaimplementowania asynchronicznej pętli sondowania:

[!code-csharp[Conceptual.TAP_Patterns#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#5)]
[!code-vb[Conceptual.TAP_Patterns#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#5)]

Klasa <xref:System.Threading.Tasks.TaskCompletionSource%601> nie ma nieogólnego odpowiednika. Jednakże <xref:System.Threading.Tasks.Task%601> pochodzi od <xref:System.Threading.Tasks.Task>, dlatego można użyć generycznego obiektu <xref:System.Threading.Tasks.TaskCompletionSource%601> dla metod powiązanych we/wy, które po prostu zwracają zadanie. W tym celu można użyć źródła z fikcyjną `TResult` (<xref:System.Boolean> jest to dobry wybór domyślny, ale jeśli jesteś użytkownikiem, który ma <xref:System.Threading.Tasks.Task> rzutowanie go do <xref:System.Threading.Tasks.Task%601>, możesz zamiast tego użyć prywatnego typu `TResult`). Na przykład Metoda `Delay` w poprzednim przykładzie zwraca bieżącą godzinę wraz z wynikowym przesunięciem (`Task<DateTimeOffset>`). Jeśli taka wartość wynikowa jest niezbędna, Metoda może być zakodowana w następujący sposób (należy zwrócić uwagę na zmianę typu zwracanego i zmianę argumentu na <xref:System.Threading.Tasks.TaskCompletionSource%601.TrySetResult%2A>):

[!code-csharp[Conceptual.TAP_Patterns#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#6)]
[!code-vb[Conceptual.TAP_Patterns#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#6)]

### <a name="mixed-compute-bound-and-io-bound-tasks"></a>Mieszane zadania powiązane z obliczeniami i operacje we/wy
Metody asynchroniczne nie są ograniczone do operacji tylko powiązanych z obliczeniami lub we/wy, ale mogą reprezentować kombinację dwóch. W rzeczywistości wiele operacji asynchronicznych często są łączone w większe operacje mieszane. Na przykład Metoda `RenderAsync` w poprzednim przykładzie wykonała operację obliczeniową intensywnie, aby renderować obraz na podstawie niektórych `imageData`wejściowych. Ten `imageData` może pochodzić z usługi sieci Web, do której masz dostęp asynchroniczny:

[!code-csharp[Conceptual.TAP_Patterns#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#7)]
[!code-vb[Conceptual.TAP_Patterns#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#7)]

W tym przykładzie pokazano również, jak pojedynczy token anulowania może być wielowątkowy przez wiele operacji asynchronicznych. Aby uzyskać więcej informacji, zobacz sekcję użycie anulowania w temacie [Używanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

## <a name="see-also"></a>Zobacz także

- [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
- [Współdziałanie z innymi wzorcami asynchronicznymi i typami](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
