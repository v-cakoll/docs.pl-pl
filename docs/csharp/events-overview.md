---
title: Wprowadzenie do zdarzeń
description: Dowiedz się więcej o zdarzeniach w .NET Core i cele projektu języka firmy Microsoft zdarzeń w tym omówieniu.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 9f14954dd2e8aeacf3c5ae70a9e891ad11a6f0d7
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45509578"
---
# <a name="introduction-to-events"></a><span data-ttu-id="6e320-103">Wprowadzenie do zdarzeń</span><span class="sxs-lookup"><span data-stu-id="6e320-103">Introduction to Events</span></span>

[<span data-ttu-id="6e320-104">Poprzednie</span><span class="sxs-lookup"><span data-stu-id="6e320-104">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="6e320-105">Zdarzenia są takie jak delegatów, *późnym wiązaniu* mechanizm.</span><span class="sxs-lookup"><span data-stu-id="6e320-105">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="6e320-106">W rzeczywistości zdarzenia są tworzone na temat obsługi języków dla obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="6e320-106">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="6e320-107">Zdarzenia są sposób obiektowi emisji (do wszystkich zainteresowanych składników w systemie), że coś się stało.</span><span class="sxs-lookup"><span data-stu-id="6e320-107">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="6e320-108">Jakikolwiek inny składnik może być subskrybowana przez zdarzenie, a otrzymasz powiadomienie, gdy wydarzenie jest podniesione.</span><span class="sxs-lookup"><span data-stu-id="6e320-108">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="6e320-109">Prawdopodobnie wykorzystano zdarzenia w niektórych z programowania.</span><span class="sxs-lookup"><span data-stu-id="6e320-109">You've probably used events in some of your programming.</span></span> <span data-ttu-id="6e320-110">Wiele systemów graficzne mają model zdarzeń na interakcję z użytkownikiem raportu.</span><span class="sxs-lookup"><span data-stu-id="6e320-110">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="6e320-111">Te zdarzenia będą raportów ruchów myszy, naciśnięcie przycisku i podobne interakcje.</span><span class="sxs-lookup"><span data-stu-id="6e320-111">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="6e320-112">Jest to jeden z najbardziej typowych, ale na pewno nie tylko scenariusz użycia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6e320-112">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="6e320-113">Można zdefiniować zdarzenia, które powinien być wywoływany dla swojej klasy.</span><span class="sxs-lookup"><span data-stu-id="6e320-113">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="6e320-114">Ważnym zagadnieniem podczas pracy ze zdarzeniami jest to, że może być dowolny obiekt zarejestrowane dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6e320-114">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="6e320-115">Należy napisać kod, aby nie zgłaszała zdarzenia w przypadku odbiorników nie są skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="6e320-115">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="6e320-116">Subskrybowanie zdarzenia tworzy sprzężenie między dwoma obiektami (źródło zdarzenia i obiekt sink zdarzenia).</span><span class="sxs-lookup"><span data-stu-id="6e320-116">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="6e320-117">Należy upewnić się, że obiekt sink zdarzenia anuluje subskrypcje ze źródła zdarzeń, gdy nie jest już są Państwo zainteresowani zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6e320-117">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="6e320-118">Cele projektu do obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="6e320-118">Design Goals for Event Support</span></span>

<span data-ttu-id="6e320-119">Projektowanie języków dla zdarzeń jest przeznaczony dla tych celów.</span><span class="sxs-lookup"><span data-stu-id="6e320-119">The language design for events targets these goals.</span></span>

<span data-ttu-id="6e320-120">Najpierw należy włączyć minimalny sprzężenia między źródłem zdarzeń i obiekt sink zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6e320-120">First, enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="6e320-121">Te dwa składniki nie może zapisywać w tej samej organizacji, a nawet mogą być aktualizowane zgodnie z harmonogramami coś zupełnie innego.</span><span class="sxs-lookup"><span data-stu-id="6e320-121">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

<span data-ttu-id="6e320-122">Po drugie powinny być bardzo prosty, aby subskrybować zdarzenia i zrezygnować z tego samego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6e320-122">Secondly, it should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

<span data-ttu-id="6e320-123">I wreszcie źródła zdarzeń powinien obsługiwać wielu subskrybentów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6e320-123">And finally, event sources should support multiple event subscribers.</span></span> <span data-ttu-id="6e320-124">Powinien również obsługiwać, posiadające żadnych subskrybentów zdarzeń dołączonych.</span><span class="sxs-lookup"><span data-stu-id="6e320-124">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="6e320-125">Widać, że cele dotyczące zdarzenia są bardzo podobne do celów dla obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="6e320-125">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="6e320-126">Dlatego obsługę języka zdarzeń jest oparta na obsługę języka delegata.</span><span class="sxs-lookup"><span data-stu-id="6e320-126">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="6e320-127">Obsługa języka dla zdarzeń</span><span class="sxs-lookup"><span data-stu-id="6e320-127">Language Support for Events</span></span>

<span data-ttu-id="6e320-128">Składnia służąca do definiowania zdarzenia, subskrypcji i anulowanie subskrypcji zdarzeń jest rozszerzeniem składni dla obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="6e320-128">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="6e320-129">Aby zdefiniować określone zdarzenie, możesz użyć `event` — słowo kluczowe:</span><span class="sxs-lookup"><span data-stu-id="6e320-129">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="6e320-130">Typ zdarzenia (`EventHandler<FileListArgs>` w tym przykładzie) musi być typem delegowanym.</span><span class="sxs-lookup"><span data-stu-id="6e320-130">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="6e320-131">Istnieje szereg Konwencji, które należy wykonać podczas deklarowania zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="6e320-131">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="6e320-132">Zazwyczaj typ delegata zdarzenia ma zwracany typ void.</span><span class="sxs-lookup"><span data-stu-id="6e320-132">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="6e320-133">Deklaracje zdarzeń powinna być czasownikiem lub frazy zlecenie.</span><span class="sxs-lookup"><span data-stu-id="6e320-133">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="6e320-134">Użyj przeszłym (w tym przykładzie), gdy zdarzenie zgłasza coś, co się stało.</span><span class="sxs-lookup"><span data-stu-id="6e320-134">Use past tense (as in this example) when the event reports something that has happened.</span></span> <span data-ttu-id="6e320-135">Użyj zlecenie teraźniejszego (na przykład `Closing`) do zgłaszania coś, co się stanie.</span><span class="sxs-lookup"><span data-stu-id="6e320-135">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="6e320-136">Często przy użyciu teraźniejszego wskazuje, że klasa obsługuje pewnego rodzaju dostosowywania zachowania.</span><span class="sxs-lookup"><span data-stu-id="6e320-136">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="6e320-137">Jednym z najbardziej typowych scenariuszy jest aby zapewnić obsługę anulowania.</span><span class="sxs-lookup"><span data-stu-id="6e320-137">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="6e320-138">Na przykład `Closing` zdarzeń może zawierać argument, który będzie wskazywać, jeśli operacja zamykania należy kontynuować, lub nie.</span><span class="sxs-lookup"><span data-stu-id="6e320-138">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="6e320-139">Inne scenariusze mogą umożliwiać wywołań zmodyfikować zachowanie, aktualizując właściwości argumentów zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6e320-139">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="6e320-140">Może wywołać zdarzenie, aby wskazać proponowane następnej akcji, który zajmie algorytm.</span><span class="sxs-lookup"><span data-stu-id="6e320-140">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="6e320-141">Program obsługi zdarzeń może uzasadniają różne akcje, modyfikując właściwości argumentu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6e320-141">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="6e320-142">Jeśli chcesz zgłosić zdarzenie, wywołujesz procedury obsługi zdarzeń przy użyciu składni wywołania delegata:</span><span class="sxs-lookup"><span data-stu-id="6e320-142">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="6e320-143">Zgodnie z opisem w sekcji na [delegatów](delegates-patterns.md),?.</span><span class="sxs-lookup"><span data-stu-id="6e320-143">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="6e320-144">Operator ułatwia zapewnienie, że należy próbować zgłosić zdarzenie, gdy istnieją nie subskrybenci tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6e320-144">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>
 
<span data-ttu-id="6e320-145">Subskrybowanie zdarzenia przy użyciu `+=` operator:</span><span class="sxs-lookup"><span data-stu-id="6e320-145">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);
lister.Progress += onProgress;
```

<span data-ttu-id="6e320-146">Metody obsługi zwykle jest prefiksem "On" następuje nazwa zdarzenia, jak pokazano powyżej.</span><span class="sxs-lookup"><span data-stu-id="6e320-146">The handler method typically is the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="6e320-147">Anulowanie subskrypcji przy użyciu `-=` operator:</span><span class="sxs-lookup"><span data-stu-id="6e320-147">You unsubscribe using the `-=` operator:</span></span>

```csharp
lister.Progress -= onProgress;
```

<span data-ttu-id="6e320-148">Należy zauważyć, że uznana za zmienną lokalną dla wyrażenia, który reprezentuje program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6e320-148">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="6e320-149">Dzięki temu usuwa Anuluj subskrypcję programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="6e320-149">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="6e320-150">Jeśli zamiast tego użyto treść wyrażenia lambda, którą chcesz usunąć program obsługi, który nigdy nie został dołączony, która nie wykonuje żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="6e320-150">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="6e320-151">W następnym artykule dowiesz się więcej na temat zdarzeń typowych wzorców i różne odmiany w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6e320-151">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="6e320-152">Next</span><span class="sxs-lookup"><span data-stu-id="6e320-152">Next</span></span>](event-pattern.md)
