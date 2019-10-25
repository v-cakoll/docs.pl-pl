---
title: Zaktualizowany wzorzec zdarzeń platformy .NET Core
description: Dowiedz się, w jaki sposób wzorzec zdarzeń platformy .NET Core umożliwia elastyczność z poprzednią zgodnością i jak zaimplementować bezpieczne przetwarzanie zdarzeń za pomocą subskrybentów asynchronicznych.
ms.date: 06/20/2016
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: 85fa4fd111a9eab01c1d32949d9fcc5f6300e33c
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798881"
---
# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="a95ff-103">Zaktualizowany wzorzec zdarzeń platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="a95ff-103">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="a95ff-104">Ubiegł</span><span class="sxs-lookup"><span data-stu-id="a95ff-104">Previous</span></span>](event-pattern.md)

<span data-ttu-id="a95ff-105">W poprzednim artykule omówiono najczęstsze wzorce zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a95ff-105">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="a95ff-106">Platforma .NET Core ma bardziej swobodny wzorzec.</span><span class="sxs-lookup"><span data-stu-id="a95ff-106">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="a95ff-107">W tej wersji definicja `EventHandler<TEventArgs>` nie ma już ograniczenia, które `TEventArgs` musi być klasą pochodną `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="a95ff-107">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="a95ff-108">Zwiększa to elastyczność i jest zgodna z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="a95ff-108">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="a95ff-109">Zacznijmy od elastyczności.</span><span class="sxs-lookup"><span data-stu-id="a95ff-109">Let's start with the flexibility.</span></span> <span data-ttu-id="a95ff-110">Klasa System. EventArgs wprowadza jedną metodę: `MemberwiseClone()`, która tworzy skróconą kopię obiektu.</span><span class="sxs-lookup"><span data-stu-id="a95ff-110">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="a95ff-111">Ta metoda musi używać odbicia w celu zaimplementowania jej funkcjonalności dla każdej klasy pochodnej z `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="a95ff-111">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="a95ff-112">Ta funkcja jest łatwiejsza do utworzenia w określonej klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="a95ff-112">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="a95ff-113">To efektywnie oznacza, że pochodny from system. EventArgs to ograniczenie, które ogranicza Twoje projekty, ale nie zapewnia dodatkowej korzyści.</span><span class="sxs-lookup"><span data-stu-id="a95ff-113">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="a95ff-114">W rzeczywistości można zmienić definicje `FileFoundArgs` i `SearchDirectoryArgs`, aby nie pochodzą one z `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="a95ff-114">In fact, you can change the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="a95ff-115">Program będzie działał dokładnie tak samo.</span><span class="sxs-lookup"><span data-stu-id="a95ff-115">The program will work exactly the same.</span></span>

<span data-ttu-id="a95ff-116">Możesz również zmienić `SearchDirectoryArgs` na strukturę, jeśli wprowadzisz nową zmianę:</span><span class="sxs-lookup"><span data-stu-id="a95ff-116">You could also change the `SearchDirectoryArgs` to a struct, if you make one more change:</span></span>

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

<span data-ttu-id="a95ff-117">Dodatkowa zmiana polega na wywołaniu konstruktora bez parametrów przed wprowadzeniem konstruktora, który inicjuje wszystkie pola.</span><span class="sxs-lookup"><span data-stu-id="a95ff-117">The additional change is to call the parameterless constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="a95ff-118">Bez tego dołączenia reguły C# będą zgłaszać dostęp do właściwości przed ich przypisaniem.</span><span class="sxs-lookup"><span data-stu-id="a95ff-118">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="a95ff-119">Nie należy zmieniać `FileFoundArgs` z klasy (typ odwołania) do struktury (typ wartości).</span><span class="sxs-lookup"><span data-stu-id="a95ff-119">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="a95ff-120">Wynika to z faktu, że protokół do obsługi anulowania wymaga, aby argumenty zdarzenia zostały przekazane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="a95ff-120">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="a95ff-121">Jeśli została wprowadzona taka sama zmiana, Klasa wyszukiwania plików nigdy nie zaobserwuje żadnych zmian dokonanych przez żadnego z subskrybentów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a95ff-121">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="a95ff-122">Nowa kopia struktury będzie używana dla każdego subskrybenta, a kopia będzie inną kopią niż ta, która jest widoczna dla obiektu wyszukiwanie plików.</span><span class="sxs-lookup"><span data-stu-id="a95ff-122">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="a95ff-123">Następnie Rozważmy, jak ta zmiana może być zgodna z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="a95ff-123">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="a95ff-124">Usunięcie ograniczenia nie ma wpływu na żaden istniejący kod.</span><span class="sxs-lookup"><span data-stu-id="a95ff-124">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="a95ff-125">Wszystkie istniejące typy argumentów zdarzeń nadal pochodzą z `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="a95ff-125">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="a95ff-126">Zgodność z poprzednimi wersjami to jeden z głównych powodów, dla których nadal będą pochodzić z `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="a95ff-126">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="a95ff-127">Wszyscy istniejący Subskrybenci zdarzeń będą subskrybentami zdarzeń, które przestrzegają wzorca klasycznego.</span><span class="sxs-lookup"><span data-stu-id="a95ff-127">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="a95ff-128">Podobnie jak w przypadku podobnej logiki, każdy typ argumentu zdarzenia utworzony teraz nie może mieć żadnych subskrybentów w żadnej z istniejących baz kodu.</span><span class="sxs-lookup"><span data-stu-id="a95ff-128">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="a95ff-129">Nowe typy zdarzeń, które nie pochodzą z `System.EventArgs`, nie spowodują przerwania tych baz kodu.</span><span class="sxs-lookup"><span data-stu-id="a95ff-129">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="a95ff-130">Zdarzenia z subskrybentami asynchronicznymi</span><span class="sxs-lookup"><span data-stu-id="a95ff-130">Events with Async subscribers</span></span>

<span data-ttu-id="a95ff-131">Masz jeden ostateczny wzorzec, aby dowiedzieć się: jak poprawnie napisać abonentów zdarzeń, które wywołują kod asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="a95ff-131">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="a95ff-132">Wyzwanie zostało opisane w artykule dotyczącym [Async i await](async.md).</span><span class="sxs-lookup"><span data-stu-id="a95ff-132">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="a95ff-133">Metody asynchroniczne mogą mieć typ zwracany void, ale nie jest to zdecydowanie odradzane.</span><span class="sxs-lookup"><span data-stu-id="a95ff-133">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="a95ff-134">Gdy kod abonenta zdarzenia wywołuje metodę asynchroniczną, nie ma możliwości wyboru, ale do utworzenia metody `async void`.</span><span class="sxs-lookup"><span data-stu-id="a95ff-134">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="a95ff-135">Podpis procedury obsługi zdarzeń wymaga tego.</span><span class="sxs-lookup"><span data-stu-id="a95ff-135">The event handler signature requires it.</span></span>

<span data-ttu-id="a95ff-136">Należy uzgodnić te przeciwstawne wskazówki.</span><span class="sxs-lookup"><span data-stu-id="a95ff-136">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="a95ff-137">W dowolny sposób należy utworzyć bezpieczną metodę `async void`.</span><span class="sxs-lookup"><span data-stu-id="a95ff-137">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="a95ff-138">Poniżej przedstawiono podstawowe informacje na temat wzorca, który należy zaimplementować:</span><span class="sxs-lookup"><span data-stu-id="a95ff-138">The basics of the pattern you need to implement are below:</span></span>

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

<span data-ttu-id="a95ff-139">Najpierw należy zauważyć, że program obsługi jest oznaczony jako procedura obsługi asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="a95ff-139">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="a95ff-140">Ponieważ jest przypisywany do typu delegata programu obsługi zdarzeń, będzie miał typ zwracany void.</span><span class="sxs-lookup"><span data-stu-id="a95ff-140">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="a95ff-141">Oznacza to, że należy postępować zgodnie z wzorcem wyświetlanym w obsłudze i nie zezwalać na wyrzucanie wyjątków z kontekstu procedury obsługi asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="a95ff-141">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="a95ff-142">Ponieważ nie zwraca zadania, nie istnieje zadanie, które może zgłosić błąd, wprowadzając stan błędu.</span><span class="sxs-lookup"><span data-stu-id="a95ff-142">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="a95ff-143">Ponieważ metoda jest asynchroniczna, metoda nie może po prostu zgłosić wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a95ff-143">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="a95ff-144">(Metoda wywołująca kontynuuje wykonywanie, ponieważ jest `async`.) Rzeczywiste zachowanie środowiska uruchomieniowego zostanie zdefiniowane inaczej dla różnych środowisk.</span><span class="sxs-lookup"><span data-stu-id="a95ff-144">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="a95ff-145">Może zakończyć wątek lub proces, który jest właścicielem wątku, lub pozostawić proces w nieokreślonym stanie.</span><span class="sxs-lookup"><span data-stu-id="a95ff-145">It may terminate the thread or the process that owns the thread, or leave the process in an indeterminate state.</span></span> <span data-ttu-id="a95ff-146">Wszystkie te potencjalne wyniki są wysoce niepożądane.</span><span class="sxs-lookup"><span data-stu-id="a95ff-146">All of these potential outcomes are highly undesirable.</span></span>

<span data-ttu-id="a95ff-147">Dlatego należy zawinąć instrukcję await dla zadania asynchronicznego we własnym bloku try.</span><span class="sxs-lookup"><span data-stu-id="a95ff-147">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="a95ff-148">Jeśli zadanie spowoduje wystąpienie błędu, można go zarejestrować.</span><span class="sxs-lookup"><span data-stu-id="a95ff-148">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="a95ff-149">Jeśli jest to błąd, z którego aplikacja nie może odzyskać, można szybko i bezpiecznie zakończyć działanie programu</span><span class="sxs-lookup"><span data-stu-id="a95ff-149">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="a95ff-150">Są to główne aktualizacje wzorca zdarzeń platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="a95ff-150">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="a95ff-151">Zobaczysz wiele przykładów wcześniejszych wersji w bibliotekach, z którymi pracujesz.</span><span class="sxs-lookup"><span data-stu-id="a95ff-151">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="a95ff-152">Należy jednak zrozumieć, jakie są również Najnowsze wzorce.</span><span class="sxs-lookup"><span data-stu-id="a95ff-152">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="a95ff-153">Następny artykuł z tej serii ułatwia rozróżnienie między `delegates`ami i `events` w projektach.</span><span class="sxs-lookup"><span data-stu-id="a95ff-153">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="a95ff-154">Są to podobne koncepcje i ten artykuł pomoże Ci w podejmowaniu najlepszej decyzji dla programów.</span><span class="sxs-lookup"><span data-stu-id="a95ff-154">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="a95ff-155">Next</span><span class="sxs-lookup"><span data-stu-id="a95ff-155">Next</span></span>](distinguish-delegates-events.md)
