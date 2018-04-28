---
title: Zdarzenia (F#)
description: 'Dowiedz się, jak zdarzenia F # umożliwiają skojarzyć wywołania funkcji z akcje użytkownika, które są ważne w programowaniu graficznego interfejsu użytkownika.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 5c5f152830d4d91a25c79a09800263cdd85ed8b7
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="events"></a>Zdarzenia

> [!NOTE]
Interfejs API łącza odwołań w tym artykule spowoduje przejście do MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

Zdarzenia umożliwiają kojarzenie wywołań funkcji z akcjami użytkownika i są ważne w programowaniu graficznych interfejsów użytkownika. Zdarzenia mogą być też wywoływane przez aplikacje lub system operacyjny.

## <a name="handling-events"></a>Obsługa zdarzeń
Gdy jest używana biblioteka graficznych interfejsów użytkownika, taka jak Windows Forms lub Windows Presentation Foundation (WPF), większość kodu aplikacji działa w odpowiedzi na zdarzenia, które są wstępnie zdefiniowane w tej bibliotece. Te wstępnie zdefiniowane zdarzenia są składowymi klas graficznego interfejsu użytkownika, takich jak formularze i formanty. Niestandardowe zachowanie można dodawać do istniejących zdarzeń, takie jak kliknij przycisk, za pomocą odwołań do konkretnego o nazwie zdarzenia zainteresowań (na przykład `Click` zdarzenie `Form` klasy) i wywoływanie `Add` metody, jak pokazano w poniższym kodzie . Jeśli to jest uruchamiane z F # Interactive, pominąć wywołanie `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

Typ `Add` jest metoda `('a -> unit) -> unit`. W związku z tym metoda obsługi zdarzeń przyjmuje jeden parametr, zwykle argumenty zdarzeń i zwraca `unit`. W poprzednim przykładzie pokazano program obsługi zdarzeń w postaci wyrażenia lambda. Program obsługi zdarzeń może być także wartością funkcji, tak jak w poniższym przykładzie kodu. W poniższym przykładzie kodu pokazano także użycie parametrów programu obsługi zdarzeń, które dostarczają informacje charakterystyczne dla typu zdarzenia. Aby uzyskać `MouseMove` przekazuje systemu zdarzeń, `System.Windows.Forms.MouseEventArgs` obiekt, który zawiera `X` i `Y` położenia wskaźnika.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]
    
## <a name="creating-custom-events"></a>Tworzenie zdarzeń niestandardowych
F # zdarzenia są reprezentowane przez język F # [zdarzeń](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) klasy, która implementuje [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) interfejsu. `IEvent` jest elementem interfejsu, który łączy funkcje dwa inne interfejsy `System.IObservable<'T>` i [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a). W związku z tym `Event`są równoważne funkcje delegatów w innych językach, a także dodatkowe funkcje z `IObservable`, co oznacza, że zdarzenia F # obsługuje filtrowanie zdarzeń i przy użyciu funkcji najwyższej jakości F # i wyrażenia lambda jako procedury obsługi zdarzeń. Ta funkcja jest udostępniany w [modułu zdarzeń](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).

Aby utworzyć zdarzenia dla klasy, która działa tak samo jak inne zdarzenia .NET Framework, Dodaj do klasy `let` powiązania, który definiuje `Event` jako pole w klasie. Odpowiedni typ argumentu zdarzenia można określić jako argument typu, ale można też pozostawić ten typu pusty, co spowoduje, że kompilator wywnioskuje odpowiedni typ. Należy także zdefiniować element członkowski zdarzenia, który będzie uwidaczniał zdarzenie jako zdarzenie CLI. Ten element członkowski powinien mieć [clievent —](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) atrybutu. Jest on zadeklarowany jako jak właściwości, oraz jego implementacji tylko wywołania [publikowania](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) właściwości zdarzenia. Klasy umożliwia `Add` metody opublikowanych zdarzenia w celu dodania programu obsługi. Argument `Add` metoda może być wyrażenie lambda. Można użyć `Trigger` właściwości zdarzenia, aby zgłosić zdarzenie, przekazywanie argumentów do funkcji programu obsługi. Pokazano to w poniższym przykładzie kodu. W tym przykładzie wywnioskowany argument typu dla zdarzenia to spójna kolekcja, która reprezentuje argumenty wyrażenia lambda.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

Dane wyjściowe są następujące:

```
Event1 occurred! Object data: Hello World!
```

Dodatkowe funkcje udostępniane przez `Event` modułu przedstawiono w tym miejscu. Poniższy przykładowy kod przedstawia podstawowe wykorzystanie `Event.create` utworzyć zdarzenie i metody wyzwalacza, Dodaj dwie procedury obsługi zdarzeń w postaci wyrażenia lambda i wyzwolić zdarzenie można wykonać oba wyrażenia lambda.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

Dane wyjściowe poprzedniego kodu wyglądają następująco:

```
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a>Przetwarzanie strumieni zdarzeń
Zamiast tylko dodawanie obsługi zdarzeń dla zdarzenia za pomocą [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) funkcji, możesz użyć funkcji w `Event` modułu do przetwarzania strumieni zdarzeń w sposób wysoce dostosowane. Aby to zrobić, należy użyć potoku do przodu (`|>`) wraz z zdarzeń jako pierwsza wartość szereg wywołania funkcji i `Event` modułu działa jako wywołania funkcji kolejne.

W poniższym przykładzie kodu pokazano, jak skonfigurować zdarzenie, dla którego program obsługi jest wywoływany tylko w określonych warunkach.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

[Observable — moduł](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) zawiera podobne funkcje, które pracują na zauważalne obiektów. Widoczne obiekty są podobne do zdarzeń, ale aktywnie subskrybują zdarzenia tylko wtedy, gdy same są subskrybowane.


## <a name="implementing-an-interface-event"></a>Implementowanie zdarzenia interfejsu
Projektowanie składników interfejsu użytkownika często rozpoczyna się od utworzenia nowego formularza lub nowego formantu, który dziedziczy z istniejącego formularza lub formantu. Zdarzenia są często definiowane w interfejsie, a w takim przypadku trzeba zaimplementować interfejs służący do implementacji zdarzeń. `System.ComponentModel.INotifyPropertyChanged` Interfejs definiuje jedną `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` zdarzeń. Poniższy kod ilustruje sposób implementacji zdarzenia definiowanego przez ten dziedziczony interfejs:

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

Jeśli chcesz podpinanie zdarzeń w Konstruktorze kod jest nieco bardziej skomplikowane, ponieważ podłączenie zdarzenia musi być w `then` blok w Konstruktorze dodatkowe, jak w poniższym przykładzie:

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

## <a name="see-also"></a>Zobacz też
[Elementy członkowskie](index.md)

[Obsługa i wywoływanie zdarzeń](../../../../docs/standard/events/index.md)

[Wyrażenia lambda: `fun` — słowo kluczowe](../functions/lambda-expressions-the-fun-keyword.md)

[Control.Event — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)

[Control.Event —&#60;'T&#62; — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)

[Control.Event —&#60;"Delegate", argumentów&#62; — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
