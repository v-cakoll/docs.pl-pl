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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cdead5a54c6e8dbe6fd61f82fc3985913bd7d381
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46473158"
---
# <a name="generic-collections-in-net"></a><span data-ttu-id="0954c-102">Kolekcje ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="0954c-102">Generic Collections in .NET</span></span>

 <span data-ttu-id="0954c-103">Biblioteka klas .NET oferuje pewną liczbę klasy kolekcji rodzajowej w <xref:System.Collections.Generic> i <xref:System.Collections.ObjectModel> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0954c-103">The .NET class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="0954c-104">Aby uzyskać szczegółowe informacje o tych klas, zobacz [powszechnie używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md).</span><span class="sxs-lookup"><span data-stu-id="0954c-104">For more detailed information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
### <a name="systemcollectionsgeneric"></a><span data-ttu-id="0954c-105">System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="0954c-105">System.Collections.Generic</span></span>  
 <span data-ttu-id="0954c-106">Wiele typy generyczne kolekcji jest bezpośrednie analogs nierodzajowymi typów.</span><span class="sxs-lookup"><span data-stu-id="0954c-106">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="0954c-107"><xref:System.Collections.Generic.Dictionary%602> jest ogólny wersją <xref:System.Collections.Hashtable>; używa ona ogólnych struktury <xref:System.Collections.Generic.KeyValuePair%602> wyliczenia zamiast <xref:System.Collections.DictionaryEntry>.</span><span class="sxs-lookup"><span data-stu-id="0954c-107"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="0954c-108"><xref:System.Collections.Generic.List%601> jest ogólny wersją <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="0954c-108"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="0954c-109">Występują ogólne <xref:System.Collections.Generic.Queue%601> i <xref:System.Collections.Generic.Stack%601> klasy, które odpowiadają nierodzajowymi wersji.</span><span class="sxs-lookup"><span data-stu-id="0954c-109">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="0954c-110">Istnieją wersje rodzajowymi i nierodzajowymi <xref:System.Collections.Generic.SortedList%602>.</span><span class="sxs-lookup"><span data-stu-id="0954c-110">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="0954c-111">Obie wersje są hybrydy słownik i listy.</span><span class="sxs-lookup"><span data-stu-id="0954c-111">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="0954c-112"><xref:System.Collections.Generic.SortedDictionary%602> Klasy generycznej jest słownikiem czysty i nie ma odpowiednika nierodzajowymi.</span><span class="sxs-lookup"><span data-stu-id="0954c-112">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="0954c-113"><xref:System.Collections.Generic.LinkedList%601> Klasy generycznej jest true połączonej listy.</span><span class="sxs-lookup"><span data-stu-id="0954c-113">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="0954c-114">Go nie ma odpowiednika nierodzajowymi.</span><span class="sxs-lookup"><span data-stu-id="0954c-114">It has no nongeneric counterpart.</span></span>  
  
### <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="0954c-115">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="0954c-115">System.Collections.ObjectModel</span></span>  
 <span data-ttu-id="0954c-116"><xref:System.Collections.ObjectModel.Collection%601> Klasy ogólnej udostępnia klasę bazową dla wyprowadzanie własne typy generyczne kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0954c-116">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="0954c-117"><xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Klasa udostępnia prosty sposób utworzyć kolekcję tylko do odczytu z dowolnego typu, który implementuje <xref:System.Collections.Generic.IList%601> interfejs generyczny.</span><span class="sxs-lookup"><span data-stu-id="0954c-117">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="0954c-118"><xref:System.Collections.ObjectModel.KeyedCollection%602> Ogólnej klasy zapewnia sposób przechowywania obiektów, które zawierają własne klucze.</span><span class="sxs-lookup"><span data-stu-id="0954c-118">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="0954c-119">Inne typy ogólne</span><span class="sxs-lookup"><span data-stu-id="0954c-119">Other Generic Types</span></span>  
 <span data-ttu-id="0954c-120"><xref:System.Nullable%601> Struktura ogólna pozwala na używanie typów wartości, tak, jakby można przypisać `null`.</span><span class="sxs-lookup"><span data-stu-id="0954c-120">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="0954c-121">Może to być przydatne podczas pracy z zapytań bazy danych, gdzie może być Brak pól, które zawierają typy wartości.</span><span class="sxs-lookup"><span data-stu-id="0954c-121">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="0954c-122">Parametr typu ogólnego może być dowolnego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="0954c-122">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0954c-123">W języku C# i Visual Basic nie jest konieczne użycie <xref:System.Nullable%601> jawnie, ponieważ język ma składnię dla typów dopuszczających wartości null.</span><span class="sxs-lookup"><span data-stu-id="0954c-123">In C# and Visual Basic, it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span> <span data-ttu-id="0954c-124">Zobacz [typów dopuszczających wartości zerowe (C# Programming Guide)](../../csharp/programming-guide/nullable-types/index.md) i [typy o wartości Zerowalnej (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="0954c-124">See [Nullable types (C# Programming Guide)](../../csharp/programming-guide/nullable-types/index.md) and [Nullable value types (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span></span> 
  
 <span data-ttu-id="0954c-125"><xref:System.ArraySegment%601> Struktura ogólna zapewnia sposób ograniczyć zakres elementów w tablicy jednowymiarowo, zaczynający się od zera w dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="0954c-125">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="0954c-126">Parametr typu ogólnego jest typ elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="0954c-126">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="0954c-127"><xref:System.EventHandler%601> Delegat ogólny eliminuje potrzebę deklarowania typu delegata obsługi zdarzeń, jeśli zdarzenie jest zgodny ze wzorcem obsługi zdarzeń, używane przez [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0954c-127">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="0954c-128">Załóżmy, że utworzono `MyEventArgs` klasy pochodzące z <xref:System.EventArgs>, do przechowywania danych dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0954c-128">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="0954c-129">Następnie można zadeklarować zdarzenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0954c-129">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="0954c-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0954c-130">See also</span></span>

- <xref:System.Collections.Generic?displayProperty=nameWithType>  
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
- [<span data-ttu-id="0954c-131">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="0954c-131">Generics</span></span>](../../../docs/standard/generics/index.md)  
- [<span data-ttu-id="0954c-132">Delegaci ogólni do manipulowania tablicami i listami</span><span class="sxs-lookup"><span data-stu-id="0954c-132">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
- [<span data-ttu-id="0954c-133">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="0954c-133">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
