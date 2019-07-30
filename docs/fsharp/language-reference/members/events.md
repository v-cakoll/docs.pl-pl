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
# <a name="events"></a><span data-ttu-id="a18dd-103">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a18dd-103">Events</span></span>

> [!NOTE]
> <span data-ttu-id="a18dd-104">Linki do odwołań do interfejsów API w tym artykule przeprowadzą Cię do subskrypcji MSDN.</span><span class="sxs-lookup"><span data-stu-id="a18dd-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="a18dd-105">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="a18dd-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="a18dd-106">Zdarzenia umożliwiają kojarzenie wywołań funkcji z akcjami użytkownika i są ważne w programowaniu graficznych interfejsów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a18dd-106">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="a18dd-107">Zdarzenia mogą być też wywoływane przez aplikacje lub system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="a18dd-107">Events can also be triggered by your applications or by the operating system.</span></span>

## <a name="handling-events"></a><span data-ttu-id="a18dd-108">Obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a18dd-108">Handling Events</span></span>

<span data-ttu-id="a18dd-109">Gdy jest używana biblioteka graficznych interfejsów użytkownika, taka jak Windows Forms lub Windows Presentation Foundation (WPF), większość kodu aplikacji działa w odpowiedzi na zdarzenia, które są wstępnie zdefiniowane w tej bibliotece.</span><span class="sxs-lookup"><span data-stu-id="a18dd-109">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="a18dd-110">Te wstępnie zdefiniowane zdarzenia są składowymi klas graficznego interfejsu użytkownika, takich jak formularze i formanty.</span><span class="sxs-lookup"><span data-stu-id="a18dd-110">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="a18dd-111">Niestandardowe zachowanie można dodać do istniejącego zdarzenia, takiego jak kliknięcie przycisku, odwołując się do określonego nazwanego zdarzenia zainteresowania (na przykład `Click` zdarzenia `Form` klasy `Add` ) i wywołując metodę, jak pokazano w poniższym kodzie. .</span><span class="sxs-lookup"><span data-stu-id="a18dd-111">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="a18dd-112">Jeśli uruchamiasz ten program F# z interaktywnego, Pomiń wywołanie `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span><span class="sxs-lookup"><span data-stu-id="a18dd-112">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="a18dd-113">Typ `Add` metody to `('a -> unit) -> unit`.</span><span class="sxs-lookup"><span data-stu-id="a18dd-113">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="a18dd-114">W związku z tym metoda obsługi zdarzeń przyjmuje jeden parametr, zazwyczaj argumenty zdarzenia i zwraca `unit`.</span><span class="sxs-lookup"><span data-stu-id="a18dd-114">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="a18dd-115">W poprzednim przykładzie pokazano program obsługi zdarzeń w postaci wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="a18dd-115">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="a18dd-116">Program obsługi zdarzeń może być także wartością funkcji, tak jak w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="a18dd-116">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="a18dd-117">W poniższym przykładzie kodu pokazano także użycie parametrów programu obsługi zdarzeń, które dostarczają informacje charakterystyczne dla typu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a18dd-117">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="a18dd-118">Dla zdarzenia system `System.Windows.Forms.MouseEventArgs` `Y` przekazuje`X` obiekt, który zawiera położenie wskaźnika i. `MouseMove`</span><span class="sxs-lookup"><span data-stu-id="a18dd-118">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a><span data-ttu-id="a18dd-119">Tworzenie zdarzeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="a18dd-119">Creating Custom Events</span></span>

<span data-ttu-id="a18dd-120">F#zdarzenia są reprezentowane przez F# klasę [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) , która implementuje interfejs [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) .</span><span class="sxs-lookup"><span data-stu-id="a18dd-120">F# events are represented by the F# [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) class, which implements the [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) interface.</span></span> <span data-ttu-id="a18dd-121">`IEvent`jest samym interfejsem, który łączy funkcje dwóch innych interfejsów `System.IObservable<'T>` i [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span><span class="sxs-lookup"><span data-stu-id="a18dd-121">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span></span> <span data-ttu-id="a18dd-122">W związku z tym program `IObservable` F# F# s ma równoważne funkcje delegatów w innych językach oraz dodatkowe funkcje od, co oznacza, że zdarzenia obsługują filtrowanie zdarzeń i używanie funkcji pierwszej klasy i `Event` wyrażenia lambda jako programy obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a18dd-122">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="a18dd-123">Ta funkcja jest dostępna w [module Event](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span><span class="sxs-lookup"><span data-stu-id="a18dd-123">This functionality is provided in the [Event module](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span></span>

<span data-ttu-id="a18dd-124">Aby utworzyć zdarzenie na klasie, która działa podobnie jak wszystkie inne zdarzenia .NET Framework, Dodaj do klasy `let` powiązanie, które `Event` definiuje jako pole w klasie.</span><span class="sxs-lookup"><span data-stu-id="a18dd-124">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="a18dd-125">Odpowiedni typ argumentu zdarzenia można określić jako argument typu, ale można też pozostawić ten typu pusty, co spowoduje, że kompilator wywnioskuje odpowiedni typ.</span><span class="sxs-lookup"><span data-stu-id="a18dd-125">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="a18dd-126">Należy także zdefiniować element członkowski zdarzenia, który będzie uwidaczniał zdarzenie jako zdarzenie CLI.</span><span class="sxs-lookup"><span data-stu-id="a18dd-126">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="a18dd-127">Ten element członkowski powinien mieć atrybut [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) .</span><span class="sxs-lookup"><span data-stu-id="a18dd-127">This member should have the [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) attribute.</span></span> <span data-ttu-id="a18dd-128">Jest on zadeklarowany jako właściwość, a jego implementacja jest tylko wywołaniem właściwości [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a18dd-128">It is declared like a property and its implementation is just a call to the [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) property of the event.</span></span> <span data-ttu-id="a18dd-129">Użytkownicy klasy mogą korzystać `Add` z metody opublikowanego zdarzenia w celu dodania procedury obsługi.</span><span class="sxs-lookup"><span data-stu-id="a18dd-129">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="a18dd-130">Argument `Add` metody może być wyrażeniem lambda.</span><span class="sxs-lookup"><span data-stu-id="a18dd-130">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="a18dd-131">Możesz użyć `Trigger` właściwości zdarzenia, aby zgłosić zdarzenie, przekazując argumenty do funkcji obsługi.</span><span class="sxs-lookup"><span data-stu-id="a18dd-131">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="a18dd-132">Pokazano to w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="a18dd-132">The following code example illustrates this.</span></span> <span data-ttu-id="a18dd-133">W tym przykładzie wywnioskowany argument typu dla zdarzenia to spójna kolekcja, która reprezentuje argumenty wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="a18dd-133">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="a18dd-134">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="a18dd-134">The output is as follows.</span></span>

```
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="a18dd-135">Dodatkowe funkcje zapewniane przez `Event` moduł przedstawiono w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="a18dd-135">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="a18dd-136">Poniższy przykład kodu ilustruje podstawowe użycie `Event.create` programu, aby utworzyć zdarzenie i metodę wyzwalacza, dodać dwa programy obsługi zdarzeń w postaci wyrażeń lambda, a następnie wyzwoli zdarzenie, aby wykonać oba wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="a18dd-136">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="a18dd-137">Dane wyjściowe poprzedniego kodu wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="a18dd-137">The output of the previous code is as follows.</span></span>

```
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="a18dd-138">Przetwarzanie strumieni zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a18dd-138">Processing Event Streams</span></span>

<span data-ttu-id="a18dd-139">Zamiast tylko dodać procedurę obsługi zdarzeń dla zdarzenia przy użyciu funkcji [Event. Add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) , można użyć funkcji w `Event` module do przetwarzania strumieni zdarzeń w sposób wysoce dostosowany.</span><span class="sxs-lookup"><span data-stu-id="a18dd-139">Instead of just adding an event handler for an event by using the [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="a18dd-140">W tym celu należy użyć potoku do przodu (`|>`) wraz ze zdarzeniem jako pierwszą wartością w szeregu wywołań funkcji, `Event` a moduł działa jako kolejne wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="a18dd-140">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="a18dd-141">W poniższym przykładzie kodu pokazano, jak skonfigurować zdarzenie, dla którego program obsługi jest wywoływany tylko w określonych warunkach.</span><span class="sxs-lookup"><span data-stu-id="a18dd-141">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="a18dd-142">[Moduł zauważalny](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) zawiera podobne funkcje, które działają na obiektach zauważalnych.</span><span class="sxs-lookup"><span data-stu-id="a18dd-142">The [Observable module](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="a18dd-143">Widoczne obiekty są podobne do zdarzeń, ale aktywnie subskrybują zdarzenia tylko wtedy, gdy same są subskrybowane.</span><span class="sxs-lookup"><span data-stu-id="a18dd-143">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>

## <a name="implementing-an-interface-event"></a><span data-ttu-id="a18dd-144">Implementowanie zdarzenia interfejsu</span><span class="sxs-lookup"><span data-stu-id="a18dd-144">Implementing an Interface Event</span></span>

<span data-ttu-id="a18dd-145">Projektowanie składników interfejsu użytkownika często rozpoczyna się od utworzenia nowego formularza lub nowego formantu, który dziedziczy z istniejącego formularza lub formantu.</span><span class="sxs-lookup"><span data-stu-id="a18dd-145">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="a18dd-146">Zdarzenia są często definiowane w interfejsie, a w takim przypadku trzeba zaimplementować interfejs służący do implementacji zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a18dd-146">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="a18dd-147">Interfejs definiuje pojedyncze `System.ComponentModel.INotifyPropertyChanged.PropertyChanged`zdarzenie. `System.ComponentModel.INotifyPropertyChanged`</span><span class="sxs-lookup"><span data-stu-id="a18dd-147">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="a18dd-148">Poniższy kod ilustruje sposób implementacji zdarzenia definiowanego przez ten dziedziczony interfejs:</span><span class="sxs-lookup"><span data-stu-id="a18dd-148">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

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

<span data-ttu-id="a18dd-149">Jeśli chcesz podłączyć zdarzenie w konstruktorze, kod jest nieco bardziej skomplikowany, ponieważ usługa Event podłączenie musi znajdować się w `then` bloku w dodatkowym konstruktorze, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a18dd-149">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a18dd-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a18dd-150">See also</span></span>

- [<span data-ttu-id="a18dd-151">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a18dd-151">Members</span></span>](index.md)
- [<span data-ttu-id="a18dd-152">Obsługa i wywoływanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a18dd-152">Handling and Raising Events</span></span>](../../../../docs/standard/events/index.md)
- [<span data-ttu-id="a18dd-153">Wyrażenia lambda: słowo kluczowe `fun`</span><span class="sxs-lookup"><span data-stu-id="a18dd-153">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)
- [<span data-ttu-id="a18dd-154">Control. Event — Moduł</span><span class="sxs-lookup"><span data-stu-id="a18dd-154">Control.Event Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)
- [<span data-ttu-id="a18dd-155">Control.&#60;eventObject&#62; — Klasa</span><span class="sxs-lookup"><span data-stu-id="a18dd-155">Control.Event&#60;'T&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)
- [<span data-ttu-id="a18dd-156">Control. Event&#60;— obiekt "Delegate"&#62; , Klasa args</span><span class="sxs-lookup"><span data-stu-id="a18dd-156">Control.Event&#60;'Delegate,'Args&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
