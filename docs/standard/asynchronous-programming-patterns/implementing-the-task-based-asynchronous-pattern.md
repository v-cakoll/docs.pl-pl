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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 670cdb369920663ffa62e224bdd5aa495fc7e622
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377698"
---
# <a name="implementing-the-task-based-asynchronous-pattern"></a>Implementacja wzorca asynchronicznego opartego na zadaniach
Oparta na zadaniach asynchronicznej wzorca (TAP) można zaimplementować na trzy sposoby: za pomocą kompilatorów języków C# i Visual Basic w programie Visual Studio, ręcznie lub przy użyciu kombinacji metod kompilatora i manualnych. W poniższych sekcjach omówiono każdej metody szczegółowo. Można używać do implementowania asynchronicznych operacji powiązany obliczeniowych i czy/Wy — powiązane z wzorca TAP. [Obciążeń](#workloads) sekcji omówiono każdy rodzaj działania.

## <a name="generating-tap-methods"></a>Generowanie metod wzorca TAP

### <a name="using-the-compilers"></a>Za pomocą kompilatorów
Począwszy od .NET Framework 4.5, dowolnej metody, która jest związana z `async` — słowo kluczowe (`Async` w języku Visual Basic) jest uznawany za metody asynchronicznej oraz C# i Kompilatory języka Visual Basic wykonywać niezbędne przekształcenia do implementuje metody asynchroniczne przy użyciu wzorca TAP. Metoda asynchroniczna powinna zwracać albo <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> lub <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> obiektu. W przypadku drugiego nagłówka, powinna zwrócić treści funkcji `TResult`, kompilator zapewnia, wynik jest udostępniany za pośrednictwem wynikowego obiektu zadania. Podobnie, wyjątki, które bardziej szczegółowo nieobsługiwany w treści metody są wysyłane do wyjścia zadania i spowodować, że wynikowe zadanie kończyła się <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> stanu. Wyjątkiem jest, gdy <xref:System.OperationCanceledException> (lub typu pochodnego) nieobsługiwany zbliża się, w którym to przypadku wynikowe zadanie kończy się na <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stanu.

### <a name="generating-tap-methods-manually"></a>Generowanie metod wzorca TAP ręcznie
Może implementacji wzorca TAP ręcznie dla lepszej kontroli nad implementacji. Kompilator opiera się na publiczny obszar narażony z <xref:System.Threading.Tasks?displayProperty=nameWithType> przestrzeni nazw i typy w obsłudze <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw. Aby zaimplementować wzorcu TAP samodzielnie, należy utworzyć <xref:System.Threading.Tasks.TaskCompletionSource%601> obiektu, wykonaj operację asynchroniczną, a po zakończeniu Wywołaj <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>, lub <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> metody lub `Try` wersji jednej z tych metod. Po zaimplementowaniu metody wzorca TAP ręcznie, wynikowe zadanie należy wykonać po zakończeniu operacji asynchronicznej reprezentowana. Na przykład:

[!code-csharp[Conceptual.TAP_Patterns#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#1)]
[!code-vb[Conceptual.TAP_Patterns#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#1)]

### <a name="hybrid-approach"></a>Podejście hybrydowe
 Może okazać się przydatne w celu implementacji wzorca TAP ręcznie, ale delegować podstawowe zasady logiczne dla implementacji do kompilatora. Na przykład, można użyć podejście hybrydowe, gdy chcesz zweryfikować argumentów spoza generowanych przez kompilator metody asynchronicznej, aby pominąć wyjątków do bezpośredniego obiektu wywołującego metody zamiast są udostępniane za pośrednictwem <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiektu:

 [!code-csharp[Conceptual.TAP_Patterns#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#2)]
 [!code-vb[Conceptual.TAP_Patterns#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#2)]

 Inny przypadek, gdzie takie delegowanie jest przydatne jest podczas wdrażania ścieżkę fast optymalizacji i chcesz zwracać buforowane zadanie.

## <a name="workloads"></a>Pakiety robocze
Jako metody wzorca TAP, może wdrożyć powiązany obliczeniowych i czy/Wy — powiązane z operacji asynchronicznych. Jednak gdy metody wzorca TAP są udostępniane publicznie z biblioteki, ich należy określić tylko w przypadku obciążeń obejmujących I/O-operacji (one może również obejmować obliczeń, ale nie powinny być wyłącznie obliczeniowe). Jeśli metoda jest wyłącznie powiązany obliczeniowych, powinny zostać ujawnione tylko jako synchroniczna implementacji. Kod, który ich używa może następnie wybrać, czy powodującą otoczenie wywołania tej metody synchronicznej, w celu odciążenia pracy do innego wątku lub do osiągnięcia równoległości zadanie. A jeśli metoda jest I/O związany, powinny zostać ujawnione tylko jako implementacji asynchronicznego.

### <a name="compute-bound-tasks"></a>Zadania powiązane z obliczeń
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Klasy idealnie nadaje się do reprezentowania operacji wymaga dużej mocy obliczeniowej. Domyślnie wykorzystuje ona specjalne wsparcie w ramach <xref:System.Threading.ThreadPool> klasy zapewnienie zapewnienia ich wydajnego wykonywania, a także zapewnia znaczną kontrolę nad tym, kiedy, gdzie i jak wykonywanie asynchronicznych obliczeń.

Można wygenerować powiązany obliczeniowych zadań w następujący sposób:

- W programie .NET Framework 4, należy użyć <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody, która akceptuje delegata (zazwyczaj <xref:System.Action%601> lub <xref:System.Func%601>) ma być wykonana asynchronicznie. Jeśli podasz <xref:System.Action%601> delegować, metoda zwraca <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiekt, który reprezentuje asynchroniczne wykonywanie delegata. Jeśli podasz <xref:System.Func%601> delegować, metoda zwraca <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> obiektu. Przeciążenia <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metoda akceptuje tokenu anulowania (<xref:System.Threading.CancellationToken>), opcje tworzenia zadań (<xref:System.Threading.Tasks.TaskCreationOptions>) i harmonogram zadań (<xref:System.Threading.Tasks.TaskScheduler>), które zapewniają szczegółową kontrolę nad tym planowania i wykonywania zadania. Wystąpienia fabryki, który jest przeznaczony dla bieżącego harmonogramu zadań jest dostępna jako właściwość statyczna (<xref:System.Threading.Tasks.Task.Factory%2A>) z <xref:System.Threading.Tasks.Task> klasy; na przykład: `Task.Factory.StartNew(…)`.

- W .NET Framework 4.5 i nowsze wersje (w tym .NET Core i .NET Standard), używa się statycznej <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metodę jako skrót do <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>. Możesz użyć <xref:System.Threading.Tasks.Task.Run%2A> można łatwo uruchomić zadanie powiązany obliczeniowych, który jest przeznaczony dla puli wątków. W .NET Framework 4.5 lub nowszy jest to preferowany sposób uruchamiania zadania powiązane z obliczeń. Użyj `StartNew` bezpośrednio tylko kiedy chcesz bardziej precyzyjną kontrolę nad zadaniem.

- Użycie konstruktorów, z `Task` typu lub `Start` metody, jeśli chcesz wygenerować i zaplanować zadania oddzielnie. Metody publiczne musi zwracać tylko zadania, które zostały rozpoczęte.

- Użyj przeciążeń <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metody. Ta metoda tworzy nowe zadanie, które jest zaplanowane, po zakończeniu innego zadania. Niektóre <xref:System.Threading.Tasks.Task.ContinueWith%2A> przeciążenia akceptują token anulowania kontynuacji i opcje harmonogramu zadań lepszą kontrolę nad planowania i wykonywania zadania kontynuacji.

- Użyj <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> metody. Te metody, Utwórz nowe zadanie, które jest zaplanowane, po ukończeniu wszystkich lub dowolnego podany zestaw zadań. Te metody także podać przeciążenia do kontrolowania, planowanie i wykonywanie tych zadań.

W zadaniach powiązany obliczeniowych system może uniemożliwić wykonywanie zaplanowanego zadania, jeśli odbierze żądanie anulowania, przed rozpoczęciem wykonywania zadania. Działa w taki sposób, jeśli podasz token anulowania (<xref:System.Threading.CancellationToken> obiektu), można przekazać ten token do kodu asynchronicznego, który monitoruje ten token. Możesz też podać token do jednej z metod opisanych powyżej takich jak `StartNew` lub `Run` tak, aby `Task` środowisko uruchomieniowe może także monitorować tokenu.

Rozważmy na przykład metoda asynchroniczna, która renderuje obraz. Treści zadania można sondować token anulowania, tak aby kod może zakończyć wcześnie, jeśli żądanie anulowania zostanie odebrana podczas renderowania. Ponadto jeśli żądanie anulowania zostanie odebrana przed rozpoczęciem renderowania, należy uniemożliwić operacji renderowania:

[!code-csharp[Conceptual.TAP_Patterns#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#3)]
[!code-vb[Conceptual.TAP_Patterns#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#3)]

Powiązany obliczeniowych zadań kończy się <xref:System.Threading.Tasks.TaskStatus.Canceled> stanie, jeśli co najmniej jeden z następujących warunków jest spełniony:

- Żądanie anulowania dociera przy użyciu <xref:System.Threading.CancellationToken> obiektu, który jest dostarczany jako argument do metody tworzenia (na przykład `StartNew` lub `Run`) przed przejścia do zadań, aby <xref:System.Threading.Tasks.TaskStatus.Running> stanu.

- <xref:System.OperationCanceledException> Wyjątek przechodzi nieobsługiwany w treści takiego zadania, wyjątek zawiera takie same <xref:System.Threading.CancellationToken> przekazana do zadania, a ten token pokazuje, czy zażądano anulowania.

Jeśli kolejny wyjątek nieobsługiwany w treści zadania, zadanie kończy się <xref:System.Threading.Tasks.TaskStatus.Faulted> stanu i wszelkie próby poczekaj na zadania lub dostęp do jego wynik powoduje zgłoszenie wyjątku.

### <a name="io-bound-tasks"></a>Czy mogę/Wy — powiązane z zadania
Aby utworzyć zadanie, które nie kopie powinny być bezpośrednio przez wątek dla całości jej wykonanie, użyj <xref:System.Threading.Tasks.TaskCompletionSource%601> typu. Ten typ przedstawia <xref:System.Threading.Tasks.TaskCompletionSource%601.Task%2A> właściwość, która zwraca wartość skojarzoną <xref:System.Threading.Tasks.Task%601> wystąpienia. Cykl życia tego zadania jest kontrolowana przez <xref:System.Threading.Tasks.TaskCompletionSource%601> metody takie jak <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A>, a ich `TrySet` wariantów.

Załóżmy, że chcesz utworzyć zadanie, które zostanie ukończone po określonym czasie. Na przykład można opóźnić działanie w interfejsie użytkownika. <xref:System.Threading.Timer?displayProperty=nameWithType> Klasy już umożliwia asynchroniczne wywołanie delegata po określonym czasie i przy użyciu <xref:System.Threading.Tasks.TaskCompletionSource%601> można umieścić <xref:System.Threading.Tasks.Task%601> frontonu czasomierza, na przykład:

[!code-csharp[Conceptual.TAP_Patterns#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#4)]
[!code-vb[Conceptual.TAP_Patterns#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#4)]

Począwszy od programu .NET Framework 4.5 <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> metoda znajduje się w tym celu i służy wewnątrz innej metody asynchronicznej, na przykład do zaimplementowania pętlę asynchronicznego sondowania:

[!code-csharp[Conceptual.TAP_Patterns#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#5)]
[!code-vb[Conceptual.TAP_Patterns#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#5)]

<xref:System.Threading.Tasks.TaskCompletionSource%601> Klasa nie ma odpowiednika nieogólnego. Jednak <xref:System.Threading.Tasks.Task%601> pochodzi od klasy <xref:System.Threading.Tasks.Task>, aby można było używać ogólnych <xref:System.Threading.Tasks.TaskCompletionSource%601> obiektu I/O-powiązane z metod, które po prostu zwracają zadania. Aby to zrobić, za pomocą źródła dummy `TResult` (<xref:System.Boolean> jest to rozwiązanie dobre domyślne, ale jeśli interesujące Cię użytkownik <xref:System.Threading.Tasks.Task> rzutowanie jego <xref:System.Threading.Tasks.Task%601>, można użyć prywatnej `TResult` typu). Na przykład `Delay` metody w poprzednim przykładzie zwraca bieżącą godzinę wraz z wynikowy przesunięcia (`Task<DateTimeOffset>`). Jeśli wartość wyniku jest niepotrzebne, metody można zamiast tego następujące kody (należy pamiętać, zmiana zwracanego typu i zmianę argument <xref:System.Threading.Tasks.TaskCompletionSource%601.TrySetResult%2A>):

[!code-csharp[Conceptual.TAP_Patterns#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#6)]
[!code-vb[Conceptual.TAP_Patterns#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#6)]

### <a name="mixed-compute-bound-and-io-bound-tasks"></a>Mieszane powiązany obliczeniowych i czy/Wy — powiązane z zadania
Metody asynchroniczne nie są ograniczone do operacji tylko powiązany obliczeniowych lub I/O-powiązane z, ale może reprezentować kombinację dwóch. W rzeczywistości wiele operacji asynchronicznych często są łączone w większych mieszane operacji. Na przykład `RenderAsync` metody w poprzednim przykładzie wykonywane operacją wymaga dużej mocy obliczeniowej, by renderować obraz na podstawie niektórych danych wejściowych `imageData`. To `imageData` może pochodzić z usługi sieci web, które asynchronicznie dostępu:

[!code-csharp[Conceptual.TAP_Patterns#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#7)]
[!code-vb[Conceptual.TAP_Patterns#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#7)]

W przykładzie pokazano również, jak token anulowania pojedynczego może wątków przez wiele operacji asynchronicznych. Aby uzyskać więcej informacji, zobacz sekcję użycia anulowania w [wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

## <a name="see-also"></a>Zobacz także

- [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
- [Współdziałanie z innymi wzorcami asynchronicznymi i typami](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
