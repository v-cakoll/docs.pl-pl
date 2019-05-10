---
title: Klasy ogólne — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 1e5a8d221468f5028f7b44af1c634b4c988063a4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596292"
---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="33ad0-102">Klasy ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="33ad0-102">Generic Classes (C# Programming Guide)</span></span>
<span data-ttu-id="33ad0-103">Klasy ogólne hermetyzować operacje, które nie są specyficzne dla określonego typu danych.</span><span class="sxs-lookup"><span data-stu-id="33ad0-103">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="33ad0-104">Jest najbardziej popularnym zastosowaniem klas ogólnych kolekcji, takich jak połączonej listy, tabele zbędnych danych, stosów, kolejek, drzewa i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="33ad0-104">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="33ad0-105">Operacje, takie jak dodawanie i usuwanie elementów z kolekcji są wykonywane w zasadzie taki sam sposób niezależnie od rodzaju przechowywanych danych.</span><span class="sxs-lookup"><span data-stu-id="33ad0-105">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="33ad0-106">W przypadku większości scenariuszy, które wymagają klasy kolekcji Zalecanym podejściem jest użycie jednego z dostarczanych w bibliotece klas programu .NET.</span><span class="sxs-lookup"><span data-stu-id="33ad0-106">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET class library.</span></span> <span data-ttu-id="33ad0-107">Aby uzyskać więcej informacji o korzystaniu z tych klas, zobacz [kolekcje ogólne w .NET](../../../standard/generics/collections.md).</span><span class="sxs-lookup"><span data-stu-id="33ad0-107">For more information about using these classes, see [Generic Collections in .NET](../../../standard/generics/collections.md).</span></span>  
  
 <span data-ttu-id="33ad0-108">Zazwyczaj tworzony klasy ogólne, począwszy od konkretnego istniejącej klasy, a zmiany typów w parametrach typu jeden do czasu osiągnięcia optymalną proporcję generalizacji i użyteczności tworzonych rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="33ad0-108">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="33ad0-109">Podczas tworzenia własnych klas ogólnych, istotne zagadnienia są następujące:</span><span class="sxs-lookup"><span data-stu-id="33ad0-109">When creating your own generic classes, important considerations include the following:</span></span>  
  
- <span data-ttu-id="33ad0-110">Typy, które można uogólnić do parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="33ad0-110">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="33ad0-111">Jako regułę, większą liczbę typów, które można zdefiniować parametry, bardziej elastyczne i wielokrotnego użytku staje się kodu.</span><span class="sxs-lookup"><span data-stu-id="33ad0-111">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="33ad0-112">Zbyt dużo Generalizacja można jednak utworzyć kod, który jest trudny innym deweloperom do odczytu lub zrozumieć.</span><span class="sxs-lookup"><span data-stu-id="33ad0-112">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
- <span data-ttu-id="33ad0-113">Jakie ograniczenia, jeśli istnieją, aby zastosować do parametrów typu (zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="33ad0-113">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="33ad0-114">Rozsądną regułą polega na zastosowaniu maksymalna ograniczenia możliwości, które pozwoli obsługiwać typy, które muszą obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="33ad0-114">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="33ad0-115">Na przykład jeśli wiesz, że Twoje klasy generycznej jest przeznaczony do użytku tylko w przypadku typów referencyjnych, mają zastosowanie ograniczenia klasy.</span><span class="sxs-lookup"><span data-stu-id="33ad0-115">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="33ad0-116">Uniemożliwi niezamierzone korzystanie z klasy z typami wartości i umożliwi przy użyciu `as` operatora na `T`i sprawdź, czy dla wartości null.</span><span class="sxs-lookup"><span data-stu-id="33ad0-116">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
- <span data-ttu-id="33ad0-117">Określa, czy uwzględnić ogólne zachowanie podstawowych klas i podklas.</span><span class="sxs-lookup"><span data-stu-id="33ad0-117">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="33ad0-118">Ponieważ klas ogólnych może służyć jako klay bazowe, tym samym zagadnienia dotyczące projektowania zgłosić się tutaj podobnie jak w przypadku nieogólnej klasy.</span><span class="sxs-lookup"><span data-stu-id="33ad0-118">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="33ad0-119">Zobacz reguły o dziedziczy z klasy bazowej ogólne w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="33ad0-119">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
- <span data-ttu-id="33ad0-120">Określa, czy zaimplementować jeden lub więcej interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="33ad0-120">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="33ad0-121">Na przykład w przypadku projektowania klasę, która będzie służyć do tworzenia elementów w kolekcji na podstawie typów ogólnych, może być konieczne takich jak implementować interfejsu <xref:System.IComparable%601> gdzie `T` jest typem klasy.</span><span class="sxs-lookup"><span data-stu-id="33ad0-121">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="33ad0-122">Na przykład prosty klasy ogólnej zobacz [wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="33ad0-122">For an example of a simple generic class, see [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span></span>  
  
 <span data-ttu-id="33ad0-123">Reguły dotyczące parametrów typu i ograniczenia dotyczą kilka zachowanie klasy generycznej, szczególnie w odniesieniu do dziedziczenia i elementów członkowskich ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="33ad0-123">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="33ad0-124">Przed kontynuowaniem należy poznać niektóre terminy.</span><span class="sxs-lookup"><span data-stu-id="33ad0-124">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="33ad0-125">Dla klasy ogólnej `Node<T>,` kod klienta może odwoływać się do klasy albo poprzez określenie argument typ, Utwórz zamknięte skonstruowanego typu (`Node<int>`).</span><span class="sxs-lookup"><span data-stu-id="33ad0-125">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="33ad0-126">Alternatywnie można pozostawić, parametr typu nie zostanie podany, na przykład po określeniu rodzajowego klasy podstawowej, aby utworzyć otwartą skonstruowany typ (`Node<T>`).</span><span class="sxs-lookup"><span data-stu-id="33ad0-126">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="33ad0-127">Klasy ogólne może dziedziczyć z konkretnej, zamknięte zbudowane lub Otwórz skonstruowanych klasach bazowych:</span><span class="sxs-lookup"><span data-stu-id="33ad0-127">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 <span data-ttu-id="33ad0-128">Innymi słowy, betonu inne niż ogólne, klasy mogą dziedziczyć z zamknięty skonstruowanych klasach bazowych, ale nie otwieranie skonstruowany klasy lub parametry typu, ponieważ nie ma żadnego sposobu, w czasie wykonywania w przypadku kodu klienta podać argument typu wymagane do utworzenia wystąpienia Klasa bazowa.</span><span class="sxs-lookup"><span data-stu-id="33ad0-128">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 <span data-ttu-id="33ad0-129">Klasy ogólne, które dziedziczą z Otwórz typy utworzone, musisz podać argumenty typu parametrów typu klasy bazowej, które nie są współdzielone przez klasy dziedziczącej, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="33ad0-129">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 <span data-ttu-id="33ad0-130">Klasy ogólne, które dziedziczą z Otwórz typy utworzone musi określić ograniczeń, które są podzbiorem, lub w sposób sugerujący ograniczenia dotyczące typu podstawowego:</span><span class="sxs-lookup"><span data-stu-id="33ad0-130">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 <span data-ttu-id="33ad0-131">Typy ogólne można użyć wielu parametrów typu i ograniczenia, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="33ad0-131">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 <span data-ttu-id="33ad0-132">Otwórz typy utworzone skonstruowany i zamknięte może służyć jako parametry metody:</span><span class="sxs-lookup"><span data-stu-id="33ad0-132">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 <span data-ttu-id="33ad0-133">Jeśli ogólne klasy implementuje interfejs, wszystkie wystąpienia tej klasy może być rzutowany tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="33ad0-133">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="33ad0-134">Klasy ogólne są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="33ad0-134">Generic classes are invariant.</span></span> <span data-ttu-id="33ad0-135">Innymi słowy Jeśli określono parametr wejściowy `List<BaseClass>`, otrzymasz błąd kompilacji, jeśli zostanie podjęta próba zapewniają `List<DerivedClass>`.</span><span class="sxs-lookup"><span data-stu-id="33ad0-135">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33ad0-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33ad0-136">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="33ad0-137">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="33ad0-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="33ad0-138">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="33ad0-138">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="33ad0-139">Zapisywanie stanu modułów wyliczających</span><span class="sxs-lookup"><span data-stu-id="33ad0-139">Saving the State of Enumerators</span></span>](https://blogs.msdn.microsoft.com/wesdyer/2006/01/13/saving-the-state-of-enumerators/)
- [<span data-ttu-id="33ad0-140">Układanki dziedziczenia część pierwsza</span><span class="sxs-lookup"><span data-stu-id="33ad0-140">An Inheritance Puzzle, Part One</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/07/27/an-inheritance-puzzle-part-one/)
