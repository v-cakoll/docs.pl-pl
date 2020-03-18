---
title: Kolekcje ogólne w .NET
ms.date: 02/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET], collections
- generic collections [.NET]
- generic types [.NET]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
ms.openlocfilehash: dce0e38b0198396ec0dbc3ced7f2f59c2b112b56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708413"
---
# <a name="generic-collections-in-net"></a><span data-ttu-id="65af1-102">Kolekcje rodzajowe w .NET</span><span class="sxs-lookup"><span data-stu-id="65af1-102">Generic collections in .NET</span></span>

 <span data-ttu-id="65af1-103">Biblioteka klas .NET zawiera wiele klas kolekcji <xref:System.Collections.Generic> <xref:System.Collections.ObjectModel> ogólnej w przestrzeniach nazw i.</span><span class="sxs-lookup"><span data-stu-id="65af1-103">The .NET class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="65af1-104">Aby uzyskać bardziej szczegółowe informacje na temat tych klas, zobacz [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md).</span><span class="sxs-lookup"><span data-stu-id="65af1-104">For more detailed information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
## <a name="systemcollectionsgeneric"></a><span data-ttu-id="65af1-105">System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="65af1-105">System.Collections.Generic</span></span>

 <span data-ttu-id="65af1-106">Wiele typów kolekcji rodzajowych są bezpośrednie analogi typów nierodzajowych.</span><span class="sxs-lookup"><span data-stu-id="65af1-106">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="65af1-107"><xref:System.Collections.Generic.Dictionary%602>jest ogólną <xref:System.Collections.Hashtable>wersją ; używa ogólnej <xref:System.Collections.Generic.KeyValuePair%602> struktury do wyliczenia zamiast <xref:System.Collections.DictionaryEntry>.</span><span class="sxs-lookup"><span data-stu-id="65af1-107"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="65af1-108"><xref:System.Collections.Generic.List%601>jest ogólną <xref:System.Collections.ArrayList>wersją pliku .</span><span class="sxs-lookup"><span data-stu-id="65af1-108"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="65af1-109">Istnieją ogólne <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Generic.Stack%601> i klas, które odpowiadają wersje nierodzajowe.</span><span class="sxs-lookup"><span data-stu-id="65af1-109">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="65af1-110">Istnieją ogólne i nieogólne <xref:System.Collections.Generic.SortedList%602>wersje .</span><span class="sxs-lookup"><span data-stu-id="65af1-110">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="65af1-111">Obie wersje są hybrydami słownika i listy.</span><span class="sxs-lookup"><span data-stu-id="65af1-111">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="65af1-112">Klasa <xref:System.Collections.Generic.SortedDictionary%602> rodzajowa jest czystym słownikiem i nie ma odpowiednika nierodzajowego.</span><span class="sxs-lookup"><span data-stu-id="65af1-112">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="65af1-113">Klasa <xref:System.Collections.Generic.LinkedList%601> ogólna jest prawdziwą listą połączoną.</span><span class="sxs-lookup"><span data-stu-id="65af1-113">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="65af1-114">Nie ma nierodzajowego odpowiednika.</span><span class="sxs-lookup"><span data-stu-id="65af1-114">It has no nongeneric counterpart.</span></span>  
  
## <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="65af1-115">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="65af1-115">System.Collections.ObjectModel</span></span>

 <span data-ttu-id="65af1-116">Klasa <xref:System.Collections.ObjectModel.Collection%601> ogólna zapewnia klasę podstawową do wyprowadzania własnych typów kolekcji rodzajowych.</span><span class="sxs-lookup"><span data-stu-id="65af1-116">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="65af1-117">Klasa <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> zapewnia łatwy sposób tworzenia kolekcji tylko do odczytu z <xref:System.Collections.Generic.IList%601> dowolnego typu, który implementuje ogólny interfejs.</span><span class="sxs-lookup"><span data-stu-id="65af1-117">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="65af1-118">Klasa <xref:System.Collections.ObjectModel.KeyedCollection%602> ogólna umożliwia przechowywanie obiektów, które zawierają własne klucze.</span><span class="sxs-lookup"><span data-stu-id="65af1-118">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="65af1-119">Inne typy rodzajowe</span><span class="sxs-lookup"><span data-stu-id="65af1-119">Other generic types</span></span>

 <span data-ttu-id="65af1-120">Struktura <xref:System.Nullable%601> ogólna umożliwia używanie typów wartości tak, `null`jakby można było je przypisać.</span><span class="sxs-lookup"><span data-stu-id="65af1-120">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="65af1-121">Może to być przydatne podczas pracy z kwerendami bazy danych, gdzie może brakować pól zawierających typy wartości.</span><span class="sxs-lookup"><span data-stu-id="65af1-121">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="65af1-122">Parametr typu ogólnego może być dowolnym typem wartości.</span><span class="sxs-lookup"><span data-stu-id="65af1-122">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65af1-123">W języku C# i Visual Basic <xref:System.Nullable%601> nie jest konieczne jawne użycie, ponieważ język ma składnię typów nullable.</span><span class="sxs-lookup"><span data-stu-id="65af1-123">In C# and Visual Basic, it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span> <span data-ttu-id="65af1-124">Zobacz [typy wartości null (odwołanie do języka C#)](../../csharp/language-reference/builtin-types/nullable-value-types.md) i wartości null [(Visual Basic).](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="65af1-124">See [Nullable value types (C# reference)](../../csharp/language-reference/builtin-types/nullable-value-types.md) and [Nullable value types (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span></span>
  
 <span data-ttu-id="65af1-125">Struktura <xref:System.ArraySegment%601> ogólna umożliwia rozgraniczenie zakresu elementów w jednowymiarowej tablicy opartej na zerowej dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="65af1-125">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="65af1-126">Parametr typu ogólnego jest typem elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="65af1-126">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="65af1-127">Ogólny <xref:System.EventHandler%601> delegat eliminuje konieczność deklarowania typu delegata do obsługi zdarzeń, jeśli zdarzenie następuje wzorca obsługi zdarzeń używane przez .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65af1-127">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the .NET Framework.</span></span> <span data-ttu-id="65af1-128">Załóżmy na przykład, `MyEventArgs` że utworzono klasę, z której pochodzą <xref:System.EventArgs>, do przechowywania danych dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="65af1-128">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="65af1-129">Następnie można zadeklarować zdarzenie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="65af1-129">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="65af1-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65af1-130">See also</span></span>

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [<span data-ttu-id="65af1-131">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="65af1-131">Generics</span></span>](../../../docs/standard/generics/index.md)
- [<span data-ttu-id="65af1-132">Delegaty ogólne do manipulowania tablicami i listami</span><span class="sxs-lookup"><span data-stu-id="65af1-132">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [<span data-ttu-id="65af1-133">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="65af1-133">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
