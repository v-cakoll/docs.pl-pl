---
title: Ogólne — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: e32eb7c60e01ca72824ffb3a1e1269cf34650f5a
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423399"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="5bd48-102">Typy ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="5bd48-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="5bd48-103">Typy ogólne zostały dodane do wersji języka C# i środowisko uruchomieniowe języka wspólnego (CLR) w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="5bd48-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="5bd48-104">Ogólne wprowadzenie do programu .NET Framework pojęcia parametrami typu, które umożliwiają projektowanie klas i metod, które Odrocz specyfikację jeden lub więcej typów, dopóki klasy lub metody jest zadeklarowana i tworzone przez kod klienta.</span><span class="sxs-lookup"><span data-stu-id="5bd48-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="5bd48-105">Na przykład za pomocą parametru typu generycznego T, można napisać jedną klasę, używaną przez inny kod klienta bez ponoszenia kosztów ani ryzyka rzutowania środowiska uruchomieniowego lub operacje na polach, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="5bd48-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

<span data-ttu-id="5bd48-106">Ogólne klasy i metody łączenia możliwość ponownego wykorzystania, bezpieczeństwa i wydajności w taki sposób, że nie można ich odpowiedniki nieogólnego.</span><span class="sxs-lookup"><span data-stu-id="5bd48-106">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="5bd48-107">Najczęściej używanych typów ogólnych za pomocą metod, które działają na nich i kolekcje.</span><span class="sxs-lookup"><span data-stu-id="5bd48-107">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="5bd48-108">Biblioteki klas .NET Framework w wersji 2.0 oferuje nową przestrzeń nazw <xref:System.Collections.Generic>, który zawiera kilka nowych klas kolekcji ogólnej.</span><span class="sxs-lookup"><span data-stu-id="5bd48-108">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="5bd48-109">Zalecane jest, że wszystkie aplikacje przeznaczone na platformę .NET Framework 2.0 i późniejszego użycia nowej kolekcji ogólnej klasy zamiast starszych odpowiedniki nieogólnego, takich jak <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="5bd48-109">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="5bd48-110">Aby uzyskać więcej informacji, zobacz [typy ogólne w .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="5bd48-110">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="5bd48-111">Oczywiście można również utworzyć niestandardowe typy ogólne i metody w celu zapewnienia własne uogólniony rozwiązań i wzorców projektowych, które są bezpieczne i wydajne.</span><span class="sxs-lookup"><span data-stu-id="5bd48-111">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="5bd48-112">Poniższy przykład kodu pokazuje prosty klasy połączonej listy ogólnej dla celów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="5bd48-112">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="5bd48-113">(W większości przypadków należy używać <xref:System.Collections.Generic.List%601> klasy biblioteki klas .NET Framework, zamiast tworzyć własne.) Parametr typu `T` jest używany w kilku lokalizacjach, gdzie konkretny typ byłyby zwykle używane do wskazać typ elementu przechowywane na liście.</span><span class="sxs-lookup"><span data-stu-id="5bd48-113">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="5bd48-114">Jest on używany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5bd48-114">It is used in the following ways:</span></span>  
  
- <span data-ttu-id="5bd48-115">Jako typ parametru metody w `AddHead` metody.</span><span class="sxs-lookup"><span data-stu-id="5bd48-115">As the type of a method parameter in the `AddHead` method.</span></span>  
  
- <span data-ttu-id="5bd48-116">Jako typ zwracany `Data` właściwość w zagnieżdżonej `Node` klasy.</span><span class="sxs-lookup"><span data-stu-id="5bd48-116">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
- <span data-ttu-id="5bd48-117">Jako typ prywatnego elementu członkowskiego `data` w klasie zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="5bd48-117">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="5bd48-118">Należy pamiętać, że T jest dostępny do zagnieżdżonego `Node` klasy.</span><span class="sxs-lookup"><span data-stu-id="5bd48-118">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="5bd48-119">Gdy `GenericList<T>` zostanie uruchomiony przy użyciu konkretnego typu, na przykład jako `GenericList<int>`, każde wystąpienie `T` zostanie zastąpiony `int`.</span><span class="sxs-lookup"><span data-stu-id="5bd48-119">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 <span data-ttu-id="5bd48-120">Poniższy przykład kodu pokazuje, jak kod klienta korzysta z ogólnego `GenericList<T>` klasy, aby utworzyć listę liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="5bd48-120">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="5bd48-121">Po prostu zmieniając argument typu, poniższy kod można łatwo można zmodyfikować, aby utworzyć listę ciągów lub dowolny inny typ niestandardowy:</span><span class="sxs-lookup"><span data-stu-id="5bd48-121">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a><span data-ttu-id="5bd48-122">Przegląd typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="5bd48-122">Generics Overview</span></span>  
  
- <span data-ttu-id="5bd48-123">Aby zmaksymalizować ponowne wykorzystanie kodu, bezpieczeństwa i wydajności, należy użyć typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="5bd48-123">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
- <span data-ttu-id="5bd48-124">Najczęściej używane typy ogólne są do tworzenia klas kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5bd48-124">The most common use of generics is to create collection classes.</span></span>  
  
- <span data-ttu-id="5bd48-125">Biblioteka klas .NET Framework zawiera kilka nowych klas ogólnych kolekcji w <xref:System.Collections.Generic> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5bd48-125">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="5bd48-126">Powinny one być stosowane zawsze, gdy to możliwe, zamiast klasy, takie jak <xref:System.Collections.ArrayList> w <xref:System.Collections> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5bd48-126">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
- <span data-ttu-id="5bd48-127">Możesz utworzyć własne interfejsy ogólne, klas, metod, zdarzeń i delegatów.</span><span class="sxs-lookup"><span data-stu-id="5bd48-127">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
- <span data-ttu-id="5bd48-128">Klasy ogólne może być ograniczona umożliwiające dostęp do metod w typach danych.</span><span class="sxs-lookup"><span data-stu-id="5bd48-128">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
- <span data-ttu-id="5bd48-129">W czasie wykonywania można uzyskać informacje na temat typów, które są używane w typie danych typu ogólnego przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="5bd48-129">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5bd48-130">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5bd48-130">Related Sections</span></span>  
 <span data-ttu-id="5bd48-131">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="5bd48-131">For more information:</span></span>  
  
- [<span data-ttu-id="5bd48-132">Parametry typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="5bd48-132">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
- [<span data-ttu-id="5bd48-133">Ograniczenia dotyczące parametrów typu</span><span class="sxs-lookup"><span data-stu-id="5bd48-133">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
- [<span data-ttu-id="5bd48-134">Klasy ogólne</span><span class="sxs-lookup"><span data-stu-id="5bd48-134">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
- [<span data-ttu-id="5bd48-135">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="5bd48-135">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
- [<span data-ttu-id="5bd48-136">Metody ogólne</span><span class="sxs-lookup"><span data-stu-id="5bd48-136">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
- [<span data-ttu-id="5bd48-137">Delegaci ogólni</span><span class="sxs-lookup"><span data-stu-id="5bd48-137">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
- [<span data-ttu-id="5bd48-138">Różnice między szablonami C++ i typami ogólnymi C#</span><span class="sxs-lookup"><span data-stu-id="5bd48-138">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
- [<span data-ttu-id="5bd48-139">Typy ogólne i odbicie</span><span class="sxs-lookup"><span data-stu-id="5bd48-139">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
- [<span data-ttu-id="5bd48-140">Typy ogólne w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="5bd48-140">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="5bd48-141">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5bd48-141">C# Language Specification</span></span>  
 <span data-ttu-id="5bd48-142">Aby uzyskać więcej informacji, zobacz [Specyfikacja języka C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="5bd48-142">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bd48-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5bd48-143">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="5bd48-144">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5bd48-144">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5bd48-145">Typy</span><span class="sxs-lookup"><span data-stu-id="5bd48-145">Types</span></span>](../../../csharp/programming-guide/types/index.md)
- [<span data-ttu-id="5bd48-146">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="5bd48-146">\<typeparam></span></span>](../../../csharp/programming-guide/xmldoc/typeparam.md)
- [<span data-ttu-id="5bd48-147">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="5bd48-147">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)
- [<span data-ttu-id="5bd48-148">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="5bd48-148">Generics in .NET</span></span>](../../../standard/generics/index.md)
