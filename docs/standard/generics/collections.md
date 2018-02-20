---
title: "Kolekcje ogólne w .NET"
ms.custom: 
ms.date: 02/15/2018
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET], collections
- generic collections [.NET]
- generic types [.NET]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 827d5a7edd335769ec5497518cbdf71181aacc2c
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2018
---
# <a name="generic-collections-in-net"></a><span data-ttu-id="5c2b8-102">Kolekcje ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="5c2b8-102">Generic Collections in .NET</span></span>

 <span data-ttu-id="5c2b8-103">Biblioteka klas programu .NET oferuje następujące klasy rodzajowej kolekcji w <xref:System.Collections.Generic> i <xref:System.Collections.ObjectModel> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-103">The .NET class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="5c2b8-104">Aby uzyskać szczegółowe informacje o tych klas, zobacz [często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md).</span><span class="sxs-lookup"><span data-stu-id="5c2b8-104">For more detailed information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
### <a name="systemcollectionsgeneric"></a><span data-ttu-id="5c2b8-105">System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="5c2b8-105">System.Collections.Generic</span></span>  
 <span data-ttu-id="5c2b8-106">Wiele typy kolekcji ogólnych jest bezpośrednie analogs nierodzajowe typów.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-106">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="5c2b8-107"><xref:System.Collections.Generic.Dictionary%602> jest ogólny wersja <xref:System.Collections.Hashtable>; używa Struktura ogólna <xref:System.Collections.Generic.KeyValuePair%602> wyliczenia zamiast <xref:System.Collections.DictionaryEntry>.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-107"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="5c2b8-108"><xref:System.Collections.Generic.List%601> jest ogólny wersja <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-108"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="5c2b8-109">Brak ogólnego <xref:System.Collections.Generic.Queue%601> i <xref:System.Collections.Generic.Stack%601> klasy, które odpowiadają nierodzajowe wersji.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-109">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="5c2b8-110">Dostępne są wersje rodzajowa i nierodzajowe <xref:System.Collections.Generic.SortedList%602>.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-110">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="5c2b8-111">Obie wersje są hybryd słownika i listy.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-111">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="5c2b8-112"><xref:System.Collections.Generic.SortedDictionary%602> Klasy generycznej jest słownikiem czysty i nie ma odpowiednika nierodzajowe.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-112">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="5c2b8-113"><xref:System.Collections.Generic.LinkedList%601> Klasy generycznej jest true listy połączonej.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-113">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="5c2b8-114">Go nie ma odpowiednika nierodzajowe.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-114">It has no nongeneric counterpart.</span></span>  
  
### <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="5c2b8-115">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="5c2b8-115">System.Collections.ObjectModel</span></span>  
 <span data-ttu-id="5c2b8-116"><xref:System.Collections.ObjectModel.Collection%601> Klasy ogólnej udostępnia klasę podstawową dla wyprowadzanie własne typy kolekcji ogólnych.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-116">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="5c2b8-117"><xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Klasa udostępnia w prosty sposób utworzyć kolekcji tylko do odczytu z dowolnego typu, który implementuje <xref:System.Collections.Generic.IList%601> interfejs generyczny.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-117">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="5c2b8-118"><xref:System.Collections.ObjectModel.KeyedCollection%602> Klasa ogólna stanowi sposób przechowywania obiektów, które zawierają własne klucze.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-118">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="5c2b8-119">Inne typy ogólne</span><span class="sxs-lookup"><span data-stu-id="5c2b8-119">Other Generic Types</span></span>  
 <span data-ttu-id="5c2b8-120"><xref:System.Nullable%601> Struktura ogólna umożliwia użycie typów wartości, tak jakby może zostać przypisana `null`.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-120">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="5c2b8-121">Może to być przydatne podczas pracy z zapytań bazy danych, gdzie mogą być brakujące pola, które zawierają typy wartości.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-121">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="5c2b8-122">Parametr typu ogólnego może być dowolnego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-122">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c2b8-123">W języku C# i Visual Basic, nie jest konieczne użycie <xref:System.Nullable%601> jawnie, ponieważ język ma składnię dla typów dopuszczających wartości zerowe.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-123">In C# and Visual Basic, it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span> <span data-ttu-id="5c2b8-124">Zobacz [typy dopuszczające wartości zerowe (C# przewodnik programowania w języku)](../../csharp/programming-guide/nullable-types/index.md) i [typy o wartości Zerowalnej (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="5c2b8-124">See [Nullable types (C# Programming Guide)](../../csharp/programming-guide/nullable-types/index.md) and [Nullable value types (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span></span> 
  
 <span data-ttu-id="5c2b8-125"><xref:System.ArraySegment%601> Struktura ogólna zapewnia sposób ograniczyć zakres elementów w tablicy jednowymiarowej tablicy, liczony od zera dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-125">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="5c2b8-126">Parametr typu ogólnego jest typ elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-126">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="5c2b8-127"><xref:System.EventHandler%601> Delegat ogólny eliminuje potrzebę zadeklarować typ obiektu delegowanego obsługi zdarzeń, jeśli zdarzenie jest zgodny ze wzorcem obsługi zdarzeń, używany przez [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c2b8-127">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="5c2b8-128">Na przykład, załóżmy, że utworzono `MyEventArgs` klasę pochodną <xref:System.EventArgs>, do przechowywania danych wydarzenia.</span><span class="sxs-lookup"><span data-stu-id="5c2b8-128">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="5c2b8-129">Następnie można zadeklarować zdarzenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5c2b8-129">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="5c2b8-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c2b8-130">See Also</span></span>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [<span data-ttu-id="5c2b8-131">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="5c2b8-131">Generics</span></span>](../../../docs/standard/generics/index.md)  
 [<span data-ttu-id="5c2b8-132">Delegaci ogólni do manipulowania tablicami i listami</span><span class="sxs-lookup"><span data-stu-id="5c2b8-132">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [<span data-ttu-id="5c2b8-133">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="5c2b8-133">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
