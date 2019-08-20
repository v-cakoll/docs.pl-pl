---
title: Klasy ogólne — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 6eb4df4489f4b377c68c5d49d1bf0bb01b835e85
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589767"
---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="59103-102">Klasy ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="59103-102">Generic Classes (C# Programming Guide)</span></span>
<span data-ttu-id="59103-103">Klasy ogólne hermetyzują operacje, które nie są specyficzne dla określonego typu danych.</span><span class="sxs-lookup"><span data-stu-id="59103-103">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="59103-104">Najbardziej typowym zastosowaniem klas ogólnych jest kolekcje, takie jak listy połączone, tabele skrótów, stosy, kolejki, drzewa i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="59103-104">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="59103-105">Operacje, takie jak dodawanie i usuwanie elementów z kolekcji, są wykonywane w taki sam sposób, niezależnie od typu przechowywanych danych.</span><span class="sxs-lookup"><span data-stu-id="59103-105">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="59103-106">W przypadku większości scenariuszy, które wymagają klas kolekcji, Zalecanym podejściem jest użycie tych, które znajdują się w bibliotece klas .NET.</span><span class="sxs-lookup"><span data-stu-id="59103-106">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET class library.</span></span> <span data-ttu-id="59103-107">Aby uzyskać więcej informacji o korzystaniu z tych klas, zobacz [kolekcje ogólne w programie .NET](../../../standard/generics/collections.md).</span><span class="sxs-lookup"><span data-stu-id="59103-107">For more information about using these classes, see [Generic Collections in .NET](../../../standard/generics/collections.md).</span></span>  
  
 <span data-ttu-id="59103-108">Zazwyczaj tworzysz klasy generyczne, rozpoczynając od istniejącej konkretnej klasy i zmieniając typy na parametry typu jeden na raz, aż osiągniesz optymalny bilans generalizacji i użyteczności.</span><span class="sxs-lookup"><span data-stu-id="59103-108">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="59103-109">Podczas tworzenia własnych klas ogólnych ważne są następujące zagadnienia:</span><span class="sxs-lookup"><span data-stu-id="59103-109">When creating your own generic classes, important considerations include the following:</span></span>  
  
- <span data-ttu-id="59103-110">Które typy są uogólniać do parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="59103-110">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="59103-111">Im więcej typów, które można Sparametryzuj, tym bardziej elastyczne i wielokrotne użycie kodu stanie się.</span><span class="sxs-lookup"><span data-stu-id="59103-111">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="59103-112">Jednak zbyt wiele generalizacji może utworzyć kod, który jest trudny do odczytania lub zrozumienia dla innych deweloperów.</span><span class="sxs-lookup"><span data-stu-id="59103-112">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
- <span data-ttu-id="59103-113">Jakie ograniczenia (jeśli istnieją) mają być stosowane do parametrów typu (zobacz [ograniczenia dotyczące parametrów typu](./constraints-on-type-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="59103-113">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](./constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="59103-114">Dobrą regułą jest zastosowanie maksymalnych ograniczeń, które nadal będą obsługiwać typy, które należy obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="59103-114">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="59103-115">Na przykład jeśli wiesz, że Klasa generyczna jest przeznaczona do użycia tylko z typami referencyjnymi, Zastosuj ograniczenie klasy.</span><span class="sxs-lookup"><span data-stu-id="59103-115">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="59103-116">Uniemożliwi to niezamierzone użycie klasy z typami wartości i umożliwi użycie `as` operatora na `T`i sprawdzenie wartości null.</span><span class="sxs-lookup"><span data-stu-id="59103-116">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
- <span data-ttu-id="59103-117">Czy należy wziąć pod uwagę ogólne zachowanie w klasach bazowych i podklasach.</span><span class="sxs-lookup"><span data-stu-id="59103-117">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="59103-118">Ponieważ klasy generyczne mogą działać jako klasy bazowe, te same zagadnienia dotyczące projektowania są stosowane w tym miejscu, jak w przypadku klas innych niż ogólne.</span><span class="sxs-lookup"><span data-stu-id="59103-118">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="59103-119">Zapoznaj się z regułami dotyczącymi dziedziczenia z generycznych klas podstawowych w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="59103-119">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
- <span data-ttu-id="59103-120">Czy zaimplementować co najmniej jeden interfejs generyczny.</span><span class="sxs-lookup"><span data-stu-id="59103-120">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="59103-121">Na przykład w przypadku projektowania klasy, która będzie używana do tworzenia elementów w kolekcji generycznej, może być konieczne zaimplementowanie interfejsu, takiego jak <xref:System.IComparable%601> gdzie `T` jest typem klasy.</span><span class="sxs-lookup"><span data-stu-id="59103-121">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="59103-122">Aby zapoznać się z przykładem prostej klasy generycznej, zobacz [wprowadzenie do typów ogólnych](./index.md).</span><span class="sxs-lookup"><span data-stu-id="59103-122">For an example of a simple generic class, see [Introduction to Generics](./index.md).</span></span>  
  
 <span data-ttu-id="59103-123">Reguły dotyczące parametrów typu i ograniczeń mają różne konsekwencje dla zachowania klasy ogólnej, szczególnie dotyczące dziedziczenia i dostępności elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="59103-123">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="59103-124">Przed kontynuowaniem należy zrozumieć pewne warunki.</span><span class="sxs-lookup"><span data-stu-id="59103-124">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="59103-125">Dla kodu klienta klasy `Node<T>,` generycznej może odwoływać się do klasy przez określenie argumentu typu, aby utworzyć zamknięty typ skonstruowany (`Node<int>`).</span><span class="sxs-lookup"><span data-stu-id="59103-125">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="59103-126">Alternatywnie można pozostawić parametr typu nieokreślony, na przykład podczas określania generycznej klasy podstawowej, aby utworzyć otwarty typ skonstruowany (`Node<T>`).</span><span class="sxs-lookup"><span data-stu-id="59103-126">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="59103-127">Klasy generyczne mogą dziedziczyć z konkretnych, zamkniętych skonstruowanych lub otwartych klas bazowych:</span><span class="sxs-lookup"><span data-stu-id="59103-127">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 <span data-ttu-id="59103-128">Nieogólne, innymi słowy, klasy mogą dziedziczyć po zamkniętych skonstruowanych klasach bazowych, ale nie z otwartych klas skonstruowanych lub parametrów typu, ponieważ w czasie wykonywania dla kodu klienta nie ma żadnego sposobu na dostarczenie argumentu typu wymaganego do wystąpienia Klasa bazowa.</span><span class="sxs-lookup"><span data-stu-id="59103-128">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 <span data-ttu-id="59103-129">Klasy generyczne dziedziczące od typów typu "Opened" muszą dostarczać argumenty typu dla wszystkich parametrów klasy bazowej, które nie są współużytkowane przez klasę dziedziczenia, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="59103-129">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 <span data-ttu-id="59103-130">Klasy generyczne dziedziczące z typów typu "Open skonstruowane" muszą określać ograniczenia, które są nadzbiorem lub implikują ograniczenia dotyczące typu podstawowego:</span><span class="sxs-lookup"><span data-stu-id="59103-130">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 <span data-ttu-id="59103-131">Typy ogólne mogą używać wielu parametrów typu i ograniczeń w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="59103-131">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 <span data-ttu-id="59103-132">Jako parametry metody można użyć otwartych i zamkniętych typów skonstruowanych:</span><span class="sxs-lookup"><span data-stu-id="59103-132">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 <span data-ttu-id="59103-133">Jeśli Klasa ogólna implementuje interfejs, wszystkie wystąpienia tej klasy mogą być rzutowane do tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="59103-133">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="59103-134">Klasy generyczne są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="59103-134">Generic classes are invariant.</span></span> <span data-ttu-id="59103-135">Innymi słowy, jeśli parametr wejściowy określa `List<BaseClass>`, zostanie wyświetlony błąd czasu kompilacji, jeśli spróbujesz `List<DerivedClass>`podać.</span><span class="sxs-lookup"><span data-stu-id="59103-135">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59103-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59103-136">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="59103-137">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="59103-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="59103-138">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="59103-138">Generics</span></span>](./index.md)
- [<span data-ttu-id="59103-139">Zapisywanie stanu modułów wyliczających</span><span class="sxs-lookup"><span data-stu-id="59103-139">Saving the State of Enumerators</span></span>](https://blogs.msdn.microsoft.com/wesdyer/2006/01/13/saving-the-state-of-enumerators/)
- [<span data-ttu-id="59103-140">Dziedziczenie, część jedna</span><span class="sxs-lookup"><span data-stu-id="59103-140">An Inheritance Puzzle, Part One</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/07/27/an-inheritance-puzzle-part-one/)
