---
title: Wykonywanie niezależnych od kultury operacji na ciągach w kolekcjach
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CaseInsensitiveComparer class, using
- CollectionsUtil.CreateCaseInsensitiveHashtable method
- culture-insensitive string operations, collections
- collections [.NET Framework], culture-insensitive string operations
- CaseInsensitiveHashCodeProvider class, using
- ArrayList.Sort method
- SortedList class, culture-insensitive string operations
- culture parameter
ms.assetid: 5cdc9396-a64b-4615-a1cd-b605db4c5983
ms.openlocfilehash: 377fa58e052e8f8e35a546c21fe2b4fb00cb103d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288267"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="1d258-102">Wykonywanie niezależnych od kultury operacji na ciągach w kolekcjach</span><span class="sxs-lookup"><span data-stu-id="1d258-102">Performing Culture-Insensitive String Operations in Collections</span></span>

<span data-ttu-id="1d258-103">Istnieją klasy i elementy członkowskie w <xref:System.Collections> przestrzeni nazw, które domyślnie udostępniają zachowania zależne od kultury.</span><span class="sxs-lookup"><span data-stu-id="1d258-103">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="1d258-104">Konstruktory bez parametrów dla <xref:System.Collections.CaseInsensitiveComparer> klas i <xref:System.Collections.CaseInsensitiveHashCodeProvider> inicjują nowe wystąpienie przy użyciu <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1d258-104">The parameterless constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="1d258-105">Wszystkie przeciążenia <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> metody tworzą nowe wystąpienie <xref:System.Collections.Hashtable> klasy przy użyciu `Thread.CurrentCulture` Domyślnie właściwości.</span><span class="sxs-lookup"><span data-stu-id="1d258-105">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="1d258-106">Przeciążenia <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> metody domyślnie wykonują sortowanie zależne od kultury przy użyciu `Thread.CurrentCulture` .</span><span class="sxs-lookup"><span data-stu-id="1d258-106">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="1d258-107">W <xref:System.Collections.SortedList> `Thread.CurrentCulture` przypadku, gdy ciągi są używane jako klucze, można mieć wpływ na sortowanie i wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="1d258-107">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="1d258-108">Postępuj zgodnie z zaleceniami dotyczącymi użycia opisanymi w tej sekcji, aby uzyskać wyniki niewrażliwe na kulturę z tych klas i metod w `Collections` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1d258-108">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="1d258-109">Przekazywanie <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> do metody porównania wykonuje porównanie nieuwzględniające kulturę.</span><span class="sxs-lookup"><span data-stu-id="1d258-109">Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="1d258-110">Nie powoduje to jednak porównania w języku innym niż język, na przykład w przypadku ścieżek plików, kluczy rejestru i zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="1d258-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="1d258-111">Żadna z tych funkcji nie wspiera podejmowania decyzji dotyczących zabezpieczeń w oparciu o wynik porównania.</span><span class="sxs-lookup"><span data-stu-id="1d258-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="1d258-112">W przypadku niezgodności z językiem lub pomocy technicznej dla decyzji o zabezpieczeniach opartych na wynikach aplikacja powinna używać metody porównania, która akceptuje <xref:System.StringComparison> wartość.</span><span class="sxs-lookup"><span data-stu-id="1d258-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="1d258-113">Aplikacja powinna następnie przejść <xref:System.StringComparison> .</span><span class="sxs-lookup"><span data-stu-id="1d258-113">The application should then pass <xref:System.StringComparison>.</span></span>

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="1d258-114">Korzystanie z klas CaseInsensitiveComparer i CaseInsensitiveHashCodeProvider</span><span class="sxs-lookup"><span data-stu-id="1d258-114">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>

<span data-ttu-id="1d258-115">Konstruktory bez parametrów dla `CaseInsensitiveHashCodeProvider` i `CaseInsensitiveComparer` inicjują nowe wystąpienie klasy przy użyciu, w `Thread.CurrentCulture` wyniku zachowania wrażliwego na kulturę.</span><span class="sxs-lookup"><span data-stu-id="1d258-115">The parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="1d258-116">Poniższy przykład kodu demonstruje Konstruktor dla `Hashtable` , który jest wrażliwy na kulturę, ponieważ używa konstruktorów bez parametrów dla `CaseInsensitiveHashCodeProvider` i `CaseInsensitiveComparer` .</span><span class="sxs-lookup"><span data-stu-id="1d258-116">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

<span data-ttu-id="1d258-117">Jeśli chcesz utworzyć niezależną `Hashtable` od kultury przy użyciu `CaseInsensitiveComparer` `CaseInsensitiveHashCodeProvider` klas i, zainicjuj nowe wystąpienia tych klas przy użyciu konstruktorów, które akceptują `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="1d258-117">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="1d258-118">Dla `culture` parametru Określ wartość <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1d258-118">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1d258-119">Poniższy przykład kodu demonstruje konstruktora dla niezależnych od kultury `Hashtable` .</span><span class="sxs-lookup"><span data-stu-id="1d258-119">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

```vb
internalHashtable = New Hashtable(New
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))
```

```csharp
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider
    (CultureInfo.InvariantCulture),
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));
```

## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="1d258-120">Korzystanie z metody CollectionsUtil. CreateCaseInsensitiveHashTable</span><span class="sxs-lookup"><span data-stu-id="1d258-120">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>

<span data-ttu-id="1d258-121">`CollectionsUtil.CreateCaseInsensitiveHashTable`Metoda jest użytecznym skrótem do tworzenia nowego wystąpienia `Hashtable` klasy, które ignoruje wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="1d258-121">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="1d258-122">Jednak wszystkie przeciążenia `CollectionsUtil.CreateCaseInsensitiveHashTable` metody są zależne od kultury, ponieważ używają `Thread.CurrentCulture` właściwości.</span><span class="sxs-lookup"><span data-stu-id="1d258-122">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="1d258-123">Nie można utworzyć bez uwzględniania kultury `Hashtable` przy użyciu tej metody.</span><span class="sxs-lookup"><span data-stu-id="1d258-123">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="1d258-124">Aby utworzyć niezależną od kultury `Hashtable` , użyj `Hashtable` konstruktora, który akceptuje `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="1d258-124">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="1d258-125">Dla `culture` parametru Określ wartość `CultureInfo.InvariantCulture` .</span><span class="sxs-lookup"><span data-stu-id="1d258-125">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="1d258-126">Poniższy przykład kodu demonstruje konstruktora dla niezależnych od kultury `Hashtable` .</span><span class="sxs-lookup"><span data-stu-id="1d258-126">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

```vb
internalHashtable = New Hashtable(New
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))
```

```csharp
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider
    (CultureInfo.InvariantCulture),
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));
```

<a name="cpconperformingculture-insensitivestringoperationsincollectionsanchor1"></a>

## <a name="using-the-sortedlist-class"></a><span data-ttu-id="1d258-127">Korzystanie z klasy SortedList</span><span class="sxs-lookup"><span data-stu-id="1d258-127">Using the SortedList Class</span></span>

<span data-ttu-id="1d258-128">`SortedList`Reprezentuje kolekcję par klucz-wartość, które są sortowane według kluczy i są dostępne dla klucza i według indeksu.</span><span class="sxs-lookup"><span data-stu-id="1d258-128">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="1d258-129">W przypadku korzystania z `SortedList` ciągów gdzie są klucze, właściwość może mieć wpływ na sortowanie i wyszukiwanie `Thread.CurrentCulture` .</span><span class="sxs-lookup"><span data-stu-id="1d258-129">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="1d258-130">Aby uzyskać zachowanie niewrażliwe na kulturę z `SortedList` , należy utworzyć `SortedList` przy użyciu jeden z konstruktorów akceptujących `comparer` parametr.</span><span class="sxs-lookup"><span data-stu-id="1d258-130">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="1d258-131">`comparer`Parametr określa <xref:System.Collections.IComparer> implementację do użycia podczas porównywania kluczy.</span><span class="sxs-lookup"><span data-stu-id="1d258-131">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="1d258-132">Dla parametru Określ niestandardową klasę porównującą używaną `CultureInfo.InvariantCulture` do porównywania kluczy.</span><span class="sxs-lookup"><span data-stu-id="1d258-132">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="1d258-133">Poniższy przykład ilustruje niestandardową klasę niezależną od kultury, którą można określić jako `comparer` parametr `SortedList` konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1d258-133">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>

```vb
Imports System.Collections
Imports System.Globalization

Friend Class InvariantComparer
    Implements IComparer
    Private m_compareInfo As CompareInfo
    Friend Shared [Default] As New InvariantComparer()

    Friend Sub New()
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo
    End Sub

    Public Function Compare(a As Object, b As Object) As Integer _
            Implements IComparer.Compare
        Dim sa As String = CType(a, String)
        Dim sb As String = CType(b, String)
        If Not (sa Is Nothing) And Not (sb Is Nothing) Then
            Return m_compareInfo.Compare(sa, sb)
        Else
            Return Comparer.Default.Compare(a, b)
        End If
    End Function
End Class
```

```csharp
using System;
using System.Collections;
using System.Globalization;

internal class InvariantComparer : IComparer
{
    private CompareInfo m_compareInfo;
    internal static readonly InvariantComparer Default = new
        InvariantComparer();

    internal InvariantComparer()
    {
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo;
    }

    public int Compare(Object a, Object b)
    {
        String sa = a as String;
        String sb = b as String;
        if (sa != null && sb != null)
            return m_compareInfo.Compare(sa, sb);
        else
            return Comparer.Default.Compare(a,b);
    }
}
```

<span data-ttu-id="1d258-134">Ogólnie rzecz biorąc, jeśli używasz `SortedList` w ciągach bez określania niestandardowej niezmiennej modułu porównującego, zmiana po wypełnieniu `Thread.CurrentCulture` listy może unieważnić listę.</span><span class="sxs-lookup"><span data-stu-id="1d258-134">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>

## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="1d258-135">Korzystanie z metody ArrayList. Sort</span><span class="sxs-lookup"><span data-stu-id="1d258-135">Using the ArrayList.Sort Method</span></span>

<span data-ttu-id="1d258-136">Przeciążenia `ArrayList.Sort` metody domyślnie wykonują sortowanie zależne od kultury przy użyciu `Thread.CurrentCulture` właściwości.</span><span class="sxs-lookup"><span data-stu-id="1d258-136">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="1d258-137">Wyniki mogą się różnić w zależności od różnych kolejności sortowania.</span><span class="sxs-lookup"><span data-stu-id="1d258-137">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="1d258-138">Aby wyeliminować zachowanie wrażliwe na kulturę, Użyj przeciążenia tej metody, która akceptuje `IComparer` implementację.</span><span class="sxs-lookup"><span data-stu-id="1d258-138">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="1d258-139">Dla `comparer` parametru należy określić niestandardową klasę niezmiennej porównującej, która używa `CultureInfo.InvariantCulture` .</span><span class="sxs-lookup"><span data-stu-id="1d258-139">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="1d258-140">Przykład niestandardowej klasy niezmiennej porównującej znajduje się w temacie [using klasy SortedList](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) .</span><span class="sxs-lookup"><span data-stu-id="1d258-140">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d258-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d258-141">See also</span></span>

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [<span data-ttu-id="1d258-142">Wykonywanie niezależnych od kultury operacji na ciągach</span><span class="sxs-lookup"><span data-stu-id="1d258-142">Performing Culture-Insensitive String Operations</span></span>](performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
