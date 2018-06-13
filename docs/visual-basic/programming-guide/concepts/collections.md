---
title: Kolekcje (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: 563cef59c0e52d41dcdeaa51b5bc4d7b8f9554f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644319"
---
# <a name="collections-visual-basic"></a><span data-ttu-id="20161-102">Kolekcje (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20161-102">Collections (Visual Basic)</span></span>
<span data-ttu-id="20161-103">Dla wielu aplikacji, dla których chcesz Utwórz i Zarządzaj grupami powiązanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="20161-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="20161-104">Istnieją dwa sposoby do obiektów grup: tworzenie tablic obiektów oraz tworzenie kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="20161-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="20161-105">Tablice są najbardziej przydatne do tworzenia i Praca z stała liczba silnie typizowanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="20161-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="20161-106">Aby uzyskać informacje dotyczące tablic, zobacz [tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="20161-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="20161-107">Kolekcje umożliwiają bardziej elastyczne do pracy z grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="20161-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="20161-108">W przeciwieństwie do tablic grupy obiektów, którymi współpracujesz można zwiększyć lub zmniejszyć dynamicznie, musi mieć zmiany aplikacji.</span><span class="sxs-lookup"><span data-stu-id="20161-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="20161-109">Niektóre zbiory klucza można przypisać do wszystkich obiektów, które można umieścić w kolekcji, tak, aby szybko można pobrać obiektu przy użyciu klucza.</span><span class="sxs-lookup"><span data-stu-id="20161-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="20161-110">Kolekcja jest klasa, więc należy zadeklarować wystąpienia klasy, aby można było dodać elementy do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="20161-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="20161-111">Jeśli kolekcja zawiera elementy tylko jednego typu danych, możesz użyć jednej z klas w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="20161-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="20161-112">Ogólnej kolekcji wymusza zabezpieczenie typów, dzięki czemu można dodać do niego inny typ danych.</span><span class="sxs-lookup"><span data-stu-id="20161-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="20161-113">Podczas pobierania elementu z kolekcji uniwersalnej, nie trzeba określić jego typu danych albo przekonwertować go.</span><span class="sxs-lookup"><span data-stu-id="20161-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20161-114">Przykłady w tym temacie, można dołączyć [importów](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instrukcje dla `System.Collections.Generic` i `System.Linq` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="20161-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="20161-115">**W tym temacie**</span><span class="sxs-lookup"><span data-stu-id="20161-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="20161-116">Przy użyciu prostych kolekcji</span><span class="sxs-lookup"><span data-stu-id="20161-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="20161-117">Typy kolekcji</span><span class="sxs-lookup"><span data-stu-id="20161-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="20161-118">System.Collections.Generic Classes</span><span class="sxs-lookup"><span data-stu-id="20161-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="20161-119">Klasy System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="20161-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="20161-120">System.Collections — klasy</span><span class="sxs-lookup"><span data-stu-id="20161-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
    -   [<span data-ttu-id="20161-121">Klasa kolekcji Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20161-121">Visual Basic Collection Class</span></span>](#BKMK_VisualBasic)  
  
-   [<span data-ttu-id="20161-122">Implementowanie kolekcję par klucz/wartość</span><span class="sxs-lookup"><span data-stu-id="20161-122">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="20161-123">Otwieranie kolekcji za pomocą LINQ</span><span class="sxs-lookup"><span data-stu-id="20161-123">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="20161-124">Sortowanie kolekcji</span><span class="sxs-lookup"><span data-stu-id="20161-124">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="20161-125">Definiowanie kolekcji niestandardowej</span><span class="sxs-lookup"><span data-stu-id="20161-125">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="20161-126">Iteratory</span><span class="sxs-lookup"><span data-stu-id="20161-126">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="20161-127">Przy użyciu prostych kolekcji</span><span class="sxs-lookup"><span data-stu-id="20161-127">Using a Simple Collection</span></span>  
 <span data-ttu-id="20161-128">Przykłady w tej sekcji używać ogólnych <xref:System.Collections.Generic.List%601> klasy, która umożliwia pracę z silnie typizowaną listę obiektów.</span><span class="sxs-lookup"><span data-stu-id="20161-128">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="20161-129">Poniższy przykład tworzy listę ciągów i następnie iteruje ciągi za pomocą [For Each... Następny](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="20161-129">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>  
  
```vb  
' Create a list of strings.  
Dim salmons As New List(Of String)  
salmons.Add("chinook")  
salmons.Add("coho")  
salmons.Add("pink")  
salmons.Add("sockeye")  
  
' Iterate through the list.  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="20161-130">Jeśli zawartość kolekcji są znane z wyprzedzeniem, możesz użyć *inicjatora kolekcji* do zainicjowania dla kolekcji.</span><span class="sxs-lookup"><span data-stu-id="20161-130">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="20161-131">Aby uzyskać więcej informacji, zobacz [inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="20161-131">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>  
  
 <span data-ttu-id="20161-132">Poniższy przykład jest taki sam, jak poprzedni przykład, z wyjątkiem inicjatora kolekcji służy do dodawania elementów do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="20161-132">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="20161-133">Można użyć [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) instrukcji zamiast `For Each` instrukcji do iterowania po kolekcji.</span><span class="sxs-lookup"><span data-stu-id="20161-133">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="20161-134">Można to zrobić, należy podczas uzyskiwania dostępu do elementów kolekcji przez indeks.</span><span class="sxs-lookup"><span data-stu-id="20161-134">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="20161-135">Indeks elementów rozpoczyna się od 0 i kończy się liczbę element pomniejszonej o 1.</span><span class="sxs-lookup"><span data-stu-id="20161-135">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="20161-136">Poniższy przykład iterację elementów kolekcji za pomocą `For…Next` zamiast `For Each`.</span><span class="sxs-lookup"><span data-stu-id="20161-136">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="20161-137">Poniższy przykład umożliwia usunięcie elementu z kolekcji, określając obiekt do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="20161-137">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
' Remove an element in the list by specifying  
' the object.  
salmons.Remove("coho")  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook pink sockeye  
```  
  
 <span data-ttu-id="20161-138">Poniższy przykład umożliwia usunięcie elementów z listy ogólnej.</span><span class="sxs-lookup"><span data-stu-id="20161-138">The following example removes elements from a generic list.</span></span> <span data-ttu-id="20161-139">Zamiast `For Each` instrukcji [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) używana jest instrukcja, która wykonuje iterację w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="20161-139">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="20161-140">Jest to spowodowane <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda powoduje elementów po usunięty element ma niższą wartość indeksu.</span><span class="sxs-lookup"><span data-stu-id="20161-140">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
```vb  
Dim numbers As New List(Of Integer) From  
    {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}  
  
' Remove odd numbers.  
For index As Integer = numbers.Count - 1 To 0 Step -1  
    If numbers(index) Mod 2 = 1 Then  
        ' Remove the element by specifying  
        ' the zero-based index in the list.  
        numbers.RemoveAt(index)  
    End If  
Next  
  
' Iterate through the list.  
' A lambda expression is placed in the ForEach method  
' of the List(T) object.  
numbers.ForEach(  
    Sub(number) Console.Write(number & " "))  
' Output: 0 2 4 6 8  
```  
  
 <span data-ttu-id="20161-141">Dla typu elementów w <xref:System.Collections.Generic.List%601>, możesz również definiować własne klasy.</span><span class="sxs-lookup"><span data-stu-id="20161-141">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="20161-142">W poniższym przykładzie `Galaxy` klasy, która jest używana przez <xref:System.Collections.Generic.List%601> jest zdefiniowany w kodzie.</span><span class="sxs-lookup"><span data-stu-id="20161-142">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
```vb  
Private Sub IterateThroughList()  
    Dim theGalaxies As New List(Of Galaxy) From  
        {  
            New Galaxy With {.Name = "Tadpole", .MegaLightYears = 400},  
            New Galaxy With {.Name = "Pinwheel", .MegaLightYears = 25},  
            New Galaxy With {.Name = "Milky Way", .MegaLightYears = 0},  
            New Galaxy With {.Name = "Andromeda", .MegaLightYears = 3}  
        }  
  
    For Each theGalaxy In theGalaxies  
        With theGalaxy  
            Console.WriteLine(.Name & "  " & .MegaLightYears)  
        End With  
    Next  
  
    ' Output:  
    '  Tadpole  400  
    '  Pinwheel  25  
    '  Milky Way  0  
    '  Andromeda  3  
End Sub  
  
Public Class Galaxy  
    Public Property Name As String  
    Public Property MegaLightYears As Integer  
End Class  
```  
  
<a name="BKMK_KindsOfCollections"></a>
## <a name="kinds-of-collections"></a><span data-ttu-id="20161-143">Typy kolekcji</span><span class="sxs-lookup"><span data-stu-id="20161-143">Kinds of Collections</span></span>   
 <span data-ttu-id="20161-144">Wielu typowych kolekcji są dostarczane przez program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="20161-144">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="20161-145">Każdy typ kolekcji jest przeznaczony dla określonego celu.</span><span class="sxs-lookup"><span data-stu-id="20161-145">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="20161-146">W tej sekcji opisano niektóre typowe klasy kolekcji:</span><span class="sxs-lookup"><span data-stu-id="20161-146">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="20161-147"><xref:System.Collections.Generic> Klasy</span><span class="sxs-lookup"><span data-stu-id="20161-147"><xref:System.Collections.Generic> classes</span></span>  
  
-   <span data-ttu-id="20161-148"><xref:System.Collections.Concurrent> Klasy</span><span class="sxs-lookup"><span data-stu-id="20161-148"><xref:System.Collections.Concurrent> classes</span></span>  
  
-   <span data-ttu-id="20161-149"><xref:System.Collections> Klasy</span><span class="sxs-lookup"><span data-stu-id="20161-149"><xref:System.Collections> classes</span></span>  
  
-   <span data-ttu-id="20161-150">Visual Basic `Collection` — klasa</span><span class="sxs-lookup"><span data-stu-id="20161-150">Visual Basic `Collection` class</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="20161-151">System.Collections.Generic Classes</span><span class="sxs-lookup"><span data-stu-id="20161-151">System.Collections.Generic Classes</span></span>  

 <span data-ttu-id="20161-152">Można utworzyć kolekcję ogólną za pomocą jednej z klas w <xref:System.Collections.Generic> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="20161-152">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="20161-153">Ogólnej kolekcji jest przydatne, gdy każdy element w kolekcji ma ten sam typ danych.</span><span class="sxs-lookup"><span data-stu-id="20161-153">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="20161-154">Wymusza ogólnej kolekcji silne wpisywanie, zezwalając tylko żądanych danych typu do dodania.</span><span class="sxs-lookup"><span data-stu-id="20161-154">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="20161-155">W poniższej tabeli przedstawiono niektóre często używane klasy <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="20161-155">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="20161-156">Class</span><span class="sxs-lookup"><span data-stu-id="20161-156">Class</span></span>|<span data-ttu-id="20161-157">Opis</span><span class="sxs-lookup"><span data-stu-id="20161-157">Description</span></span>|  
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="20161-158">Reprezentuje kolekcję pary klucz wartość, które są zorganizowane według klucza.</span><span class="sxs-lookup"><span data-stu-id="20161-158">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="20161-159">Reprezentuje listę obiektów, które mogą być udostępniane przez indeks.</span><span class="sxs-lookup"><span data-stu-id="20161-159">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="20161-160">Udostępnia metody do wyszukiwania, sortowania i modyfikowania list.</span><span class="sxs-lookup"><span data-stu-id="20161-160">Provides methods to search, sort, and modify lists.</span></span>|  
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="20161-161">Reprezentuje pierwszy w pierwszym FIFO kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="20161-161">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="20161-162">Reprezentuje kolekcję par klucz/wartość, które są sortowane według klucza opartego na skojarzonym <xref:System.Collections.Generic.IComparer%601> implementacji.</span><span class="sxs-lookup"><span data-stu-id="20161-162">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="20161-163">Reprezentuje ostatni w pierwszym LIFO kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="20161-163">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="20161-164">Aby uzyskać dodatkowe informacje, zobacz [często używane typy kolekcji](../../../standard/collections/commonly-used-collection-types.md), [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md), i <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="20161-164">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="20161-165">System.Collections.Concurrent Classes</span><span class="sxs-lookup"><span data-stu-id="20161-165">System.Collections.Concurrent Classes</span></span>   
 <span data-ttu-id="20161-166">W programie .NET Framework 4 lub nowszego, kolekcje w <xref:System.Collections.Concurrent> przestrzeni nazw zapewniają wydajność operacji wątkowo do uzyskiwania dostępu do kolekcji elementów, wiele wątków.</span><span class="sxs-lookup"><span data-stu-id="20161-166">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="20161-167">Klasy w <xref:System.Collections.Concurrent> przestrzeń nazw powinna być używana zamiast odpowiednie typy w <xref:System.Collections.Generic?displayProperty=nameWithType> i <xref:System.Collections?displayProperty=nameWithType> przestrzeni nazw w każdym przypadku, gdy wiele wątków jednocześnie uzyskują kolekcji.</span><span class="sxs-lookup"><span data-stu-id="20161-167">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="20161-168">Aby uzyskać więcej informacji, zobacz [kolekcje obsługujące wielowątkowość](../../../standard/collections/thread-safe/index.md) i <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="20161-168">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="20161-169">Niektóre klasy uwzględnione w <xref:System.Collections.Concurrent> przestrzeni nazw są <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, i <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="20161-169">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="20161-170">System.Collections — klasy</span><span class="sxs-lookup"><span data-stu-id="20161-170">System.Collections Classes</span></span>    
 <span data-ttu-id="20161-171">Klasy w <xref:System.Collections?displayProperty=nameWithType> przestrzeni nazw nie należy przechowywać elementów, w szczególności obiektów określonego typu, ale jako obiekty typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="20161-171">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="20161-172">Jeśli to możliwe, należy użyć kolekcje ogólne w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw lub <xref:System.Collections.Concurrent> przestrzeni nazw zamiast starsze typy w `System.Collections` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="20161-172">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="20161-173">W poniższej tabeli przedstawiono niektóre często używane klasy w `System.Collections` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="20161-173">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="20161-174">Class</span><span class="sxs-lookup"><span data-stu-id="20161-174">Class</span></span>|<span data-ttu-id="20161-175">Opis</span><span class="sxs-lookup"><span data-stu-id="20161-175">Description</span></span>|  
|---|---|  
|<xref:System.Collections.ArrayList>|<span data-ttu-id="20161-176">Reprezentuje tablicę obiektów, którego rozmiar jest dynamicznie zwiększony jako wymagane.</span><span class="sxs-lookup"><span data-stu-id="20161-176">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<xref:System.Collections.Hashtable>|<span data-ttu-id="20161-177">Reprezentuje kolekcję pary klucz wartość, które są podzielone na podstawie kodu skrótu klucza.</span><span class="sxs-lookup"><span data-stu-id="20161-177">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<xref:System.Collections.Queue>|<span data-ttu-id="20161-178">Reprezentuje pierwszy w pierwszym FIFO kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="20161-178">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Stack>|<span data-ttu-id="20161-179">Reprezentuje ostatni w pierwszym LIFO kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="20161-179">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="20161-180"><xref:System.Collections.Specialized> Przestrzeń nazw zawiera klasy specjalistyczne i jednoznacznie kolekcji, takie jak kolekcji tylko do ciągów i słowników połączone listy i hybrydowych.</span><span class="sxs-lookup"><span data-stu-id="20161-180">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a><span data-ttu-id="20161-181">Klasa kolekcji Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20161-181">Visual Basic Collection Class</span></span>  
 <span data-ttu-id="20161-182">Korzystając z języka Visual Basic <xref:Microsoft.VisualBasic.Collection> klasa do dostępu do elementu przy użyciu liczbowym indeksem kolekcji lub a `String` klucza.</span><span class="sxs-lookup"><span data-stu-id="20161-182">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="20161-183">Elementy można dodać do obiektu kolekcji lub bez określenia klucza.</span><span class="sxs-lookup"><span data-stu-id="20161-183">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="20161-184">Jeśli dodasz do elementu bez klucza, należy użyć jego indeksu liczbowego dostępu do niego.</span><span class="sxs-lookup"><span data-stu-id="20161-184">If you add an item without a key, you must use its numeric index to access it.</span></span>  
  
 <span data-ttu-id="20161-185">Visual Basic `Collection` klasy wszystkie jego elementy są przechowywane jako typ `Object`, dzięki czemu można dodać elementu każdego typu danych.</span><span class="sxs-lookup"><span data-stu-id="20161-185">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="20161-186">Nie ma żadnych zabezpieczenie przed typy danych nieodpowiednie dodawany.</span><span class="sxs-lookup"><span data-stu-id="20161-186">There is no safeguard against inappropriate data types being added.</span></span>  
  
 <span data-ttu-id="20161-187">Jeśli używasz programu Visual Basic `Collection` klasy, pierwszy element w kolekcji ma indeks równy 1.</span><span class="sxs-lookup"><span data-stu-id="20161-187">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="20161-188">To różni się od klasy kolekcji .NET Framework, dla których początkowy indeks jest 0.</span><span class="sxs-lookup"><span data-stu-id="20161-188">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>  
  
 <span data-ttu-id="20161-189">Jeśli to możliwe, należy użyć kolekcje ogólne w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw lub <xref:System.Collections.Concurrent> przestrzeni nazw zamiast Visual Basic `Collection` klasy.</span><span class="sxs-lookup"><span data-stu-id="20161-189">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>  
  
 <span data-ttu-id="20161-190">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Collection>.</span><span class="sxs-lookup"><span data-stu-id="20161-190">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="20161-191">Implementowanie kolekcję par klucz/wartość</span><span class="sxs-lookup"><span data-stu-id="20161-191">Implementing a Collection of Key/Value Pairs</span></span>   
 <span data-ttu-id="20161-192"><xref:System.Collections.Generic.Dictionary%602> Kolekcji ogólnych umożliwia dostęp do elementów w kolekcji przy użyciu klucza każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="20161-192">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="20161-193">Każda dodatkowa do słownika składa się z wartością i skojarzonego z nim klucza.</span><span class="sxs-lookup"><span data-stu-id="20161-193">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="20161-194">Pobieranie wartości przy użyciu swojego klucza jest szybkie, ponieważ `Dictionary` klasy jest zaimplementowany jako tablicy skrótów.</span><span class="sxs-lookup"><span data-stu-id="20161-194">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="20161-195">Poniższy przykład tworzy `Dictionary` kolekcji i iteruje po słowniku przy użyciu `For Each` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="20161-195">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>  
  
```vb  
Private Sub IterateThroughDictionary()  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    For Each kvp As KeyValuePair(Of String, Element) In elements  
        Dim theElement As Element = kvp.Value  
  
        Console.WriteLine("key: " & kvp.Key)  
        With theElement  
            Console.WriteLine("values: " & .Symbol & " " &  
                .Name & " " & .AtomicNumber)  
        End With  
    Next  
End Sub  
  
Private Function BuildDictionary() As Dictionary(Of String, Element)  
    Dim elements As New Dictionary(Of String, Element)  
  
    AddToDictionary(elements, "K", "Potassium", 19)  
    AddToDictionary(elements, "Ca", "Calcium", 20)  
    AddToDictionary(elements, "Sc", "Scandium", 21)  
    AddToDictionary(elements, "Ti", "Titanium", 22)  
  
    Return elements  
End Function  
  
Private Sub AddToDictionary(ByVal elements As Dictionary(Of String, Element),  
ByVal symbol As String, ByVal name As String, ByVal atomicNumber As Integer)  
    Dim theElement As New Element  
  
    theElement.Symbol = symbol  
    theElement.Name = name  
    theElement.AtomicNumber = atomicNumber  
  
    elements.Add(Key:=theElement.Symbol, value:=theElement)  
End Sub  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 <span data-ttu-id="20161-196">Aby zamiast tego użyj inicjatora kolekcji, aby utworzyć `Dictionary` kolekcji, można zastąpić `BuildDictionary` i `AddToDictionary` metody przy użyciu następującej metody.</span><span class="sxs-lookup"><span data-stu-id="20161-196">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
```vb  
Private Function BuildDictionary2() As Dictionary(Of String, Element)  
    Return New Dictionary(Of String, Element) From  
        {  
            {"K", New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {"Ca", New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {"Sc", New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {"Ti", New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
```  
  
 <span data-ttu-id="20161-197">W poniższym przykładzie użyto <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> — metoda i <xref:System.Collections.Generic.Dictionary%602.Item%2A> właściwość `Dictionary` można szybko znaleźć elementu według klucza.</span><span class="sxs-lookup"><span data-stu-id="20161-197">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="20161-198">`Item` Właściwość umożliwia dostęp do elementu w `elements` kolekcji przy użyciu `elements(symbol)` kodu w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="20161-198">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>  
  
```vb  
Private Sub FindInDictionary(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    If elements.ContainsKey(symbol) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Dim theElement = elements(symbol)  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
 <span data-ttu-id="20161-199">W poniższym przykładzie zamiast niego użyto <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody szybko znaleźć elementu według klucza.</span><span class="sxs-lookup"><span data-stu-id="20161-199">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
```vb  
Private Sub FindInDictionary2(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    Dim theElement As Element = Nothing  
    If elements.TryGetValue(symbol, theElement) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
<a name="BKMK_LINQ"></a> 
##  <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="20161-200">Otwieranie kolekcji za pomocą LINQ</span><span class="sxs-lookup"><span data-stu-id="20161-200">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="20161-201">LINQ (zapytania język Language-Integrated) można uzyskać dostępu do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="20161-201">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="20161-202">Zapytania LINQ zapewniają filtrowanie, kolejność i grupowanie możliwości.</span><span class="sxs-lookup"><span data-stu-id="20161-202">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="20161-203">Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="20161-203">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="20161-204">W poniższym przykładzie uruchamiane zapytania LINQ względem ogólnego `List`.</span><span class="sxs-lookup"><span data-stu-id="20161-204">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="20161-205">Zapytania LINQ zwraca innej kolekcji z wynikami.</span><span class="sxs-lookup"><span data-stu-id="20161-205">The LINQ query returns a different collection that contains the results.</span></span>  
  
```vb  
Private Sub ShowLINQ()  
    Dim elements As List(Of Element) = BuildList()  
  
    ' LINQ Query.  
    Dim subset = From theElement In elements  
                  Where theElement.AtomicNumber < 22  
                  Order By theElement.Name  
  
    For Each theElement In subset  
        Console.WriteLine(theElement.Name & " " & theElement.AtomicNumber)  
    Next  
  
    ' Output:  
    '  Calcium 20  
    '  Potassium 19  
    '  Scandium 21  
End Sub  
  
Private Function BuildList() As List(Of Element)  
    Return New List(Of Element) From  
        {  
            {New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 <a name="BKMK_Sorting"></a> 
## <a name="sorting-a-collection"></a><span data-ttu-id="20161-206">Sortowanie kolekcji</span><span class="sxs-lookup"><span data-stu-id="20161-206">Sorting a Collection</span></span>  
 <span data-ttu-id="20161-207">Poniższy przykład przedstawia procedurę sortowanie kolekcji.</span><span class="sxs-lookup"><span data-stu-id="20161-207">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="20161-208">Przykład sortuje wystąpienia `Car` klasy, które są przechowywane w <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="20161-208">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="20161-209">`Car` Klasa implementuje <xref:System.IComparable%601> interfejs, który wymaga, aby <xref:System.IComparable%601.CompareTo%2A> metoda zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="20161-209">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="20161-210">Każde wywołanie <xref:System.IComparable%601.CompareTo%2A> metoda pozwala jednym porównanie, które jest używane do sortowania.</span><span class="sxs-lookup"><span data-stu-id="20161-210">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="20161-211">Napisany przez użytkownika kod `CompareTo` metoda zwraca wartość dla każdego porównania bieżący obiekt z innym obiektem.</span><span class="sxs-lookup"><span data-stu-id="20161-211">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="20161-212">Wartość zwracana jest mniejsza niż zero, jeśli bieżący obiekt jest mniejsza od drugiego obiektu, większa niż zero, jeśli bieżący obiekt jest większy niż drugi obiekt i zero czy są równe.</span><span class="sxs-lookup"><span data-stu-id="20161-212">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="20161-213">Dzięki temu można zdefiniować w kodzie kryteria większa niż poniżej, a równa.</span><span class="sxs-lookup"><span data-stu-id="20161-213">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="20161-214">W `ListCars` metody `cars.Sort()` instrukcji sortuje listę.</span><span class="sxs-lookup"><span data-stu-id="20161-214">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="20161-215">To wywołanie <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> powoduje, że `CompareTo` wywoływanej automatycznie dla metody `Car` obiekty w `List`.</span><span class="sxs-lookup"><span data-stu-id="20161-215">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
```vb  
Public Sub ListCars()  
  
    ' Create some new cars.  
    Dim cars As New List(Of Car) From  
    {  
        New Car With {.Name = "car1", .Color = "blue", .Speed = 20},  
        New Car With {.Name = "car2", .Color = "red", .Speed = 50},  
        New Car With {.Name = "car3", .Color = "green", .Speed = 10},  
        New Car With {.Name = "car4", .Color = "blue", .Speed = 50},  
        New Car With {.Name = "car5", .Color = "blue", .Speed = 30},  
        New Car With {.Name = "car6", .Color = "red", .Speed = 60},  
        New Car With {.Name = "car7", .Color = "green", .Speed = 50}  
    }  
  
    ' Sort the cars by color alphabetically, and then by speed  
    ' in descending order.  
    cars.Sort()  
  
    ' View all of the cars.  
    For Each thisCar As Car In cars  
        Console.Write(thisCar.Color.PadRight(5) & " ")  
        Console.Write(thisCar.Speed.ToString & " ")  
        Console.Write(thisCar.Name)  
        Console.WriteLine()  
    Next  
  
    ' Output:  
    '  blue  50 car4  
    '  blue  30 car5  
    '  blue  20 car1  
    '  green 50 car7  
    '  green 10 car3  
    '  red   60 car6  
    '  red   50 car2  
End Sub  
  
Public Class Car  
    Implements IComparable(Of Car)  
  
    Public Property Name As String  
    Public Property Speed As Integer  
    Public Property Color As String  
  
    Public Function CompareTo(ByVal other As Car) As Integer _  
        Implements System.IComparable(Of Car).CompareTo  
        ' A call to this method makes a single comparison that is  
        ' used for sorting.  
  
        ' Determine the relative order of the objects being compared.  
        ' Sort by color alphabetically, and then by speed in  
        ' descending order.  
  
        ' Compare the colors.  
        Dim compare As Integer  
        compare = String.Compare(Me.Color, other.Color, True)  
  
        ' If the colors are the same, compare the speeds.  
        If compare = 0 Then  
            compare = Me.Speed.CompareTo(other.Speed)  
  
            ' Use descending order for speed.  
            compare = -compare  
        End If  
  
        Return compare  
    End Function  
End Class  
```  
  
<a name="BKMK_CustomCollection"></a> 
## <a name="defining-a-custom-collection"></a><span data-ttu-id="20161-216">Definiowanie kolekcji niestandardowej</span><span class="sxs-lookup"><span data-stu-id="20161-216">Defining a Custom Collection</span></span>  
 <span data-ttu-id="20161-217">Należy zdefiniować kolekcję zaimplementowanie <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="20161-217">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="20161-218">Aby uzyskać dodatkowe informacje, zobacz [wyliczanie kolekcji](http://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).</span><span class="sxs-lookup"><span data-stu-id="20161-218">For additional information, see [Enumerating a Collection](http://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).</span></span>  
  
 <span data-ttu-id="20161-219">Mimo że można zdefiniować niestandardowej kolekcji, jest zazwyczaj lepiej jest użyć kolekcje, które znajdują się w programie .NET Framework, które zostały opisane w [rodzaje kolekcji](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) wcześniej w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="20161-219">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) earlier in this topic.</span></span>  
  
 <span data-ttu-id="20161-220">W poniższym przykładzie zdefiniowano klasę kolekcji niestandardowej o nazwie `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="20161-220">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="20161-221">Ta klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który wymaga, aby <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="20161-221">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="20161-222">`GetEnumerator` Metoda zwraca wystąpienie klasy `ColorEnumerator` klasy.</span><span class="sxs-lookup"><span data-stu-id="20161-222">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="20161-223">`ColorEnumerator` implementuje <xref:System.Collections.IEnumerator> interfejs, który wymaga, aby <xref:System.Collections.IEnumerator.Current%2A> właściwość <xref:System.Collections.IEnumerator.MoveNext%2A> metody i <xref:System.Collections.IEnumerator.Reset%2A> metoda zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="20161-223">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
```vb  
Public Sub ListColors()  
    Dim colors As New AllColors()  
  
    For Each theColor As Color In colors  
        Console.Write(theColor.Name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: red blue green  
End Sub  
  
' Collection class.  
Public Class AllColors  
    Implements System.Collections.IEnumerable  
  
    Private _colors() As Color =  
    {  
        New Color With {.Name = "red"},  
        New Color With {.Name = "blue"},  
        New Color With {.Name = "green"}  
    }  
  
    Public Function GetEnumerator() As System.Collections.IEnumerator _  
        Implements System.Collections.IEnumerable.GetEnumerator  
  
        Return New ColorEnumerator(_colors)  
  
        ' Instead of creating a custom enumerator, you could  
        ' use the GetEnumerator of the array.  
        'Return _colors.GetEnumerator  
    End Function  
  
    ' Custom enumerator.  
    Private Class ColorEnumerator  
        Implements System.Collections.IEnumerator  
  
        Private _colors() As Color  
        Private _position As Integer = -1  
  
        Public Sub New(ByVal colors() As Color)  
            _colors = colors  
        End Sub  
  
        Public ReadOnly Property Current() As Object _  
            Implements System.Collections.IEnumerator.Current  
            Get  
                Return _colors(_position)  
            End Get  
        End Property  
  
        Public Function MoveNext() As Boolean _  
            Implements System.Collections.IEnumerator.MoveNext  
            _position += 1  
            Return (_position < _colors.Length)  
        End Function  
  
        Public Sub Reset() Implements System.Collections.IEnumerator.Reset  
            _position = -1  
        End Sub  
    End Class  
End Class  
  
' Element class.  
Public Class Color  
    Public Property Name As String  
End Class  
```  
  
<a name="BKMK_Iterators"></a>
##  <a name="iterators"></a><span data-ttu-id="20161-224">Iteratory</span><span class="sxs-lookup"><span data-stu-id="20161-224">Iterators</span></span>  
 <span data-ttu-id="20161-225">*Iterator* służy do przeprowadzania niestandardowej iteracji w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="20161-225">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="20161-226">Iterator może być metodą lub `get` dostępu.</span><span class="sxs-lookup"><span data-stu-id="20161-226">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="20161-227">Używa iteratora [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instrukcji, aby zwracany był każdy element kolekcji jednym naraz.</span><span class="sxs-lookup"><span data-stu-id="20161-227">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="20161-228">Należy wywołać przy użyciu iteratora [For Each... Następny](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="20161-228">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="20161-229">Każdej iteracji `For Each` pętli wywołuje iteratora.</span><span class="sxs-lookup"><span data-stu-id="20161-229">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="20161-230">Gdy `Yield` iteratora osiągnie instrukcję, wyrażenie jest zwracany i są przechowywane w bieżącej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="20161-230">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="20161-231">Wykonanie jest ponownie z tej lokalizacji iteratora jest wywoływana przy następnym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="20161-231">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="20161-232">Aby uzyskać więcej informacji, zobacz [Iteratory (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="20161-232">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="20161-233">W poniższym przykładzie użyto metody iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="20161-233">The following example uses an iterator method.</span></span> <span data-ttu-id="20161-234">Iterator — metoda ma `Yield` instrukcji, która znajduje się wewnątrz [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) pętli.</span><span class="sxs-lookup"><span data-stu-id="20161-234">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="20161-235">W `ListEvenNumbers` metoda, każdej iteracji `For Each` treść instrukcji tworzy wywołanie do metody iteracyjne, który przechodzi do następnego `Yield` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="20161-235">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>  
  
```vb  
Public Sub ListEvenNumbers()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    Console.WriteLine()  
    ' Output: 6 8 10 12 14 16 18  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As IEnumerable(Of Integer)  
  
' Yield even numbers in the range.  
    For number = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="20161-236">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20161-236">See Also</span></span>  
 [<span data-ttu-id="20161-237">Inicjatory kolekcji</span><span class="sxs-lookup"><span data-stu-id="20161-237">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [<span data-ttu-id="20161-238">Koncepcje programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20161-238">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="20161-239">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="20161-239">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="20161-240">LINQ do obiektów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20161-240">LINQ to Objects (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="20161-241">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="20161-241">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)  
 [<span data-ttu-id="20161-242">Kolekcje i struktury danych</span><span class="sxs-lookup"><span data-stu-id="20161-242">Collections and Data Structures</span></span>](../../../standard/collections/index.md)  
 [<span data-ttu-id="20161-243">Tworzenie i operowanie nimi kolekcje</span><span class="sxs-lookup"><span data-stu-id="20161-243">Creating and Manipulating Collections</span></span>](http://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
 [<span data-ttu-id="20161-244">Wybieranie klasy kolekcji</span><span class="sxs-lookup"><span data-stu-id="20161-244">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)  
 [<span data-ttu-id="20161-245">Porównywanie i sortowanie w ramach kolekcji</span><span class="sxs-lookup"><span data-stu-id="20161-245">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
 [<span data-ttu-id="20161-246">Kiedy należy używać kolekcji ogólnych</span><span class="sxs-lookup"><span data-stu-id="20161-246">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
