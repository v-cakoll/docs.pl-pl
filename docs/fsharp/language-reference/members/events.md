---
title: Zdarzenia
description: Dowiedz F# się, jak zdarzenia umożliwiają kojarzenie wywołań funkcji z akcjami użytkownika, które są ważne w programowaniu graficznego interfejsu użytkownika.
ms.date: 05/16/2016
ms.openlocfilehash: eed2caff569638ea5aa972a000dfa71a3b64f60b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627568"
---
# <a name="events"></a>Zdarzenia

> [!NOTE]
> Linki do odwołań do interfejsów API w tym artykule przeprowadzą Cię do subskrypcji MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

Zdarzenia umożliwiają kojarzenie wywołań funkcji z akcjami użytkownika i są ważne w programowaniu graficznych interfejsów użytkownika. Zdarzenia mogą być też wywoływane przez aplikacje lub system operacyjny.

## <a name="handling-events"></a>Obsługa zdarzeń

Gdy jest używana biblioteka graficznych interfejsów użytkownika, taka jak Windows Forms lub Windows Presentation Foundation (WPF), większość kodu aplikacji działa w odpowiedzi na zdarzenia, które są wstępnie zdefiniowane w tej bibliotece. Te wstępnie zdefiniowane zdarzenia są składowymi klas graficznego interfejsu użytkownika, takich jak formularze i formanty. Niestandardowe zachowanie można dodać do istniejącego zdarzenia, takiego jak kliknięcie przycisku, odwołując się do określonego nazwanego zdarzenia zainteresowania (na przykład `Click` zdarzenia `Form` klasy `Add` ) i wywołując metodę, jak pokazano w poniższym kodzie. . Jeśli uruchamiasz ten program F# z interaktywnego, Pomiń wywołanie `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

Typ `Add` metody to `('a -> unit) -> unit`. W związku z tym metoda obsługi zdarzeń przyjmuje jeden parametr, zazwyczaj argumenty zdarzenia i zwraca `unit`. W poprzednim przykładzie pokazano program obsługi zdarzeń w postaci wyrażenia lambda. Program obsługi zdarzeń może być także wartością funkcji, tak jak w poniższym przykładzie kodu. W poniższym przykładzie kodu pokazano także użycie parametrów programu obsługi zdarzeń, które dostarczają informacje charakterystyczne dla typu zdarzenia. Dla zdarzenia system `System.Windows.Forms.MouseEventArgs` `Y` przekazuje`X` obiekt, który zawiera położenie wskaźnika i. `MouseMove`

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a>Tworzenie zdarzeń niestandardowych

F#zdarzenia są reprezentowane przez F# klasę [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) , która implementuje interfejs [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) . `IEvent`jest samym interfejsem, który łączy funkcje dwóch innych interfejsów `System.IObservable<'T>` i [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a). W związku z tym program `IObservable` F# F# s ma równoważne funkcje delegatów w innych językach oraz dodatkowe funkcje od, co oznacza, że zdarzenia obsługują filtrowanie zdarzeń i używanie funkcji pierwszej klasy i `Event` wyrażenia lambda jako programy obsługi zdarzeń. Ta funkcja jest dostępna w [module Event](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).

Aby utworzyć zdarzenie na klasie, która działa podobnie jak wszystkie inne zdarzenia .NET Framework, Dodaj do klasy `let` powiązanie, które `Event` definiuje jako pole w klasie. Odpowiedni typ argumentu zdarzenia można określić jako argument typu, ale można też pozostawić ten typu pusty, co spowoduje, że kompilator wywnioskuje odpowiedni typ. Należy także zdefiniować element członkowski zdarzenia, który będzie uwidaczniał zdarzenie jako zdarzenie CLI. Ten element członkowski powinien mieć atrybut [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) . Jest on zadeklarowany jako właściwość, a jego implementacja jest tylko wywołaniem właściwości [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) zdarzenia. Użytkownicy klasy mogą korzystać `Add` z metody opublikowanego zdarzenia w celu dodania procedury obsługi. Argument `Add` metody może być wyrażeniem lambda. Możesz użyć `Trigger` właściwości zdarzenia, aby zgłosić zdarzenie, przekazując argumenty do funkcji obsługi. Pokazano to w poniższym przykładzie kodu. W tym przykładzie wywnioskowany argument typu dla zdarzenia to spójna kolekcja, która reprezentuje argumenty wyrażenia lambda.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

Dane wyjściowe są następujące:

```
Event1 occurred! Object data: Hello World!
```

Dodatkowe funkcje zapewniane przez `Event` moduł przedstawiono w tym miejscu. Poniższy przykład kodu ilustruje podstawowe użycie `Event.create` programu, aby utworzyć zdarzenie i metodę wyzwalacza, dodać dwa programy obsługi zdarzeń w postaci wyrażeń lambda, a następnie wyzwoli zdarzenie, aby wykonać oba wyrażenia lambda.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

Dane wyjściowe poprzedniego kodu wyglądają następująco:

```
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a>Przetwarzanie strumieni zdarzeń

Zamiast tylko dodać procedurę obsługi zdarzeń dla zdarzenia przy użyciu funkcji [Event. Add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) , można użyć funkcji w `Event` module do przetwarzania strumieni zdarzeń w sposób wysoce dostosowany. W tym celu należy użyć potoku do przodu (`|>`) wraz ze zdarzeniem jako pierwszą wartością w szeregu wywołań funkcji, `Event` a moduł działa jako kolejne wywołania funkcji.

W poniższym przykładzie kodu pokazano, jak skonfigurować zdarzenie, dla którego program obsługi jest wywoływany tylko w określonych warunkach.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

[Moduł zauważalny](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) zawiera podobne funkcje, które działają na obiektach zauważalnych. Widoczne obiekty są podobne do zdarzeń, ale aktywnie subskrybują zdarzenia tylko wtedy, gdy same są subskrybowane.

## <a name="implementing-an-interface-event"></a>Implementowanie zdarzenia interfejsu

Projektowanie składników interfejsu użytkownika często rozpoczyna się od utworzenia nowego formularza lub nowego formantu, który dziedziczy z istniejącego formularza lub formantu. Zdarzenia są często definiowane w interfejsie, a w takim przypadku trzeba zaimplementować interfejs służący do implementacji zdarzeń. Interfejs definiuje pojedyncze `System.ComponentModel.INotifyPropertyChanged.PropertyChanged`zdarzenie. `System.ComponentModel.INotifyPropertyChanged` Poniższy kod ilustruje sposób implementacji zdarzenia definiowanego przez ten dziedziczony interfejs:

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

type AppForm() as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs -> this.Property1 <- "text2"
        this.Property2 <- "text3")

    // This property does not have the property-changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property-changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    // Expose the PropertyChanged event as a first class .NET event.
    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = propertyChanged.Publish.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = propertyChanged.Publish.RemoveHandler(handler)

    // This is the event-handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
let inpc = appForm :> INotifyPropertyChanged
inpc.PropertyChanged.Add(appForm.OnPropertyChanged)
Application.Run(appForm)
```

Jeśli chcesz podłączyć zdarzenie w konstruktorze, kod jest nieco bardziej skomplikowany, ponieważ usługa Event podłączenie musi znajdować się w `then` bloku w dodatkowym konstruktorze, jak w poniższym przykładzie:

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

// Create a private constructor with a dummy argument so that the public
// constructor can have no arguments.
type AppForm private (dummy) as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs -> this.Property1 <- "text2"
        this.Property2 <- "text3")

    // This property does not have the property changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = this.PropertyChanged.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = this.PropertyChanged.RemoveHandler(handler)

    // This is the event handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

    new() as this =
        new AppForm(0)
        then
            let inpc = this :> INotifyPropertyChanged
            inpc.PropertyChanged.Add(this.OnPropertyChanged)

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
Application.Run(appForm)
```

## <a name="see-also"></a>Zobacz także

- [Elementy członkowskie](index.md)
- [Obsługa i wywoływanie zdarzeń](../../../../docs/standard/events/index.md)
- [Wyrażenia lambda: słowo kluczowe `fun`](../functions/lambda-expressions-the-fun-keyword.md)
- [Control. Event — Moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)
- [Control.&#60;eventObject&#62; — Klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)
- [Control. Event&#60;— obiekt "Delegate"&#62; , Klasa args](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
