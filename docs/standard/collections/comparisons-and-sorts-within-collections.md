---
title: Porównywanie i sortowanie w kolekcjach
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET Framework], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48838a90939899fc1e7e91cdb7bbe98019591416
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210302"
---
# <a name="comparisons-and-sorts-within-collections"></a><span data-ttu-id="f890a-102">Porównywanie i sortowanie w kolekcjach</span><span class="sxs-lookup"><span data-stu-id="f890a-102">Comparisons and Sorts Within Collections</span></span>
<span data-ttu-id="f890a-103"><xref:System.Collections> Klasy wykonania porównania w prawie wszystkich procesów zarządzania kolekcjami, czy wyszukiwanie elementu do usunięcia lub zwracania wartości parę klucza i wartości.</span><span class="sxs-lookup"><span data-stu-id="f890a-103">The <xref:System.Collections> classes perform comparisons in almost all the processes involved in managing collections, whether searching for the element to remove or returning the value of a key-and-value pair.</span></span>  
  
 <span data-ttu-id="f890a-104">Kolekcje wykorzystywać zazwyczaj moduł porównujący równość i/lub szeregowania porównania.</span><span class="sxs-lookup"><span data-stu-id="f890a-104">Collections typically utilize an equality comparer and/or an ordering comparer.</span></span> <span data-ttu-id="f890a-105">Konstrukcje dwa są używane do porównania.</span><span class="sxs-lookup"><span data-stu-id="f890a-105">Two constructs are used for comparisons.</span></span>  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a><span data-ttu-id="f890a-106">Sprawdzanie pod kątem równości</span><span class="sxs-lookup"><span data-stu-id="f890a-106">Checking for equality</span></span>  
 <span data-ttu-id="f890a-107">Metody takie jak `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, i `Remove` moduł porównujący równość na użytek elementów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f890a-107">Methods such as `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, and `Remove` use an equality comparer for the collection elements.</span></span> <span data-ttu-id="f890a-108">Jeśli kolekcja jest ogólna, niż elementy są porównywane pod kątem równości, zgodnie z następującymi wytycznymi:</span><span class="sxs-lookup"><span data-stu-id="f890a-108">If the collection is generic, than items are compared for equality according to the following guidelines:</span></span>  
  
-   <span data-ttu-id="f890a-109">Jeśli typ T implementuje <xref:System.IEquatable%601> ogólny interfejs, a następnie moduł porównujący równość jest <xref:System.IEquatable%601.Equals%2A> metody tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f890a-109">If type T implements the <xref:System.IEquatable%601> generic interface, then the equality comparer is the <xref:System.IEquatable%601.Equals%2A> method of that interface.</span></span>  
  
-   <span data-ttu-id="f890a-110">Jeśli typ T nie implementuje <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> jest używany.</span><span class="sxs-lookup"><span data-stu-id="f890a-110">If type T does not implement <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> is used.</span></span>  
  
 <span data-ttu-id="f890a-111">Ponadto niektóre przeciążenia konstruktora dla kolekcji słownika, Zaakceptuj <xref:System.Collections.Generic.IEqualityComparer%601> wdrażania, który służy do porównywania kluczy pod kątem równości.</span><span class="sxs-lookup"><span data-stu-id="f890a-111">In addition, Some constructor overloads for dictionary collections accept an <xref:System.Collections.Generic.IEqualityComparer%601> implementation, which is used to compare keys for equality.</span></span> <span data-ttu-id="f890a-112">Aby uzyskać przykład, zobacz <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f890a-112">For an example, see the <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> constructor.</span></span>  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a><span data-ttu-id="f890a-113">Określanie kolejności sortowania</span><span class="sxs-lookup"><span data-stu-id="f890a-113">Determining sort order</span></span>  
 <span data-ttu-id="f890a-114">Metody takie jak `BinarySearch` i `Sort` szeregowania modułu porównującego na użytek elementów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f890a-114">Methods such as `BinarySearch` and `Sort` use an ordering comparer for the collection elements.</span></span> <span data-ttu-id="f890a-115">Porównania mogą być, między elementy kolekcji lub między elementem i określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="f890a-115">The comparisons can be between elements of the collection, or between an element and a specified value.</span></span> <span data-ttu-id="f890a-116">Porównywanie obiektów, jest koncepcji `default comparer` i `explicit comparer`.</span><span class="sxs-lookup"><span data-stu-id="f890a-116">For comparing objects, there is the concept of a `default comparer` and an `explicit comparer`.</span></span>  
  
 <span data-ttu-id="f890a-117">Domyślny moduł porównujący opiera się na co najmniej jeden z obiektów, którą jest porównywany do zaimplementowania **IComparable** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f890a-117">The default comparer relies on at least one of the objects being compared to implement the **IComparable** interface.</span></span> <span data-ttu-id="f890a-118">Jest dobrą praktyką, aby zaimplementować **IComparable** na wszystkie klasy są używane jako wartości w kolekcji listy lub kluczy w słowniku kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f890a-118">It is a good practice to implement **IComparable** on all classes are used as values in a list collection or as keys in a dictionary collection.</span></span> <span data-ttu-id="f890a-119">Dla ogólnej kolekcji porównania jest określana zgodnie z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="f890a-119">For a generic collection, equality comparison is determined according to the following:</span></span>  
  
-   <span data-ttu-id="f890a-120">Jeśli implementacja typu T <xref:System.IComparable%601?displayProperty=nameWithType> jest ogólny interfejs, a następnie domyślny moduł porównujący <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> metody interfejsu</span><span class="sxs-lookup"><span data-stu-id="f890a-120">If type T implements the <xref:System.IComparable%601?displayProperty=nameWithType> generic interface, then the default comparer is the <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> method of that interface</span></span>  
  
-   <span data-ttu-id="f890a-121">Jeśli typ T implementuje niepodstawowy <xref:System.IComparable?displayProperty=nameWithType> interfejsu, a następnie jest domyślna funkcja porównująca <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> metody tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f890a-121">If type T implements the non-generic <xref:System.IComparable?displayProperty=nameWithType> interface, then the default comparer is the <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> method of that interface.</span></span>  
  
-   <span data-ttu-id="f890a-122">Jeśli typ T nie implementuje interfejsu albo, to nie ma żadnych domyślny moduł porównujący i musi być jawnie podana delegat modułu porównującego lub porównywania.</span><span class="sxs-lookup"><span data-stu-id="f890a-122">If type T doesn’t implement either interface, then there is no default comparer, and a comparer or comparison delegate must be provided explicitly.</span></span>  
  
 <span data-ttu-id="f890a-123">Aby podać jawne porównanie, niektóre metody akceptują **IComparer** implementacji jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f890a-123">To provide explicit comparisons, some methods accept an **IComparer** implementation as a parameter.</span></span> <span data-ttu-id="f890a-124">Na przykład <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metoda przyjmuje <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementacji.</span><span class="sxs-lookup"><span data-stu-id="f890a-124">For example, the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> method accepts an <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation.</span></span>  
  
 <span data-ttu-id="f890a-125">Bieżące ustawienia kulturowe systemu może wpłynąć na, porównywanie i sortowanie w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f890a-125">The current culture setting of the system can affect the comparisons and sorts within a collection.</span></span> <span data-ttu-id="f890a-126">Domyślnie, porównywania i sortowania w **kolekcje** klasy są zależne od kultury.</span><span class="sxs-lookup"><span data-stu-id="f890a-126">By default, the comparisons and sorts in the **Collections** classes are culture-sensitive.</span></span> <span data-ttu-id="f890a-127">Aby ignorować ustawienie kultury i dlatego uzyskanie spójnego porównywanie i sortowanie wyników, użyj <xref:System.Globalization.CultureInfo.InvariantCulture%2A> za pomocą przeciążenia składowych, które akceptują <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="f890a-127">To ignore the culture setting and therefore obtain consistent comparison and sorting results, use the <xref:System.Globalization.CultureInfo.InvariantCulture%2A> with member overloads that accept a <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="f890a-128">Aby uzyskać więcej informacji, zobacz [wykonywanie niezależnych od kultury operacje na ciągach w kolekcjach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) i [wykonywanie niezależnych od kultury operacje na ciągach w tablicach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="f890a-128">For more information, see [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) and [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span></span>  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a><span data-ttu-id="f890a-129">Przykład równości i sortowania</span><span class="sxs-lookup"><span data-stu-id="f890a-129">Equality and sort example</span></span>  
 <span data-ttu-id="f890a-130">Poniższy kod przedstawia implementację <xref:System.IEquatable%601> i <xref:System.IComparable%601> obiektu proste biznesowych.</span><span class="sxs-lookup"><span data-stu-id="f890a-130">The following code demonstrates an implementation of <xref:System.IEquatable%601> and <xref:System.IComparable%601> on a simple business object.</span></span> <span data-ttu-id="f890a-131">Ponadto, gdy obiekt jest przechowywana na liście i sortowane, zobaczysz że wywołanie <xref:System.Collections.Generic.List%601.Sort> metody powoduje użycie domyślny moduł porównujący dla `Part` typu i <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> metody implementowane za pomocą metody anonimowej.</span><span class="sxs-lookup"><span data-stu-id="f890a-131">In addition, when the object is stored in a list and sorted, you will see that calling the <xref:System.Collections.Generic.List%601.Sort> method results in the use of the default comparer for the `Part` type, and the <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> method implemented by using an anonymous method.</span></span>  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f890a-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f890a-132">See also</span></span>

- <xref:System.Collections.IComparer>  
- <xref:System.IEquatable%601>  
- <xref:System.Collections.Generic.IComparer%601>  
- <xref:System.IComparable>  
- <xref:System.IComparable%601>
