---
title: Klasy ogólne — przewodnik programowania języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 1fdfaa833ad32428d341b6f3a61cc7f638036183
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937503"
---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="9a5b1-102">Klasy ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="9a5b1-102">Generic Classes (C# Programming Guide)</span></span>
<span data-ttu-id="9a5b1-103">Klasy ogólne hermetyzują operacje, które nie są specyficzne dla określonego typu danych.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-103">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="9a5b1-104">Najczęstszym zastosowaniem dla klas ogólnych jest z kolekcji, takich jak listy połączone, tabele mieszania, stosy, kolejki, drzewa i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-104">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="9a5b1-105">Operacje, takie jak dodawanie i usuwanie elementów z kolekcji są wykonywane w zasadzie w taki sam sposób, niezależnie od typu przechowywanych danych.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-105">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="9a5b1-106">W przypadku większości scenariuszy, które wymagają klas kolekcji, zaleca się podejście jest użycie tych, które są podane w bibliotece klas .NET.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-106">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET class library.</span></span> <span data-ttu-id="9a5b1-107">Aby uzyskać więcej informacji na temat korzystania z tych klas, zobacz [Kolekcje ogólne w .NET](../../../standard/generics/collections.md).</span><span class="sxs-lookup"><span data-stu-id="9a5b1-107">For more information about using these classes, see [Generic Collections in .NET](../../../standard/generics/collections.md).</span></span>  
  
 <span data-ttu-id="9a5b1-108">Zazwyczaj można utworzyć klasy ogólne, zaczynając od istniejącej klasy betonu i zmieniając typy na parametry typu po jednym naraz, aż do osiągnięcia optymalnej równowagi uogólnienia i użyteczności.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-108">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="9a5b1-109">Podczas tworzenia własnych klas ogólnych ważne zagadnienia obejmują następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="9a5b1-109">When creating your own generic classes, important considerations include the following:</span></span>  
  
- <span data-ttu-id="9a5b1-110">Które typy do uogólniania do parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-110">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="9a5b1-111">Z reguły im więcej typów można parametryzować, tym bardziej elastyczny i wielokrotnego użytku staje się kod.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-111">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="9a5b1-112">Jednak zbyt wiele generalizacji można utworzyć kod, który jest trudny do odczytania lub zrozumienia dla innych deweloperów.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-112">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
- <span data-ttu-id="9a5b1-113">Jakie ograniczenia, jeśli istnieją, aby zastosować do parametrów typu (zobacz [Ograniczenia parametrów typu](./constraints-on-type-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="9a5b1-113">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](./constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="9a5b1-114">Dobrą zasadą jest zastosowanie maksymalnych możliwych ograniczeń, które nadal umożliwiają obsługę typów, które należy obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-114">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="9a5b1-115">Na przykład jeśli wiesz, że klasa ogólna jest przeznaczona tylko do użytku z typami odwołań, należy zastosować ograniczenie klasy.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-115">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="9a5b1-116">Zapobiegnie to niezamierzonemu użyciu klasy z typami wartości `as` i `T`umożliwi użycie operatora na i sprawdzenie wartości null.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-116">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
- <span data-ttu-id="9a5b1-117">Czy uwzględniać ogólne zachowanie w klasach podstawowych i podklasach.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-117">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="9a5b1-118">Ponieważ klasy ogólne mogą służyć jako klasy podstawowe, te same zagadnienia dotyczące projektowania mają zastosowanie w tym miejscu, jak w przypadku klas nieogólnych.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-118">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="9a5b1-119">Zobacz reguły dotyczące dziedziczenia z ogólnych klas podstawowych w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-119">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
- <span data-ttu-id="9a5b1-120">Czy zaimplementować jeden lub więcej ogólnych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-120">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="9a5b1-121">Na przykład jeśli projektujesz klasę, która będzie używana do tworzenia elementów w kolekcji opartej na rodzajowych, może być konieczne zaimplementowanie interfejsu, takiego jak <xref:System.IComparable%601> where `T` jest typem klasy.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-121">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="9a5b1-122">Na przykład prostej klasy ogólnej zobacz [Wprowadzenie do typów ogólnych](./index.md).</span><span class="sxs-lookup"><span data-stu-id="9a5b1-122">For an example of a simple generic class, see [Introduction to Generics](./index.md).</span></span>  
  
 <span data-ttu-id="9a5b1-123">Reguły parametrów typu i ograniczeń mają kilka implikacji dla zachowania klasy ogólnej, szczególnie w odniesieniu do dziedziczenia i dostępności elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-123">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="9a5b1-124">Przed kontynuowaniem należy zapoznać się z pewnymi terminami.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-124">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="9a5b1-125">Dla klasy `Node<T>,` ogólnej kod klienta może odwoływać się do klasy albo określając`Node<int>`argument typu, aby utworzyć zamknięty typ konstruowany ( ).</span><span class="sxs-lookup"><span data-stu-id="9a5b1-125">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="9a5b1-126">Alternatywnie może pozostawić parametr typu nieokreślony, na przykład po określeniu ogólnej klasy podstawowej, aby utworzyć otwarty typ konstruowany (`Node<T>`).</span><span class="sxs-lookup"><span data-stu-id="9a5b1-126">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="9a5b1-127">Klasy ogólne mogą dziedziczyć z betonu, zamknięte skonstruowane lub otwarte skonstruowane klasy podstawowe:</span><span class="sxs-lookup"><span data-stu-id="9a5b1-127">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 <span data-ttu-id="9a5b1-128">Non-generic, innymi słowy konkretne, klasy mogą dziedziczyć z zamkniętych skonstruowanych klas podstawowych, ale nie z otwartych klas skonstruowanych lub z parametrów typu, ponieważ nie ma sposobu w czasie wykonywania dla kodu klienta, aby podać argument typu wymagany do wystąpienia wystąpienia klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-128">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 <span data-ttu-id="9a5b1-129">Klasy ogólne, które dziedziczą z otwartych typów skonstruowanych musi podać argumenty typu dla wszystkich parametrów typu klasy podstawowej, które nie są współużytkowane przez klasę dziedziczenia, jak pokazano w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="9a5b1-129">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 <span data-ttu-id="9a5b1-130">Klasy ogólne, które dziedziczą z otwartych typów skonstruowanych musi określić ograniczenia, które są nadzbiorem lub sugerować, ograniczenia typu podstawowego:</span><span class="sxs-lookup"><span data-stu-id="9a5b1-130">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 <span data-ttu-id="9a5b1-131">Typy ogólne mogą używać wielu parametrów i ograniczeń typu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9a5b1-131">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 <span data-ttu-id="9a5b1-132">Jako parametry metody można stosować typy konstrukcji skonstruowanych i zamkniętych:</span><span class="sxs-lookup"><span data-stu-id="9a5b1-132">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 <span data-ttu-id="9a5b1-133">Jeśli klasa ogólna implementuje interfejs, wszystkie wystąpienia tej klasy mogą być rzutowani do tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-133">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="9a5b1-134">Klasy ogólne są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="9a5b1-134">Generic classes are invariant.</span></span> <span data-ttu-id="9a5b1-135">Innymi słowy, jeśli parametr wejściowy `List<BaseClass>`określa , otrzymasz błąd czasu kompilacji, jeśli `List<DerivedClass>`spróbujesz podać .</span><span class="sxs-lookup"><span data-stu-id="9a5b1-135">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a5b1-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a5b1-136">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="9a5b1-137">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="9a5b1-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9a5b1-138">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="9a5b1-138">Generics</span></span>](./index.md)
- [<span data-ttu-id="9a5b1-139">Zapisywanie stanu wyliczaczy</span><span class="sxs-lookup"><span data-stu-id="9a5b1-139">Saving the State of Enumerators</span></span>](https://docs.microsoft.com/archive/blogs/wesdyer/saving-the-state-of-enumerators)
- [<span data-ttu-id="9a5b1-140">Zagadka dziedziczenia, część pierwsze</span><span class="sxs-lookup"><span data-stu-id="9a5b1-140">An Inheritance Puzzle, Part One</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/an-inheritance-puzzle-part-one)
