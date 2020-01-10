---
title: Typy ogólne — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 330aa74538ab15d1de19d80b0f57b3d0921c5c55
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712159"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="4e102-102">Typy ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="4e102-102">Generics (C# Programming Guide)</span></span>

<span data-ttu-id="4e102-103">Typy ogólne wprowadzają koncepcję parametrów typu do .NET Framework, co umożliwia zaprojektowanie klas i metod, które opóźniają specyfikację jednego lub kilku typów do momentu zadeklarowania klasy lub metody i wystąpienia przez kod klienta.</span><span class="sxs-lookup"><span data-stu-id="4e102-103">Generics introduce the concept of type parameters to the .NET Framework, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="4e102-104">Na przykład przy użyciu parametru typu ogólnego `T`można napisać pojedynczą klasę, której może użyć inny kod klienta, bez ponoszenia kosztów lub ryzyka związanego z rzutowaniem lub zapakowywaniem środowiska uruchomieniowego, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="4e102-104">For example, by using a generic type parameter `T`, you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

<span data-ttu-id="4e102-105">Klasy generyczne i metody łączą użyteczność, bezpieczeństwo typów i wydajność w taki sposób, że ich nieogólnymi odpowiednikami nie jest.</span><span class="sxs-lookup"><span data-stu-id="4e102-105">Generic classes and methods combine reusability, type safety, and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="4e102-106">Typy ogólne są najczęściej używane z kolekcjami i metodami, które działają na nich.</span><span class="sxs-lookup"><span data-stu-id="4e102-106">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="4e102-107">Przestrzeń nazw <xref:System.Collections.Generic> zawiera kilka ogólnych klas kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4e102-107">The <xref:System.Collections.Generic> namespace contains several generic-based collection classes.</span></span> <span data-ttu-id="4e102-108">Kolekcje inne niż ogólne, takie jak <xref:System.Collections.ArrayList> nie są zalecane i są obsługiwane w celu zapewnienia zgodności.</span><span class="sxs-lookup"><span data-stu-id="4e102-108">The non-generic collections, such as <xref:System.Collections.ArrayList> are not recommended and are maintained for compatibility purposes.</span></span> <span data-ttu-id="4e102-109">Aby uzyskać więcej informacji, zobacz [typy ogólne w programie .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="4e102-109">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>

<span data-ttu-id="4e102-110">Oczywiście można również tworzyć niestandardowe typy ogólne i metody w celu udostępniania własnych uogólnionych rozwiązań i wzorców projektowych, które są bezpieczne i wydajne.</span><span class="sxs-lookup"><span data-stu-id="4e102-110">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="4e102-111">Poniższy przykład kodu pokazuje prostą ogólną klasę listy połączonej w celach demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="4e102-111">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="4e102-112">(W większości przypadków należy użyć klasy <xref:System.Collections.Generic.List%601> dostarczonej przez bibliotekę klas .NET Framework zamiast tworzyć własne). Parametr typu `T` jest używany w kilku lokalizacjach, w których konkretny typ jest zwykle używany do wskazania typu elementu przechowywanego na liście.</span><span class="sxs-lookup"><span data-stu-id="4e102-112">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="4e102-113">Jest on używany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4e102-113">It is used in the following ways:</span></span>

- <span data-ttu-id="4e102-114">Jako typ parametru metody w metodzie `AddHead`.</span><span class="sxs-lookup"><span data-stu-id="4e102-114">As the type of a method parameter in the `AddHead` method.</span></span>
- <span data-ttu-id="4e102-115">Jako zwracany typ właściwości `Data` w klasie `Node` zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="4e102-115">As the return type of the `Data` property in the nested `Node` class.</span></span>
- <span data-ttu-id="4e102-116">Jako typ prywatnego elementu członkowskiego `data` w klasie zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="4e102-116">As the type of the private member `data` in the nested class.</span></span>

 <span data-ttu-id="4e102-117">Należy pamiętać, że `T` jest dostępny dla zagnieżdżonej klasy `Node`.</span><span class="sxs-lookup"><span data-stu-id="4e102-117">Note that `T` is available to the nested `Node` class.</span></span> <span data-ttu-id="4e102-118">Gdy `GenericList<T>` jest tworzone przy użyciu konkretnego typu, na przykład jako `GenericList<int>`, każde wystąpienie `T` zostanie zastąpione `int`.</span><span class="sxs-lookup"><span data-stu-id="4e102-118">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)] 

<span data-ttu-id="4e102-119">Poniższy przykład kodu pokazuje, jak kod klienta używa klasy generycznej `GenericList<T>` do tworzenia listy liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="4e102-119">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="4e102-120">Po prostu poprzez zmianę argumentu typu można łatwo zmodyfikować następujący kod w celu utworzenia list ciągów lub dowolnego innego typu niestandardowego:</span><span class="sxs-lookup"><span data-stu-id="4e102-120">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a><span data-ttu-id="4e102-121">Ogólne — przegląd</span><span class="sxs-lookup"><span data-stu-id="4e102-121">Generics overview</span></span>

- <span data-ttu-id="4e102-122">Używaj typów ogólnych do maksymalizowania ponownego użycia kodu, bezpieczeństwa typów i wydajności.</span><span class="sxs-lookup"><span data-stu-id="4e102-122">Use generic types to maximize code reuse, type safety, and performance.</span></span>
- <span data-ttu-id="4e102-123">Typowym zastosowaniem typów ogólnych jest utworzenie klas kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4e102-123">The most common use of generics is to create collection classes.</span></span>
- <span data-ttu-id="4e102-124">Biblioteka klas .NET Framework zawiera kilka nowych klas kolekcji ogólnych w przestrzeni nazw <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="4e102-124">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="4e102-125">Powinny one być używane, gdy jest to możliwe, zamiast klas takich jak <xref:System.Collections.ArrayList> w przestrzeni nazw <xref:System.Collections>.</span><span class="sxs-lookup"><span data-stu-id="4e102-125">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>
- <span data-ttu-id="4e102-126">Można tworzyć własne interfejsy, klasy, metody, zdarzenia i Delegaty.</span><span class="sxs-lookup"><span data-stu-id="4e102-126">You can create your own generic interfaces, classes, methods, events, and delegates.</span></span>
- <span data-ttu-id="4e102-127">Klasy generyczne mogą być ograniczone, aby umożliwić dostęp do metod dla konkretnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="4e102-127">Generic classes may be constrained to enable access to methods on particular data types.</span></span>
- <span data-ttu-id="4e102-128">Informacje na temat typów, które są używane w ogólnym typie danych, można uzyskać w czasie wykonywania przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="4e102-128">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>

## <a name="related-sections"></a><span data-ttu-id="4e102-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="4e102-129">Related sections</span></span>

- [<span data-ttu-id="4e102-130">Parametry typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="4e102-130">Generic Type Parameters</span></span>](generic-type-parameters.md)
- [<span data-ttu-id="4e102-131">Ograniczenia dotyczące parametrów typu</span><span class="sxs-lookup"><span data-stu-id="4e102-131">Constraints on Type Parameters</span></span>](constraints-on-type-parameters.md)
- [<span data-ttu-id="4e102-132">Klasy ogólne</span><span class="sxs-lookup"><span data-stu-id="4e102-132">Generic Classes</span></span>](generic-classes.md)
- [<span data-ttu-id="4e102-133">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="4e102-133">Generic Interfaces</span></span>](generic-interfaces.md)
- [<span data-ttu-id="4e102-134">Metody ogólne</span><span class="sxs-lookup"><span data-stu-id="4e102-134">Generic Methods</span></span>](generic-methods.md)
- [<span data-ttu-id="4e102-135">Delegaci ogólni</span><span class="sxs-lookup"><span data-stu-id="4e102-135">Generic Delegates</span></span>](generic-delegates.md)
- [<span data-ttu-id="4e102-136">Różnice między szablonami C++ i typami ogólnymi C#</span><span class="sxs-lookup"><span data-stu-id="4e102-136">Differences Between C++ Templates and C# Generics</span></span>](differences-between-cpp-templates-and-csharp-generics.md)
- [<span data-ttu-id="4e102-137">Typy ogólne i odbicie</span><span class="sxs-lookup"><span data-stu-id="4e102-137">Generics and Reflection</span></span>](generics-and-reflection.md)
- [<span data-ttu-id="4e102-138">Typy ogólne w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="4e102-138">Generics in the Run Time</span></span>](generics-in-the-run-time.md)

## <a name="c-language-specification"></a><span data-ttu-id="4e102-139">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4e102-139">C# language specification</span></span>

<span data-ttu-id="4e102-140">Aby uzyskać więcej informacji, zobacz [Specyfikacja języka C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="4e102-140">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e102-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e102-141">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="4e102-142">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4e102-142">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4e102-143">Typy</span><span class="sxs-lookup"><span data-stu-id="4e102-143">Types</span></span>](../types/index.md)
- [<span data-ttu-id="4e102-144">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="4e102-144">\<typeparam></span></span>](../xmldoc/typeparam.md)
- [<span data-ttu-id="4e102-145">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="4e102-145">\<typeparamref></span></span>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="4e102-146">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="4e102-146">Generics in .NET</span></span>](../../../standard/generics/index.md)
