---
title: Kolekcje (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: 734eeba001c243fa3466ac608feb766d6d94c394
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698768"
---
# <a name="collections-visual-basic"></a><span data-ttu-id="053ff-102">Kolekcje (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="053ff-102">Collections (Visual Basic)</span></span>
<span data-ttu-id="053ff-103">W przypadku wielu aplikacji, dla których chcesz utworzyć grupy i zarządzać nimi powiązanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="053ff-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="053ff-104">Istnieją dwa sposoby grupowania obiektów: poprzez tworzenie tablic obiektów oraz poprzez tworzenie kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="053ff-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="053ff-105">Tablice są najbardziej przydatne do tworzenia i pracy ze stałą liczbą jednoznacznie silnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="053ff-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="053ff-106">Aby uzyskać informacje na temat tablic, zobacz [tablic](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="053ff-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="053ff-107">Kolekcje zapewniają bardziej elastyczny sposób pracy z grupami obiektów.</span><span class="sxs-lookup"><span data-stu-id="053ff-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="053ff-108">W odróżnieniu od tablic grupa obiektów, którymi pracujesz można zwiększyć lub zmniejszyć dynamicznie, potrzeb zmiany aplikacji.</span><span class="sxs-lookup"><span data-stu-id="053ff-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="053ff-109">W niektórych kolekcjach można przypisać klawisz do dowolnych obiektów umieszczonych do kolekcji, tak aby pozwala na szybkie pobranie obiektu przy użyciu klucza.</span><span class="sxs-lookup"><span data-stu-id="053ff-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="053ff-110">Kolekcja jest klasą, więc należy zadeklarować wystąpienia klasy, aby można było dodać elementy do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="053ff-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="053ff-111">Jeśli kolekcja zawiera elementy tylko jednego typu danych, możesz użyć jednej z klas w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="053ff-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="053ff-112">Ogólna kolekcja wymusza typ bezpieczeństwa tak, aby żaden typ danych można dodać do niego.</span><span class="sxs-lookup"><span data-stu-id="053ff-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="053ff-113">Po pobraniu elementu z kolekcji generycznej, nie trzeba określać jego typu danych, ani go konwertować.</span><span class="sxs-lookup"><span data-stu-id="053ff-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="053ff-114">W przykładach w tym temacie zawierają [Importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instrukcji dla `System.Collections.Generic` i `System.Linq` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="053ff-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="053ff-115">**W tym temacie**</span><span class="sxs-lookup"><span data-stu-id="053ff-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="053ff-116">Za pomocą prostej kolekcji</span><span class="sxs-lookup"><span data-stu-id="053ff-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="053ff-117">Rodzaje kolekcji</span><span class="sxs-lookup"><span data-stu-id="053ff-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="053ff-118">System.Collections.Generic Classes</span><span class="sxs-lookup"><span data-stu-id="053ff-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="053ff-119">System.Collections.Concurrent Classes</span><span class="sxs-lookup"><span data-stu-id="053ff-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="053ff-120">System.Collections Classes</span><span class="sxs-lookup"><span data-stu-id="053ff-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
    -   [<span data-ttu-id="053ff-121">Klasa kolekcji Visual Basic</span><span class="sxs-lookup"><span data-stu-id="053ff-121">Visual Basic Collection Class</span></span>](#BKMK_VisualBasic)  
  
-   [<span data-ttu-id="053ff-122">Implementowanie kolekcji par klucz/wartość</span><span class="sxs-lookup"><span data-stu-id="053ff-122">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="053ff-123">Za pomocą LINQ do dostępu do kolekcji</span><span class="sxs-lookup"><span data-stu-id="053ff-123">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="053ff-124">Sortowanie kolekcji</span><span class="sxs-lookup"><span data-stu-id="053ff-124">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="053ff-125">Definiowanie kolekcji niestandardowej</span><span class="sxs-lookup"><span data-stu-id="053ff-125">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="053ff-126">Iteratory</span><span class="sxs-lookup"><span data-stu-id="053ff-126">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="053ff-127">Za pomocą prostej kolekcji</span><span class="sxs-lookup"><span data-stu-id="053ff-127">Using a Simple Collection</span></span>  
 <span data-ttu-id="053ff-128">W przykładach w tej sekcji użyto ogólnego <xref:System.Collections.Generic.List%601> klasy, która umożliwia pracę z silnie typizowanej listy obiektów.</span><span class="sxs-lookup"><span data-stu-id="053ff-128">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="053ff-129">Poniższy przykład tworzy listę ciągów i następnie iterację przez ciągi przy użyciu [For Each... Następny](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="053ff-129">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>  
  
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
  
 <span data-ttu-id="053ff-130">Jeśli zawartość kolekcji jest znana z wyprzedzeniem, można użyć *inicjatora kolekcji* do zainicjowania dla kolekcji.</span><span class="sxs-lookup"><span data-stu-id="053ff-130">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="053ff-131">Aby uzyskać więcej informacji, zobacz [inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="053ff-131">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>  
  
 <span data-ttu-id="053ff-132">Poniższy przykład jest taka sama, jak w poprzednim przykładzie, z wyjątkiem inicjatora kolekcji jest używana do dodawania elementów do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="053ff-132">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
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
  
 <span data-ttu-id="053ff-133">Możesz użyć [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) instrukcji zamiast `For Each` instrukcję do iterowania po kolekcji.</span><span class="sxs-lookup"><span data-stu-id="053ff-133">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="053ff-134">Osiągniesz to uzyskując dostęp do elementów kolekcji przez pozycję indeksu.</span><span class="sxs-lookup"><span data-stu-id="053ff-134">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="053ff-135">Indeks elementów zaczyna się od 0 i kończy się liczbą elementów pomniejszoną o 1.</span><span class="sxs-lookup"><span data-stu-id="053ff-135">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="053ff-136">Poniższy przykład wykonuje iterację przez elementy kolekcji za pomocą `For…Next` zamiast `For Each`.</span><span class="sxs-lookup"><span data-stu-id="053ff-136">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="053ff-137">Poniższy przykład usuwa element z kolekcji określając obiekt do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="053ff-137">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
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
  
 <span data-ttu-id="053ff-138">Poniższy przykład usuwa elementy z listy ogólnej.</span><span class="sxs-lookup"><span data-stu-id="053ff-138">The following example removes elements from a generic list.</span></span> <span data-ttu-id="053ff-139">Zamiast `For Each` instrukcji [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) używana jest instrukcja, która dokonuje iteracji w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="053ff-139">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="053ff-140">Jest to spowodowane <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda powoduje, że elementy po usuniętym elemencie muszą mieć niższą wartość indeksu.</span><span class="sxs-lookup"><span data-stu-id="053ff-140">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
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
  
 <span data-ttu-id="053ff-141">Aby uzyskać typ elementów w <xref:System.Collections.Generic.List%601>, można również definiować własne klasy.</span><span class="sxs-lookup"><span data-stu-id="053ff-141">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="053ff-142">W poniższym przykładzie `Galaxy` klasę, która jest używana przez <xref:System.Collections.Generic.List%601> jest zdefiniowana w kodzie.</span><span class="sxs-lookup"><span data-stu-id="053ff-142">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
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
## <a name="kinds-of-collections"></a><span data-ttu-id="053ff-143">Rodzaje kolekcji</span><span class="sxs-lookup"><span data-stu-id="053ff-143">Kinds of Collections</span></span>   
 <span data-ttu-id="053ff-144">Wiele typowych kolekcji jest dostarczanych przez program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="053ff-144">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="053ff-145">Każdy typu kolekcji jest przeznaczony do określonego celu.</span><span class="sxs-lookup"><span data-stu-id="053ff-145">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="053ff-146">W tej sekcji opisano niektóre typowe klasy kolekcji:</span><span class="sxs-lookup"><span data-stu-id="053ff-146">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="053ff-147"><xref:System.Collections.Generic> Klasy</span><span class="sxs-lookup"><span data-stu-id="053ff-147"><xref:System.Collections.Generic> classes</span></span>  
  
-   <span data-ttu-id="053ff-148"><xref:System.Collections.Concurrent> Klasy</span><span class="sxs-lookup"><span data-stu-id="053ff-148"><xref:System.Collections.Concurrent> classes</span></span>  
  
-   <span data-ttu-id="053ff-149"><xref:System.Collections> Klasy</span><span class="sxs-lookup"><span data-stu-id="053ff-149"><xref:System.Collections> classes</span></span>  
  
-   <span data-ttu-id="053ff-150">Visual Basic `Collection` klasy</span><span class="sxs-lookup"><span data-stu-id="053ff-150">Visual Basic `Collection` class</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="053ff-151">System.Collections.Generic Classes</span><span class="sxs-lookup"><span data-stu-id="053ff-151">System.Collections.Generic Classes</span></span>  

 <span data-ttu-id="053ff-152">Możesz utworzyć ogólną kolekcję używając jednej z klas w <xref:System.Collections.Generic> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="053ff-152">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="053ff-153">Ogólna kolekcja jest przydatna w przypadku, gdy każdy element w kolekcji ma ten sam typ danych.</span><span class="sxs-lookup"><span data-stu-id="053ff-153">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="053ff-154">Ogólna kolekcja wymusza silne wpisywanie, zezwalając tylko na żądane dane typu ma zostać dodana.</span><span class="sxs-lookup"><span data-stu-id="053ff-154">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="053ff-155">W poniższej tabeli wymieniono niektóre z najczęściej używanych klas <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="053ff-155">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="053ff-156">Class</span><span class="sxs-lookup"><span data-stu-id="053ff-156">Class</span></span>|<span data-ttu-id="053ff-157">Opis</span><span class="sxs-lookup"><span data-stu-id="053ff-157">Description</span></span>|  
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="053ff-158">Przedstawia kolekcję par klucz wartość, które są zorganizowane na podstawie klucza.</span><span class="sxs-lookup"><span data-stu-id="053ff-158">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="053ff-159">Reprezentuje listę obiektów, które mogą być udostępniane przez indeks.</span><span class="sxs-lookup"><span data-stu-id="053ff-159">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="053ff-160">Udostępnia metody do wyszukiwania, sortowania i modyfikowania list.</span><span class="sxs-lookup"><span data-stu-id="053ff-160">Provides methods to search, sort, and modify lists.</span></span>|  
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="053ff-161">Reprezentuje pierwszy na wejściu, pierwszy FIFO kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="053ff-161">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="053ff-162">Przedstawia kolekcję par klucz wartość, które są sortowane według klucza, w oparciu o związaną <xref:System.Collections.Generic.IComparer%601> implementacji.</span><span class="sxs-lookup"><span data-stu-id="053ff-162">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="053ff-163">Reprezentuje ostatni na wejściu, pierwszy LIFO kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="053ff-163">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="053ff-164">Aby uzyskać więcej informacji, zobacz [powszechnie używane typy kolekcji](../../../standard/collections/commonly-used-collection-types.md), [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md), i <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="053ff-164">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="053ff-165">System.Collections.Concurrent Classes</span><span class="sxs-lookup"><span data-stu-id="053ff-165">System.Collections.Concurrent Classes</span></span>   
 <span data-ttu-id="053ff-166">W .NET Framework 4 lub nowszej, kolekcje w programie <xref:System.Collections.Concurrent> przestrzeni nazw zapewniają efektywne działania wątków do uzyskiwania dostępu do elementów kolekcji z wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="053ff-166">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="053ff-167">Klasy w <xref:System.Collections.Concurrent> przestrzeni nazw powinny być używane zamiast odpowiednich typów w <xref:System.Collections.Generic?displayProperty=nameWithType> i <xref:System.Collections?displayProperty=nameWithType> przestrzeni nazw w każdym przypadku, gdy wiele wątków jednocześnie uzyskują kolekcji.</span><span class="sxs-lookup"><span data-stu-id="053ff-167">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="053ff-168">Aby uzyskać więcej informacji, zobacz [kolekcje obsługujące wielowątkowość](../../../standard/collections/thread-safe/index.md) i <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="053ff-168">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="053ff-169">Niektóre klasy uwzględnione w <xref:System.Collections.Concurrent> nazw są <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, i <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="053ff-169">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="053ff-170">System.Collections Classes</span><span class="sxs-lookup"><span data-stu-id="053ff-170">System.Collections Classes</span></span>    
 <span data-ttu-id="053ff-171">Klasy w <xref:System.Collections?displayProperty=nameWithType> przestrzeni nazw nie przechowują elementów jako specjalnie typowanych obiektów, ale jako obiekty typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="053ff-171">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="053ff-172">Jeśli to możliwe, należy używać ogólnych kolekcji w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw lub <xref:System.Collections.Concurrent> przestrzeni nazw, zamiast typów odziedziczonych w `System.Collections` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="053ff-172">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="053ff-173">W poniższej tabeli wymieniono niektóre z najczęściej używanych klas w `System.Collections` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="053ff-173">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="053ff-174">Class</span><span class="sxs-lookup"><span data-stu-id="053ff-174">Class</span></span>|<span data-ttu-id="053ff-175">Opis</span><span class="sxs-lookup"><span data-stu-id="053ff-175">Description</span></span>|  
|---|---|  
|<xref:System.Collections.ArrayList>|<span data-ttu-id="053ff-176">Reprezentuje tablicę obiektów, których rozmiar jest dynamicznie zwiększany w miarę wymagane.</span><span class="sxs-lookup"><span data-stu-id="053ff-176">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<xref:System.Collections.Hashtable>|<span data-ttu-id="053ff-177">Przedstawia kolekcję par klucz wartość, które są zorganizowane na podstawie kodu skrótu klucza.</span><span class="sxs-lookup"><span data-stu-id="053ff-177">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<xref:System.Collections.Queue>|<span data-ttu-id="053ff-178">Reprezentuje pierwszy na wejściu, pierwszy FIFO kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="053ff-178">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Stack>|<span data-ttu-id="053ff-179">Reprezentuje ostatni na wejściu, pierwszy LIFO kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="053ff-179">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="053ff-180"><xref:System.Collections.Specialized> Przestrzeń nazw zawiera specjalistyczne i silnie typizowanych klas kolekcji, takich jak kolekcje wyłącznie ciągów i listy powiązane i słowniki hybrydowe.</span><span class="sxs-lookup"><span data-stu-id="053ff-180">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a><span data-ttu-id="053ff-181">Klasa kolekcji Visual Basic</span><span class="sxs-lookup"><span data-stu-id="053ff-181">Visual Basic Collection Class</span></span>  
 <span data-ttu-id="053ff-182">Visual Basic można użyć <xref:Microsoft.VisualBasic.Collection> klasy dostęp do elementu kolekcji, korzystając albo z indeksu numerycznego lub a `String` klucza.</span><span class="sxs-lookup"><span data-stu-id="053ff-182">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="053ff-183">Można dodać elementy do obiektu kolekcji z lub bez określenia klucza.</span><span class="sxs-lookup"><span data-stu-id="053ff-183">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="053ff-184">Jeśli dodajesz element bez klucza, należy użyć jego indeksu liczbowego do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="053ff-184">If you add an item without a key, you must use its numeric index to access it.</span></span>  
  
 <span data-ttu-id="053ff-185">Visual Basic `Collection` klasa przechowuje wszystkie elementy jako typ `Object`, więc można dodać element każdego typu danych.</span><span class="sxs-lookup"><span data-stu-id="053ff-185">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="053ff-186">Nie ma zabezpieczenia nieprawidłowych typów danych dodawane.</span><span class="sxs-lookup"><span data-stu-id="053ff-186">There is no safeguard against inappropriate data types being added.</span></span>  
  
 <span data-ttu-id="053ff-187">Jeśli używasz języka Visual Basic `Collection` klasy, pierwszy element kolekcji posiada indeks 1.</span><span class="sxs-lookup"><span data-stu-id="053ff-187">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="053ff-188">To różni się od klas kolekcji .NET Framework, dla których indeks początkowy to 0.</span><span class="sxs-lookup"><span data-stu-id="053ff-188">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>  
  
 <span data-ttu-id="053ff-189">Jeśli to możliwe, należy używać ogólnych kolekcji w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw lub <xref:System.Collections.Concurrent> przestrzeni nazw, a nie Visual Basic `Collection` klasy.</span><span class="sxs-lookup"><span data-stu-id="053ff-189">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>  
  
 <span data-ttu-id="053ff-190">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Collection>.</span><span class="sxs-lookup"><span data-stu-id="053ff-190">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="053ff-191">Implementowanie kolekcji par klucz/wartość</span><span class="sxs-lookup"><span data-stu-id="053ff-191">Implementing a Collection of Key/Value Pairs</span></span>   
 <span data-ttu-id="053ff-192"><xref:System.Collections.Generic.Dictionary%602> Kolekcji ogólnej umożliwia dostęp do elementów w kolekcji za pomocą klucza każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="053ff-192">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="053ff-193">Każdy dodatkem do słownika składa się z wartości i skojarzonego z nim klucza.</span><span class="sxs-lookup"><span data-stu-id="053ff-193">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="053ff-194">Pobieranie wartości przy użyciu własnego klucza jest szybkie ponieważ `Dictionary` klasy jest implementowany jako tabelę mieszania.</span><span class="sxs-lookup"><span data-stu-id="053ff-194">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="053ff-195">Poniższy przykład tworzy `Dictionary` kolekcji i wykonuje iteracje przez słownik za pomocą `For Each` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="053ff-195">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>  
  
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
  
 <span data-ttu-id="053ff-196">Zamiast tego za pomocą inicjatora kolekcji tworzyć `Dictionary` kolekcji, można zastąpić `BuildDictionary` i `AddToDictionary` metody przy użyciu następującej metody.</span><span class="sxs-lookup"><span data-stu-id="053ff-196">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
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
  
 <span data-ttu-id="053ff-197">W poniższym przykładzie użyto <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metody i <xref:System.Collections.Generic.Dictionary%602.Item%2A> właściwość `Dictionary` szybko znaleźć element według klucza.</span><span class="sxs-lookup"><span data-stu-id="053ff-197">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="053ff-198">`Item` Właściwość pozwala na dostęp do elementu w `elements` kolekcji przy użyciu `elements(symbol)` kodu w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="053ff-198">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>  
  
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
  
 <span data-ttu-id="053ff-199">W poniższym przykładzie zamiast użyto <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metoda szybko znaleźć element według klucza.</span><span class="sxs-lookup"><span data-stu-id="053ff-199">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
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
##  <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="053ff-200">Za pomocą LINQ do dostępu do kolekcji</span><span class="sxs-lookup"><span data-stu-id="053ff-200">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="053ff-201">LINQ (Language-Integrated Query) może służyć do dostępu do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="053ff-201">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="053ff-202">Zapytania LINQ zapewniają filtrowanie, porządkowanie i możliwości grupowania.</span><span class="sxs-lookup"><span data-stu-id="053ff-202">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="053ff-203">Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="053ff-203">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="053ff-204">Poniższy przykład wykonuje zapytanie LINQ na ogólnej `List`.</span><span class="sxs-lookup"><span data-stu-id="053ff-204">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="053ff-205">Zapytanie LINQ zwraca inną kolekcję, która zawiera wyniki.</span><span class="sxs-lookup"><span data-stu-id="053ff-205">The LINQ query returns a different collection that contains the results.</span></span>  
  
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
## <a name="sorting-a-collection"></a><span data-ttu-id="053ff-206">Sortowanie kolekcji</span><span class="sxs-lookup"><span data-stu-id="053ff-206">Sorting a Collection</span></span>  
 <span data-ttu-id="053ff-207">Poniżej przedstawiono przykładową procedurę sortowania zbioru.</span><span class="sxs-lookup"><span data-stu-id="053ff-207">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="053ff-208">Przykład sortuje wystąpienia `Car` klasy, które są przechowywane w <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="053ff-208">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="053ff-209">`Car` Klasy implementuje <xref:System.IComparable%601> interfejs, który wymaga, aby <xref:System.IComparable%601.CompareTo%2A> metoda zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="053ff-209">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="053ff-210">Każde wywołanie <xref:System.IComparable%601.CompareTo%2A> metody tworzy pojedyncze porównanie, który jest używane do sortowania.</span><span class="sxs-lookup"><span data-stu-id="053ff-210">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="053ff-211">Kod napisany przez użytkownika w `CompareTo` metoda zwraca wartość dla każdego porównania bieżącego obiektu z innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="053ff-211">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="053ff-212">Wartość zwracana jest mniejsza niż zero, jeżeli bieżący obiekt jest mniejszy niż inny obiekt, większa niż zero, jeśli bieżący obiekt jest większy niż inny obiekt i zero czy są równe.</span><span class="sxs-lookup"><span data-stu-id="053ff-212">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="053ff-213">Umożliwia to definiowanie w kodzie kryteriów dla większych niż, mniejsze więc równa.</span><span class="sxs-lookup"><span data-stu-id="053ff-213">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="053ff-214">W `ListCars` metody `cars.Sort()` instrukcji sortuje listy.</span><span class="sxs-lookup"><span data-stu-id="053ff-214">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="053ff-215">To wywołanie <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> powoduje, że `CompareTo` metoda zostaje wywołana automatycznie dla `Car` obiekty w `List`.</span><span class="sxs-lookup"><span data-stu-id="053ff-215">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
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
## <a name="defining-a-custom-collection"></a><span data-ttu-id="053ff-216">Definiowanie kolekcji niestandardowej</span><span class="sxs-lookup"><span data-stu-id="053ff-216">Defining a Custom Collection</span></span>  
 <span data-ttu-id="053ff-217">Można zdefiniować kolekcję implementując <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="053ff-217">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="053ff-218">Aby uzyskać więcej informacji, zobacz [wyliczania kolekcji](https://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).</span><span class="sxs-lookup"><span data-stu-id="053ff-218">For additional information, see [Enumerating a Collection](https://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).</span></span>  
  
 <span data-ttu-id="053ff-219">Chociaż można zdefiniować kolekcję niestandardową, to zazwyczaj lepiej jest użyć zamiast tego kolekcje, które znajdują się w .NET Framework, które są opisane w [rodzaje kolekcji](#kinds-of-collections) we wcześniejszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="053ff-219">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#kinds-of-collections) earlier in this topic.</span></span>  
  
 <span data-ttu-id="053ff-220">W poniższym przykładzie zdefiniowano klasę kolekcji niestandardowej o nazwie `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="053ff-220">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="053ff-221">Ta klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który wymaga, aby <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="053ff-221">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="053ff-222">`GetEnumerator` Metoda zwraca wystąpienie `ColorEnumerator` klasy.</span><span class="sxs-lookup"><span data-stu-id="053ff-222">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="053ff-223">`ColorEnumerator` implementuje <xref:System.Collections.IEnumerator> interfejs, który wymaga, aby <xref:System.Collections.IEnumerator.Current%2A> właściwości <xref:System.Collections.IEnumerator.MoveNext%2A> metody i <xref:System.Collections.IEnumerator.Reset%2A> metoda zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="053ff-223">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
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
##  <a name="iterators"></a><span data-ttu-id="053ff-224">Iteratory</span><span class="sxs-lookup"><span data-stu-id="053ff-224">Iterators</span></span>  
 <span data-ttu-id="053ff-225">*Iteratora* służy do wykonywania niestandardowych iteracji przez kolekcję.</span><span class="sxs-lookup"><span data-stu-id="053ff-225">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="053ff-226">Iteracją może być metodą lub `get` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="053ff-226">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="053ff-227">Używa iteratora [uzyskanie](../../../visual-basic/language-reference/statements/yield-statement.md) instrukcja zwraca każdy element kolekcji naraz.</span><span class="sxs-lookup"><span data-stu-id="053ff-227">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="053ff-228">Wywołujesz iterację używając [For Each... Następny](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="053ff-228">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="053ff-229">Każda iteracja `For Each` pętli wywołuje iteratora.</span><span class="sxs-lookup"><span data-stu-id="053ff-229">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="053ff-230">Gdy `Yield` osiągnięciu instrukcji w iteratorze, wyrażenie jest zwracane, a bieżąca lokalizacja w kodzie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="053ff-230">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="053ff-231">Wykonanie jest uruchamiane ponownie z tej lokalizacji w przy następnym wywołaniu iteratora.</span><span class="sxs-lookup"><span data-stu-id="053ff-231">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="053ff-232">Aby uzyskać więcej informacji, zobacz [Iteratory (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="053ff-232">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="053ff-233">Poniższy przykład wykorzystuje metodę iteratora.</span><span class="sxs-lookup"><span data-stu-id="053ff-233">The following example uses an iterator method.</span></span> <span data-ttu-id="053ff-234">Metoda iteratora ma `Yield` instrukcji, która znajduje się wewnątrz [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) pętli.</span><span class="sxs-lookup"><span data-stu-id="053ff-234">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="053ff-235">W `ListEvenNumbers` metody, każda iteracja `For Each` treść instrukcji tworzy wywołanie metody iteracyjnej, która przechodzi do następnej `Yield` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="053ff-235">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="053ff-236">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="053ff-236">See also</span></span>

- [<span data-ttu-id="053ff-237">Inicjatory kolekcji</span><span class="sxs-lookup"><span data-stu-id="053ff-237">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="053ff-238">Koncepcje programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="053ff-238">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="053ff-239">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="053ff-239">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="053ff-240">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="053ff-240">LINQ to Objects (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="053ff-241">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="053ff-241">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)
- [<span data-ttu-id="053ff-242">Kolekcje i struktury danych</span><span class="sxs-lookup"><span data-stu-id="053ff-242">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="053ff-243">Tworzenie kolekcji i manipulowanie nimi</span><span class="sxs-lookup"><span data-stu-id="053ff-243">Creating and Manipulating Collections</span></span>](https://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)
- [<span data-ttu-id="053ff-244">Wybieranie klasy kolekcji</span><span class="sxs-lookup"><span data-stu-id="053ff-244">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="053ff-245">Porównywanie i sortowanie w ramach kolekcji</span><span class="sxs-lookup"><span data-stu-id="053ff-245">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="053ff-246">Kiedy należy używać kolekcji ogólnych</span><span class="sxs-lookup"><span data-stu-id="053ff-246">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
