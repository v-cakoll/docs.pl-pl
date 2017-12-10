---
title: Zdarzenia (F#)
description: "Dowiedz się, jak zdarzenia F # umożliwiają skojarzyć wywołania funkcji z akcje użytkownika, które są ważne w programowaniu graficznego interfejsu użytkownika."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 28b588f2-0c9e-4c0d-babf-901ed934638a
ms.openlocfilehash: 9465f33bac6fa8234f684ddefe24cbe4d6c71028
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="events"></a><span data-ttu-id="f2458-104">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f2458-104">Events</span></span>

> [!NOTE]
<span data-ttu-id="f2458-105">Interfejs API łącza odwołań w tym artykule spowoduje przejście do MSDN.</span><span class="sxs-lookup"><span data-stu-id="f2458-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="f2458-106">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="f2458-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="f2458-107">Zdarzenia umożliwiają kojarzenie wywołań funkcji z akcjami użytkownika i są ważne w programowaniu graficznych interfejsów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f2458-107">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="f2458-108">Zdarzenia mogą być też wywoływane przez aplikacje lub system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="f2458-108">Events can also be triggered by your applications or by the operating system.</span></span>

## <a name="handling-events"></a><span data-ttu-id="f2458-109">Obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="f2458-109">Handling Events</span></span>
<span data-ttu-id="f2458-110">Gdy jest używana biblioteka graficznych interfejsów użytkownika, taka jak Windows Forms lub Windows Presentation Foundation (WPF), większość kodu aplikacji działa w odpowiedzi na zdarzenia, które są wstępnie zdefiniowane w tej bibliotece.</span><span class="sxs-lookup"><span data-stu-id="f2458-110">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="f2458-111">Te wstępnie zdefiniowane zdarzenia są składowymi klas graficznego interfejsu użytkownika, takich jak formularze i formanty.</span><span class="sxs-lookup"><span data-stu-id="f2458-111">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="f2458-112">Niestandardowe zachowanie można dodawać do istniejących zdarzeń, takie jak kliknij przycisk, za pomocą odwołań do konkretnego o nazwie zdarzenia zainteresowań (na przykład `Click` zdarzenie `Form` klasy) i wywoływanie `Add` metody, jak pokazano w poniższym kodzie .</span><span class="sxs-lookup"><span data-stu-id="f2458-112">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="f2458-113">Jeśli to jest uruchamiane z F # Interactive, pominąć wywołanie `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span><span class="sxs-lookup"><span data-stu-id="f2458-113">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="f2458-114">Typ `Add` jest metoda `('a -> unit) -> unit`.</span><span class="sxs-lookup"><span data-stu-id="f2458-114">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="f2458-115">W związku z tym metoda obsługi zdarzeń przyjmuje jeden parametr, zwykle argumenty zdarzeń i zwraca `unit`.</span><span class="sxs-lookup"><span data-stu-id="f2458-115">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="f2458-116">W poprzednim przykładzie pokazano program obsługi zdarzeń w postaci wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="f2458-116">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="f2458-117">Program obsługi zdarzeń może być także wartością funkcji, tak jak w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="f2458-117">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="f2458-118">W poniższym przykładzie kodu pokazano także użycie parametrów programu obsługi zdarzeń, które dostarczają informacje charakterystyczne dla typu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f2458-118">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="f2458-119">Aby uzyskać `MouseMove` przekazuje systemu zdarzeń, `System.Windows.Forms.MouseEventArgs` obiekt, który zawiera `X` i `Y` położenia wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="f2458-119">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]
    
## <a name="creating-custom-events"></a><span data-ttu-id="f2458-120">Tworzenie zdarzeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="f2458-120">Creating Custom Events</span></span>
<span data-ttu-id="f2458-121">F # zdarzenia są reprezentowane przez język F # [zdarzeń](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) klasy, która implementuje [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f2458-121">F# events are represented by the F# [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) class, which implements the [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) interface.</span></span> <span data-ttu-id="f2458-122">`IEvent`jest elementem interfejsu, który łączy funkcje dwa inne interfejsy `System.IObservable<'T>` i [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span><span class="sxs-lookup"><span data-stu-id="f2458-122">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span></span> <span data-ttu-id="f2458-123">W związku z tym `Event`są równoważne funkcje delegatów w innych językach, a także dodatkowe funkcje z `IObservable`, co oznacza, że zdarzenia F # obsługuje filtrowanie zdarzeń i przy użyciu funkcji najwyższej jakości F # i wyrażenia lambda jako procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f2458-123">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="f2458-124">Ta funkcja jest udostępniany w [modułu zdarzeń](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span><span class="sxs-lookup"><span data-stu-id="f2458-124">This functionality is provided in the [Event module](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span></span>

<span data-ttu-id="f2458-125">Aby utworzyć zdarzenia dla klasy, która działa tak samo jak inne zdarzenia .NET Framework, Dodaj do klasy `let` powiązania, który definiuje `Event` jako pole w klasie.</span><span class="sxs-lookup"><span data-stu-id="f2458-125">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="f2458-126">Odpowiedni typ argumentu zdarzenia można określić jako argument typu, ale można też pozostawić ten typu pusty, co spowoduje, że kompilator wywnioskuje odpowiedni typ.</span><span class="sxs-lookup"><span data-stu-id="f2458-126">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="f2458-127">Należy także zdefiniować element członkowski zdarzenia, który będzie uwidaczniał zdarzenie jako zdarzenie CLI.</span><span class="sxs-lookup"><span data-stu-id="f2458-127">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="f2458-128">Ten element członkowski powinien mieć [clievent —](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f2458-128">This member should have the [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) attribute.</span></span> <span data-ttu-id="f2458-129">Jest on zadeklarowany jako jak właściwości, oraz jego implementacji tylko wywołania [publikowania](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) właściwości zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f2458-129">It is declared like a property and its implementation is just a call to the [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) property of the event.</span></span> <span data-ttu-id="f2458-130">Klasy umożliwia `Add` metody opublikowanych zdarzenia w celu dodania programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="f2458-130">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="f2458-131">Argument `Add` metoda może być wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="f2458-131">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="f2458-132">Można użyć `Trigger` właściwości zdarzenia, aby zgłosić zdarzenie, przekazywanie argumentów do funkcji programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="f2458-132">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="f2458-133">Pokazano to w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="f2458-133">The following code example illustrates this.</span></span> <span data-ttu-id="f2458-134">W tym przykładzie wywnioskowany argument typu dla zdarzenia to spójna kolekcja, która reprezentuje argumenty wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="f2458-134">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="f2458-135">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="f2458-135">The output is as follows.</span></span>

```
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="f2458-136">Dodatkowe funkcje udostępniane przez `Event` modułu przedstawiono w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="f2458-136">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="f2458-137">Poniższy przykładowy kod przedstawia podstawowe wykorzystanie `Event.create` utworzyć zdarzenie i metody wyzwalacza, Dodaj dwie procedury obsługi zdarzeń w postaci wyrażenia lambda i wyzwolić zdarzenie można wykonać oba wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="f2458-137">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="f2458-138">Dane wyjściowe poprzedniego kodu wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="f2458-138">The output of the previous code is as follows.</span></span>

```
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="f2458-139">Przetwarzanie strumieni zdarzeń</span><span class="sxs-lookup"><span data-stu-id="f2458-139">Processing Event Streams</span></span>
<span data-ttu-id="f2458-140">Zamiast tylko dodawanie obsługi zdarzeń dla zdarzenia za pomocą [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) funkcji, możesz użyć funkcji w `Event` modułu do przetwarzania strumieni zdarzeń w sposób wysoce dostosowane.</span><span class="sxs-lookup"><span data-stu-id="f2458-140">Instead of just adding an event handler for an event by using the [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="f2458-141">Aby to zrobić, należy użyć potoku do przodu (`|>`) wraz z zdarzeń jako pierwsza wartość szereg wywołania funkcji i `Event` modułu działa jako wywołania funkcji kolejne.</span><span class="sxs-lookup"><span data-stu-id="f2458-141">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="f2458-142">W poniższym przykładzie kodu pokazano, jak skonfigurować zdarzenie, dla którego program obsługi jest wywoływany tylko w określonych warunkach.</span><span class="sxs-lookup"><span data-stu-id="f2458-142">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="f2458-143">[Observable — moduł](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) zawiera podobne funkcje, które pracują na zauważalne obiektów.</span><span class="sxs-lookup"><span data-stu-id="f2458-143">The [Observable module](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="f2458-144">Widoczne obiekty są podobne do zdarzeń, ale aktywnie subskrybują zdarzenia tylko wtedy, gdy same są subskrybowane.</span><span class="sxs-lookup"><span data-stu-id="f2458-144">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>


## <a name="implementing-an-interface-event"></a><span data-ttu-id="f2458-145">Implementowanie zdarzenia interfejsu</span><span class="sxs-lookup"><span data-stu-id="f2458-145">Implementing an Interface Event</span></span>
<span data-ttu-id="f2458-146">Projektowanie składników interfejsu użytkownika często rozpoczyna się od utworzenia nowego formularza lub nowego formantu, który dziedziczy z istniejącego formularza lub formantu.</span><span class="sxs-lookup"><span data-stu-id="f2458-146">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="f2458-147">Zdarzenia są często definiowane w interfejsie, a w takim przypadku trzeba zaimplementować interfejs służący do implementacji zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f2458-147">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="f2458-148">`System.ComponentModel.INotifyPropertyChanged` Interfejs definiuje jedną `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f2458-148">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="f2458-149">Poniższy kod ilustruje sposób implementacji zdarzenia definiowanego przez ten dziedziczony interfejs:</span><span class="sxs-lookup"><span data-stu-id="f2458-149">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

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

<span data-ttu-id="f2458-150">Jeśli chcesz podpinanie zdarzeń w Konstruktorze kod jest nieco bardziej skomplikowane, ponieważ podłączenie zdarzenia musi być w `then` blok w Konstruktorze dodatkowe, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f2458-150">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f2458-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2458-151">See Also</span></span>
[<span data-ttu-id="f2458-152">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f2458-152">Members</span></span>](index.md)

[<span data-ttu-id="f2458-153">Obsługa i wywoływanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="f2458-153">Handling and Raising Events</span></span>](../../../../docs/standard/events/index.md)

[<span data-ttu-id="f2458-154">Wyrażenia lambda: `fun` — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="f2458-154">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)

[<span data-ttu-id="f2458-155">Control.Event — moduł</span><span class="sxs-lookup"><span data-stu-id="f2458-155">Control.Event Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)

[<span data-ttu-id="f2458-156">Control.Event — &#60; " T &#62; Klasy</span><span class="sxs-lookup"><span data-stu-id="f2458-156">Control.Event&#60;'T&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)

[<span data-ttu-id="f2458-157">Control.Event — &#60; " Delegat,'Args &#62; Klasy</span><span class="sxs-lookup"><span data-stu-id="f2458-157">Control.Event&#60;'Delegate,'Args&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
