---
title: Typy ogólne — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 7d212aeaa7d7a8c3f152f8610a7ef3fe5de0fe23
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589596"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="2431c-102">Typy ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="2431c-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="2431c-103">Typy ogólne zostały dodane do wersji 2,0 C# języka i środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="2431c-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="2431c-104">Typy ogólne wprowadzają do .NET Framework koncepcji parametrów typu, które umożliwiają zaprojektowanie klas i metod, które opóźniają specyfikację jednego lub kilku typów do momentu zadeklarowania klasy lub metody jako wystąpienia przez kod klienta.</span><span class="sxs-lookup"><span data-stu-id="2431c-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="2431c-105">Na przykład przy użyciu parametru typu ogólnego T można napisać pojedynczą klasę, która może być używana przez inny kod klienta, bez ponoszenia kosztów lub ryzyka związanego z rzutowaniem lub zapakowywaniem środowiska uruchomieniowego, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="2431c-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

<span data-ttu-id="2431c-106">Klasy generyczne i metody łączą użyteczność, bezpieczeństwo typów i wydajność w taki sposób, że ich nieogólnymi odpowiednikami nie jest.</span><span class="sxs-lookup"><span data-stu-id="2431c-106">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="2431c-107">Typy ogólne są najczęściej używane z kolekcjami i metodami, które działają na nich.</span><span class="sxs-lookup"><span data-stu-id="2431c-107">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="2431c-108">Wersja 2,0 biblioteki klas .NET Framework udostępnia nową przestrzeń nazw <xref:System.Collections.Generic>, która zawiera kilka nowych klas kolekcji opartych na typach ogólnych.</span><span class="sxs-lookup"><span data-stu-id="2431c-108">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="2431c-109">Zaleca się, aby wszystkie aplikacje przeznaczone dla .NET Framework 2,0 i później używały nowych klas kolekcji ogólnej zamiast starszych nieogólnych odpowiedników, takich jak <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="2431c-109">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="2431c-110">Aby uzyskać więcej informacji, zobacz [typy ogólne w programie .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="2431c-110">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="2431c-111">Oczywiście można również tworzyć niestandardowe typy ogólne i metody w celu udostępniania własnych uogólnionych rozwiązań i wzorców projektowych, które są bezpieczne i wydajne.</span><span class="sxs-lookup"><span data-stu-id="2431c-111">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="2431c-112">Poniższy przykład kodu pokazuje prostą ogólną klasę listy połączonej w celach demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="2431c-112">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="2431c-113">(W większości przypadków należy użyć <xref:System.Collections.Generic.List%601> klasy dostarczonej przez .NET Framework bibliotekę klas zamiast tworzyć własne.) Parametr `T` typu jest używany w kilku lokalizacjach, w których konkretny typ jest zwykle używany do wskazania typu elementu przechowywanego na liście.</span><span class="sxs-lookup"><span data-stu-id="2431c-113">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="2431c-114">Jest on używany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2431c-114">It is used in the following ways:</span></span>  
  
- <span data-ttu-id="2431c-115">Jako typ parametru metody w `AddHead` metodzie.</span><span class="sxs-lookup"><span data-stu-id="2431c-115">As the type of a method parameter in the `AddHead` method.</span></span>  
  
- <span data-ttu-id="2431c-116">Jako zwracany typ `Data` właściwości w klasie zagnieżdżonej `Node` .</span><span class="sxs-lookup"><span data-stu-id="2431c-116">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
- <span data-ttu-id="2431c-117">Jako typ prywatnego elementu członkowskiego `data` w klasie zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="2431c-117">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="2431c-118">Należy zauważyć, że T jest dostępny dla `Node` klasy zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="2431c-118">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="2431c-119">Gdy `GenericList<T>` jest tworzona przy użyciu konkretnego typu, na przykład `GenericList<int>`jako, każde wystąpienie `T` zostanie zastąpione `int`.</span><span class="sxs-lookup"><span data-stu-id="2431c-119">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 <span data-ttu-id="2431c-120">Poniższy przykład kodu pokazuje, jak kod klienta używa klasy generycznej `GenericList<T>` do tworzenia listy liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="2431c-120">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="2431c-121">Po prostu poprzez zmianę argumentu typu można łatwo zmodyfikować następujący kod w celu utworzenia list ciągów lub dowolnego innego typu niestandardowego:</span><span class="sxs-lookup"><span data-stu-id="2431c-121">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a><span data-ttu-id="2431c-122">Ogólne — przegląd</span><span class="sxs-lookup"><span data-stu-id="2431c-122">Generics Overview</span></span>  
  
- <span data-ttu-id="2431c-123">Używaj typów ogólnych do maksymalizowania ponownego użycia kodu, bezpieczeństwa typów i wydajności.</span><span class="sxs-lookup"><span data-stu-id="2431c-123">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
- <span data-ttu-id="2431c-124">Typowym zastosowaniem typów ogólnych jest utworzenie klas kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2431c-124">The most common use of generics is to create collection classes.</span></span>  
  
- <span data-ttu-id="2431c-125">Biblioteka klas .NET Framework zawiera kilka nowych klas kolekcji ogólnych w <xref:System.Collections.Generic> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2431c-125">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="2431c-126">Powinny one być używane w miarę możliwości zamiast klas takich jak <xref:System.Collections.ArrayList> <xref:System.Collections> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2431c-126">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
- <span data-ttu-id="2431c-127">Można tworzyć własne interfejsy, klasy, metody, zdarzenia i Delegaty.</span><span class="sxs-lookup"><span data-stu-id="2431c-127">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
- <span data-ttu-id="2431c-128">Klasy generyczne mogą być ograniczone, aby umożliwić dostęp do metod dla konkretnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="2431c-128">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
- <span data-ttu-id="2431c-129">Informacje na temat typów, które są używane w ogólnym typie danych, można uzyskać w czasie wykonywania przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="2431c-129">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2431c-130">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="2431c-130">Related Sections</span></span>  
 <span data-ttu-id="2431c-131">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="2431c-131">For more information:</span></span>  
  
- [<span data-ttu-id="2431c-132">Parametry typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="2431c-132">Generic Type Parameters</span></span>](./generic-type-parameters.md)  
  
- [<span data-ttu-id="2431c-133">Ograniczenia dotyczące parametrów typu</span><span class="sxs-lookup"><span data-stu-id="2431c-133">Constraints on Type Parameters</span></span>](./constraints-on-type-parameters.md)  
  
- [<span data-ttu-id="2431c-134">Klasy ogólne</span><span class="sxs-lookup"><span data-stu-id="2431c-134">Generic Classes</span></span>](./generic-classes.md)  
  
- [<span data-ttu-id="2431c-135">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="2431c-135">Generic Interfaces</span></span>](./generic-interfaces.md)  
  
- [<span data-ttu-id="2431c-136">Metody ogólne</span><span class="sxs-lookup"><span data-stu-id="2431c-136">Generic Methods</span></span>](./generic-methods.md)  
  
- [<span data-ttu-id="2431c-137">Delegaci ogólni</span><span class="sxs-lookup"><span data-stu-id="2431c-137">Generic Delegates</span></span>](./generic-delegates.md)  
  
- [<span data-ttu-id="2431c-138">Różnice między szablonami C++ i typami ogólnymi C#</span><span class="sxs-lookup"><span data-stu-id="2431c-138">Differences Between C++ Templates and C# Generics</span></span>](./differences-between-cpp-templates-and-csharp-generics.md)  
  
- [<span data-ttu-id="2431c-139">Typy ogólne i odbicie</span><span class="sxs-lookup"><span data-stu-id="2431c-139">Generics and Reflection</span></span>](./generics-and-reflection.md)  
  
- [<span data-ttu-id="2431c-140">Typy ogólne w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="2431c-140">Generics in the Run Time</span></span>](./generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="2431c-141">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2431c-141">C# Language Specification</span></span>  
 <span data-ttu-id="2431c-142">Aby uzyskać więcej informacji, zobacz [Specyfikacja języka C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="2431c-142">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2431c-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2431c-143">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="2431c-144">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2431c-144">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2431c-145">Typy</span><span class="sxs-lookup"><span data-stu-id="2431c-145">Types</span></span>](../types/index.md)
- [<span data-ttu-id="2431c-146">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="2431c-146">\<typeparam></span></span>](../xmldoc/typeparam.md)
- [<span data-ttu-id="2431c-147">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="2431c-147">\<typeparamref></span></span>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="2431c-148">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="2431c-148">Generics in .NET</span></span>](../../../standard/generics/index.md)
