---
title: Interfejsy ogólne — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: fb2c570b251979adb76ad2af1a3b6f54b75a15ff
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589716"
---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="ef733-102">Interfejsy ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="ef733-102">Generic Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="ef733-103">Często warto zdefiniować interfejsy dla klas kolekcji generycznej lub dla klas ogólnych, które reprezentują elementy w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ef733-103">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="ef733-104">Preferencją dla klas ogólnych jest użycie interfejsów ogólnych, takich jak <xref:System.IComparable%601> <xref:System.IComparable>zamiast, aby uniknąć pakowania i rozpakowywania operacji na typach wartości.</span><span class="sxs-lookup"><span data-stu-id="ef733-104">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="ef733-105">Biblioteka klas .NET Framework definiuje kilka ogólnych interfejsów do użycia z klasami kolekcji w <xref:System.Collections.Generic> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ef733-105">The .NET Framework class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="ef733-106">Gdy interfejs jest określony jako ograniczenie dla parametru typu, można użyć tylko typów, które implementują interfejs.</span><span class="sxs-lookup"><span data-stu-id="ef733-106">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="ef733-107">Poniższy przykład kodu pokazuje `SortedList<T>` klasę, która dziedziczy `GenericList<T>` z klasy.</span><span class="sxs-lookup"><span data-stu-id="ef733-107">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="ef733-108">Aby uzyskać więcej informacji, zobacz [wprowadzenie do typów ogólnych](./index.md).</span><span class="sxs-lookup"><span data-stu-id="ef733-108">For more information, see [Introduction to Generics](./index.md).</span></span> <span data-ttu-id="ef733-109">`SortedList<T>`dodaje ograniczenie `where T : IComparable<T>`.</span><span class="sxs-lookup"><span data-stu-id="ef733-109">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="ef733-110">Dzięki `BubbleSort` temu Metoda w programie `SortedList<T>` może używać metody ogólnej <xref:System.IComparable%601.CompareTo%2A> dla elementów listy.</span><span class="sxs-lookup"><span data-stu-id="ef733-110">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="ef733-111">W tym przykładzie elementy list są prostą klasą `Person`, która implementuje. `IComparable<Person>`</span><span class="sxs-lookup"><span data-stu-id="ef733-111">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 <span data-ttu-id="ef733-112">Można określić wiele interfejsów jako ograniczenia dotyczące pojedynczego typu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ef733-112">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 <span data-ttu-id="ef733-113">Interfejs może definiować więcej niż jeden parametr typu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ef733-113">An interface can define more than one type parameter, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 <span data-ttu-id="ef733-114">Reguły dziedziczenia stosowane do klas dotyczą również interfejsów:</span><span class="sxs-lookup"><span data-stu-id="ef733-114">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 <span data-ttu-id="ef733-115">Interfejsy generyczne mogą dziedziczyć z interfejsów innych niż ogólne, jeśli interfejs generyczny jest kontrawariantne, co oznacza, że używa jego parametru typu jako wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="ef733-115">Generic interfaces can inherit from non-generic interfaces if the generic interface is contravariant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="ef733-116">W bibliotece klas .NET Framework dziedziczy z <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerable> , ponieważ <xref:System.Collections.Generic.IEnumerable%601> używa `T` tylko w wartości <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> zwracanej i w <xref:System.Collections.Generic.IEnumerator%601.Current%2A> metodzie pobierającej właściwości.</span><span class="sxs-lookup"><span data-stu-id="ef733-116">In the .NET Framework class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="ef733-117">Konkretne klasy mogą zaimplementować zamknięte interfejsy skonstruowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ef733-117">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 <span data-ttu-id="ef733-118">Klasy generyczne mogą implementować interfejsy ogólne lub zamknięte skonstruowane interfejsy, o ile lista parametrów klasy dostarcza wszystkie argumenty wymagane przez interfejs, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ef733-118">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 <span data-ttu-id="ef733-119">Reguły przeciążania metody kontrolującej są takie same dla metod w klasach ogólnych, strukturach ogólnych lub w interfejsach ogólnych.</span><span class="sxs-lookup"><span data-stu-id="ef733-119">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="ef733-120">Aby uzyskać więcej informacji, zobacz [metody ogólne](./generic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="ef733-120">For more information, see [Generic Methods](./generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef733-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef733-121">See also</span></span>

- [<span data-ttu-id="ef733-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ef733-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ef733-123">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="ef733-123">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="ef733-124">interface</span><span class="sxs-lookup"><span data-stu-id="ef733-124">interface</span></span>](../../language-reference/keywords/interface.md)
- [<span data-ttu-id="ef733-125">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="ef733-125">Generics</span></span>](~/docs/standard/generics/index.md)
