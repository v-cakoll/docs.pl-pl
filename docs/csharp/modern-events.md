---
title: Zaktualizowany wzorzec zdarzenia rdzenia .NET
description: Dowiedz się, jak wzorzec zdarzenia .NET Core umożliwia elastyczność zgodności z poprzednimi wersjami i jak zaimplementować bezpieczne przetwarzanie zdarzeń z subskrybentami asynchronii.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: c8858158ede761db8a3002beb26e521880f77feb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170439"
---
# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="8dd31-103">Zaktualizowany wzorzec zdarzenia rdzenia .NET</span><span class="sxs-lookup"><span data-stu-id="8dd31-103">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="8dd31-104">Wstecz</span><span class="sxs-lookup"><span data-stu-id="8dd31-104">Previous</span></span>](event-pattern.md)

<span data-ttu-id="8dd31-105">W poprzednim artykule omówiono najczęstsze wzorce zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8dd31-105">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="8dd31-106">.NET Core ma bardziej zrelaksowany wzór.</span><span class="sxs-lookup"><span data-stu-id="8dd31-106">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="8dd31-107">W tej wersji `EventHandler<TEventArgs>` definicja nie ma już `TEventArgs` ograniczenia, które musi `System.EventArgs`być klasą wywodzącą się z .</span><span class="sxs-lookup"><span data-stu-id="8dd31-107">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="8dd31-108">Zwiększa to elastyczność i jest zgodne z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="8dd31-108">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="8dd31-109">Zacznijmy od elastyczności.</span><span class="sxs-lookup"><span data-stu-id="8dd31-109">Let's start with the flexibility.</span></span> <span data-ttu-id="8dd31-110">Klasa System.EventArgs wprowadza jedną `MemberwiseClone()`metodę: , która tworzy płytką kopię obiektu.</span><span class="sxs-lookup"><span data-stu-id="8dd31-110">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="8dd31-111">Metoda ta musi używać odbicia w celu zaimplementowania `EventArgs`jego funkcji dla dowolnej klasy pochodzącej z .</span><span class="sxs-lookup"><span data-stu-id="8dd31-111">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="8dd31-112">Ta funkcja jest łatwiejsze do utworzenia w określonej klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="8dd31-112">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="8dd31-113">Oznacza to, że wynikające z System.EventArgs jest ograniczeniem, które ogranicza projekty, ale nie zapewnia żadnych dodatkowych korzyści.</span><span class="sxs-lookup"><span data-stu-id="8dd31-113">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="8dd31-114">W rzeczywistości można zmienić definicje `FileFoundArgs` `SearchDirectoryArgs` i tak, aby nie `EventArgs`pochodzą one z .</span><span class="sxs-lookup"><span data-stu-id="8dd31-114">In fact, you can change the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="8dd31-115">Program będzie działał dokładnie tak samo.</span><span class="sxs-lookup"><span data-stu-id="8dd31-115">The program will work exactly the same.</span></span>

<span data-ttu-id="8dd31-116">Można również zmienić `SearchDirectoryArgs` strukturę, jeśli włożysz jeszcze jedną zmianę:</span><span class="sxs-lookup"><span data-stu-id="8dd31-116">You could also change the `SearchDirectoryArgs` to a struct, if you make one more change:</span></span>

```csharp
internal struct SearchDirectoryArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs) : this()
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
```

<span data-ttu-id="8dd31-117">Dodatkową zmianą jest wywołanie konstruktora bez parametrów przed wejściem do konstruktora, który inicjuje wszystkie pola.</span><span class="sxs-lookup"><span data-stu-id="8dd31-117">The additional change is to call the parameterless constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="8dd31-118">Bez tego dodatku reguły Języka C# zgłaszałyby, że właściwości są dostępne przed ich przypisaniem.</span><span class="sxs-lookup"><span data-stu-id="8dd31-118">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="8dd31-119">Nie należy zmieniać `FileFoundArgs` z klasy (typ odwołania) na strukturę (typ wartości).</span><span class="sxs-lookup"><span data-stu-id="8dd31-119">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="8dd31-120">Dzieje się tak, ponieważ protokół do obsługi anulowania wymaga, aby argumenty zdarzenia były przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="8dd31-120">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="8dd31-121">Jeśli ta sama zmiana została wniesiona, klasa wyszukiwania plików nigdy nie będzie mogła zaobserwować żadnych zmian dokonanych przez subskrybentów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8dd31-121">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="8dd31-122">Nowa kopia struktury będzie używana dla każdego subskrybenta, a ta kopia będzie inną kopią niż ta widoczna dla obiektu wyszukiwania plików.</span><span class="sxs-lookup"><span data-stu-id="8dd31-122">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="8dd31-123">Następnie zastanówmy się, jak ta zmiana może być wstecznie zgodna.</span><span class="sxs-lookup"><span data-stu-id="8dd31-123">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="8dd31-124">Usunięcie ograniczenia nie ma wpływu na istniejący kod.</span><span class="sxs-lookup"><span data-stu-id="8dd31-124">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="8dd31-125">Wszystkie istniejące typy argumentów zdarzeń nadal pochodzą z `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="8dd31-125">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="8dd31-126">Wsteczna kompatybilność jest jednym z głównych powodów, `System.EventArgs`dla których będą nadal pochodzić z .</span><span class="sxs-lookup"><span data-stu-id="8dd31-126">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="8dd31-127">Wszystkich istniejących subskrybentów zdarzeń będą subskrybentami zdarzenia, które następuje klasyczny wzorzec.</span><span class="sxs-lookup"><span data-stu-id="8dd31-127">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="8dd31-128">Zgodnie z podobną logiką każdy typ argumentu zdarzenia utworzony teraz nie będzie miał żadnych subskrybentów w istniejących baz kodu.</span><span class="sxs-lookup"><span data-stu-id="8dd31-128">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="8dd31-129">Nowe typy zdarzeń, które `System.EventArgs` nie pochodzą z nie spowoduje przerwania tych baz kodu.</span><span class="sxs-lookup"><span data-stu-id="8dd31-129">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="8dd31-130">Wydarzenia z subskrybentami Async</span><span class="sxs-lookup"><span data-stu-id="8dd31-130">Events with Async subscribers</span></span>

<span data-ttu-id="8dd31-131">Masz jeden końcowy wzorzec, aby dowiedzieć się: Jak poprawnie napisać subskrybentów zdarzeń, które wywołają kod asynchronii.</span><span class="sxs-lookup"><span data-stu-id="8dd31-131">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="8dd31-132">Wyzwanie jest opisane w artykule na [async i czekają](async.md).</span><span class="sxs-lookup"><span data-stu-id="8dd31-132">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="8dd31-133">Metody asynchroniczne mogą mieć typ zwracania void, ale jest to zdecydowanie odradzane.</span><span class="sxs-lookup"><span data-stu-id="8dd31-133">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="8dd31-134">Gdy kod subskrybenta zdarzenia wywołuje metodę asynchronia, nie `async void` masz wyboru, jak tylko utworzyć metodę.</span><span class="sxs-lookup"><span data-stu-id="8dd31-134">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="8dd31-135">Wymaga tego podpis programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8dd31-135">The event handler signature requires it.</span></span>

<span data-ttu-id="8dd31-136">Musisz pogodzić to przeciwstawne wskazówki.</span><span class="sxs-lookup"><span data-stu-id="8dd31-136">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="8dd31-137">W jakiś sposób musisz `async void` stworzyć bezpieczną metodę.</span><span class="sxs-lookup"><span data-stu-id="8dd31-137">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="8dd31-138">Podstawy wzoru, który musisz zaimplementować, są poniżej:</span><span class="sxs-lookup"><span data-stu-id="8dd31-138">The basics of the pattern you need to implement are below:</span></span>

```csharp
worker.StartWorking += async (sender, eventArgs) =>
{
    try
    {
        await DoWorkAsync();
    }
    catch (Exception e)
    {
        //Some form of logging.
        Console.WriteLine($"Async task failure: {e.ToString()}");
        // Consider gracefully, and quickly exiting.
    }
};
```

<span data-ttu-id="8dd31-139">Po pierwsze należy zauważyć, że program obsługi jest oznaczony jako program obsługi asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="8dd31-139">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="8dd31-140">Ponieważ jest on przypisany do typu delegata obsługi zdarzeń, będzie miał typ zwracany void.</span><span class="sxs-lookup"><span data-stu-id="8dd31-140">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="8dd31-141">Oznacza to, że należy postępować zgodnie z wzorcem pokazano w programie obsługi i nie zezwalaj na wszelkie wyjątki, które mają być odrzucane z kontekstu programu obsługi asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="8dd31-141">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="8dd31-142">Ponieważ nie zwraca zadania, nie ma żadnego zadania, które można zgłosić błąd, wprowadzając stan błędu.</span><span class="sxs-lookup"><span data-stu-id="8dd31-142">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="8dd31-143">Ponieważ metoda jest async, metoda nie można po prostu zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8dd31-143">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="8dd31-144">(Metoda wywołująca ma dalsze wykonywanie, ponieważ jest `async`.) Rzeczywiste zachowanie środowiska uruchomieniowego zostanie zdefiniowane inaczej dla różnych środowisk.</span><span class="sxs-lookup"><span data-stu-id="8dd31-144">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="8dd31-145">Może zakończyć wątek lub proces, który jest właścicielem wątku lub pozostawić proces w stanie nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="8dd31-145">It may terminate the thread or the process that owns the thread, or leave the process in an indeterminate state.</span></span> <span data-ttu-id="8dd31-146">Wszystkie te potencjalne wyniki są wysoce niepożądane.</span><span class="sxs-lookup"><span data-stu-id="8dd31-146">All of these potential outcomes are highly undesirable.</span></span>

<span data-ttu-id="8dd31-147">Dlatego należy owinąć await instrukcji dla zadania asynchronicznego w swoim własnym bloku try.</span><span class="sxs-lookup"><span data-stu-id="8dd31-147">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="8dd31-148">Jeśli powoduje to wadliwe zadanie, można rejestrować błąd.</span><span class="sxs-lookup"><span data-stu-id="8dd31-148">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="8dd31-149">Jeśli jest to błąd, z którego aplikacja nie może odzyskać, można zamknąć program szybko i z wdziękiem</span><span class="sxs-lookup"><span data-stu-id="8dd31-149">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="8dd31-150">Są to główne aktualizacje wzorca zdarzeń .NET.</span><span class="sxs-lookup"><span data-stu-id="8dd31-150">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="8dd31-151">Zobaczysz wiele przykładów wcześniejszych wersji w bibliotekach, z których pracujesz.</span><span class="sxs-lookup"><span data-stu-id="8dd31-151">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="8dd31-152">Jednak należy zrozumieć, jakie są najnowsze wzorce, jak również.</span><span class="sxs-lookup"><span data-stu-id="8dd31-152">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="8dd31-153">Następny artykuł z tej serii pomaga `delegates` `events` odróżnić użycie i w projektach.</span><span class="sxs-lookup"><span data-stu-id="8dd31-153">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="8dd31-154">Są to podobne pojęcia, a ten artykuł pomoże Ci podjąć najlepszą decyzję dla twoich programów.</span><span class="sxs-lookup"><span data-stu-id="8dd31-154">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="8dd31-155">Dalej</span><span class="sxs-lookup"><span data-stu-id="8dd31-155">Next</span></span>](distinguish-delegates-events.md)
