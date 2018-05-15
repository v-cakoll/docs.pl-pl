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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c8972a8e9d73adc60e073a5eab9388260c907b68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="26709-102">Wykonywanie niezależnych od kultury operacji na ciągach w kolekcjach</span><span class="sxs-lookup"><span data-stu-id="26709-102">Performing Culture-Insensitive String Operations in Collections</span></span>
<span data-ttu-id="26709-103">Brak klas i członków w <xref:System.Collections> przestrzeni nazw, która zapewniają zależne od kultury zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="26709-103">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="26709-104">Konstruktory domyślne <xref:System.Collections.CaseInsensitiveComparer> i <xref:System.Collections.CaseInsensitiveHashCodeProvider> klasy zainicjować nowego wystąpienia przy użyciu <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="26709-104">The default constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="26709-105">Skompilowanie wszystkich przeciążeń <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> metody Utwórz nowe wystąpienie klasy <xref:System.Collections.Hashtable> przy użyciu `Thread.CurrentCulture` właściwość domyślnie.</span><span class="sxs-lookup"><span data-stu-id="26709-105">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="26709-106">Overloads z <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> metody wykonanie zależne od kultury sortowania przy użyciu domyślnego `Thread.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="26709-106">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="26709-107">Sortowanie i wyszukiwanie w <xref:System.Collections.SortedList> mogą mieć wpływ `Thread.CurrentCulture` Jeśli ciągi są używane jako klucze.</span><span class="sxs-lookup"><span data-stu-id="26709-107">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="26709-108">Postępować zgodnie z zaleceniami użycia podane w tej sekcji można uzyskać niezależne od kultury wyniki z tych klas i metod w `Collections` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="26709-108">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>  
  
 <span data-ttu-id="26709-109">**Uwaga** przekazywanie <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> do porównania metody przeprowadzenia porównania niezależnych od kultury.</span><span class="sxs-lookup"><span data-stu-id="26709-109">**Note** Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="26709-110">Jednak go nie powoduje-językowe porównania, na przykład ścieżki do plików, kluczy rejestru i zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="26709-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="26709-111">Nie obsługuje zabezpieczeń decyzje na podstawie wyniku porównania.</span><span class="sxs-lookup"><span data-stu-id="26709-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="26709-112">Dla porównania językowe lub obsługę decyzje na podstawie wyniku zabezpieczeń, aplikacja powinna używać metody porównania, która akceptuje <xref:System.StringComparison> wartość.</span><span class="sxs-lookup"><span data-stu-id="26709-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="26709-113">Następnie należy przekazać aplikacji <xref:System.StringComparison>.</span><span class="sxs-lookup"><span data-stu-id="26709-113">The application should then pass <xref:System.StringComparison>.</span></span>  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="26709-114">Przy użyciu caseinsensitivecomparer — i caseinsensitivehashcodeprovider — klasy</span><span class="sxs-lookup"><span data-stu-id="26709-114">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>  
 <span data-ttu-id="26709-115">Konstruktory domyślne `CaseInsensitiveHashCodeProvider` i `CaseInsensitiveComparer` zainicjować nowe wystąpienie klasy przy użyciu `Thread.CurrentCulture`, co działanie zależne od kultury.</span><span class="sxs-lookup"><span data-stu-id="26709-115">The default constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="26709-116">Poniższy przykład kodu pokazuje Konstruktor `Hashtable` to zależne od kultury, ponieważ używa domyślnych konstruktorów dla `CaseInsensitiveHashCodeProvider` i `CaseInsensitiveComparer`.</span><span class="sxs-lookup"><span data-stu-id="26709-116">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the default constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 <span data-ttu-id="26709-117">Jeśli chcesz utworzyć niezależnych od kultury `Hashtable` przy użyciu `CaseInsensitiveComparer` i `CaseInsensitiveHashCodeProvider` klas, zainicjować nowego wystąpienia tych klas używanie konstruktorów, które akceptują `culture` parametru.</span><span class="sxs-lookup"><span data-stu-id="26709-117">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="26709-118">Aby uzyskać `culture` parametru, określ <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26709-118">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="26709-119">Poniższy przykład kodu pokazuje konstruktora dla kultury niewrażliwe `Hashtable`.</span><span class="sxs-lookup"><span data-stu-id="26709-119">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>  
  
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
  
## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="26709-120">Przy użyciu CollectionsUtil.CreateCaseInsensitiveHashTable — metoda</span><span class="sxs-lookup"><span data-stu-id="26709-120">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>  
 <span data-ttu-id="26709-121">`CollectionsUtil.CreateCaseInsensitiveHashTable` Metoda jest przydatna skrót do tworzenia nowego wystąpienia klasy `Hashtable` klasy, która ignoruje wielkość liter ciągów.</span><span class="sxs-lookup"><span data-stu-id="26709-121">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="26709-122">Jednak wszystkie overloads z `CollectionsUtil.CreateCaseInsensitiveHashTable` metody są zależne od kultury, ponieważ używają one `Thread.CurrentCulture` właściwości.</span><span class="sxs-lookup"><span data-stu-id="26709-122">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="26709-123">Nie można utworzyć niezależnych od kultury `Hashtable` za pomocą tej metody.</span><span class="sxs-lookup"><span data-stu-id="26709-123">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="26709-124">Aby utworzyć niezależnych od kultury `Hashtable`, użyj `Hashtable` konstruktora akceptującego `culture` parametru.</span><span class="sxs-lookup"><span data-stu-id="26709-124">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="26709-125">Aby uzyskać `culture` parametru, określ `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="26709-125">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="26709-126">Poniższy przykład kodu pokazuje konstruktora dla kultury niewrażliwe `Hashtable`.</span><span class="sxs-lookup"><span data-stu-id="26709-126">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>  
  
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
## <a name="using-the-sortedlist-class"></a><span data-ttu-id="26709-127">Przy użyciu SortedList — klasa</span><span class="sxs-lookup"><span data-stu-id="26709-127">Using the SortedList Class</span></span>  
 <span data-ttu-id="26709-128">A `SortedList` reprezentuje kolekcję par klucz wartość są sortowane według kluczy i są dostępne za pomocą klucza i indeksu.</span><span class="sxs-lookup"><span data-stu-id="26709-128">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="26709-129">Jeśli używasz `SortedList` Jeśli ciągi są klucze, sortowanie i wyszukiwanie mogą mieć wpływ `Thread.CurrentCulture` właściwości.</span><span class="sxs-lookup"><span data-stu-id="26709-129">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="26709-130">Aby uzyskać niezależne od kultury zachowanie z `SortedList`, Utwórz `SortedList` przy użyciu jednego z konstruktorów, które akceptuje `comparer` parametru.</span><span class="sxs-lookup"><span data-stu-id="26709-130">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="26709-131">`comparer` Określa parametr <xref:System.Collections.IComparer> implementacji do używania przy porównywaniu kluczy.</span><span class="sxs-lookup"><span data-stu-id="26709-131">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="26709-132">W przypadku parametru określić klasy niestandardowej funkcji porównującej, która używa `CultureInfo.InvariantCulture` do porównania kluczy.</span><span class="sxs-lookup"><span data-stu-id="26709-132">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="26709-133">Poniższy przykład przedstawia klasę Niestandardowa funkcja porównująca niezależnych od kultury, która może służyć jako `comparer` parametr `SortedList` konstruktora.</span><span class="sxs-lookup"><span data-stu-id="26709-133">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>  
  
```vb  
Imports System  
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
  
 <span data-ttu-id="26709-134">Ogólnie, jeśli używasz `SortedList` na ciągi bez określania niestandardowych porównania niezmiennej zmianę `Thread.CurrentCulture` po wypełnione listy może unieważnić listy.</span><span class="sxs-lookup"><span data-stu-id="26709-134">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>  
  
## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="26709-135">Przy użyciu ArrayList.Sort — metoda</span><span class="sxs-lookup"><span data-stu-id="26709-135">Using the ArrayList.Sort Method</span></span>  
 <span data-ttu-id="26709-136">Overloads z `ArrayList.Sort` metody wykonanie zależne od kultury sortowania przy użyciu domyślnego `Thread.CurrentCulture` właściwości.</span><span class="sxs-lookup"><span data-stu-id="26709-136">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="26709-137">Wyniki można różnią się zależnie od kultury z powodu innego sortowania.</span><span class="sxs-lookup"><span data-stu-id="26709-137">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="26709-138">Aby wyeliminować zachowanie zależne od kultury, użyj przeciążenie tej metody, które akceptują `IComparer` implementacji.</span><span class="sxs-lookup"><span data-stu-id="26709-138">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="26709-139">Dla `comparer` parametru, określ klasy niestandardowej funkcji porównującej niezmienna, która używa `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="26709-139">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="26709-140">Przykład klasy niestandardowej funkcji porównującej niezmiennej znajduje się w [za pomocą klasy SortedList](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) tematu.</span><span class="sxs-lookup"><span data-stu-id="26709-140">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26709-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26709-141">See Also</span></span>  
 <xref:System.Collections.CaseInsensitiveComparer>  
 <xref:System.Collections.CaseInsensitiveHashCodeProvider>  
 <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Collections.SortedList>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Collections.IComparer>  
 [<span data-ttu-id="26709-142">Wykonywanie niezależnych od kultury operacji na ciągach</span><span class="sxs-lookup"><span data-stu-id="26709-142">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
 <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
