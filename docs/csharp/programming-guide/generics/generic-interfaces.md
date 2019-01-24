---
title: Interfejsy ogólne — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: d0b9d35a7e814d8790ee57f1169f2b35f7c42536
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564214"
---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="252a9-102">Interfejsy ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="252a9-102">Generic Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="252a9-103">Często jest to przydatne do definiowania interfejsów dla klasy kolekcji rodzajowej lub dla klas ogólnych, które reprezentują elementy w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="252a9-103">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="252a9-104">Preferencje dla klas ogólnych jest używać interfejsów ogólnych, takich jak <xref:System.IComparable%601> zamiast <xref:System.IComparable>, aby unikać operacji pakowania, jak i rozpakowania dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="252a9-104">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="252a9-105">Biblioteka klas .NET Framework definiuje kilka interfejsów ogólnych do użytku z klas kolekcji przestrzeni <xref:System.Collections.Generic> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="252a9-105">The .NET Framework class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="252a9-106">Jeśli interfejs jest określony jako ograniczenia dla parametru typu, może służyć tylko typy, które implementują interfejs.</span><span class="sxs-lookup"><span data-stu-id="252a9-106">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="252a9-107">Poniższy kod przedstawia przykład `SortedList<T>` klasę pochodzącą od `GenericList<T>` klasy.</span><span class="sxs-lookup"><span data-stu-id="252a9-107">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="252a9-108">Aby uzyskać więcej informacji, zobacz [wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="252a9-108">For more information, see [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span></span> <span data-ttu-id="252a9-109">`SortedList<T>` dodaje ograniczenie `where T : IComparable<T>`.</span><span class="sxs-lookup"><span data-stu-id="252a9-109">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="252a9-110">Dzięki temu `BubbleSort` method in Class metoda `SortedList<T>` musieli używać ogólnych <xref:System.IComparable%601.CompareTo%2A> metody na liście elementów.</span><span class="sxs-lookup"><span data-stu-id="252a9-110">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="252a9-111">W tym przykładzie, elementy listy są klasą prostą `Person`, która implementuje `IComparable<Person>`.</span><span class="sxs-lookup"><span data-stu-id="252a9-111">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]  
  
 <span data-ttu-id="252a9-112">Wiele interfejsów można określić jako warunki ograniczające w jednego typu, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="252a9-112">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]  
  
 <span data-ttu-id="252a9-113">Interfejs można zdefiniować więcej niż jeden parametr typu, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="252a9-113">An interface can define more than one type parameter, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]  
  
 <span data-ttu-id="252a9-114">Reguły dziedziczenia, które są stosowane do klasy, która jest również zastosowanie do interfejsów:</span><span class="sxs-lookup"><span data-stu-id="252a9-114">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]  
  
 <span data-ttu-id="252a9-115">Interfejsy ogólne może dziedziczyć po elemencie nieogólnego interfejsów, jeśli ogólny interfejs jest kontrawariantny, co oznacza, że jej parametr typu jest stosowana tylko jako wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="252a9-115">Generic interfaces can inherit from non-generic interfaces if the generic interface is contravariant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="252a9-116">W bibliotece klas programu .NET Framework <xref:System.Collections.Generic.IEnumerable%601> dziedziczy <xref:System.Collections.IEnumerable> ponieważ <xref:System.Collections.Generic.IEnumerable%601> używa tylko `T` w zwracanej wartości <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> i <xref:System.Collections.Generic.IEnumerator%601.Current%2A> metoda pobierająca właściwości.</span><span class="sxs-lookup"><span data-stu-id="252a9-116">In the .NET Framework class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="252a9-117">Konkretnych klas można zaimplementować zamknięte interfejsów skonstruowany, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="252a9-117">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]  
  
 <span data-ttu-id="252a9-118">Klasy ogólne można zaimplementować interfejsów ogólnych lub zamkniętych skonstruowany interfejsów, tak długo, jak lista parametrów klasy dostarcza wszystkie argumenty wymagane przy użyciu interfejsu, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="252a9-118">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]  
  
 <span data-ttu-id="252a9-119">Reguły które kontrolują, przeciążenie metody są takie same dla metod w obrębie klasy ogólne, ogólny struktury lub interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="252a9-119">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="252a9-120">Aby uzyskać więcej informacji, zobacz [metod ogólnych](../../../csharp/programming-guide/generics/generic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="252a9-120">For more information, see [Generic Methods](../../../csharp/programming-guide/generics/generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="252a9-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="252a9-121">See also</span></span>

- [<span data-ttu-id="252a9-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="252a9-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="252a9-123">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="252a9-123">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)
- [<span data-ttu-id="252a9-124">interface</span><span class="sxs-lookup"><span data-stu-id="252a9-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)
- [<span data-ttu-id="252a9-125">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="252a9-125">Generics</span></span>](~/docs/standard/generics/index.md)
