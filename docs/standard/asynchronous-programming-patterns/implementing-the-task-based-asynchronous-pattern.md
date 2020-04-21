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
ms.openlocfilehash: e09ed853598dcbb13cc8dc3fe963276e4b5e974d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739650"
---
# <a name="implementing-the-task-based-asynchronous-pattern"></a>Implementacja wzorca asynchronicznego opartego na zadaniach
Wzorzec asynchroniczne oparte na zadaniach (TAP) można zaimplementować na trzy sposoby: przy użyciu kompilatorów języka C# i Visual Basic w programie Visual Studio ręcznie lub za pomocą kombinacji kompilatora i metod ręcznych. W poniższych sekcjach omówiono szczegółowo każdą metodę. Szykuj TAP służy do implementowania zarówno operacji asynchronicznych związanych z obliczeniami, jak i operacji asynchronicznych związanych z we/wy. W sekcji [Obciążenia](#workloads) omówiono każdy typ operacji.

## <a name="generating-tap-methods"></a>Generowanie metod TAP

### <a name="using-the-compilers"></a>Korzystanie z kompilatorów
Począwszy od .NET Framework 4.5, każda `async` metoda, która jest przypisana ze słowem kluczowym (w`Async` języku Visual Basic) jest uważany za metodę asynchronicznie, a kompilatory C# i Visual Basic wykonują niezbędne przekształcenia w celu zaimplementowania metody asynchronicznie przy użyciu TAP. Metoda asynchroniczne należy zwrócić <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> lub <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> obiektu. Dla tego ostatniego treść funkcji powinna `TResult`zwracać , a kompilator zapewnia, że ten wynik jest udostępniany za pośrednictwem wynikowego obiektu zadania. Podobnie wszelkie wyjątki, które go nieobsługiwał w treści metody są kierowane do zadania wyjściowego i spowodować wynikowe zadanie do końca w <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> stanie. Wyjątkiem od tej reguły <xref:System.OperationCanceledException> jest, gdy (lub typu pochodnego) idzie nieobsługiwane, w którym to przypadku wynikowe zadanie kończy się w <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stanie.

### <a name="generating-tap-methods-manually"></a>Ręczne generowanie metod TAP
Wzorzec TAP można zaimplementować ręcznie, aby uzyskać lepszą kontrolę nad implementacją. Kompilator opiera się na obszarze <xref:System.Threading.Tasks?displayProperty=nameWithType> powierzchni publicznej udostępniane z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> obszaru nazw i typów pomocniczych w obszarze nazw. Aby samodzielnie zaimplementować <xref:System.Threading.Tasks.TaskCompletionSource%601> TAP, należy utworzyć obiekt, wykonać operację asynchronizacyjną, a po jej zakończeniu <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>wywołać <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>metodę lub <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> metodę lub `Try` wersję jednej z tych metod. Podczas ręcznego implementowania metody TAP należy wykonać wynikowe zadanie po zakończeniu reprezentowanej operacji asynchronicznego. Przykład:

[!code-csharp[Conceptual.TAP_Patterns#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#1)]
[!code-vb[Conceptual.TAP_Patterns#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#1)]

### <a name="hybrid-approach"></a>Podejście hybrydowe
 Może się okazać przydatne do zaimplementowania wzorca TAP ręcznie, ale do delegowania logiki rdzenia dla implementacji do kompilatora. Na przykład można użyć podejścia hybrydowego, gdy chcesz zweryfikować argumenty poza kompilatorem generowane metody asynchroniczne, tak aby wyjątki mogą <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> uciec do bezpośredniego wywołującego metody, a nie są udostępniane przez obiekt:

 [!code-csharp[Conceptual.TAP_Patterns#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#2)]
 [!code-vb[Conceptual.TAP_Patterns#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#2)]

 Innym przypadkiem, w którym takie delegowanie jest przydatne, jest podczas implementowania optymalizacji szybkiej ścieżki i chcesz zwrócić zadanie w pamięci podręcznej.

## <a name="workloads"></a>Obciążenia
Można zaimplementować zarówno operacje asynchroniczne związane z obliczeniami, jak i operacje asynchroniczne związane z we/wy jako metody TAP. Jednak gdy metody TAP są udostępniane publicznie z biblioteki, powinny być udostępniane tylko dla obciążeń, które obejmują operacje związane z we/wy (mogą również obejmować obliczenia, ale nie powinny być czysto obliczeniowe). Jeśli metoda jest czysto powiązanych obliczeń, powinny być widoczne tylko jako implementacji synchroniczną. Kod, który zużywa może następnie wybrać, czy zawinąć wywołanie tej metody synchronicznego do zadania, aby odciążyć pracę do innego wątku lub osiągnąć równoległość. A jeśli metoda jest powiązana we/wy, powinna być widoczna tylko jako implementacja asynchroniczną.

### <a name="compute-bound-tasks"></a>Zadania związane z obliczeniami
Klasa <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> idealnie nadaje się do reprezentowania operacji intensywnie korzystających z obliczeń. Domyślnie korzysta ze specjalnej obsługi <xref:System.Threading.ThreadPool> w klasie, aby zapewnić wydajne wykonywanie, a także zapewnia znaczną kontrolę nad kiedy, gdzie i jak wykonuje się obliczenia asynchroniczne.

Zadania związane z obliczeniami można wygenerować w następujący sposób:

- W .NET Framework 4 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> użyj metody, która akceptuje delegata <xref:System.Action%601> (zazwyczaj lub <xref:System.Func%601>) do wykonania asynchronicznie. Jeśli podasz <xref:System.Action%601> delegata, metoda <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> zwraca obiekt, który reprezentuje asynchroniczne wykonanie tego delegata. Jeśli podasz <xref:System.Func%601> delegata, metoda <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> zwraca obiekt. Przeciążenia <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metody akceptują token<xref:System.Threading.CancellationToken>anulowania (<xref:System.Threading.Tasks.TaskCreationOptions>), opcje tworzenia zadań<xref:System.Threading.Tasks.TaskScheduler>( ) i harmonogram zadań ( ), z których wszystkie zapewniają szczegółową kontrolę nad planowaniem i wykonywaniem zadania. Wystąpienie fabryczne, które jest przeznaczone dla bieżącego<xref:System.Threading.Tasks.Task.Factory%2A>harmonogramu <xref:System.Threading.Tasks.Task> zadań, jest dostępne jako właściwość statyczna ( ) klasy; na przykład: `Task.Factory.StartNew(…)`.

- W wersjach .NET Framework 4.5 i nowszych (w tym <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> .NET Core <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>i .NET Standard) użyj metody statycznej jako skrótu do . Można użyć <xref:System.Threading.Tasks.Task.Run%2A> do łatwego uruchamiania zadania związanego z obliczeniami, które są przeznaczone dla puli wątków. W .NET Framework 4.5 i nowszych wersjach jest to preferowany mechanizm uruchamiania zadania związanego z obliczeniami. Używaj `StartNew` bezpośrednio tylko wtedy, gdy chcesz bardziej szczegółowe kontroli nad zadaniem.

- Użyj konstruktorów `Task` typu `Start` lub metody, jeśli chcesz wygenerować i zaplanować zadanie oddzielnie. Metody publiczne muszą zwracać tylko zadania, które zostały już uruchomione.

- Użyj przeciążenia <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metody. Ta metoda tworzy nowe zadanie, które jest zaplanowane po zakończeniu innego zadania. Niektóre <xref:System.Threading.Tasks.Task.ContinueWith%2A> przeciążenia zaakceptować token anulowania, opcje kontynuacji i harmonogram zadań dla lepszej kontroli nad planowaniem i wykonywaniem zadania kontynuacji.

- Użyj <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> metody. Te metody tworzą nowe zadanie, które jest zaplanowane po zakończeniu wszystkich lub dowolnych z dostarczonych zadań. Te metody zapewniają również przeciążenia do kontrolowania planowania i wykonywania tych zadań.

W zadaniach związanych z obliczeniami system może uniemożliwić wykonanie zaplanowanego zadania, jeśli otrzyma żądanie anulowania przed rozpoczęciem uruchamiania zadania. W związku z tym jeśli<xref:System.Threading.CancellationToken> podasz token anulowania (obiekt), można przekazać tego tokenu do kodu asynchroniowego, który monitoruje token. Można również podać token do jednej z wcześniej wymienionych `StartNew` `Run` metod, `Task` takich jak lub tak, że środowisko wykonawcze może również monitorować tokenu.

Rozważmy na przykład metodę asynchronizacę, która renderuje obraz. Treść zadania można sondować token anulowania, tak aby kod może zakończyć się wcześniej, jeśli żądanie anulowania nadejdzie podczas renderowania. Ponadto jeśli żądanie anulowania pojawi się przed rozpoczęciem renderowania, należy zapobiec operacji renderowania:

[!code-csharp[Conceptual.TAP_Patterns#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#3)]
[!code-vb[Conceptual.TAP_Patterns#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#3)]

Zadania związane z obliczeniami <xref:System.Threading.Tasks.TaskStatus.Canceled> kończą się w stanie, jeśli spełnia się co najmniej jeden z następujących warunków:

- Żądanie anulowania dociera <xref:System.Threading.CancellationToken> za pośrednictwem obiektu, który jest dostarczany jako `StartNew` argument `Run`do metody tworzenia (na przykład lub ) przed przejściem zadania do <xref:System.Threading.Tasks.TaskStatus.Running> stanu.

- Wyjątek <xref:System.OperationCanceledException> nie jest obsłużony w treści takiego zadania, ten wyjątek zawiera ten sam, <xref:System.Threading.CancellationToken> który jest przekazywany do zadania, a token pokazuje, że żądanie anulowania jest wymagane.

Jeśli inny wyjątek nie jest obsłużony w treści <xref:System.Threading.Tasks.TaskStatus.Faulted> zadania, zadanie kończy się w stanie, a wszelkie próby oczekiwania na zadanie lub uzyskania dostępu do jego wyniku powoduje wyjątek.

### <a name="io-bound-tasks"></a>Zadania związane z we/wy
Aby utworzyć zadanie, które nie powinny być bezpośrednio wspierane przez wątek <xref:System.Threading.Tasks.TaskCompletionSource%601> dla całego jego wykonania, należy użyć typu. Ten typ udostępnia <xref:System.Threading.Tasks.TaskCompletionSource%601.Task%2A> właściwość, która <xref:System.Threading.Tasks.Task%601> zwraca skojarzone wystąpienie. Cykl życia tego zadania jest <xref:System.Threading.Tasks.TaskCompletionSource%601> kontrolowany <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A> <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>za <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A>pomocą `TrySet` takich metod jak , , i ich wariantów.

Załóżmy, że chcesz utworzyć zadanie, które zostanie ukończone po określonym czasie. Na przykład można opóźnić działanie w interfejsie użytkownika. Klasa <xref:System.Threading.Timer?displayProperty=nameWithType> już zapewnia możliwość asynchronicznie wywołać delegata po określonym czasie i <xref:System.Threading.Tasks.TaskCompletionSource%601> za pomocą <xref:System.Threading.Tasks.Task%601> można umieścić front na czasomierza, na przykład:

[!code-csharp[Conceptual.TAP_Patterns#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#4)]
[!code-vb[Conceptual.TAP_Patterns#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#4)]

Począwszy od .NET Framework 4.5, <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> metoda jest dostarczana w tym celu i można go używać wewnątrz innej metody asynchroniczne, na przykład do zaimplementowania asynchroniczne pętli sondowania:

[!code-csharp[Conceptual.TAP_Patterns#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#5)]
[!code-vb[Conceptual.TAP_Patterns#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#5)]

Klasa <xref:System.Threading.Tasks.TaskCompletionSource%601> nie ma odpowiednika nierodzgonego. Jednak <xref:System.Threading.Tasks.Task%601> wywodzi się z <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.TaskCompletionSource%601> dzięki czemu można użyć obiektu ogólnego dla metod związanych z we/wy, które po prostu zwracają zadanie. Aby to zrobić, można użyć źródła `TResult` z<xref:System.Boolean> manekina ( jest dobrym wyborem domyślnym, ale <xref:System.Threading.Tasks.Task> jeśli obawiasz <xref:System.Threading.Tasks.Task%601>się o użytkownika `TResult` downcasting go do , można użyć typu prywatnego zamiast). Na przykład `Delay` metoda w poprzednim przykładzie zwraca bieżący czas`Task<DateTimeOffset>`wraz z wynikowym przesunięciem ( ). Jeśli taka wartość wyniku jest zbędna, metoda może być zakodowana w następujący <xref:System.Threading.Tasks.TaskCompletionSource%601.TrySetResult%2A>sposób (zwróć uwagę na zmianę typu zwracanego i zmianę argumentu na):

[!code-csharp[Conceptual.TAP_Patterns#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#6)]
[!code-vb[Conceptual.TAP_Patterns#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#6)]

### <a name="mixed-compute-bound-and-io-bound-tasks"></a>Mieszane zadania związane z obliczeniami i we/wy
Metody asynchroniczne nie są ograniczone tylko do operacji związanych z obliczeniami lub operacji związanych z we/wy, ale mogą reprezentować mieszaninę tych dwóch operacji. W rzeczywistości wiele operacji asynchronicznych są często łączone w większe operacje mieszane. Na przykład `RenderAsync` metoda w poprzednim przykładzie wykonała operację intensywnie korzystającą `imageData`z obliczeń, aby renderować obraz na podstawie niektórych danych wejściowych. Może `imageData` to pochodzić z usługi sieci web, do której można asynchronicznie uzyskać dostęp:

[!code-csharp[Conceptual.TAP_Patterns#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#7)]
[!code-vb[Conceptual.TAP_Patterns#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#7)]

W tym przykładzie pokazano również, jak token anulowania pojedynczego mogą być gwintowane za pośrednictwem wielu operacji asynchronicznych. Aby uzyskać więcej informacji, zobacz sekcję użycie anulowania w części [Korzystanie z wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

## <a name="see-also"></a>Zobacz też

- [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
- [Współdziałanie z innymi wzorcami asynchronicznymi i typami](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
