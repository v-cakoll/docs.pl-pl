---
title: Wprowadzenie do zdarzeń
description: Dowiedz się więcej o wydarzeniach w .NET Core i naszych celach projektowania języka dla wydarzeń w tym przeglądzie.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 4e660f85eecfd5668919baf21a0d26f858faf5a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146117"
---
# <a name="introduction-to-events"></a><span data-ttu-id="6296c-103">Wprowadzenie do zdarzeń</span><span class="sxs-lookup"><span data-stu-id="6296c-103">Introduction to events</span></span>

[<span data-ttu-id="6296c-104">Wstecz</span><span class="sxs-lookup"><span data-stu-id="6296c-104">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="6296c-105">Zdarzenia są, podobnie jak delegaci, mechanizm *późnego wiązania.*</span><span class="sxs-lookup"><span data-stu-id="6296c-105">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="6296c-106">W rzeczywistości zdarzenia są zbudowane na obsługę języka dla delegatów.</span><span class="sxs-lookup"><span data-stu-id="6296c-106">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="6296c-107">Zdarzenia są sposobem na obiekt do emisji (do wszystkich zainteresowanych składników w systemie), że coś się stało.</span><span class="sxs-lookup"><span data-stu-id="6296c-107">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="6296c-108">Każdy inny składnik może subskrybować zdarzenie i otrzymywać powiadomienia o wysuwaniu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6296c-108">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="6296c-109">Prawdopodobnie używałeś zdarzeń w niektórych programach.</span><span class="sxs-lookup"><span data-stu-id="6296c-109">You've probably used events in some of your programming.</span></span> <span data-ttu-id="6296c-110">Wiele systemów graficznych ma model zdarzeń do raportowania interakcji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6296c-110">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="6296c-111">Zdarzenia te będą raportować ruch myszy, naciśnięcia przycisków i podobne interakcje.</span><span class="sxs-lookup"><span data-stu-id="6296c-111">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="6296c-112">Jest to jeden z najczęstszych, ale z pewnością nie jedyny scenariusz, w którym są używane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6296c-112">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="6296c-113">Można zdefiniować zdarzenia, które powinny być wywoływane dla klas.</span><span class="sxs-lookup"><span data-stu-id="6296c-113">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="6296c-114">Jedną z ważnych kwestii podczas pracy ze zdarzeniami jest to, że nie może być żadnego obiektu zarejestrowanego dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6296c-114">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="6296c-115">Należy napisać kod, aby nie zgłaszał zdarzenia, gdy nie są skonfigurowane odbiorniki.</span><span class="sxs-lookup"><span data-stu-id="6296c-115">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="6296c-116">Subskrybowanie zdarzenia tworzy również sprzężenie między dwoma obiektami (źródłem zdarzeń i ujściem zdarzenia).</span><span class="sxs-lookup"><span data-stu-id="6296c-116">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="6296c-117">Należy upewnić się, że sink zdarzenia anulują subskrypcję ze źródła zdarzeń, gdy nie są już zainteresowani wydarzeniami.</span><span class="sxs-lookup"><span data-stu-id="6296c-117">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="6296c-118">Cele projektowe dla obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="6296c-118">Design goals for event support</span></span>

<span data-ttu-id="6296c-119">Projekt języka dla zdarzeń jest przeznaczony dla następujących celów:</span><span class="sxs-lookup"><span data-stu-id="6296c-119">The language design for events targets these goals:</span></span>

- <span data-ttu-id="6296c-120">Włącz bardzo minimalne sprzężenie między źródłem zdarzeń a pochłaniaczem zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6296c-120">Enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="6296c-121">Te dwa składniki mogą nie być zapisywane przez tę samą organizację, a nawet mogą być aktualizowane według zupełnie innych harmonogramów.</span><span class="sxs-lookup"><span data-stu-id="6296c-121">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

- <span data-ttu-id="6296c-122">Subskrypcja wydarzenia powinna być bardzo prosta i rezygnacja z subskrypcji tego samego wydarzenia.</span><span class="sxs-lookup"><span data-stu-id="6296c-122">It should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

- <span data-ttu-id="6296c-123">Źródła zdarzeń powinny obsługiwać wielu subskrybentów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6296c-123">Event sources should support multiple event subscribers.</span></span> <span data-ttu-id="6296c-124">Powinien również obsługiwać brak subskrybenów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6296c-124">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="6296c-125">Widać, że cele dla wydarzeń są bardzo podobne do celów dla delegatów.</span><span class="sxs-lookup"><span data-stu-id="6296c-125">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="6296c-126">Dlatego obsługa języka zdarzenia jest zbudowana na obsłudze języka delegata.</span><span class="sxs-lookup"><span data-stu-id="6296c-126">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="6296c-127">Obsługa językowa wydarzeń</span><span class="sxs-lookup"><span data-stu-id="6296c-127">Language support for events</span></span>

<span data-ttu-id="6296c-128">Składnia definiowania zdarzeń oraz subskrybowania lub cofania subskrypcji ze zdarzeń jest rozszerzeniem składni delegatów.</span><span class="sxs-lookup"><span data-stu-id="6296c-128">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="6296c-129">Aby zdefiniować zdarzenie, `event` użyjesz słowa kluczowego:</span><span class="sxs-lookup"><span data-stu-id="6296c-129">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="6296c-130">Typ zdarzenia (`EventHandler<FileListArgs>` w tym przykładzie) musi być typem delegata.</span><span class="sxs-lookup"><span data-stu-id="6296c-130">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="6296c-131">Istnieje wiele konwencji, które należy wykonać podczas deklarowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6296c-131">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="6296c-132">Zazwyczaj typ delegata zdarzenia ma zwrot void.</span><span class="sxs-lookup"><span data-stu-id="6296c-132">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="6296c-133">Deklaracje zdarzeń powinny być czasownikiem lub wyrażeniem czasownika.</span><span class="sxs-lookup"><span data-stu-id="6296c-133">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="6296c-134">Użyj czasu przeszłego, gdy zdarzenie zgłasza coś, co się stało.</span><span class="sxs-lookup"><span data-stu-id="6296c-134">Use past tense when the event reports something that has happened.</span></span> <span data-ttu-id="6296c-135">Użyj czasownika czasu teraźniejszego (na przykład), aby zgłosić coś, `Closing`co ma się wydarzyć.</span><span class="sxs-lookup"><span data-stu-id="6296c-135">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="6296c-136">Często przy użyciu czasu teraźniejszego wskazuje, że klasa obsługuje pewnego rodzaju zachowanie dostosowywania.</span><span class="sxs-lookup"><span data-stu-id="6296c-136">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="6296c-137">Jednym z najczęstszych scenariuszy jest obsługa anulowania.</span><span class="sxs-lookup"><span data-stu-id="6296c-137">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="6296c-138">Na przykład `Closing` zdarzenie może zawierać argument, który wskazywałby, czy operacja zamknięcia powinna być kontynuowana, czy nie.</span><span class="sxs-lookup"><span data-stu-id="6296c-138">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="6296c-139">Inne scenariusze mogą umożliwić wywołującym zmodyfikować zachowanie, aktualizując właściwości argumentów zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6296c-139">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="6296c-140">Możesz zgłosić zdarzenie, aby wskazać proponowaną następną akcję, którą podejmie algorytm.</span><span class="sxs-lookup"><span data-stu-id="6296c-140">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="6296c-141">Program obsługi zdarzeń może nakazać inną akcję, modyfikując właściwości argumentu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6296c-141">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="6296c-142">Jeśli chcesz podnieść zdarzenie, należy wywołać programy obsługi zdarzeń przy użyciu składni wywołania delegata:</span><span class="sxs-lookup"><span data-stu-id="6296c-142">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="6296c-143">Jak omówiono w sekcji na [delegatów](delegates-patterns.md), ?.</span><span class="sxs-lookup"><span data-stu-id="6296c-143">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="6296c-144">operator ułatwia zapewnienie, że nie próbujesz podnieść zdarzenie, gdy nie ma żadnych subskrybentów tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6296c-144">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>

<span data-ttu-id="6296c-145">Subskrybujesz wydarzenie `+=` za pomocą operatora:</span><span class="sxs-lookup"><span data-stu-id="6296c-145">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) =>
    Console.WriteLine(eventArgs.FoundFile);

fileLister.Progress += onProgress;
```

<span data-ttu-id="6296c-146">Metoda obsługi zazwyczaj ma prefiks "On", po którym następuje nazwa zdarzenia, jak pokazano powyżej.</span><span class="sxs-lookup"><span data-stu-id="6296c-146">The handler method typically has the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="6296c-147">Zrezygnacje z subskrypcji za pomocą `-=` operatora:</span><span class="sxs-lookup"><span data-stu-id="6296c-147">You unsubscribe using the `-=` operator:</span></span>

```csharp
fileLister.Progress -= onProgress;
```

<span data-ttu-id="6296c-148">Należy pamiętać, że zadeklarowałem zmienną lokalną dla wyrażenia reprezentującego program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6296c-148">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="6296c-149">Dzięki temu anulowanie subskrypcji usuwa program obsługi.</span><span class="sxs-lookup"><span data-stu-id="6296c-149">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="6296c-150">Jeśli zamiast tego użyto treści wyrażenia lambda, próbujesz usunąć program obsługi, który nigdy nie został dołączony, co nic nie robi.</span><span class="sxs-lookup"><span data-stu-id="6296c-150">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="6296c-151">W następnym artykule dowiesz się więcej o typowych wzorcach zdarzeń i różnych odmianach tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="6296c-151">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="6296c-152">Dalej</span><span class="sxs-lookup"><span data-stu-id="6296c-152">Next</span></span>](event-pattern.md)
