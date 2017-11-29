---
title: "Klasy ogólne (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c92efd63f7b24917dc50ca0864f1a132c5c2bf00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="5536a-102">Klasy ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="5536a-102">Generic Classes (C# Programming Guide)</span></span>
<span data-ttu-id="5536a-103">Klasy ogólne hermetyzować operacje, które nie są specyficzne dla określonego typu danych.</span><span class="sxs-lookup"><span data-stu-id="5536a-103">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="5536a-104">Jest najbardziej popularnym zastosowaniem klas ogólnych z kolekcjami, takie jak listy połączonej, tabelach skrótów, stosy, kolejek, drzewa i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="5536a-104">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="5536a-105">Operacje, takie jak dodawanie i usuwanie elementów z kolekcji są wykonywane w zasadniczo taki sam sposób, bez względu na typ przechowywanych danych.</span><span class="sxs-lookup"><span data-stu-id="5536a-105">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="5536a-106">Dla większości scenariuszy, które wymagają klasy kolekcji zalecanym rozwiązaniem jest użycie jednego z dostarczanych w bibliotece klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5536a-106">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET Framework class library.</span></span> <span data-ttu-id="5536a-107">Aby uzyskać więcej informacji o korzystaniu z tych klas, zobacz [typy ogólne w bibliotece klas programu .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).</span><span class="sxs-lookup"><span data-stu-id="5536a-107">For more information about using these classes, see [Generics in the .NET Framework Class Library](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).</span></span>  
  
 <span data-ttu-id="5536a-108">Zazwyczaj do tworzenia klas rodzajowych począwszy od konkretnego istniejącej klasy, a zmiany typów w parametrach typu jeden w chwili, aż dojdziesz optymalną proporcję uogólnianie i użyteczność.</span><span class="sxs-lookup"><span data-stu-id="5536a-108">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="5536a-109">Podczas tworzenia własnych klas rodzajowych, ważne następujące czynniki:</span><span class="sxs-lookup"><span data-stu-id="5536a-109">When creating your own generic classes, important considerations include the following:</span></span>  
  
-   <span data-ttu-id="5536a-110">Jakie typy do uogólnienia do parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="5536a-110">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="5536a-111">Jako regułę, więcej typów, które można parametryzacja, bardziej elastyczne i do ponownego użycia kodu staje się.</span><span class="sxs-lookup"><span data-stu-id="5536a-111">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="5536a-112">Jednak zbyt dużo generalizacji można tworzyć kod, który jest trudne dla innych projektantów do odczytu lub zrozumieć.</span><span class="sxs-lookup"><span data-stu-id="5536a-112">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
-   <span data-ttu-id="5536a-113">Jakie ograniczenia, jeśli istnieją, aby zastosować do parametrów typu (zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="5536a-113">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="5536a-114">Rozsądną regułą jest zastosowanie maksymalną ograniczenia możliwości umożliwiających będą nadal obsługiwać typy, które muszą obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="5536a-114">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="5536a-115">Na przykład jeśli wiadomo, że ogólny klasy jest przeznaczona do użycia tylko w przypadku typów referencyjnych, mają zastosowanie ograniczenia klasy.</span><span class="sxs-lookup"><span data-stu-id="5536a-115">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="5536a-116">Uniemożliwi użycie niezamierzone klasy z typów wartości i umożliwi użytkownikowi korzystanie z `as` operator na `T`i sprawdź, czy wartości null.</span><span class="sxs-lookup"><span data-stu-id="5536a-116">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
-   <span data-ttu-id="5536a-117">Określa, czy uwzględnić ogólne zachowanie podstawowych klas i podklas.</span><span class="sxs-lookup"><span data-stu-id="5536a-117">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="5536a-118">Ponieważ klasy rodzajowe mogą służyć jako klasy podstawowe, te same projektowania kwestie tutaj za pomocą klasy nieogólnego.</span><span class="sxs-lookup"><span data-stu-id="5536a-118">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="5536a-119">Zobacz zasady dotyczące dziedziczenia z klasy podstawowej ogólne w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5536a-119">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
-   <span data-ttu-id="5536a-120">Określa, czy wdrożyć jeden lub więcej interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="5536a-120">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="5536a-121">Na przykład w przypadku projektowania klasy, która będzie służyć do tworzenia elementów w kolekcji na podstawie ogólne, może być konieczne implementować interfejsu, takich jak <xref:System.IComparable%601> gdzie `T` jest typem klasy.</span><span class="sxs-lookup"><span data-stu-id="5536a-121">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="5536a-122">Na przykład prosty klasy ogólnej zobacz [wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="5536a-122">For an example of a simple generic class, see [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span></span>  
  
 <span data-ttu-id="5536a-123">Reguły dotyczące parametrów typu i ograniczenia dotyczą kilka zachowanie klasy ogólnej, szczególnie w odniesieniu do dziedziczenia i element członkowski ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="5536a-123">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="5536a-124">Przed kontynuowaniem należy poznać niektóre warunki.</span><span class="sxs-lookup"><span data-stu-id="5536a-124">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="5536a-125">Dla klasy ogólnej `Node<T>,` klienta kod można odwoływać się do klasy przez określenie typu argumentu, można utworzyć zamkniętego skonstruowanego typu (`Node<int>`).</span><span class="sxs-lookup"><span data-stu-id="5536a-125">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="5536a-126">Alternatywnie można pozostawić parametr typu określony, na przykład po określeniu ogólny klasy podstawowej, można utworzyć otwarty skonstruować typu (`Node<T>`).</span><span class="sxs-lookup"><span data-stu-id="5536a-126">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="5536a-127">Klasy ogólne może dziedziczyć z konkretnych, zamkniętego utworzone lub otwarte skonstruowane klas podstawowych:</span><span class="sxs-lookup"><span data-stu-id="5536a-127">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#16](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_1.cs)]  
  
 <span data-ttu-id="5536a-128">Innymi słowy, specyficzne inne niż ogólne, klasy mogą dziedziczyć zamkniętego skonstruowane klas podstawowych, ale nie z klasy skonstruowane Otwórz lub parametrów typu, ponieważ w czasie wykonywania dla kodu klienta podać argument typu wymagane do utworzenia wystąpienia nie istnieje sposób Klasa podstawowa.</span><span class="sxs-lookup"><span data-stu-id="5536a-128">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#17](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_2.cs)]  
  
 <span data-ttu-id="5536a-129">Klasy ogólne, które dziedziczą z Otwórz typy utworzone, musisz podać argumentów typu dla parametrów typu klasy podstawowej, które nie są udostępnione przez klasę dziedziczących, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="5536a-129">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#18](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_3.cs)]  
  
 <span data-ttu-id="5536a-130">Klasy ogólne, które dziedziczą z Otwórz typy utworzone musi określić ograniczeń, które są podzbiorem lub oznaczać ograniczenia dotyczące typu podstawowego:</span><span class="sxs-lookup"><span data-stu-id="5536a-130">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#19](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_4.cs)]  
  
 <span data-ttu-id="5536a-131">Typy ogólne i można używać wielu parametrów typu ograniczenia, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5536a-131">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#20](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_5.cs)]  
  
 <span data-ttu-id="5536a-132">Otwórz typy utworzone skonstruowane i zamknięte może być używane jako parametry metody:</span><span class="sxs-lookup"><span data-stu-id="5536a-132">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#21](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_6.cs)]  
  
 <span data-ttu-id="5536a-133">Jeśli klasy ogólnej implementuje interfejs, wszystkie wystąpienia tej klasy można rzutować na ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="5536a-133">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="5536a-134">Klasy ogólne są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="5536a-134">Generic classes are invariant.</span></span> <span data-ttu-id="5536a-135">Innymi słowy Jeśli określono parametr wejściowy `List<BaseClass>`, wystąpi błąd kompilacji Jeśli spróbujesz podaj `List<DerivedClass>`.</span><span class="sxs-lookup"><span data-stu-id="5536a-135">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5536a-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5536a-136">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="5536a-137">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5536a-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5536a-138">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="5536a-138">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="5536a-139">Zapisywanie stanu moduły wyliczające</span><span class="sxs-lookup"><span data-stu-id="5536a-139">Saving the State of Enumerators</span></span>](http://go.microsoft.com/fwlink/?LinkId=112390)  
 [<span data-ttu-id="5536a-140">Układanki dziedziczenia jedną część</span><span class="sxs-lookup"><span data-stu-id="5536a-140">An Inheritance Puzzle, Part One</span></span>](http://go.microsoft.com/fwlink/?LinkId=112380)
