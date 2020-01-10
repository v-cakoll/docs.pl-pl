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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708413"
---
# <a name="generic-collections-in-net"></a><span data-ttu-id="b1397-102">Kolekcje ogólne w programie .NET</span><span class="sxs-lookup"><span data-stu-id="b1397-102">Generic collections in .NET</span></span>

 <span data-ttu-id="b1397-103">Biblioteka klas .NET zawiera szereg klas ogólnych kolekcji w przestrzeni nazw <xref:System.Collections.Generic> i <xref:System.Collections.ObjectModel>.</span><span class="sxs-lookup"><span data-stu-id="b1397-103">The .NET class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="b1397-104">Aby uzyskać bardziej szczegółowe informacje o tych klasach, zobacz [powszechnie używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md).</span><span class="sxs-lookup"><span data-stu-id="b1397-104">For more detailed information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
## <a name="systemcollectionsgeneric"></a><span data-ttu-id="b1397-105">System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="b1397-105">System.Collections.Generic</span></span>

 <span data-ttu-id="b1397-106">Wiele typów kolekcji ogólnej to bezpośrednie analogowe typy nieogólne.</span><span class="sxs-lookup"><span data-stu-id="b1397-106">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="b1397-107"><xref:System.Collections.Generic.Dictionary%602> to ogólna wersja <xref:System.Collections.Hashtable>; używa struktury ogólnej <xref:System.Collections.Generic.KeyValuePair%602> do wyliczenia, a nie <xref:System.Collections.DictionaryEntry>.</span><span class="sxs-lookup"><span data-stu-id="b1397-107"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="b1397-108"><xref:System.Collections.Generic.List%601> to ogólna wersja <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="b1397-108"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="b1397-109">Istnieją ogólne klasy <xref:System.Collections.Generic.Queue%601> i <xref:System.Collections.Generic.Stack%601>, które odpowiadają nieogólnym wersjom.</span><span class="sxs-lookup"><span data-stu-id="b1397-109">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="b1397-110">Istnieją podstawowe i nieogólne wersje <xref:System.Collections.Generic.SortedList%602>.</span><span class="sxs-lookup"><span data-stu-id="b1397-110">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="b1397-111">Obie wersje są hybrydowymi słownikiem i listą.</span><span class="sxs-lookup"><span data-stu-id="b1397-111">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="b1397-112">Klasa generyczna <xref:System.Collections.Generic.SortedDictionary%602> jest czystym słownikiem i nie ma własnego odpowiednika.</span><span class="sxs-lookup"><span data-stu-id="b1397-112">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="b1397-113">Klasa ogólna <xref:System.Collections.Generic.LinkedList%601> jest połączoną listą.</span><span class="sxs-lookup"><span data-stu-id="b1397-113">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="b1397-114">Nie ma żadnego nieogólnego odpowiednika.</span><span class="sxs-lookup"><span data-stu-id="b1397-114">It has no nongeneric counterpart.</span></span>  
  
## <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="b1397-115">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="b1397-115">System.Collections.ObjectModel</span></span>

 <span data-ttu-id="b1397-116">Klasa generyczna <xref:System.Collections.ObjectModel.Collection%601> dostarcza klasę bazową do wyprowadzania własnych typów kolekcji rodzajowych.</span><span class="sxs-lookup"><span data-stu-id="b1397-116">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="b1397-117">Klasa <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> zapewnia łatwy sposób tworzenia kolekcji tylko do odczytu z dowolnego typu, który implementuje interfejs <xref:System.Collections.Generic.IList%601> generycznego.</span><span class="sxs-lookup"><span data-stu-id="b1397-117">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="b1397-118">Klasa generyczna <xref:System.Collections.ObjectModel.KeyedCollection%602> zapewnia sposób przechowywania obiektów, które zawierają własne klucze.</span><span class="sxs-lookup"><span data-stu-id="b1397-118">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="b1397-119">Inne typy ogólne</span><span class="sxs-lookup"><span data-stu-id="b1397-119">Other generic types</span></span>

 <span data-ttu-id="b1397-120">Struktura ogólna <xref:System.Nullable%601> pozwala używać typów wartości, tak jakby mogły być przypisane `null`.</span><span class="sxs-lookup"><span data-stu-id="b1397-120">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="b1397-121">Może to być przydatne podczas pracy z kwerendami bazy danych, gdzie nie można zawierać pól zawierających typy wartości.</span><span class="sxs-lookup"><span data-stu-id="b1397-121">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="b1397-122">Parametr typu generycznego może być dowolnym typem wartości.</span><span class="sxs-lookup"><span data-stu-id="b1397-122">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1397-123">W C# i Visual Basic nie trzeba używać <xref:System.Nullable%601> jawnie, ponieważ język ma składnię dla typów dopuszczających wartość null.</span><span class="sxs-lookup"><span data-stu-id="b1397-123">In C# and Visual Basic, it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span> <span data-ttu-id="b1397-124">Zobacz [typy wartości null (C# odwołanie)](../../csharp/language-reference/builtin-types/nullable-value-types.md) i [typy wartości null (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="b1397-124">See [Nullable value types (C# reference)](../../csharp/language-reference/builtin-types/nullable-value-types.md) and [Nullable value types (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span></span>
  
 <span data-ttu-id="b1397-125">Ogólna struktura <xref:System.ArraySegment%601> umożliwia rozgraniczenie zakresu elementów w jednowymiarowej tablicy dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="b1397-125">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="b1397-126">Parametr typu ogólnego to typ elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="b1397-126">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="b1397-127">Delegat ogólny <xref:System.EventHandler%601> eliminuje konieczność deklarowania typu delegata do obsługi zdarzeń, jeśli zdarzenie jest zgodne ze wzorcem obsługi zdarzeń używanym przez .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1397-127">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the .NET Framework.</span></span> <span data-ttu-id="b1397-128">Załóżmy na przykład, że utworzono klasę `MyEventArgs`, pochodną od <xref:System.EventArgs>, do przechowywania danych dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b1397-128">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="b1397-129">Następnie można zadeklarować zdarzenie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b1397-129">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="b1397-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1397-130">See also</span></span>

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [<span data-ttu-id="b1397-131">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="b1397-131">Generics</span></span>](../../../docs/standard/generics/index.md)
- [<span data-ttu-id="b1397-132">Delegaci ogólni do manipulowania tablicami i listami</span><span class="sxs-lookup"><span data-stu-id="b1397-132">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [<span data-ttu-id="b1397-133">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="b1397-133">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
