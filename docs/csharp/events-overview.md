---
title: Wprowadzenie do zdarzeń
description: Zapoznaj się z informacjami o zdarzeniach w programie .NET Core i naszych celach projektowania języka dla zdarzeń w tym omówieniu.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: b1fd2ebe2ae91b55c9179f280d8894f6b40ced9b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771918"
---
# <a name="introduction-to-events"></a><span data-ttu-id="dc027-103">Wprowadzenie do zdarzeń</span><span class="sxs-lookup"><span data-stu-id="dc027-103">Introduction to Events</span></span>

[<span data-ttu-id="dc027-104">Ubiegł</span><span class="sxs-lookup"><span data-stu-id="dc027-104">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="dc027-105">Zdarzenia są takie jak Delegaty, mechanizm *późnego wiązania* .</span><span class="sxs-lookup"><span data-stu-id="dc027-105">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="dc027-106">W rzeczywistości zdarzenia są tworzone w oparciu o obsługę języka dla delegatów.</span><span class="sxs-lookup"><span data-stu-id="dc027-106">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="dc027-107">Zdarzenia są sposobem na wyemitowanie obiektu (do wszystkich zainteresowanych składników w systemie), które wystąpiły.</span><span class="sxs-lookup"><span data-stu-id="dc027-107">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="dc027-108">Każdy inny składnik może subskrybować zdarzenie i otrzymywać powiadomienia o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="dc027-108">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="dc027-109">Prawdopodobnie wykorzystano zdarzenia w niektórych programowaniu.</span><span class="sxs-lookup"><span data-stu-id="dc027-109">You've probably used events in some of your programming.</span></span> <span data-ttu-id="dc027-110">Wiele systemów graficznych ma model zdarzeń służący do zgłaszania interakcji z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="dc027-110">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="dc027-111">Te zdarzenia spowodują przemieszczenie myszy, naciśnięcie przycisków i podobne interakcje.</span><span class="sxs-lookup"><span data-stu-id="dc027-111">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="dc027-112">Jest to jeden z najczęstszych, ale nie jedyny scenariusz, w którym są używane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="dc027-112">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="dc027-113">Można zdefiniować zdarzenia, które powinny być zgłaszane dla klas.</span><span class="sxs-lookup"><span data-stu-id="dc027-113">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="dc027-114">Ważnym zagadnieniem podczas pracy ze zdarzeniami jest fakt, że nie istnieje żaden obiekt zarejestrowany dla danego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="dc027-114">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="dc027-115">Należy napisać kod, aby nie zgłaszał zdarzeń, gdy nie skonfigurowano żadnych odbiorników.</span><span class="sxs-lookup"><span data-stu-id="dc027-115">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="dc027-116">Subskrybowanie zdarzenia również tworzy sprzężenie między dwoma obiektami (źródłem zdarzenia i ujścia zdarzeń).</span><span class="sxs-lookup"><span data-stu-id="dc027-116">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="dc027-117">Musisz się upewnić, że obiekt ujścia zdarzeń anuluje subskrypcję źródła zdarzeń, gdy nie będą już zainteresowani zdarzeniami.</span><span class="sxs-lookup"><span data-stu-id="dc027-117">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="dc027-118">Cele projektu dotyczące obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="dc027-118">Design Goals for Event Support</span></span>

<span data-ttu-id="dc027-119">Projektowanie języka dla zdarzeń przeznaczonych dla tych celów.</span><span class="sxs-lookup"><span data-stu-id="dc027-119">The language design for events targets these goals.</span></span>

<span data-ttu-id="dc027-120">Najpierw włącz bardzo minimalne sprzęganie między źródłem zdarzenia a obiektem sink zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="dc027-120">First, enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="dc027-121">Te dwa składniki mogą nie być zapisywane w tej samej organizacji i mogą nawet być aktualizowane w odniesieniu do całkowicie różnych harmonogramów.</span><span class="sxs-lookup"><span data-stu-id="dc027-121">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

<span data-ttu-id="dc027-122">Po drugie, powinno być bardzo proste, aby subskrybować wydarzenie i anulować subskrypcję tego samego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="dc027-122">Secondly, it should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

<span data-ttu-id="dc027-123">Ponadto źródła zdarzeń powinny obsługiwać wielu subskrybentów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="dc027-123">And finally, event sources should support multiple event subscribers.</span></span> <span data-ttu-id="dc027-124">Dział IT powinien również obsługiwać niedołączone Subskrybenci zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="dc027-124">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="dc027-125">Można zobaczyć, że cele dla zdarzeń są bardzo podobne do celów delegatów.</span><span class="sxs-lookup"><span data-stu-id="dc027-125">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="dc027-126">Dlatego obsługa języka zdarzeń jest oparta na obsłudze języka delegatów.</span><span class="sxs-lookup"><span data-stu-id="dc027-126">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="dc027-127">Obsługa języka dla zdarzeń</span><span class="sxs-lookup"><span data-stu-id="dc027-127">Language Support for Events</span></span>

<span data-ttu-id="dc027-128">Składnia do definiowania zdarzeń oraz subskrybowanie lub anulowanie subskrypcji zdarzeń jest rozszerzeniem składni dla delegatów.</span><span class="sxs-lookup"><span data-stu-id="dc027-128">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="dc027-129">Aby zdefiniować zdarzenie, użyj słowa kluczowego `event`:</span><span class="sxs-lookup"><span data-stu-id="dc027-129">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="dc027-130">Typ zdarzenia (`EventHandler<FileListArgs>` w tym przykładzie) musi być typem delegata.</span><span class="sxs-lookup"><span data-stu-id="dc027-130">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="dc027-131">Podczas deklarowania zdarzenia należy przestrzegać kilku Konwencji.</span><span class="sxs-lookup"><span data-stu-id="dc027-131">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="dc027-132">Zwykle typ delegata zdarzenia ma zwracaną wartość void.</span><span class="sxs-lookup"><span data-stu-id="dc027-132">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="dc027-133">Deklaracje zdarzeń powinny być czasownikiem lub wyrażeniem orzeczenia.</span><span class="sxs-lookup"><span data-stu-id="dc027-133">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="dc027-134">Użyj minionych natężeń, gdy zdarzenie zgłosi coś, co się stało.</span><span class="sxs-lookup"><span data-stu-id="dc027-134">Use past tense when the event reports something that has happened.</span></span> <span data-ttu-id="dc027-135">Użyj obecnego zlecenia dwuprzyciskowego (na przykład `Closing`), aby zgłosić coś, co się dzieje.</span><span class="sxs-lookup"><span data-stu-id="dc027-135">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="dc027-136">Często użycie obecnego dwustopniowego oznacza, że Klasa obsługuje pewne zachowanie w zakresie dostosowywania.</span><span class="sxs-lookup"><span data-stu-id="dc027-136">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="dc027-137">Jednym z najczęstszych scenariuszy jest obsługa anulowania.</span><span class="sxs-lookup"><span data-stu-id="dc027-137">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="dc027-138">Na przykład zdarzenie `Closing` może zawierać argument, który wskazuje, czy operacja zamknięcia powinna być kontynuowana, czy nie.</span><span class="sxs-lookup"><span data-stu-id="dc027-138">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="dc027-139">Inne scenariusze mogą umożliwić wywoływanie obiektów wywołujących w celu zmodyfikowania zachowania przez zaktualizowanie Właściwości argumentów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="dc027-139">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="dc027-140">Możesz zgłosić zdarzenie, aby wskazać proponowaną następną akcję do wykonania przez algorytm.</span><span class="sxs-lookup"><span data-stu-id="dc027-140">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="dc027-141">Program obsługi zdarzeń może wykonać inną akcję przez modyfikację właściwości argumentu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="dc027-141">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="dc027-142">Aby zgłosić zdarzenie, należy wywołać programy obsługi zdarzeń przy użyciu składni delegata wywołania:</span><span class="sxs-lookup"><span data-stu-id="dc027-142">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="dc027-143">Zgodnie z opisem w sekcji [delegatów](delegates-patterns.md),?.</span><span class="sxs-lookup"><span data-stu-id="dc027-143">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="dc027-144">ułatwia to zapewnienie, że nie próbujesz podnieść zdarzenia, gdy nie ma subskrybentów tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="dc027-144">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>
 
<span data-ttu-id="dc027-145">Subskrybujesz zdarzenie przy użyciu operatora `+=`:</span><span class="sxs-lookup"><span data-stu-id="dc027-145">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);

fileLister.Progress += onProgress;
```

<span data-ttu-id="dc027-146">Metoda obsługi zazwyczaj jest prefiksem "on", po którym następuje nazwa zdarzenia, jak pokazano powyżej.</span><span class="sxs-lookup"><span data-stu-id="dc027-146">The handler method typically is the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="dc027-147">Anulowanie subskrypcji przy użyciu operatora `-=`:</span><span class="sxs-lookup"><span data-stu-id="dc027-147">You unsubscribe using the `-=` operator:</span></span>

```csharp
fileLister.Progress -= onProgress;
```

<span data-ttu-id="dc027-148">Należy zauważyć, że zadeklarowano zmienną lokalną dla wyrażenia, które reprezentuje procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="dc027-148">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="dc027-149">Dzięki temu anulowanie subskrypcji spowoduje usunięcie programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="dc027-149">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="dc027-150">Jeśli zamiast tego użyto treści wyrażenia lambda, podjęto próbę usunięcia programu obsługi, który nigdy nie został dołączony, co nic nie robi.</span><span class="sxs-lookup"><span data-stu-id="dc027-150">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="dc027-151">W następnym artykule dowiesz się więcej na temat typowych wzorców zdarzeń i różnej zmienności w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="dc027-151">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="dc027-152">Next</span><span class="sxs-lookup"><span data-stu-id="dc027-152">Next</span></span>](event-pattern.md)
