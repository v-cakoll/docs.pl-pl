---
title: Wzorzec zdarzenie Core zaktualizowanej platformy .NET
description: "Dowiedz się, jak wzorzec zdarzenia platformy .NET Core umożliwia elastyczność zapewnienia zgodności i implementowania przetwarzania zdarzeń bezpieczne z subskrybentami asynchronicznego."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: cf69cbe0a7adbd274d1cb9e9544dda77d9fa1740
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="9c958-104">Wzorzec zdarzenie Core zaktualizowanej platformy .NET</span><span class="sxs-lookup"><span data-stu-id="9c958-104">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="9c958-105">Poprzednie</span><span class="sxs-lookup"><span data-stu-id="9c958-105">Previous</span></span>](event-pattern.md)

<span data-ttu-id="9c958-106">Poprzednim artykule opisano najbardziej typowe wzorce zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9c958-106">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="9c958-107">Oprogramowanie .NET core ma użycie wzorca.</span><span class="sxs-lookup"><span data-stu-id="9c958-107">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="9c958-108">W tej wersji `EventHandler<TEventArgs>` definicja zawiera już ograniczenie który `TEventArgs` musi być klasą pochodną `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="9c958-108">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="9c958-109">Zwiększa to elastyczność dla Ciebie i jest wstecznie zgodna.</span><span class="sxs-lookup"><span data-stu-id="9c958-109">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="9c958-110">Zacznijmy od elastyczność.</span><span class="sxs-lookup"><span data-stu-id="9c958-110">Let's start with the flexibility.</span></span> <span data-ttu-id="9c958-111">Klasa System.EventArgs wprowadza jedną metodę: `MemberwiseClone()`, który tworzy kopię pobieżną obiektu.</span><span class="sxs-lookup"><span data-stu-id="9c958-111">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="9c958-112">Metoda musi używać odbicia w celu wdrożenia jego działanie dla wszystkich klas pochodnych `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="9c958-112">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="9c958-113">Ta funkcjonalność jest łatwiejsze do tworzenia w określonej klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="9c958-113">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="9c958-114">Które skutecznie oznacza, że pochodny System.EventArgs ograniczenia, które ogranicza projektów, ale nie ma żadnych dodatkowych korzyści.</span><span class="sxs-lookup"><span data-stu-id="9c958-114">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="9c958-115">W rzeczywistości zmienia się z definicjami `FileFoundArgs` i `SearchDirectoryArgs` tak, aby nie pochodzą one od `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="9c958-115">In fact, you can changes the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="9c958-116">Program będzie działać dokładnie tak samo.</span><span class="sxs-lookup"><span data-stu-id="9c958-116">The program will work exactly the same.</span></span>

<span data-ttu-id="9c958-117">Można również zmienić `SearchDirectoryArgs` strukturę, jeśli wprowadzisz zmiany więcej jeden:</span><span class="sxs-lookup"><span data-stu-id="9c958-117">You could also change the `SearchDirectoryArgs` to a struct, if you also make one more change:</span></span>

```csharp  
internal struct SearchDirectoryArgs  
{  
    internal string CurrentSearchDirectory { get; }  
    internal int TotalDirs { get; }  
    internal int CompletedDirs { get; }  
    
    internal SearchDirectoryArgs(string dir, int totalDirs, 
        int completedDirs) : this()  
    {  
        CurrentSearchDirectory = dir;  
        TotalDirs = totalDirs;  
        CompletedDirs = completedDirs;  
    }  
}  
```   

<span data-ttu-id="9c958-118">Dodatkowe zmiana ma na celu wywołania konstruktora domyślnego przed wprowadzeniem Konstruktor, który inicjuje wszystkie pola.</span><span class="sxs-lookup"><span data-stu-id="9c958-118">The additional change is to call the default constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="9c958-119">Bez tego dodatku reguły języka C# rozpoczną przesyłanie raportów, że właściwości są dostępne przed zostały przypisane.</span><span class="sxs-lookup"><span data-stu-id="9c958-119">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="9c958-120">Nie należy zmieniać `FileFoundArgs` z klasy (typ odwołania) na strukturę (typ wartości).</span><span class="sxs-lookup"><span data-stu-id="9c958-120">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="9c958-121">To, ponieważ protokół obsługi anulowania wymaga, czy argumenty zdarzeń są przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="9c958-121">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="9c958-122">Jeśli wprowadzono zmiany w tej samej klasy wyszukiwania plików nigdy nie można obserwować zmiany wprowadzone przez wszystkich subskrybentów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9c958-122">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="9c958-123">Nową kopię struktury będzie używany na potrzeby każdego subskrybenta, a tej kopii będzie kopię innego niż widoczne dla obiekt wyszukiwania plików.</span><span class="sxs-lookup"><span data-stu-id="9c958-123">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="9c958-124">Następnie zastanówmy się, jak ta zmiana może być wstecznie zgodne.</span><span class="sxs-lookup"><span data-stu-id="9c958-124">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="9c958-125">Usunięcie ograniczenie nie ma wpływu na istniejący kod.</span><span class="sxs-lookup"><span data-stu-id="9c958-125">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="9c958-126">Wszystkie istniejące typy argumentów zdarzenia nadal pochodzić od `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="9c958-126">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="9c958-127">Zapewnienia zgodności jest główną przyczyną Dlaczego będą one nadal pochodzić od `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="9c958-127">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="9c958-128">Wszystkie istniejące subskrybentów zdarzeń będzie subskrybentów do zdarzenia, a następnie klasycznego wzorzec.</span><span class="sxs-lookup"><span data-stu-id="9c958-128">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="9c958-129">Po każdym podobne logiki codebases utworzony typ teraz nie będzie zawierało żadnych subskrybentów w żadnych istniejących argumentu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9c958-129">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="9c958-130">Nowe typy zdarzeń, które nie pochodzą z `System.EventArgs` będzie przerwać tych codebases.</span><span class="sxs-lookup"><span data-stu-id="9c958-130">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="9c958-131">Zdarzenia z subskrybentami Async</span><span class="sxs-lookup"><span data-stu-id="9c958-131">Events with Async subscribers</span></span>

<span data-ttu-id="9c958-132">Masz jeden wzorzec końcowego Aby dowiedzieć się więcej: jak poprawnie zapisać subskrybentów zdarzeń, wywołujące kod asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="9c958-132">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="9c958-133">Żądanie jest opisany w artykule na [async i await](async.md).</span><span class="sxs-lookup"><span data-stu-id="9c958-133">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="9c958-134">Metody asynchroniczne może mieć zwracanego typu void, ale jest to zdecydowanie niezalecane.</span><span class="sxs-lookup"><span data-stu-id="9c958-134">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="9c958-135">Gdy kod subskrybenta zdarzeń wywołuje metody asynchronicznej, masz nie choice, a do utworzenia `async void` metody.</span><span class="sxs-lookup"><span data-stu-id="9c958-135">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="9c958-136">Podpis programu obsługi zdarzeń wymagają.</span><span class="sxs-lookup"><span data-stu-id="9c958-136">The event handler signature requires it.</span></span>

<span data-ttu-id="9c958-137">Należy uzgodnić tych przeciwna wskazówek.</span><span class="sxs-lookup"><span data-stu-id="9c958-137">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="9c958-138">Aplikacja, należy utworzyć sejfie `async void` metody.</span><span class="sxs-lookup"><span data-stu-id="9c958-138">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="9c958-139">Podstawowe informacje potrzebne do zaimplementowania wzorca się poniżej:</span><span class="sxs-lookup"><span data-stu-id="9c958-139">The basics of the pattern you need to implement are below:</span></span>

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

<span data-ttu-id="9c958-140">Po pierwsze Zwróć uwagę, czy program obsługi jest oznaczony jako program obsługi asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="9c958-140">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="9c958-141">Ponieważ jest ona obecnie przypisywana do programu obsługi zdarzeń typ delegowany, będzie mieć zwrócony typ void.</span><span class="sxs-lookup"><span data-stu-id="9c958-141">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="9c958-142">Oznacza to, należy zgodne ze wzorcem wyświetlany w obsłudze, a nie zezwalaj na wyjątki zostanie wygenerowany poza kontekstem obsługi async.</span><span class="sxs-lookup"><span data-stu-id="9c958-142">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="9c958-143">Ponieważ nie zwraca zadania, brak nie można zgłosić błąd, wprowadzając stan zadania.</span><span class="sxs-lookup"><span data-stu-id="9c958-143">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="9c958-144">Ponieważ metoda jest asynchroniczne, metody nie można po prostu zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9c958-144">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="9c958-145">(Nadal wykonanie wywołania metody, ponieważ jest on `async`.) Rzeczywiste działanie zostanie określony inaczej dla różnych środowisk.</span><span class="sxs-lookup"><span data-stu-id="9c958-145">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="9c958-146">Może zakończyć wątek, może zakończyć program lub mogłoby to spowodować program nieokreślony stan.</span><span class="sxs-lookup"><span data-stu-id="9c958-146">It may terminate the thread, it may terminate the program, or it may leave the program in an undetermined state.</span></span> <span data-ttu-id="9c958-147">Żaden z tych nie jest dobrym wyników.</span><span class="sxs-lookup"><span data-stu-id="9c958-147">None of those are good outcomes.</span></span>

<span data-ttu-id="9c958-148">Dlatego powinna być zawijana instrukcja await asynchroniczne zadanie w własne bloku try.</span><span class="sxs-lookup"><span data-stu-id="9c958-148">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="9c958-149">Jeśli powoduje ona błędnej zadań, możesz zalogować się kod błędu.</span><span class="sxs-lookup"><span data-stu-id="9c958-149">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="9c958-150">Jeśli jest błąd, z którego nie można odzyskać aplikacji, można zamknąć program szybko i bezpiecznie</span><span class="sxs-lookup"><span data-stu-id="9c958-150">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="9c958-151">Są to wprowadzono znaczące aktualizacje z wzorcem zdarzenia platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="9c958-151">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="9c958-152">Zostanie wyświetlone wiele przykładów starszych wersji w pracy z bibliotekami.</span><span class="sxs-lookup"><span data-stu-id="9c958-152">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="9c958-153">Jednak należy zrozumieć, jakie najnowsze wzorce są również.</span><span class="sxs-lookup"><span data-stu-id="9c958-153">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="9c958-154">W tym artykule pomaga odróżnić przy użyciu `delegates` i `events` w projektach.</span><span class="sxs-lookup"><span data-stu-id="9c958-154">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="9c958-155">Są one podobne pojęcia i ten artykuł pomoże Ci podjęcie najlepszych decyzji programów.</span><span class="sxs-lookup"><span data-stu-id="9c958-155">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="9c958-156">Dalej</span><span class="sxs-lookup"><span data-stu-id="9c958-156">Next</span></span>](distinguish-delegates-events.md)
