---
title: "Kolekcje ogólne w oprogramowaniu .NET Framework"
ms.custom: 
ms.date: 03/30/2017
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
- generics [.NET Framework], collections
- generic collections [.NET Framework]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d7e7d11446c14cffbef1e5cade5f082874187636
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="generic-collections-in-the-net-framework"></a><span data-ttu-id="810ba-102">Kolekcje ogólne w oprogramowaniu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="810ba-102">Generic Collections in the .NET Framework</span></span>
<span data-ttu-id="810ba-103">Ten temat zawiera przegląd klasy rodzajowej kolekcji i innych typów ogólnych w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="810ba-103">This topic provides an overview of the generic collection classes and other generic types in the .NET Framework.</span></span>  
  
## <a name="generic-collections-in-the-net-framework"></a><span data-ttu-id="810ba-104">Kolekcje ogólne w oprogramowaniu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="810ba-104">Generic Collections in the .NET Framework</span></span>  
 <span data-ttu-id="810ba-105">Biblioteka klas programu .NET Framework udostępnia wiele kolekcji ogólnej klasy w <xref:System.Collections.Generic> i <xref:System.Collections.ObjectModel> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="810ba-105">The .NET Framework class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="810ba-106">Aby uzyskać więcej informacji na temat tych klas, zobacz [często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md).</span><span class="sxs-lookup"><span data-stu-id="810ba-106">For more information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
### <a name="systemcollectionsgeneric"></a><span data-ttu-id="810ba-107">System.Collections.Generic —</span><span class="sxs-lookup"><span data-stu-id="810ba-107">System.Collections.Generic</span></span>  
 <span data-ttu-id="810ba-108">Wiele typy kolekcji ogólnych jest bezpośrednie analogs nierodzajowe typów.</span><span class="sxs-lookup"><span data-stu-id="810ba-108">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="810ba-109"><xref:System.Collections.Generic.Dictionary%602>jest ogólny wersja <xref:System.Collections.Hashtable>; używa Struktura ogólna <xref:System.Collections.Generic.KeyValuePair%602> wyliczenia zamiast <xref:System.Collections.DictionaryEntry>.</span><span class="sxs-lookup"><span data-stu-id="810ba-109"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="810ba-110"><xref:System.Collections.Generic.List%601>jest ogólny wersja <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="810ba-110"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="810ba-111">Brak ogólnego <xref:System.Collections.Generic.Queue%601> i <xref:System.Collections.Generic.Stack%601> klasy, które odpowiadają nierodzajowe wersji.</span><span class="sxs-lookup"><span data-stu-id="810ba-111">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="810ba-112">Dostępne są wersje rodzajowa i nierodzajowe <xref:System.Collections.Generic.SortedList%602>.</span><span class="sxs-lookup"><span data-stu-id="810ba-112">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="810ba-113">Obie wersje są hybryd słownika i listy.</span><span class="sxs-lookup"><span data-stu-id="810ba-113">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="810ba-114"><xref:System.Collections.Generic.SortedDictionary%602> Klasy generycznej jest słownikiem czysty i nie ma odpowiednika nierodzajowe.</span><span class="sxs-lookup"><span data-stu-id="810ba-114">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="810ba-115"><xref:System.Collections.Generic.LinkedList%601> Klasy generycznej jest true listy połączonej.</span><span class="sxs-lookup"><span data-stu-id="810ba-115">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="810ba-116">Go nie ma odpowiednika nierodzajowe.</span><span class="sxs-lookup"><span data-stu-id="810ba-116">It has no nongeneric counterpart.</span></span>  
  
### <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="810ba-117">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="810ba-117">System.Collections.ObjectModel</span></span>  
 <span data-ttu-id="810ba-118"><xref:System.Collections.ObjectModel.Collection%601> Klasy ogólnej udostępnia klasę podstawową dla wyprowadzanie własne typy kolekcji ogólnych.</span><span class="sxs-lookup"><span data-stu-id="810ba-118">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="810ba-119"><xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Klasa udostępnia w prosty sposób utworzyć kolekcji tylko do odczytu z dowolnego typu, który implementuje <xref:System.Collections.Generic.IList%601> interfejs generyczny.</span><span class="sxs-lookup"><span data-stu-id="810ba-119">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="810ba-120"><xref:System.Collections.ObjectModel.KeyedCollection%602> Klasa ogólna stanowi sposób przechowywania obiektów, które zawierają własne klucze.</span><span class="sxs-lookup"><span data-stu-id="810ba-120">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="810ba-121">Inne typy ogólne</span><span class="sxs-lookup"><span data-stu-id="810ba-121">Other Generic Types</span></span>  
 <span data-ttu-id="810ba-122"><xref:System.Nullable%601> Struktura ogólna umożliwia użycie typów wartości, tak jakby może zostać przypisana `null`.</span><span class="sxs-lookup"><span data-stu-id="810ba-122">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="810ba-123">Może to być przydatne podczas pracy z zapytań bazy danych, gdzie mogą być brakujące pola, które zawierają typy wartości.</span><span class="sxs-lookup"><span data-stu-id="810ba-123">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="810ba-124">Parametr typu ogólnego może być dowolnego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="810ba-124">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="810ba-125">W języku C# nie jest konieczne użycie <xref:System.Nullable%601> jawnie, ponieważ język ma składnię dla typów dopuszczających wartości zerowe.</span><span class="sxs-lookup"><span data-stu-id="810ba-125">In C# it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span>  
  
 <span data-ttu-id="810ba-126"><xref:System.ArraySegment%601> Struktura ogólna zapewnia sposób ograniczyć zakres elementów w tablicy jednowymiarowej tablicy, liczony od zera dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="810ba-126">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="810ba-127">Parametr typu ogólnego jest typ elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="810ba-127">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="810ba-128"><xref:System.EventHandler%601> Delegat ogólny eliminuje potrzebę zadeklarować typ obiektu delegowanego obsługi zdarzeń, jeśli zdarzenie jest zgodny ze wzorcem obsługi zdarzeń, używany przez [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="810ba-128">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="810ba-129">Na przykład, załóżmy, że utworzono `MyEventArgs` klasę pochodną <xref:System.EventArgs>, do przechowywania danych wydarzenia.</span><span class="sxs-lookup"><span data-stu-id="810ba-129">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="810ba-130">Następnie można zadeklarować zdarzenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="810ba-130">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="810ba-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="810ba-131">See Also</span></span>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [<span data-ttu-id="810ba-132">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="810ba-132">Generics</span></span>](../../../docs/standard/generics/index.md)  
 [<span data-ttu-id="810ba-133">Delegaci ogólni do manipulowania tablicami i listami</span><span class="sxs-lookup"><span data-stu-id="810ba-133">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [<span data-ttu-id="810ba-134">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="810ba-134">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
