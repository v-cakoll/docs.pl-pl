---
title: Standardowe wzorce zdarzenia platformy .NET
description: "Więcej informacji na temat wzorców zdarzeń .NET i tworzenie źródła zdarzeń w wersji standard i subskrypcji i przetworzyć standardowych zdarzeń w kodzie."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: 703b7b13a2175fb9c40ff707f333a1bf1530df8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="standard-net-event-patterns"></a><span data-ttu-id="c7943-104">Standardowe wzorce zdarzenia platformy .NET</span><span class="sxs-lookup"><span data-stu-id="c7943-104">Standard .NET event patterns</span></span>

[<span data-ttu-id="c7943-105">Poprzednie</span><span class="sxs-lookup"><span data-stu-id="c7943-105">Previous</span></span>](events-overview.md)

<span data-ttu-id="c7943-106">Zdarzenia platformy .NET zazwyczaj należy wykonać kilka znane wzorce.</span><span class="sxs-lookup"><span data-stu-id="c7943-106">.NET events generally follow a few known patterns.</span></span> <span data-ttu-id="c7943-107">Standaryzacja te wzorce oznacza, że deweloperzy mogą korzystać z wiedzę na temat tych standardowe wzorce, które mogą być stosowane do dowolnego programu zdarzenia platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="c7943-107">Standardizing on these patterns means that developers can leverage knowledge of those standard patterns, which can be applied to any .NET event program.</span></span>

<span data-ttu-id="c7943-108">Przejdźmy przy użyciu tych wzorców standardowe, konieczne będzie wiedzy, które należy utworzyć źródła zdarzeń w wersji standard i subskrybowanie i przetworzyć standardowych zdarzeń w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c7943-108">Let's go through these standard patterns so you will have all the knowledge you need to create standard event sources, and subscribe and process standard events in your code.</span></span>

## <a name="event-delegate-signatures"></a><span data-ttu-id="c7943-109">Podpisy delegata zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c7943-109">Event Delegate Signatures</span></span>

<span data-ttu-id="c7943-110">Standardowa podpis dla delegata zdarzenia .NET jest:</span><span class="sxs-lookup"><span data-stu-id="c7943-110">The standard signature for a .NET event delegate is:</span></span>

```csharp
void OnEventRaised(object sender, EventArgs args);
```

<span data-ttu-id="c7943-111">Typ zwracany jest typ void.</span><span class="sxs-lookup"><span data-stu-id="c7943-111">The return type is void.</span></span> <span data-ttu-id="c7943-112">Zdarzenia są oparte na delegatów i są obiekty delegowane multiemisji.</span><span class="sxs-lookup"><span data-stu-id="c7943-112">Events are based on delegates and are multicast delegates.</span></span> <span data-ttu-id="c7943-113">Obsługujący wiele subskrybentów dla dowolnego źródła zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c7943-113">That supports multiple subscribers for any event source.</span></span> <span data-ttu-id="c7943-114">Pojedynczy wartość zwracana z metody nie skalować do wielu subskrybentów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c7943-114">The single return value from a method doesn't scale to multiple event subscribers.</span></span> <span data-ttu-id="c7943-115">Które zwracają wartość oznacza Zobacz źródło zdarzeń po wywołaniem zdarzenia?</span><span class="sxs-lookup"><span data-stu-id="c7943-115">Which return value does the event source see after raising an event?</span></span> <span data-ttu-id="c7943-116">W dalszej części tego artykułu zobaczysz sposobu tworzenia zdarzeń protokołów, które obsługują subskrybentów zdarzeń informacji raportu ze źródłem zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c7943-116">Later in this article you'll see how to create event protocols that support event subscribers that report information to the event source.</span></span>

<span data-ttu-id="c7943-117">Lista argumentów zawiera dwa argumenty: nadawcy i argumenty zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c7943-117">The argument list contains two arguments: the sender, and the event arguments.</span></span> <span data-ttu-id="c7943-118">Typ czasu kompilacji `sender` jest `System.Object`, nawet jeśli wiesz, prawdopodobnie bardziej pochodny typ, który zawsze są poprawne.</span><span class="sxs-lookup"><span data-stu-id="c7943-118">The compile time type of `sender` is `System.Object`, even though you likely know a more derived type that would always be correct.</span></span> <span data-ttu-id="c7943-119">Konwencja, użyj `object`.</span><span class="sxs-lookup"><span data-stu-id="c7943-119">By convention, use `object`.</span></span>

<span data-ttu-id="c7943-120">Drugi argument zwykle został typ, który pochodzi od `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="c7943-120">The second argument has typically been a type that is derived from `System.EventArgs`.</span></span> <span data-ttu-id="c7943-121">(Będzie [następnej sekcji](modern-events.md) która Konwencja przestaną być wymuszane.) Jeśli danego typu zdarzenia nie wymaga żadnych dodatkowych argumentów, nadal zapewni oba argumenty.</span><span class="sxs-lookup"><span data-stu-id="c7943-121">(You'll see in the [next section](modern-events.md) that this convention is no longer enforced.) If your event type does not need any additional arguments, you will still provide both arguments.</span></span>
<span data-ttu-id="c7943-122">Jest wartością specjalną `EventArgs.Empty` należy używać do określenia, że zdarzenie nie zawiera żadnych dodatkowych informacji.</span><span class="sxs-lookup"><span data-stu-id="c7943-122">There is a special value, `EventArgs.Empty` that you should use to denote that your event does not contain any additional information.</span></span>

<span data-ttu-id="c7943-123">Utworzymy klasę, która zawiera listę plików w katalogu lub jego podkatalogach przestrzeganie wzorca.</span><span class="sxs-lookup"><span data-stu-id="c7943-123">Let's build a class that lists files in a directory, or any of its subdirectories that follow a pattern.</span></span> <span data-ttu-id="c7943-124">Ten składnik wywołuje zdarzenie, dla każdego pliku znaleźć odpowiadającego wzorzec.</span><span class="sxs-lookup"><span data-stu-id="c7943-124">This component raises an event for each file found that matches the pattern.</span></span>

<span data-ttu-id="c7943-125">Przy użyciu modelu zdarzeń zawiera niektóre zalety projektu.</span><span class="sxs-lookup"><span data-stu-id="c7943-125">Using an event model provides some design advantages.</span></span> <span data-ttu-id="c7943-126">Możesz utworzyć wiele odbiorników zdarzeń, wykonujących różne akcje po znalezieniu używanych plików.</span><span class="sxs-lookup"><span data-stu-id="c7943-126">You can create multiple event listeners that perform different actions when a sought file is found.</span></span> <span data-ttu-id="c7943-127">Łączenie różnych odbiorników można tworzyć bardziej niezawodne algorytmów.</span><span class="sxs-lookup"><span data-stu-id="c7943-127">Combining the different listeners can create more robust algorithms.</span></span>

<span data-ttu-id="c7943-128">Oto deklaracji argument początkowej zdarzenia do znajdowania używanych plików:</span><span class="sxs-lookup"><span data-stu-id="c7943-128">Here is the initial event argument declaration for finding a sought file:</span></span> 

```csharp
public class FileFoundArgs : EventArgs
{
    public string FoundFile { get; }

    public FileFoundArgs(string fileName)
    {
        FoundFile = fileName;
    }
}
```

<span data-ttu-id="c7943-129">Mimo że ten typ wygląda jak typ małe, tylko dane, postępuj zgodnie z Konwencją i odnieść (`class`) typu.</span><span class="sxs-lookup"><span data-stu-id="c7943-129">Even though this type looks like a small, data-only type, you should follow the convention and make it a reference (`class`) type.</span></span> <span data-ttu-id="c7943-130">Oznacza to obiekt argument zostanie przekazany przez odwołanie, a wszelkie zmiany danych ma być wyświetlana przez wszystkich subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="c7943-130">That means the argument object will be passed by reference, and any updates to the data will be viewed by all subscribers.</span></span> <span data-ttu-id="c7943-131">Pierwsza wersja jest niezmienialny obiektu.</span><span class="sxs-lookup"><span data-stu-id="c7943-131">The first version is an immutable object.</span></span> <span data-ttu-id="c7943-132">Należy wolisz właściwości były czcionką argument zdarzenia niezmienialny.</span><span class="sxs-lookup"><span data-stu-id="c7943-132">You should prefer to make the properties in your event argument type immutable.</span></span> <span data-ttu-id="c7943-133">Dzięki temu jeden subskrybent nie można zmienić wartości, przed subskrybenta innego będzie je widział.</span><span class="sxs-lookup"><span data-stu-id="c7943-133">That way, one subscriber cannot change the values before another subscriber sees them.</span></span> <span data-ttu-id="c7943-134">(Istnieją wyjątki od tej reguły, jak można zauważyć poniżej.)</span><span class="sxs-lookup"><span data-stu-id="c7943-134">(There are exceptions to this, as you'll see below.)</span></span>  

<span data-ttu-id="c7943-135">Następnie należy utworzyć deklaracji zdarzenia w klasie FileSearcher.</span><span class="sxs-lookup"><span data-stu-id="c7943-135">Next, we need to create the event declaration in the FileSearcher class.</span></span> <span data-ttu-id="c7943-136">Wykorzystanie `EventHandler<T>` typ oznacza, że nie trzeba tworzyć jeszcze innej definicji typu.</span><span class="sxs-lookup"><span data-stu-id="c7943-136">Leveraging the `EventHandler<T>` type means that you don't need to create yet another type definition.</span></span> <span data-ttu-id="c7943-137">Po prostu użyć specjalizacji ogólnego.</span><span class="sxs-lookup"><span data-stu-id="c7943-137">You simply use a generic specialization.</span></span>

<span data-ttu-id="c7943-138">Umożliwia wypełnianie klasy FileSearcher do wyszukiwania plików zgodnych ze wzorcem i wywołaj zdarzenie prawidłowe, gdy zostanie wykryta dopasowania.</span><span class="sxs-lookup"><span data-stu-id="c7943-138">Let's fill out the FileSearcher class to search for files that match a pattern, and raise the correct event when a match is discovered.</span></span>

```csharp
public class FileSearcher
{
    public event EventHandler<FileFoundArgs> FileFound;

    public void Search(string directory, string searchPattern)
    {
        foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
        {
            FileFound?.Invoke(this, new FileFoundArgs(file));
        }
    }
}
```

## <a name="definining-and-raising-field-like-events"></a><span data-ttu-id="c7943-139">Definining i wywoływanie zdarzeń podobnych pola</span><span class="sxs-lookup"><span data-stu-id="c7943-139">Definining and Raising Field-Like Events</span></span>

<span data-ttu-id="c7943-140">Najprostszym sposobem, aby dodać zdarzenie do własnej klasy jest można zadeklarować tego zdarzenia jako pole publiczne, tak jak w powyższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c7943-140">The simplest way to add an event to your class is to declare that event as a public field, as in the above example:</span></span>

```csharp
public event EventHandler<FileFoundArgs> FileFound;
```

<span data-ttu-id="c7943-141">To prawdopodobnie jest deklarowanie publiczne pola, które wydają się być zły obiektowej rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="c7943-141">This looks like it's declaring a public field, which would appear to be bad object oriented practice.</span></span> <span data-ttu-id="c7943-142">Chcesz chronić dostęp do danych za pośrednictwem właściwości lub metody.</span><span class="sxs-lookup"><span data-stu-id="c7943-142">You want to protect data access through properties, or methods.</span></span> <span data-ttu-id="c7943-143">Gdy to, że wygląda jak rozwiązaniem zły kod wygenerowany przez kompilator tworzenie otok tak, aby obiekty zdarzeń można uzyskać tylko w sposób bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="c7943-143">While this make look like a bad practice, the code generated by the compiler does create wrappers so that the event objects can only be accessed in safe ways.</span></span> <span data-ttu-id="c7943-144">Tylko operacje dostępne dla zdarzeń podobnych pola są Dodaj program obsługi:</span><span class="sxs-lookup"><span data-stu-id="c7943-144">The only operations available on a field-like event are add handler:</span></span>

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
    Console.WriteLine(eventArgs.FoundFile);
lister.FileFound += onFIleFound;
```

<span data-ttu-id="c7943-145">i usunąć program obsługi:</span><span class="sxs-lookup"><span data-stu-id="c7943-145">and remove handler:</span></span>

```csharp
lister.FileFound -= onFileFound;
```

<span data-ttu-id="c7943-146">Należy pamiętać, że zmienna lokalna dla programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="c7943-146">Note that there's a local variable for the handler.</span></span> <span data-ttu-id="c7943-147">Jeśli używasz treści Wyrażenie lambda, Usuń nie będzie działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="c7943-147">If you used the body of the lambda, the remove would not work correctly.</span></span> <span data-ttu-id="c7943-148">Może być inne wystąpienie delegata i dyskretnej nic nie rób.</span><span class="sxs-lookup"><span data-stu-id="c7943-148">It would be a different instance of the delegate, and silently do nothing.</span></span>

<span data-ttu-id="c7943-149">Kod poza klasy nie mogą wywoływać zdarzeń ani nie można wykonać innych operacji.</span><span class="sxs-lookup"><span data-stu-id="c7943-149">Code outside the class cannot raise the event, nor can it perform any other operations.</span></span>

## <a name="returning-values-from-event-subscribers"></a><span data-ttu-id="c7943-150">Zwracanie wartości z subskrybentów zdarzeń</span><span class="sxs-lookup"><span data-stu-id="c7943-150">Returning Values from Event Subscribers</span></span>

<span data-ttu-id="c7943-151">Proste wersji działa prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="c7943-151">Your simple version is working fine.</span></span> <span data-ttu-id="c7943-152">Dodajmy inna funkcja: anulowania.</span><span class="sxs-lookup"><span data-stu-id="c7943-152">Let's add another feature: Cancellation.</span></span>

<span data-ttu-id="c7943-153">Po podniesieniu zdarzenia znaleziono odbiorników powinno być możliwe zatrzymać dalsze przetwarzanie, jeśli ten plik jest, że ostatni poszukiwania.</span><span class="sxs-lookup"><span data-stu-id="c7943-153">When you raise the found event, listeners should be able to stop further processing, if this file is that last one sought.</span></span>

<span data-ttu-id="c7943-154">Obsługi zdarzeń nie zwraca wartości, więc należy do komunikowania się, że w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="c7943-154">The event handlers do not return a value, so you need to communicate that in another way.</span></span> <span data-ttu-id="c7943-155">Wzorzec zdarzeń w wersji standard używa obiektu EventArgs zawierać pól, które subskrybenci zdarzeń mogą używać do komunikowania się Anuluj.</span><span class="sxs-lookup"><span data-stu-id="c7943-155">The standard event pattern uses the EventArgs object to include fields that event subscribers can use to communicate cancel.</span></span>

<span data-ttu-id="c7943-156">Istnieją dwa różne wzorce, które mogłyby zostać użyte, oparte na semantykę kontraktu Anuluj.</span><span class="sxs-lookup"><span data-stu-id="c7943-156">There are two different patterns that could be used, based on the semantics of the Cancel contract.</span></span> <span data-ttu-id="c7943-157">W obu przypadkach warto polem EventArguments zdarzenia znaleziony plik.</span><span class="sxs-lookup"><span data-stu-id="c7943-157">In both cases, you'll add a boolean field to the EventArguments for the found file event.</span></span> 

<span data-ttu-id="c7943-158">Wzorzec co pozwoliłoby żadnych jednego abonenta anulować operację.</span><span class="sxs-lookup"><span data-stu-id="c7943-158">One pattern would allow any one subscriber to cancel the operation.</span></span>
<span data-ttu-id="c7943-159">Dla tego wzorca nowego pola jest ustawiana na `false`.</span><span class="sxs-lookup"><span data-stu-id="c7943-159">For this pattern, the new field is initialized to `false`.</span></span> <span data-ttu-id="c7943-160">Wszelkie subskrybenta można go zmienić `true`.</span><span class="sxs-lookup"><span data-stu-id="c7943-160">Any subscriber can change it to `true`.</span></span> <span data-ttu-id="c7943-161">Po wszystkich subskrybentów jak już wspomniano Zdarzenie wywoływane, składnik FileSearcher sprawdza, czy wartość logiczną i podejmuje działania.</span><span class="sxs-lookup"><span data-stu-id="c7943-161">After all subscribers have seen the event raised, the FileSearcher component examines the boolean value and takes action.</span></span>

<span data-ttu-id="c7943-162">Drugi wzorzec tylko czy anulować operację, jeśli operacja została anulowana wszystkich subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="c7943-162">The second pattern would only cancel the operation if all subscribers wanted the operation cancelled.</span></span> <span data-ttu-id="c7943-163">W tym wzorcu nowego pola jest ustawiana na wskazują, należy anulować operacji oraz wszystkie subskrybent może zmienić wskazująca, że należy kontynuować operacji.</span><span class="sxs-lookup"><span data-stu-id="c7943-163">In this pattern, the new field is initialized to indicate the operation should cancel, and any subscriber could change it to indicate the operation should continue.</span></span>
<span data-ttu-id="c7943-164">Po wszystkich subskrybentów jak już wspomniano Zdarzenie wywoływane, składnik FileSearcher sprawdza typu boolean i podejmuje działania.</span><span class="sxs-lookup"><span data-stu-id="c7943-164">After all subscribers have seen the event raised, the FileSearcher component examines the boolean and takes action.</span></span> <span data-ttu-id="c7943-165">Brak jednego dodatkowego kroku w tym wzorcu: składnik musi wiedzieć, jeśli zdarzenie przejrzane żadnych subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="c7943-165">There is one extra step in this pattern: the component needs to know if any subscribers have seen the event.</span></span> <span data-ttu-id="c7943-166">Jeśli nie ma żadnych subskrybentów, pole wskazuje cancel niepoprawnie.</span><span class="sxs-lookup"><span data-stu-id="c7943-166">If there are no subscribers, the field would indicate a cancel incorrectly.</span></span>

<span data-ttu-id="c7943-167">Umożliwia wdrożenie pierwszej wersji dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="c7943-167">Let's implement the first version for this sample.</span></span> <span data-ttu-id="c7943-168">Konieczne jest dodanie polem z typem FileFoundEventArgs:</span><span class="sxs-lookup"><span data-stu-id="c7943-168">You need to add a boolean field to the FileFoundEventArgs type:</span></span>

```csharp
public class FileFoundArgs : EventArgs
{
    public string FoundFile { get; }
    public bool CancelRequested { get; set; }

    public FileFoundArgs(string fileName)
    {
        FoundFile = fileName;
    }
}
```

<span data-ttu-id="c7943-169">Powinien być inicjowany tego nowego pola na wartość false, nie Anuluj bez powodu.</span><span class="sxs-lookup"><span data-stu-id="c7943-169">This new Field should be initialized to false, so you don't cancel for no reason.</span></span> <span data-ttu-id="c7943-170">To wartością domyślną dla polem, tak że odbywa się automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c7943-170">That is the default value for a boolean field, so that happens automatically.</span></span> <span data-ttu-id="c7943-171">Jedyną inną zmianą do składnika jest sprawdzanie flagę po wywoływanie zdarzeń, aby zobaczyć, jeśli dowolne subskrybentów żądanych anulowania:</span><span class="sxs-lookup"><span data-stu-id="c7943-171">The only other change to the component is to check the flag after raising the event to see if any of the subscribers have requested a cancellation:</span></span>

```csharp
public void List(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

<span data-ttu-id="c7943-172">Jedną z zalet tego wzorca jest, że nie jest istotne zmiany.</span><span class="sxs-lookup"><span data-stu-id="c7943-172">One advantage of this pattern is that it isn't a breaking change.</span></span>
<span data-ttu-id="c7943-173">Brak subskrybentów żądanie anulowania przed i nadal nie są one.</span><span class="sxs-lookup"><span data-stu-id="c7943-173">None of the subscribers requested a cancel before, and they still are not.</span></span> <span data-ttu-id="c7943-174">Żaden kod subskrybenta nie musi aktualizacji, chyba że chcą, aby obsługiwać nowy protokół Anuluj.</span><span class="sxs-lookup"><span data-stu-id="c7943-174">None of the subscriber code needs updating unless they want to support the new cancel protocol.</span></span> <span data-ttu-id="c7943-175">Bardzo luźno jest powiązane.</span><span class="sxs-lookup"><span data-stu-id="c7943-175">It's very loosely coupled.</span></span>

<span data-ttu-id="c7943-176">Teraz należy zaktualizować subskrybenta, tak aby żądania anulowania po znalezieniu pierwszy plik wykonywalny:</span><span class="sxs-lookup"><span data-stu-id="c7943-176">Let's update the subscriber so that it requests a cancellation once it finds the first executable:</span></span>

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a><span data-ttu-id="c7943-177">Dodawanie innego deklaracja zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c7943-177">Adding Another Event Declaration</span></span>

<span data-ttu-id="c7943-178">Teraz Dodaj jedną funkcję więcej i Wykaż innych idioms języka dla zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c7943-178">Let's add one more feature, and demonstrate other language idioms for events.</span></span> <span data-ttu-id="c7943-179">Dodajmy przeciążenia `Search()` metody, który przechodzi przez wszystkie podkatalogi w poszukiwaniu plików.</span><span class="sxs-lookup"><span data-stu-id="c7943-179">Let's add an overload of the `Search()` method that traverses all subdirectories in search of files.</span></span>

<span data-ttu-id="c7943-180">Ten można pobrać jako długotrwałej operacji w katalogu za dużo podkatalogów.</span><span class="sxs-lookup"><span data-stu-id="c7943-180">This could get to be a lengthy operation in a directory with many sub-directories.</span></span> <span data-ttu-id="c7943-181">Dodajmy zdarzenie, które pobiera wywoływane, gdy rozpoczyna się każdego nowego wyszukiwania w katalogu.</span><span class="sxs-lookup"><span data-stu-id="c7943-181">Let's add an event that gets raised when each new directory search begins.</span></span> <span data-ttu-id="c7943-182">Dzięki temu subskrybentów śledzić postęp i zaktualizować użytkownika dotyczące postępu.</span><span class="sxs-lookup"><span data-stu-id="c7943-182">This enables subscribers to track progress, and update the user as to progress.</span></span> <span data-ttu-id="c7943-183">Wszystkie przykłady dotąd utworzony są publiczne.</span><span class="sxs-lookup"><span data-stu-id="c7943-183">All the samples you've created so far are public.</span></span> <span data-ttu-id="c7943-184">Upewnijmy tego Zdarzenie wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="c7943-184">Let's make this one an internal event.</span></span> <span data-ttu-id="c7943-185">Oznacza to, że należy również wybrać typy używane dla argumentów wewnętrzny również.</span><span class="sxs-lookup"><span data-stu-id="c7943-185">That means you can also make the types used for the arguments internal as well.</span></span>

<span data-ttu-id="c7943-186">Będzie rozpoczyna się od utworzenia nowej klasy EventArgs pochodnych dla raportowania nowy katalog i postępu.</span><span class="sxs-lookup"><span data-stu-id="c7943-186">You'll start by creating the new EventArgs derived class for reporting the new directory and progress.</span></span> 

```csharp
internal class SearchDirectoryArgs : EventArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs)
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
``` 

<span data-ttu-id="c7943-187">Ponownie mogą postępować zgodnie z zaleceniami aby typu niezmienne odwołania dla argumentów zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c7943-187">Again, you can follow the recommendations to make an immutable reference type for the event arguments.</span></span>

<span data-ttu-id="c7943-188">Następnie określ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c7943-188">Next, define the event.</span></span> <span data-ttu-id="c7943-189">Tym razem użyjesz innej składni.</span><span class="sxs-lookup"><span data-stu-id="c7943-189">This time, you'll use a different syntax.</span></span> <span data-ttu-id="c7943-190">Oprócz przy użyciu składni pola, można jawnie utworzyć właściwości, z Dodaj i usuń programy obsługi.</span><span class="sxs-lookup"><span data-stu-id="c7943-190">In addition to using the field syntax, you can explicitly create the property, with add and remove handlers.</span></span> <span data-ttu-id="c7943-191">W tym przykładzie nie wymaga dodatkowego kodu w tych programów obsługi, w tym projekcie, ale oznacza to, jak należy je utworzyć.</span><span class="sxs-lookup"><span data-stu-id="c7943-191">In this sample, you won't need extra code in those handlers in this project, but this shows how you would create them.</span></span>

```csharp
internal event EventHandler<SearchDirectoryArgs> DirectoryChanged
{
    add { directoryChanged += value; }
    remove { directoryChanged -= value; }
}
private EventHandler<SearchDirectoryArgs> directoryChanged;
```

<span data-ttu-id="c7943-192">W może sposoby, zapisywany kod, w tym miejscu wstecznych się, że kod kompilator generuje się definicje zdarzeń pól przedstawiono wcześniej.</span><span class="sxs-lookup"><span data-stu-id="c7943-192">In may ways, the code you write here mirrors the code the compiler generates for the field event definitions you've seen earlier.</span></span> <span data-ttu-id="c7943-193">Utwórz zdarzenie przy użyciu składni bardzo podobne do celów [właściwości](properties.md).</span><span class="sxs-lookup"><span data-stu-id="c7943-193">You create the event using syntax very similar to that used for [properties](properties.md).</span></span> <span data-ttu-id="c7943-194">Powiadomienie, że obsługi mają różne nazwy elementu: `add` i `remove`.</span><span class="sxs-lookup"><span data-stu-id="c7943-194">Notice that the handlers have different names: `add` and `remove`.</span></span> <span data-ttu-id="c7943-195">Są one nazywane subskrypcji zdarzenia lub zrezygnować z zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c7943-195">These are called to subscribe to the event, or unsubscribe from the event.</span></span> <span data-ttu-id="c7943-196">Zwróć uwagę, czy też należy zadeklarować polem zapasowym prywatnych do przechowywania zmiennej zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c7943-196">Notice that you also must declare a private backing field to store the event variable.</span></span> <span data-ttu-id="c7943-197">Jest on zainicjowany do wartości null.</span><span class="sxs-lookup"><span data-stu-id="c7943-197">It is initialized to null.</span></span>

<span data-ttu-id="c7943-198">Następnie możemy dodać przeciążenia metody Search(), która jest przesyłany w podkatalogach i zgłasza obu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c7943-198">Next, let's add the overload of the Search() method that traverses subdirectories and raises both events.</span></span> <span data-ttu-id="c7943-199">W tym celu najłatwiej Użyj domyślnego argumentu, aby określić, czy chcesz wyszukać wszystkich katalogów:</span><span class="sxs-lookup"><span data-stu-id="c7943-199">The easiest way to accomplish this is to use a default argument to specify that you want to search all directories:</span></span>

```csharp
public void Search(string directory, string searchPattern, bool searchSubDirs = false)
{
    if (searchSubDirs)
    {
        var allDirectories = Directory.GetDirectories(directory, "*.*", SearchOption.AllDirectories);
        var completedDirs = 0;
        var totalDirs = allDirectories.Length + 1;
        foreach (var dir in allDirectories)
        {
            directoryChanged?.Invoke(this,
                new SearchDirectoryArgs(dir, totalDirs, completedDirs++));
            // Recursively search this child directory:
            SearchDirectory(dir, searchPattern);
        }
        // Include the Current Directory:
        directoryChanged?.Invoke(this,
            new SearchDirectoryArgs(directory, totalDirs, completedDirs++));
        SearchDirectory(directory, searchPattern);
    }
    else
    {
        SearchDirectory(directory, searchPattern);
    }
}

private void SearchDirectory(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

<span data-ttu-id="c7943-200">W tym momencie można uruchomić aplikacji wywoływania przeciążenia wszystkie podkatalogi wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="c7943-200">At this point, you can run the application calling the overload for searching all sub-directories.</span></span> <span data-ttu-id="c7943-201">Na nowe nie ma żadnych subskrybentów `ChangeDirectory` zdarzeń, ale przy użyciu `?.Invoke()` idiom gwarantuje, że to działa prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="c7943-201">There are no subscribers on the new `ChangeDirectory` event, but using the `?.Invoke()` idiom ensures that this works correctly.</span></span>

 <span data-ttu-id="c7943-202">Dodajmy obsługi do zapisywania wiersza, który będzie wyświetlany postęp w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="c7943-202">Let's add a handler to write a line that shows the progress in the console window.</span></span> 

```csharp
lister.DirectoryChanged += (sender, eventArgs) =>
{
    Console.Write($"Entering '{eventArgs.CurrentSearchDirectory}'.");
    Console.WriteLine($" {eventArgs.CompletedDirs} of {eventArgs.TotalDirs} completed...");
};
```

<span data-ttu-id="c7943-203">Przedstawiono wzorców, które zostaną wykonane przez cały ekosystem .NET.</span><span class="sxs-lookup"><span data-stu-id="c7943-203">You've seen patterns that are followed throughout the .NET ecosystem.</span></span>
<span data-ttu-id="c7943-204">Przez nauki tych wzorców i konwencje napiszesz idiomatyczne C# i .NET szybko.</span><span class="sxs-lookup"><span data-stu-id="c7943-204">By learning these patterns and conventions, you'll be writing idiomatic C# and .NET quickly.</span></span>

<span data-ttu-id="c7943-205">Następnie zostanie wyświetlony pewne zmiany w tych wzorców w najnowszej wersji programu .NET.</span><span class="sxs-lookup"><span data-stu-id="c7943-205">Next, you'll see some changes in these patterns in the most recent release of .NET.</span></span>

[<span data-ttu-id="c7943-206">Dalej</span><span class="sxs-lookup"><span data-stu-id="c7943-206">Next</span></span>](modern-events.md)
