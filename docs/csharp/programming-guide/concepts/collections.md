---
title: Kolekcje (C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
caps.latest.revision: "6"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 271939b869433742f8b5720ba05955169ea5c410
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="collections-c"></a><span data-ttu-id="46c93-102">Kolekcje (C#)</span><span class="sxs-lookup"><span data-stu-id="46c93-102">Collections (C#)</span></span>
<span data-ttu-id="46c93-103">Dla wielu aplikacji, dla których chcesz Utwórz i Zarządzaj grupami powiązanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="46c93-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="46c93-104">Istnieją dwa sposoby do obiektów grup: tworzenie tablic obiektów oraz tworzenie kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="46c93-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="46c93-105">Tablice są najbardziej przydatne do tworzenia i Praca z stała liczba silnie typizowanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="46c93-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="46c93-106">Aby uzyskać informacje dotyczące tablic, zobacz [tablice](../../../csharp/programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="46c93-106">For information about arrays, see [Arrays](../../../csharp/programming-guide/arrays/index.md).</span></span>  
  
 <span data-ttu-id="46c93-107">Kolekcje umożliwiają bardziej elastyczne do pracy z grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="46c93-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="46c93-108">W przeciwieństwie do tablic grupy obiektów, którymi współpracujesz można zwiększyć lub zmniejszyć dynamicznie, musi mieć zmiany aplikacji.</span><span class="sxs-lookup"><span data-stu-id="46c93-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="46c93-109">Niektóre zbiory klucza można przypisać do wszystkich obiektów, które można umieścić w kolekcji, tak, aby szybko można pobrać obiektu przy użyciu klucza.</span><span class="sxs-lookup"><span data-stu-id="46c93-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="46c93-110">Kolekcja jest klasa, więc należy zadeklarować wystąpienia klasy, aby można było dodać elementy do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="46c93-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="46c93-111">Jeśli kolekcja zawiera elementy tylko jednego typu danych, możesz użyć jednej z klas w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="46c93-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="46c93-112">Ogólnej kolekcji wymusza zabezpieczenie typów, dzięki czemu można dodać do niego inny typ danych.</span><span class="sxs-lookup"><span data-stu-id="46c93-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="46c93-113">Podczas pobierania elementu z kolekcji uniwersalnej, nie trzeba określić jego typu danych albo przekonwertować go.</span><span class="sxs-lookup"><span data-stu-id="46c93-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46c93-114">Przykłady w tym temacie, można dołączyć [przy użyciu](../../../csharp/language-reference/keywords/using-directive.md) dyrektywy `System.Collections.Generic` i `System.Linq` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="46c93-114">For the examples in this topic, include [using](../../../csharp/language-reference/keywords/using-directive.md) directives for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="46c93-115">**W tym temacie**</span><span class="sxs-lookup"><span data-stu-id="46c93-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="46c93-116">Przy użyciu prostych kolekcji</span><span class="sxs-lookup"><span data-stu-id="46c93-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="46c93-117">Typy kolekcji</span><span class="sxs-lookup"><span data-stu-id="46c93-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="46c93-118">System.Collections.Generic Classes</span><span class="sxs-lookup"><span data-stu-id="46c93-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="46c93-119">System.Collections.Concurrent Classes</span><span class="sxs-lookup"><span data-stu-id="46c93-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="46c93-120">System.Collections — klasy</span><span class="sxs-lookup"><span data-stu-id="46c93-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
-   [<span data-ttu-id="46c93-121">Implementowanie kolekcję par klucz/wartość</span><span class="sxs-lookup"><span data-stu-id="46c93-121">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="46c93-122">Otwieranie kolekcji za pomocą LINQ</span><span class="sxs-lookup"><span data-stu-id="46c93-122">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="46c93-123">Sortowanie kolekcji</span><span class="sxs-lookup"><span data-stu-id="46c93-123">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="46c93-124">Definiowanie kolekcji niestandardowej</span><span class="sxs-lookup"><span data-stu-id="46c93-124">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="46c93-125">Iteratory</span><span class="sxs-lookup"><span data-stu-id="46c93-125">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="46c93-126">Przy użyciu prostych kolekcji</span><span class="sxs-lookup"><span data-stu-id="46c93-126">Using a Simple Collection</span></span>  
 <span data-ttu-id="46c93-127">Przykłady w tej sekcji używać ogólnych <xref:System.Collections.Generic.List%601> klasy, która umożliwia pracę z silnie typizowaną listę obiektów.</span><span class="sxs-lookup"><span data-stu-id="46c93-127">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="46c93-128">Poniższy przykład tworzy listę ciągów i następnie iteruje ciągi za pomocą lub [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="46c93-128">The following example creates a list of strings and then iterates through the strings by using a or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span>  
  
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
  
 <span data-ttu-id="46c93-129">Jeśli zawartość kolekcji są znane z wyprzedzeniem, możesz użyć *inicjatora kolekcji* do zainicjowania dla kolekcji.</span><span class="sxs-lookup"><span data-stu-id="46c93-129">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="46c93-130">Aby uzyskać więcej informacji, zobacz [inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="46c93-130">For more information, see [Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
 <span data-ttu-id="46c93-131">Poniższy przykład jest taki sam, jak poprzedni przykład, z wyjątkiem inicjatora kolekcji służy do dodawania elementów do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="46c93-131">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
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
  
 <span data-ttu-id="46c93-132">Można użyć [dla](../../../csharp/language-reference/keywords/for.md) instrukcji zamiast `foreach` instrukcji do iterowania po kolekcji.</span><span class="sxs-lookup"><span data-stu-id="46c93-132">You can use a [for](../../../csharp/language-reference/keywords/for.md) statement instead of a `foreach` statement to iterate through a collection.</span></span> <span data-ttu-id="46c93-133">Można to zrobić, należy podczas uzyskiwania dostępu do elementów kolekcji przez indeks.</span><span class="sxs-lookup"><span data-stu-id="46c93-133">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="46c93-134">Indeks elementów rozpoczyna się od 0 i kończy się liczbę element pomniejszonej o 1.</span><span class="sxs-lookup"><span data-stu-id="46c93-134">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="46c93-135">Poniższy przykład iterację elementów kolekcji za pomocą `for` zamiast `foreach`.</span><span class="sxs-lookup"><span data-stu-id="46c93-135">The following example iterates through the elements of a collection by using `for` instead of `foreach`.</span></span>  
  
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
  
 <span data-ttu-id="46c93-136">Poniższy przykład umożliwia usunięcie elementu z kolekcji, określając obiekt do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="46c93-136">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
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
  
 <span data-ttu-id="46c93-137">Poniższy przykład umożliwia usunięcie elementów z listy ogólnej.</span><span class="sxs-lookup"><span data-stu-id="46c93-137">The following example removes elements from a generic list.</span></span> <span data-ttu-id="46c93-138">Zamiast `foreach` instrukcji, [dla](../../../csharp/language-reference/keywords/for.md) używana jest instrukcja, która wykonuje iterację w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="46c93-138">Instead of a `foreach` statement, a [for](../../../csharp/language-reference/keywords/for.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="46c93-139">Jest to spowodowane <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda powoduje elementów po usunięty element ma niższą wartość indeksu.</span><span class="sxs-lookup"><span data-stu-id="46c93-139">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
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
  
 <span data-ttu-id="46c93-140">Dla typu elementów w <xref:System.Collections.Generic.List%601>, możesz również definiować własne klasy.</span><span class="sxs-lookup"><span data-stu-id="46c93-140">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="46c93-141">W poniższym przykładzie `Galaxy` klasy, która jest używana przez <xref:System.Collections.Generic.List%601> jest zdefiniowany w kodzie.</span><span class="sxs-lookup"><span data-stu-id="46c93-141">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
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
## <a name="kinds-of-collections"></a><span data-ttu-id="46c93-142">Typy kolekcji</span><span class="sxs-lookup"><span data-stu-id="46c93-142">Kinds of Collections</span></span> 
 <span data-ttu-id="46c93-143">Wielu typowych kolekcji są dostarczane przez program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="46c93-143">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="46c93-144">Każdy typ kolekcji jest przeznaczony dla określonego celu.</span><span class="sxs-lookup"><span data-stu-id="46c93-144">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="46c93-145">W tej sekcji opisano niektóre typowe klasy kolekcji:</span><span class="sxs-lookup"><span data-stu-id="46c93-145">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="46c93-146"><xref:System.Collections.Generic>klasy</span><span class="sxs-lookup"><span data-stu-id="46c93-146"><xref:System.Collections.Generic> classes</span></span>  
  
-   <span data-ttu-id="46c93-147"><xref:System.Collections.Concurrent>klasy</span><span class="sxs-lookup"><span data-stu-id="46c93-147"><xref:System.Collections.Concurrent> classes</span></span>  
  
-   <span data-ttu-id="46c93-148"><xref:System.Collections>klasy</span><span class="sxs-lookup"><span data-stu-id="46c93-148"><xref:System.Collections> classes</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="46c93-149">System.Collections.Generic Classes</span><span class="sxs-lookup"><span data-stu-id="46c93-149">System.Collections.Generic Classes</span></span>  
 <span data-ttu-id="46c93-150">Można utworzyć kolekcję ogólną za pomocą jednej z klas w <xref:System.Collections.Generic> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="46c93-150">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="46c93-151">Ogólnej kolekcji jest przydatne, gdy każdy element w kolekcji ma ten sam typ danych.</span><span class="sxs-lookup"><span data-stu-id="46c93-151">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="46c93-152">Wymusza ogólnej kolekcji silne wpisywanie, zezwalając tylko żądanych danych typu do dodania.</span><span class="sxs-lookup"><span data-stu-id="46c93-152">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="46c93-153">W poniższej tabeli przedstawiono niektóre często używane klasy <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="46c93-153">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>  

|<span data-ttu-id="46c93-154">Class</span><span class="sxs-lookup"><span data-stu-id="46c93-154">Class</span></span>|<span data-ttu-id="46c93-155">Opis</span><span class="sxs-lookup"><span data-stu-id="46c93-155">Description</span></span>| 
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="46c93-156">Reprezentuje kolekcję pary klucz wartość, które są zorganizowane według klucza.</span><span class="sxs-lookup"><span data-stu-id="46c93-156">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="46c93-157">Reprezentuje listę obiektów, które mogą być udostępniane przez indeks.</span><span class="sxs-lookup"><span data-stu-id="46c93-157">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="46c93-158">Udostępnia metody do wyszukiwania, sortowania i modyfikowania list.</span><span class="sxs-lookup"><span data-stu-id="46c93-158">Provides methods to search, sort, and modify lists.</span></span>|  
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="46c93-159">Reprezentuje pierwszy w pierwszym FIFO kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="46c93-159">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="46c93-160">Reprezentuje kolekcję par klucz/wartość, które są sortowane według klucza opartego na skojarzonym <xref:System.Collections.Generic.IComparer%601> implementacji.</span><span class="sxs-lookup"><span data-stu-id="46c93-160">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="46c93-161">Reprezentuje ostatni w pierwszym LIFO kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="46c93-161">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="46c93-162">Aby uzyskać dodatkowe informacje, zobacz [często używane typy kolekcji](../../../standard/collections/commonly-used-collection-types.md), [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md), i <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="46c93-162">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="46c93-163">System.Collections.Concurrent Classes</span><span class="sxs-lookup"><span data-stu-id="46c93-163">System.Collections.Concurrent Classes</span></span>  
 <span data-ttu-id="46c93-164">W programie .NET Framework 4 lub nowszego, kolekcje w <xref:System.Collections.Concurrent> przestrzeni nazw zapewniają wydajność operacji wątkowo do uzyskiwania dostępu do kolekcji elementów, wiele wątków.</span><span class="sxs-lookup"><span data-stu-id="46c93-164">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="46c93-165">Klasy w <xref:System.Collections.Concurrent> przestrzeń nazw powinna być używana zamiast odpowiednie typy w <xref:System.Collections.Generic?displayProperty=nameWithType> i <xref:System.Collections?displayProperty=nameWithType> przestrzeni nazw w każdym przypadku, gdy wiele wątków jednocześnie uzyskują kolekcji.</span><span class="sxs-lookup"><span data-stu-id="46c93-165">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="46c93-166">Aby uzyskać więcej informacji, zobacz [kolekcje obsługujące wielowątkowość](../../../standard/collections/thread-safe/index.md) i <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="46c93-166">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="46c93-167">Niektóre klasy uwzględnione w <xref:System.Collections.Concurrent> przestrzeni nazw są <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, i <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="46c93-167">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="46c93-168">System.Collections — klasy</span><span class="sxs-lookup"><span data-stu-id="46c93-168">System.Collections Classes</span></span>  
 <span data-ttu-id="46c93-169">Klasy w <xref:System.Collections?displayProperty=nameWithType> przestrzeni nazw nie należy przechowywać elementów, w szczególności obiektów określonego typu, ale jako obiekty typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="46c93-169">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="46c93-170">Jeśli to możliwe, należy użyć kolekcje ogólne w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw lub <xref:System.Collections.Concurrent> przestrzeni nazw zamiast starsze typy w `System.Collections` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="46c93-170">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="46c93-171">W poniższej tabeli przedstawiono niektóre często używane klasy w `System.Collections` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="46c93-171">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="46c93-172">Class</span><span class="sxs-lookup"><span data-stu-id="46c93-172">Class</span></span>|<span data-ttu-id="46c93-173">Opis</span><span class="sxs-lookup"><span data-stu-id="46c93-173">Description</span></span>|  
|---|---|  
|<xref:System.Collections.ArrayList>|<span data-ttu-id="46c93-174">Reprezentuje tablicę obiektów, którego rozmiar jest dynamicznie zwiększony jako wymagane.</span><span class="sxs-lookup"><span data-stu-id="46c93-174">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<xref:System.Collections.Hashtable>|<span data-ttu-id="46c93-175">Reprezentuje kolekcję pary klucz wartość, które są podzielone na podstawie kodu skrótu klucza.</span><span class="sxs-lookup"><span data-stu-id="46c93-175">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<xref:System.Collections.Queue>|<span data-ttu-id="46c93-176">Reprezentuje pierwszy w pierwszym FIFO kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="46c93-176">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Stack>|<span data-ttu-id="46c93-177">Reprezentuje ostatni w pierwszym LIFO kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="46c93-177">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="46c93-178"><xref:System.Collections.Specialized> Przestrzeń nazw zawiera klasy specjalistyczne i jednoznacznie kolekcji, takie jak kolekcji tylko do ciągów i słowników połączone listy i hybrydowych.</span><span class="sxs-lookup"><span data-stu-id="46c93-178">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="46c93-179">Implementowanie kolekcję par klucz/wartość</span><span class="sxs-lookup"><span data-stu-id="46c93-179">Implementing a Collection of Key/Value Pairs</span></span>  
 <span data-ttu-id="46c93-180"><xref:System.Collections.Generic.Dictionary%602> Kolekcji ogólnych umożliwia dostęp do elementów w kolekcji przy użyciu klucza każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="46c93-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="46c93-181">Każda dodatkowa do słownika składa się z wartością i skojarzonego z nim klucza.</span><span class="sxs-lookup"><span data-stu-id="46c93-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="46c93-182">Pobieranie wartości przy użyciu swojego klucza jest szybkie, ponieważ `Dictionary` klasy jest zaimplementowany jako tablicy skrótów.</span><span class="sxs-lookup"><span data-stu-id="46c93-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="46c93-183">Poniższy przykład tworzy `Dictionary` kolekcji i iteruje po słowniku przy użyciu `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="46c93-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `foreach` statement.</span></span>  
  
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
  
 <span data-ttu-id="46c93-184">Aby zamiast tego użyj inicjatora kolekcji, aby utworzyć `Dictionary` kolekcji, można zastąpić `BuildDictionary` i `AddToDictionary` metody przy użyciu następującej metody.</span><span class="sxs-lookup"><span data-stu-id="46c93-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
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
  
 <span data-ttu-id="46c93-185">W poniższym przykładzie użyto <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> — metoda i <xref:System.Collections.Generic.Dictionary%602.Item%2A> właściwość `Dictionary` można szybko znaleźć elementu według klucza.</span><span class="sxs-lookup"><span data-stu-id="46c93-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="46c93-186">`Item` Właściwość umożliwia dostęp do elementu w `elements` kolekcji przy użyciu `elements[symbol]` w języku C#.</span><span class="sxs-lookup"><span data-stu-id="46c93-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements[symbol]` in C#.</span></span>  
  
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
  
 <span data-ttu-id="46c93-187">W poniższym przykładzie zamiast niego użyto <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody szybko znaleźć elementu według klucza.</span><span class="sxs-lookup"><span data-stu-id="46c93-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
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
## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="46c93-188">Otwieranie kolekcji za pomocą LINQ</span><span class="sxs-lookup"><span data-stu-id="46c93-188">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="46c93-189">LINQ (zapytania język Language-Integrated) można uzyskać dostępu do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="46c93-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="46c93-190">Zapytania LINQ zapewniają filtrowanie, kolejność i grupowanie możliwości.</span><span class="sxs-lookup"><span data-stu-id="46c93-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="46c93-191">Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="46c93-191">For more information, see  [Getting Started with LINQ in C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="46c93-192">W poniższym przykładzie uruchamiane zapytania LINQ względem ogólnego `List`.</span><span class="sxs-lookup"><span data-stu-id="46c93-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="46c93-193">Zapytania LINQ zwraca innej kolekcji z wynikami.</span><span class="sxs-lookup"><span data-stu-id="46c93-193">The LINQ query returns a different collection that contains the results.</span></span>  
  
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
## <a name="sorting-a-collection"></a><span data-ttu-id="46c93-194">Sortowanie kolekcji</span><span class="sxs-lookup"><span data-stu-id="46c93-194">Sorting a Collection</span></span>  
 <span data-ttu-id="46c93-195">Poniższy przykład przedstawia procedurę sortowanie kolekcji.</span><span class="sxs-lookup"><span data-stu-id="46c93-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="46c93-196">Przykład sortuje wystąpienia `Car` klasy, które są przechowywane w <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="46c93-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="46c93-197">`Car` Klasa implementuje <xref:System.IComparable%601> interfejs, który wymaga, aby <xref:System.IComparable%601.CompareTo%2A> metoda zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="46c93-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="46c93-198">Każde wywołanie <xref:System.IComparable%601.CompareTo%2A> metoda pozwala jednym porównanie, które jest używane do sortowania.</span><span class="sxs-lookup"><span data-stu-id="46c93-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="46c93-199">Napisany przez użytkownika kod `CompareTo` metoda zwraca wartość dla każdego porównania bieżący obiekt z innym obiektem.</span><span class="sxs-lookup"><span data-stu-id="46c93-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="46c93-200">Wartość zwracana jest mniejsza niż zero, jeśli bieżący obiekt jest mniejsza od drugiego obiektu, większa niż zero, jeśli bieżący obiekt jest większy niż drugi obiekt i zero czy są równe.</span><span class="sxs-lookup"><span data-stu-id="46c93-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="46c93-201">Dzięki temu można zdefiniować w kodzie kryteria większa niż poniżej, a równa.</span><span class="sxs-lookup"><span data-stu-id="46c93-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="46c93-202">W `ListCars` metody `cars.Sort()` instrukcji sortuje listę.</span><span class="sxs-lookup"><span data-stu-id="46c93-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="46c93-203">To wywołanie <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> powoduje, że `CompareTo` wywoływanej automatycznie dla metody `Car` obiekty w `List`.</span><span class="sxs-lookup"><span data-stu-id="46c93-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
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
## <a name="defining-a-custom-collection"></a><span data-ttu-id="46c93-204">Definiowanie kolekcji niestandardowej</span><span class="sxs-lookup"><span data-stu-id="46c93-204">Defining a Custom Collection</span></span>  
 <span data-ttu-id="46c93-205">Należy zdefiniować kolekcję zaimplementowanie <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="46c93-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="46c93-206">Aby uzyskać dodatkowe informacje, zobacz [porady: uzyskiwanie dostępu do klasy kolekcji za pomocą instrukcji foreach](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md).</span><span class="sxs-lookup"><span data-stu-id="46c93-206">For additional information, see [How to: Access a Collection Class with foreach](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md).</span></span>  
  
 <span data-ttu-id="46c93-207">Mimo że można zdefiniować niestandardowej kolekcji, jest zazwyczaj lepiej jest użyć kolekcje, które znajdują się w programie .NET Framework, które zostały opisane w [rodzaje kolekcji](#BKMK_KindsOfCollections) wcześniej w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="46c93-207">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#BKMK_KindsOfCollections) earlier in this topic.</span></span>  
  
 <span data-ttu-id="46c93-208">W poniższym przykładzie zdefiniowano klasę kolekcji niestandardowej o nazwie `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="46c93-208">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="46c93-209">Ta klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który wymaga, aby <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="46c93-209">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="46c93-210">`GetEnumerator` Metoda zwraca wystąpienie klasy `ColorEnumerator` klasy.</span><span class="sxs-lookup"><span data-stu-id="46c93-210">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="46c93-211">`ColorEnumerator`implementuje <xref:System.Collections.IEnumerator> interfejs, który wymaga, aby <xref:System.Collections.IEnumerator.Current%2A> właściwość <xref:System.Collections.IEnumerator.MoveNext%2A> metody i <xref:System.Collections.IEnumerator.Reset%2A> metoda zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="46c93-211">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
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
##  <a name="iterators"></a><span data-ttu-id="46c93-212">Iteratory</span><span class="sxs-lookup"><span data-stu-id="46c93-212">Iterators</span></span>  
 <span data-ttu-id="46c93-213">*Iterator* służy do przeprowadzania niestandardowej iteracji w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="46c93-213">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="46c93-214">Iterator może być metodą lub `get` dostępu.</span><span class="sxs-lookup"><span data-stu-id="46c93-214">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="46c93-215">Używa iteratora [yield return](../../../csharp/language-reference/keywords/yield.md) instrukcji, aby zwracany był każdy element kolekcji jednym naraz.</span><span class="sxs-lookup"><span data-stu-id="46c93-215">An iterator uses a [yield return](../../../csharp/language-reference/keywords/yield.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="46c93-216">Należy wywołać przy użyciu iteratora [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="46c93-216">You call an iterator by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="46c93-217">Każdej iteracji `foreach` pętli wywołuje iteratora.</span><span class="sxs-lookup"><span data-stu-id="46c93-217">Each iteration of the `foreach` loop calls the iterator.</span></span> <span data-ttu-id="46c93-218">Gdy `yield return` iteratora osiągnie instrukcję, wyrażenie jest zwracany i są przechowywane w bieżącej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="46c93-218">When a `yield return` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="46c93-219">Wykonanie jest ponownie z tej lokalizacji iteratora jest wywoływana przy następnym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="46c93-219">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="46c93-220">Aby uzyskać więcej informacji, zobacz [Iteratory (C#)](../../../csharp/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="46c93-220">For more information, see [Iterators (C#)](../../../csharp/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="46c93-221">W poniższym przykładzie użyto metody iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="46c93-221">The following example uses an iterator method.</span></span> <span data-ttu-id="46c93-222">Iterator — metoda ma `yield return` instrukcji, która znajduje się wewnątrz [dla](../../../csharp/language-reference/keywords/for.md) pętli.</span><span class="sxs-lookup"><span data-stu-id="46c93-222">The iterator method has a `yield return` statement that is inside a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="46c93-223">W `ListEvenNumbers` metoda, każdej iteracji `foreach` treść instrukcji tworzy wywołanie do metody iteracyjne, który przechodzi do następnego `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="46c93-223">In the `ListEvenNumbers` method, each iteration of the `foreach` statement body creates a call to the iterator method, which proceeds to the next `yield return` statement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="46c93-224">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46c93-224">See Also</span></span>  
 [<span data-ttu-id="46c93-225">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="46c93-225">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="46c93-226">Koncepcje programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="46c93-226">Programming Concepts (C#)</span></span>](../../../csharp/programming-guide/concepts/index.md)  
 [<span data-ttu-id="46c93-227">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="46c93-227">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="46c93-228">LINQ do obiektów (C#)</span><span class="sxs-lookup"><span data-stu-id="46c93-228">LINQ to Objects (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="46c93-229">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="46c93-229">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)  
 [<span data-ttu-id="46c93-230">Kolekcje i struktury danych</span><span class="sxs-lookup"><span data-stu-id="46c93-230">Collections and Data Structures</span></span>](../../../standard/collections/index.md)  
 [<span data-ttu-id="46c93-231">Tworzenie i operowanie nimi kolekcje</span><span class="sxs-lookup"><span data-stu-id="46c93-231">Creating and Manipulating Collections</span></span>](http://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
 [<span data-ttu-id="46c93-232">Wybieranie klasy kolekcji</span><span class="sxs-lookup"><span data-stu-id="46c93-232">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)  
 [<span data-ttu-id="46c93-233">Porównywanie i sortowanie w ramach kolekcji</span><span class="sxs-lookup"><span data-stu-id="46c93-233">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
 [<span data-ttu-id="46c93-234">Kiedy należy używać kolekcji ogólnych</span><span class="sxs-lookup"><span data-stu-id="46c93-234">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)  
 [<span data-ttu-id="46c93-235">Instrukcje: uzyskiwanie dostępu do klasy kolekcji za pomocą instrukcji foreach</span><span class="sxs-lookup"><span data-stu-id="46c93-235">How to: Access a Collection Class with foreach</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)
