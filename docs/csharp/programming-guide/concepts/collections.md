---
title: Kolekcje (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: 23d73a26bbe0e711bb3a081994826e06634c4bac
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418705"
---
# <a name="collections-c"></a><span data-ttu-id="c8c06-102">Kolekcje (C#)</span><span class="sxs-lookup"><span data-stu-id="c8c06-102">Collections (C#)</span></span>

<span data-ttu-id="c8c06-103">W przypadku wielu aplikacji, należy utworzyć grupy powiązanych obiektów i zarządzać nimi.</span><span class="sxs-lookup"><span data-stu-id="c8c06-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="c8c06-104">Istnieją dwa sposoby grupowania obiektów: przez tworzenie tablic obiektów i tworzenie kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="c8c06-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>

<span data-ttu-id="c8c06-105">Tablice są najbardziej przydatne do tworzenia i pracy ze stałą liczbą obiektów o jednoznacznie określonym typie.</span><span class="sxs-lookup"><span data-stu-id="c8c06-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="c8c06-106">Aby uzyskać informacje na temat tablic, zobacz [tablice](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="c8c06-106">For information about arrays, see [Arrays](../arrays/index.md).</span></span>

<span data-ttu-id="c8c06-107">Kolekcje zapewniają bardziej elastyczny sposób pracy z grupami obiektów.</span><span class="sxs-lookup"><span data-stu-id="c8c06-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="c8c06-108">W przeciwieństwie do tablic, Grupa obiektów, z którymi pracujesz, może być zwiększana i zmniejszana dynamicznie w miarę potrzeby zmiany aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8c06-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="c8c06-109">W przypadku niektórych kolekcji można przypisać klucz do dowolnego obiektu, który został umieszczony w kolekcji, dzięki czemu można szybko pobrać obiekt przy użyciu klucza.</span><span class="sxs-lookup"><span data-stu-id="c8c06-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="c8c06-110">Kolekcja jest klasą, więc należy zadeklarować wystąpienie klasy, aby można było dodać elementy do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c8c06-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>

<span data-ttu-id="c8c06-111">Jeśli kolekcja zawiera elementy tylko jednego typu danych, można użyć jednej z klas w przestrzeni nazw <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c8c06-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c8c06-112">Ogólna kolekcja wymusza bezpieczeństwo typu, tak aby nie można było dodać do niego żadnego innego typu danych.</span><span class="sxs-lookup"><span data-stu-id="c8c06-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="c8c06-113">Po pobraniu elementu z kolekcji ogólnej nie trzeba określać jego typu danych ani go przekonwertować.</span><span class="sxs-lookup"><span data-stu-id="c8c06-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>

> [!NOTE]
> <span data-ttu-id="c8c06-114">Przykłady w tym temacie obejmują dyrektywy [using](../../language-reference/keywords/using-directive.md) dla `System.Collections.Generic` i `System.Linq` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c8c06-114">For the examples in this topic, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>

 <span data-ttu-id="c8c06-115">**W tym temacie**</span><span class="sxs-lookup"><span data-stu-id="c8c06-115">**In this topic**</span></span>

- [<span data-ttu-id="c8c06-116">Korzystanie z prostej kolekcji</span><span class="sxs-lookup"><span data-stu-id="c8c06-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)

- [<span data-ttu-id="c8c06-117">Rodzaje kolekcji</span><span class="sxs-lookup"><span data-stu-id="c8c06-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)

  - [<span data-ttu-id="c8c06-118">Klasy System. Collections. Generic</span><span class="sxs-lookup"><span data-stu-id="c8c06-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)

  - [<span data-ttu-id="c8c06-119">Klasy System. Collections. współbieżne</span><span class="sxs-lookup"><span data-stu-id="c8c06-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)

  - [<span data-ttu-id="c8c06-120">Klasy System. Collections</span><span class="sxs-lookup"><span data-stu-id="c8c06-120">System.Collections Classes</span></span>](#BKMK_Collections)

- [<span data-ttu-id="c8c06-121">Implementowanie kolekcji par klucz/wartość</span><span class="sxs-lookup"><span data-stu-id="c8c06-121">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)

- [<span data-ttu-id="c8c06-122">Używanie LINQ do uzyskiwania dostępu do kolekcji</span><span class="sxs-lookup"><span data-stu-id="c8c06-122">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)

- [<span data-ttu-id="c8c06-123">Sortowanie kolekcji</span><span class="sxs-lookup"><span data-stu-id="c8c06-123">Sorting a Collection</span></span>](#BKMK_Sorting)

- [<span data-ttu-id="c8c06-124">Definiowanie kolekcji niestandardowej</span><span class="sxs-lookup"><span data-stu-id="c8c06-124">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)

- [<span data-ttu-id="c8c06-125">Iteratory</span><span class="sxs-lookup"><span data-stu-id="c8c06-125">Iterators</span></span>](#BKMK_Iterators)

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a><span data-ttu-id="c8c06-126">Korzystanie z prostej kolekcji</span><span class="sxs-lookup"><span data-stu-id="c8c06-126">Using a Simple Collection</span></span>

<span data-ttu-id="c8c06-127">W przykładach w tej sekcji użyto ogólnej klasy <xref:System.Collections.Generic.List%601>, która pozwala na współpracę z silnie wpisaną listą obiektów.</span><span class="sxs-lookup"><span data-stu-id="c8c06-127">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>

<span data-ttu-id="c8c06-128">Poniższy przykład tworzy listę ciągów, a następnie iteruje przez ciągi przy użyciu instrukcji [foreach](../../language-reference/keywords/foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="c8c06-128">The following example creates a list of strings and then iterates through the strings by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

```csharp
// Create a list of strings.
var salmons = new List<string>();
salmons.Add("chinook");
salmons.Add("coho");
salmons.Add("pink");
salmons.Add("sockeye");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="c8c06-129">Jeśli zawartość kolekcji jest znana z wyprzedzeniem, można użyć *inicjatora kolekcji* w celu zainicjowania kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c8c06-129">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="c8c06-130">Aby uzyskać więcej informacji, zobacz [Inicjatory obiektów i kolekcji](../classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="c8c06-130">For more information, see [Object and Collection Initializers](../classes-and-structs/object-and-collection-initializers.md).</span></span>

<span data-ttu-id="c8c06-131">Poniższy przykład jest taki sam jak w poprzednim przykładzie, z wyjątkiem tego, że inicjator kolekcji jest używany do dodawania elementów do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c8c06-131">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="c8c06-132">Można użyć instrukcji [for](../../language-reference/keywords/for.md) zamiast instrukcji `foreach`, aby wykonać iterację kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c8c06-132">You can use a [for](../../language-reference/keywords/for.md) statement instead of a `foreach` statement to iterate through a collection.</span></span> <span data-ttu-id="c8c06-133">Można to osiągnąć, uzyskując dostęp do elementów kolekcji według pozycji indeksu.</span><span class="sxs-lookup"><span data-stu-id="c8c06-133">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="c8c06-134">Indeks elementów zaczyna się od 0 i kończą się na liczbie elementów pomniejszonej o 1.</span><span class="sxs-lookup"><span data-stu-id="c8c06-134">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>

<span data-ttu-id="c8c06-135">Poniższy przykład wykonuje iterację elementów kolekcji przy użyciu `for`, a nie `foreach`.</span><span class="sxs-lookup"><span data-stu-id="c8c06-135">The following example iterates through the elements of a collection by using `for` instead of `foreach`.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

for (var index = 0; index < salmons.Count; index++)
{
    Console.Write(salmons[index] + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="c8c06-136">Poniższy przykład usuwa element z kolekcji przez określenie obiektu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="c8c06-136">The following example removes an element from the collection by specifying the object to remove.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Remove an element from the list by specifying
// the object.
salmons.Remove("coho");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook pink sockeye
```

<span data-ttu-id="c8c06-137">Poniższy przykład usuwa elementy z listy ogólnej.</span><span class="sxs-lookup"><span data-stu-id="c8c06-137">The following example removes elements from a generic list.</span></span> <span data-ttu-id="c8c06-138">Zamiast instrukcji `foreach`, należy użyć instrukcji [for](../../language-reference/keywords/for.md) , która iteruje w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="c8c06-138">Instead of a `foreach` statement, a [for](../../language-reference/keywords/for.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="c8c06-139">Wynika to z faktu, że metoda <xref:System.Collections.Generic.List%601.RemoveAt%2A> powoduje, że elementy po usuniętym elemencie mają niższą wartość indeksu.</span><span class="sxs-lookup"><span data-stu-id="c8c06-139">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>

```csharp
var numbers = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };

// Remove odd numbers.
for (var index = numbers.Count - 1; index >= 0; index--)
{
    if (numbers[index] % 2 == 1)
    {
        // Remove the element by specifying
        // the zero-based index in the list.
        numbers.RemoveAt(index);
    }
}

// Iterate through the list.
// A lambda expression is placed in the ForEach method
// of the List(T) object.
numbers.ForEach(
    number => Console.Write(number + " "));
// Output: 0 2 4 6 8
```

<span data-ttu-id="c8c06-140">Dla typu elementów w <xref:System.Collections.Generic.List%601>można również zdefiniować własną klasę.</span><span class="sxs-lookup"><span data-stu-id="c8c06-140">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="c8c06-141">W poniższym przykładzie Klasa `Galaxy`, która jest używana przez <xref:System.Collections.Generic.List%601>, jest zdefiniowana w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c8c06-141">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>

```csharp
private static void IterateThroughList()
{
    var theGalaxies = new List<Galaxy>
        {
            new Galaxy() { Name="Tadpole", MegaLightYears=400},
            new Galaxy() { Name="Pinwheel", MegaLightYears=25},
            new Galaxy() { Name="Milky Way", MegaLightYears=0},
            new Galaxy() { Name="Andromeda", MegaLightYears=3}
        };

    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears);
    }

    // Output:
    //  Tadpole  400
    //  Pinwheel  25
    //  Milky Way  0
    //  Andromeda  3
}

public class Galaxy
{
    public string Name { get; set; }
    public int MegaLightYears { get; set; }
}
```

<a name="BKMK_KindsOfCollections"></a>

## <a name="kinds-of-collections"></a><span data-ttu-id="c8c06-142">Rodzaje kolekcji</span><span class="sxs-lookup"><span data-stu-id="c8c06-142">Kinds of Collections</span></span>

<span data-ttu-id="c8c06-143">.NET Framework udostępnia wiele popularnych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c8c06-143">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="c8c06-144">Każdy typ kolekcji jest przeznaczony do określonego celu.</span><span class="sxs-lookup"><span data-stu-id="c8c06-144">Each type of collection is designed for a specific purpose.</span></span>

<span data-ttu-id="c8c06-145">Niektóre popularne klasy kolekcji zostały opisane w tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="c8c06-145">Some of the common collection classes are described in this section:</span></span>

- <span data-ttu-id="c8c06-146"><xref:System.Collections.Generic>, klasy</span><span class="sxs-lookup"><span data-stu-id="c8c06-146"><xref:System.Collections.Generic> classes</span></span>

- <span data-ttu-id="c8c06-147"><xref:System.Collections.Concurrent>, klasy</span><span class="sxs-lookup"><span data-stu-id="c8c06-147"><xref:System.Collections.Concurrent> classes</span></span>

- <span data-ttu-id="c8c06-148"><xref:System.Collections>, klasy</span><span class="sxs-lookup"><span data-stu-id="c8c06-148"><xref:System.Collections> classes</span></span>

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="c8c06-149">Klasy System. Collections. Generic</span><span class="sxs-lookup"><span data-stu-id="c8c06-149">System.Collections.Generic Classes</span></span>

<span data-ttu-id="c8c06-150">Można utworzyć ogólną kolekcję przy użyciu jednej z klas w przestrzeni nazw <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="c8c06-150">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="c8c06-151">Kolekcja ogólna jest przydatna, gdy każdy element w kolekcji ma ten sam typ danych.</span><span class="sxs-lookup"><span data-stu-id="c8c06-151">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="c8c06-152">Ogólna kolekcja wymusza silne wpisywanie przez umożliwienie dodania tylko żądanego typu danych.</span><span class="sxs-lookup"><span data-stu-id="c8c06-152">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>

<span data-ttu-id="c8c06-153">W poniższej tabeli wymieniono niektóre często używane klasy przestrzeni nazw <xref:System.Collections.Generic?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="c8c06-153">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="c8c06-154">Class</span><span class="sxs-lookup"><span data-stu-id="c8c06-154">Class</span></span>|<span data-ttu-id="c8c06-155">Opis</span><span class="sxs-lookup"><span data-stu-id="c8c06-155">Description</span></span>|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="c8c06-156">Reprezentuje kolekcję par klucz/wartość, które są zorganizowane na podstawie klucza.</span><span class="sxs-lookup"><span data-stu-id="c8c06-156">Represents a collection of key/value pairs that are organized based on the key.</span></span>|
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="c8c06-157">Reprezentuje listę obiektów, do których można uzyskać dostęp za pomocą indeksu.</span><span class="sxs-lookup"><span data-stu-id="c8c06-157">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="c8c06-158">Zapewnia metody wyszukiwania, sortowania i modyfikowania list.</span><span class="sxs-lookup"><span data-stu-id="c8c06-158">Provides methods to search, sort, and modify lists.</span></span>|
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="c8c06-159">Przedstawia kolekcję obiektów First In, First Out (FIFO).</span><span class="sxs-lookup"><span data-stu-id="c8c06-159">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="c8c06-160">Reprezentuje kolekcję par klucz/wartość, które są posortowane według klucza na podstawie skojarzonej implementacji <xref:System.Collections.Generic.IComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="c8c06-160">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="c8c06-161">Przedstawia kolekcję obiektów w ostatniej pierwszej, wychodzącej (LIFO).</span><span class="sxs-lookup"><span data-stu-id="c8c06-161">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="c8c06-162">Aby uzyskać dodatkowe informacje, zobacz [powszechnie używane typy kolekcji](../../../standard/collections/commonly-used-collection-types.md), [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md)i <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="c8c06-162">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic>.</span></span>

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="c8c06-163">Klasy System. Collections. współbieżne</span><span class="sxs-lookup"><span data-stu-id="c8c06-163">System.Collections.Concurrent Classes</span></span>

<span data-ttu-id="c8c06-164">W .NET Framework 4 lub nowszej kolekcje w przestrzeni nazw <xref:System.Collections.Concurrent> zapewniają wydajne, bezpieczne dla wątków operacje umożliwiające dostęp do elementów kolekcji z wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="c8c06-164">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>

<span data-ttu-id="c8c06-165">Klasy w przestrzeni nazw <xref:System.Collections.Concurrent> powinny być używane zamiast odpowiednich typów w przestrzeniach nazw <xref:System.Collections.Generic?displayProperty=nameWithType> i <xref:System.Collections?displayProperty=nameWithType>, gdy wiele wątków uzyskuje dostęp do kolekcji współbieżnie.</span><span class="sxs-lookup"><span data-stu-id="c8c06-165">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="c8c06-166">Aby uzyskać więcej informacji, zobacz [kolekcje bezpieczne dla wątków](../../../standard/collections/thread-safe/index.md) i <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="c8c06-166">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>

<span data-ttu-id="c8c06-167">Niektóre klasy zawarte w przestrzeni nazw <xref:System.Collections.Concurrent> są <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>i <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="c8c06-167">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a><span data-ttu-id="c8c06-168">Klasy System. Collections</span><span class="sxs-lookup"><span data-stu-id="c8c06-168">System.Collections Classes</span></span>

<span data-ttu-id="c8c06-169">Klasy w przestrzeni nazw <xref:System.Collections?displayProperty=nameWithType> nie przechowują elementów jako obiekty o określonych typach, ale jako obiekty typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="c8c06-169">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>

<span data-ttu-id="c8c06-170">Jeśli to możliwe, należy używać kolekcji ogólnych w przestrzeni nazw <xref:System.Collections.Generic?displayProperty=nameWithType> lub przestrzeni nazw <xref:System.Collections.Concurrent> zamiast starszych typów w przestrzeni nazw `System.Collections`.</span><span class="sxs-lookup"><span data-stu-id="c8c06-170">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>

<span data-ttu-id="c8c06-171">W poniższej tabeli przedstawiono niektóre z najczęściej używanych klas w przestrzeni nazw `System.Collections`:</span><span class="sxs-lookup"><span data-stu-id="c8c06-171">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>

|<span data-ttu-id="c8c06-172">Class</span><span class="sxs-lookup"><span data-stu-id="c8c06-172">Class</span></span>|<span data-ttu-id="c8c06-173">Opis</span><span class="sxs-lookup"><span data-stu-id="c8c06-173">Description</span></span>|
|---|---|
|<xref:System.Collections.ArrayList>|<span data-ttu-id="c8c06-174">Reprezentuje tablicę obiektów, których rozmiar jest dynamicznie zwiększany w miarę potrzeb.</span><span class="sxs-lookup"><span data-stu-id="c8c06-174">Represents an array of objects whose size is dynamically increased as required.</span></span>|
|<xref:System.Collections.Hashtable>|<span data-ttu-id="c8c06-175">Reprezentuje kolekcję par klucz/wartość, które są zorganizowane na podstawie kodu skrótu klucza.</span><span class="sxs-lookup"><span data-stu-id="c8c06-175">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|
|<xref:System.Collections.Queue>|<span data-ttu-id="c8c06-176">Przedstawia kolekcję obiektów First In, First Out (FIFO).</span><span class="sxs-lookup"><span data-stu-id="c8c06-176">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Stack>|<span data-ttu-id="c8c06-177">Przedstawia kolekcję obiektów w ostatniej pierwszej, wychodzącej (LIFO).</span><span class="sxs-lookup"><span data-stu-id="c8c06-177">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="c8c06-178">Przestrzeń nazw <xref:System.Collections.Specialized> udostępnia wyspecjalizowane i silnie wpisywane klasy kolekcji, takie jak kolekcje tylko do ciągów i połączone listy i słowniki hybrydowe.</span><span class="sxs-lookup"><span data-stu-id="c8c06-178">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="c8c06-179">Implementowanie kolekcji par klucz/wartość</span><span class="sxs-lookup"><span data-stu-id="c8c06-179">Implementing a Collection of Key/Value Pairs</span></span>

<span data-ttu-id="c8c06-180"><xref:System.Collections.Generic.Dictionary%602> Ogólna kolekcja umożliwia dostęp do elementów w kolekcji za pomocą klucza każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="c8c06-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="c8c06-181">Każde dodanie do słownika składa się z wartości i skojarzonego z nim klucza.</span><span class="sxs-lookup"><span data-stu-id="c8c06-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="c8c06-182">Pobieranie wartości przy użyciu jej klucza jest szybkie, ponieważ Klasa `Dictionary` jest zaimplementowana jako tablica skrótów.</span><span class="sxs-lookup"><span data-stu-id="c8c06-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>

<span data-ttu-id="c8c06-183">Poniższy przykład tworzy kolekcję `Dictionary` i wykonuje iterację w słowniku przy użyciu instrukcji `foreach`.</span><span class="sxs-lookup"><span data-stu-id="c8c06-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `foreach` statement.</span></span>

```csharp
private static void IterateThruDictionary()
{
    Dictionary<string, Element> elements = BuildDictionary();

    foreach (KeyValuePair<string, Element> kvp in elements)
    {
        Element theElement = kvp.Value;

        Console.WriteLine("key: " + kvp.Key);
        Console.WriteLine("values: " + theElement.Symbol + " " +
            theElement.Name + " " + theElement.AtomicNumber);
    }
}

private static Dictionary<string, Element> BuildDictionary()
{
    var elements = new Dictionary<string, Element>();

    AddToDictionary(elements, "K", "Potassium", 19);
    AddToDictionary(elements, "Ca", "Calcium", 20);
    AddToDictionary(elements, "Sc", "Scandium", 21);
    AddToDictionary(elements, "Ti", "Titanium", 22);

    return elements;
}

private static void AddToDictionary(Dictionary<string, Element> elements,
    string symbol, string name, int atomicNumber)
{
    Element theElement = new Element();

    theElement.Symbol = symbol;
    theElement.Name = name;
    theElement.AtomicNumber = atomicNumber;

    elements.Add(key: theElement.Symbol, value: theElement);
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

<span data-ttu-id="c8c06-184">Aby zamiast tego użyć inicjatora kolekcji do skompilowania kolekcji `Dictionary`, można zastąpić metody `BuildDictionary` i `AddToDictionary` przy użyciu następującej metody.</span><span class="sxs-lookup"><span data-stu-id="c8c06-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>

```csharp
private static Dictionary<string, Element> BuildDictionary2()
{
    return new Dictionary<string, Element>
    {
        {"K",
            new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        {"Ca",
            new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        {"Sc",
            new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        {"Ti",
            new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}
```

<span data-ttu-id="c8c06-185">W poniższym przykładzie zastosowano metodę <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> i Właściwość <xref:System.Collections.Generic.Dictionary%602.Item%2A> `Dictionary`, aby szybko znaleźć element według klucza.</span><span class="sxs-lookup"><span data-stu-id="c8c06-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="c8c06-186">Właściwość `Item` umożliwia dostęp do elementu w kolekcji `elements` przy użyciu `elements[symbol]` w C#.</span><span class="sxs-lookup"><span data-stu-id="c8c06-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements[symbol]` in C#.</span></span>

```csharp
private static void FindInDictionary(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    if (elements.ContainsKey(symbol) == false)
    {
        Console.WriteLine(symbol + " not found");
    }
    else
    {
        Element theElement = elements[symbol];
        Console.WriteLine("found: " + theElement.Name);
    }
}
```

<span data-ttu-id="c8c06-187">W poniższym przykładzie przy użyciu metody <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> szybko Znajdź element według klucza.</span><span class="sxs-lookup"><span data-stu-id="c8c06-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>

```csharp
private static void FindInDictionary2(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    Element theElement = null;
    if (elements.TryGetValue(symbol, out theElement) == false)
        Console.WriteLine(symbol + " not found");
    else
        Console.WriteLine("found: " + theElement.Name);
}
```

<a name="BKMK_LINQ"></a>

## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="c8c06-188">Używanie LINQ do uzyskiwania dostępu do kolekcji</span><span class="sxs-lookup"><span data-stu-id="c8c06-188">Using LINQ to Access a Collection</span></span>

<span data-ttu-id="c8c06-189">LINQ (zapytanie zintegrowane z językiem) może służyć do uzyskiwania dostępu do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c8c06-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="c8c06-190">Zapytania LINQ zapewniają możliwości filtrowania, porządkowania i grupowania.</span><span class="sxs-lookup"><span data-stu-id="c8c06-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="c8c06-191">Aby uzyskać więcej informacji, zobacz [wprowadzenie z LINQ C#in ](/dotnet/csharp/programming-guide/concepts/linq/).</span><span class="sxs-lookup"><span data-stu-id="c8c06-191">For more information, see  [Getting Started with LINQ in C#](/dotnet/csharp/programming-guide/concepts/linq/).</span></span>

<span data-ttu-id="c8c06-192">Poniższy przykład wykonuje zapytanie LINQ względem ogólnego `List`.</span><span class="sxs-lookup"><span data-stu-id="c8c06-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="c8c06-193">Zapytanie LINQ zwraca inną kolekcję, która zawiera wyniki.</span><span class="sxs-lookup"><span data-stu-id="c8c06-193">The LINQ query returns a different collection that contains the results.</span></span>

```csharp
private static void ShowLINQ()
{
    List<Element> elements = BuildList();

    // LINQ Query.
    var subset = from theElement in elements
                 where theElement.AtomicNumber < 22
                 orderby theElement.Name
                 select theElement;

    foreach (Element theElement in subset)
    {
        Console.WriteLine(theElement.Name + " " + theElement.AtomicNumber);
    }

    // Output:
    //  Calcium 20
    //  Potassium 19
    //  Scandium 21
}

private static List<Element> BuildList()
{
    return new List<Element>
    {
        { new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        { new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        { new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        { new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

<a name="BKMK_Sorting"></a>

## <a name="sorting-a-collection"></a><span data-ttu-id="c8c06-194">Sortowanie kolekcji</span><span class="sxs-lookup"><span data-stu-id="c8c06-194">Sorting a Collection</span></span>

<span data-ttu-id="c8c06-195">Poniższy przykład ilustruje procedurę sortowania kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c8c06-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="c8c06-196">Przykład sortuje wystąpienia klasy `Car`, które są przechowywane w <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="c8c06-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="c8c06-197">Klasa `Car` implementuje interfejs <xref:System.IComparable%601>, który wymaga zaimplementowania metody <xref:System.IComparable%601.CompareTo%2A>.</span><span class="sxs-lookup"><span data-stu-id="c8c06-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>

<span data-ttu-id="c8c06-198">Każde wywołanie metody <xref:System.IComparable%601.CompareTo%2A> wykonuje pojedyncze porównanie, które jest używane do sortowania.</span><span class="sxs-lookup"><span data-stu-id="c8c06-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="c8c06-199">Kod pisany przez użytkownika w metodzie `CompareTo` zwraca wartość dla każdego porównania bieżącego obiektu z innym obiektem.</span><span class="sxs-lookup"><span data-stu-id="c8c06-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="c8c06-200">Zwracana wartość jest mniejsza niż zero, jeśli bieżący obiekt jest mniejszy niż inny obiekt, większy niż zero, jeśli bieżący obiekt jest większy niż inny obiekt, i zero, jeśli są równe.</span><span class="sxs-lookup"><span data-stu-id="c8c06-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="c8c06-201">Dzięki temu można zdefiniować w kodzie kryteria dla wartości większej niż, mniejszej niż i równej.</span><span class="sxs-lookup"><span data-stu-id="c8c06-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>

<span data-ttu-id="c8c06-202">W metodzie `ListCars` instrukcja `cars.Sort()` sortuje listę.</span><span class="sxs-lookup"><span data-stu-id="c8c06-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="c8c06-203">To wywołanie metody <xref:System.Collections.Generic.List%601.Sort%2A> <xref:System.Collections.Generic.List%601> powoduje automatyczne wywoływanie metody `CompareTo` dla obiektów `Car` w `List`.</span><span class="sxs-lookup"><span data-stu-id="c8c06-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>

```csharp
private static void ListCars()
{
    var cars = new List<Car>
    {
        { new Car() { Name = "car1", Color = "blue", Speed = 20}},
        { new Car() { Name = "car2", Color = "red", Speed = 50}},
        { new Car() { Name = "car3", Color = "green", Speed = 10}},
        { new Car() { Name = "car4", Color = "blue", Speed = 50}},
        { new Car() { Name = "car5", Color = "blue", Speed = 30}},
        { new Car() { Name = "car6", Color = "red", Speed = 60}},
        { new Car() { Name = "car7", Color = "green", Speed = 50}}
    };

    // Sort the cars by color alphabetically, and then by speed
    // in descending order.
    cars.Sort();

    // View all of the cars.
    foreach (Car thisCar in cars)
    {
        Console.Write(thisCar.Color.PadRight(5) + " ");
        Console.Write(thisCar.Speed.ToString() + " ");
        Console.Write(thisCar.Name);
        Console.WriteLine();
    }

    // Output:
    //  blue  50 car4
    //  blue  30 car5
    //  blue  20 car1
    //  green 50 car7
    //  green 10 car3
    //  red   60 car6
    //  red   50 car2
}

public class Car : IComparable<Car>
{
    public string Name { get; set; }
    public int Speed { get; set; }
    public string Color { get; set; }

    public int CompareTo(Car other)
    {
        // A call to this method makes a single comparison that is
        // used for sorting.

        // Determine the relative order of the objects being compared.
        // Sort by color alphabetically, and then by speed in
        // descending order.

        // Compare the colors.
        int compare;
        compare = String.Compare(this.Color, other.Color, true);

        // If the colors are the same, compare the speeds.
        if (compare == 0)
        {
            compare = this.Speed.CompareTo(other.Speed);

            // Use descending order for speed.
            compare = -compare;
        }

        return compare;
    }
}
```

<a name="BKMK_CustomCollection"></a>

## <a name="defining-a-custom-collection"></a><span data-ttu-id="c8c06-204">Definiowanie kolekcji niestandardowej</span><span class="sxs-lookup"><span data-stu-id="c8c06-204">Defining a Custom Collection</span></span>

<span data-ttu-id="c8c06-205">Kolekcję można zdefiniować przez implementację interfejsu <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="c8c06-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span>

<span data-ttu-id="c8c06-206">Chociaż można zdefiniować kolekcję niestandardową, zazwyczaj lepiej jest używać kolekcji, które znajdują się w .NET Framework, które są opisane w [typach kolekcji](#BKMK_KindsOfCollections) wcześniej w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="c8c06-206">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#BKMK_KindsOfCollections) earlier in this topic.</span></span>

<span data-ttu-id="c8c06-207">W poniższym przykładzie zdefiniowano klasę kolekcji niestandardowej o nazwie `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="c8c06-207">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="c8c06-208">Ta klasa implementuje interfejs <xref:System.Collections.IEnumerable>, który wymaga zaimplementowania metody <xref:System.Collections.IEnumerable.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="c8c06-208">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>

<span data-ttu-id="c8c06-209">Metoda `GetEnumerator` zwraca wystąpienie klasy `ColorEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="c8c06-209">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="c8c06-210">`ColorEnumerator` implementuje interfejs <xref:System.Collections.IEnumerator>, który wymaga zaimplementowania właściwości <xref:System.Collections.IEnumerator.Current%2A>, metody <xref:System.Collections.IEnumerator.MoveNext%2A> i metody <xref:System.Collections.IEnumerator.Reset%2A>.</span><span class="sxs-lookup"><span data-stu-id="c8c06-210">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>

```csharp
private static void ListColors()
{
    var colors = new AllColors();

    foreach (Color theColor in colors)
    {
        Console.Write(theColor.Name + " ");
    }
    Console.WriteLine();
    // Output: red blue green
}

// Collection class.
public class AllColors : System.Collections.IEnumerable
{
    Color[] _colors =
    {
        new Color() { Name = "red" },
        new Color() { Name = "blue" },
        new Color() { Name = "green" }
    };

    public System.Collections.IEnumerator GetEnumerator()
    {
        return new ColorEnumerator(_colors);

        // Instead of creating a custom enumerator, you could
        // use the GetEnumerator of the array.
        //return _colors.GetEnumerator();
    }

    // Custom enumerator.
    private class ColorEnumerator : System.Collections.IEnumerator
    {
        private Color[] _colors;
        private int _position = -1;

        public ColorEnumerator(Color[] colors)
        {
            _colors = colors;
        }

        object System.Collections.IEnumerator.Current
        {
            get
            {
                return _colors[_position];
            }
        }

        bool System.Collections.IEnumerator.MoveNext()
        {
            _position++;
            return (_position < _colors.Length);
        }

        void System.Collections.IEnumerator.Reset()
        {
            _position = -1;
        }
    }
}

// Element class.
public class Color
{
    public string Name { get; set; }
}
```

<a name="BKMK_Iterators"></a>

## <a name="iterators"></a><span data-ttu-id="c8c06-211">Iteratory</span><span class="sxs-lookup"><span data-stu-id="c8c06-211">Iterators</span></span>

<span data-ttu-id="c8c06-212">*Iterator* jest używany do wykonywania niestandardowej iteracji w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c8c06-212">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="c8c06-213">Iterator może być metodą lub `get` akcesorem.</span><span class="sxs-lookup"><span data-stu-id="c8c06-213">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="c8c06-214">Iterator używa instrukcji [yield return](../../language-reference/keywords/yield.md) , aby zwrócić każdy element kolekcji pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="c8c06-214">An iterator uses a [yield return](../../language-reference/keywords/yield.md) statement to return each element of the collection one at a time.</span></span>

<span data-ttu-id="c8c06-215">Należy wywołać iterator przy użyciu instrukcji [foreach](../../language-reference/keywords/foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="c8c06-215">You call an iterator by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="c8c06-216">Każda iteracja pętli `foreach` wywołuje iterator.</span><span class="sxs-lookup"><span data-stu-id="c8c06-216">Each iteration of the `foreach` loop calls the iterator.</span></span> <span data-ttu-id="c8c06-217">Gdy w iteratoru zostanie osiągnięta instrukcja `yield return`, zwracane jest wyrażenie, a bieżąca lokalizacja w kodzie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="c8c06-217">When a `yield return` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="c8c06-218">Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu iteratora.</span><span class="sxs-lookup"><span data-stu-id="c8c06-218">Execution is restarted from that location the next time that the iterator is called.</span></span>

<span data-ttu-id="c8c06-219">Aby uzyskać więcej informacji, zobacz [IteratoryC#()](./iterators.md).</span><span class="sxs-lookup"><span data-stu-id="c8c06-219">For more information, see [Iterators (C#)](./iterators.md).</span></span>

<span data-ttu-id="c8c06-220">W poniższym przykładzie zastosowano metodę iteratora.</span><span class="sxs-lookup"><span data-stu-id="c8c06-220">The following example uses an iterator method.</span></span> <span data-ttu-id="c8c06-221">Metoda iteratora zawiera instrukcję `yield return`, która znajduje się wewnątrz pętli [for](../../language-reference/keywords/for.md) .</span><span class="sxs-lookup"><span data-stu-id="c8c06-221">The iterator method has a `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="c8c06-222">W metodzie `ListEvenNumbers` każda iteracja treści instrukcji `foreach` tworzy wywołanie metody iteratora, która przechodzi do następnej instrukcji `yield return`.</span><span class="sxs-lookup"><span data-stu-id="c8c06-222">In the `ListEvenNumbers` method, each iteration of the `foreach` statement body creates a call to the iterator method, which proceeds to the next `yield return` statement.</span></span>

```csharp
private static void ListEvenNumbers()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    Console.WriteLine();
    // Output: 6 8 10 12 14 16 18
}

private static IEnumerable<int> EvenSequence(
    int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (var number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="c8c06-223">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8c06-223">See also</span></span>

- [<span data-ttu-id="c8c06-224">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="c8c06-224">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="c8c06-225">Koncepcje programowaniaC#()</span><span class="sxs-lookup"><span data-stu-id="c8c06-225">Programming Concepts (C#)</span></span>](./index.md)
- [<span data-ttu-id="c8c06-226">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c8c06-226">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="c8c06-227">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="c8c06-227">LINQ to Objects (C#)</span></span>](./linq/linq-to-objects.md)
- [<span data-ttu-id="c8c06-228">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="c8c06-228">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)
- [<span data-ttu-id="c8c06-229">Kolekcje i struktury danych</span><span class="sxs-lookup"><span data-stu-id="c8c06-229">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="c8c06-230">Wybieranie klasy kolekcji</span><span class="sxs-lookup"><span data-stu-id="c8c06-230">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="c8c06-231">Porównywanie i sortowanie w ramach kolekcji</span><span class="sxs-lookup"><span data-stu-id="c8c06-231">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="c8c06-232">Kiedy należy używać kolekcji ogólnych</span><span class="sxs-lookup"><span data-stu-id="c8c06-232">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
