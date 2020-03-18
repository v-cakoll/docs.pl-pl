---
title: Generics - Przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: c7252180c9c98a8ca99c8cc6b3faaf8b1b8f0749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167495"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="27bb4-102">Typy ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="27bb4-102">Generics (C# Programming Guide)</span></span>

<span data-ttu-id="27bb4-103">Rodzajowe wprowadzić pojęcie parametrów typu do .NET Framework, które umożliwiają projektowanie klas i metod, które odroczyć specyfikację jednego lub więcej typów, dopóki klasa lub metoda jest zadeklarowana i tworzone przez kod klienta.</span><span class="sxs-lookup"><span data-stu-id="27bb4-103">Generics introduce the concept of type parameters to the .NET Framework, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="27bb4-104">Na przykład za pomocą parametru `T`typu ogólnego, można napisać jedną klasę, której można użyć inny kod klienta bez ponoszenia kosztów lub ryzyka rzutowania w czasie wykonywania lub operacji bokserskich, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="27bb4-104">For example, by using a generic type parameter `T`, you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

<span data-ttu-id="27bb4-105">Ogólne klasy i metody łączą możliwości ponownego użycia, bezpieczeństwo typów i wydajność w sposób, który nie może być ich odpowiednikami nierodzajowymi.</span><span class="sxs-lookup"><span data-stu-id="27bb4-105">Generic classes and methods combine reusability, type safety, and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="27bb4-106">Rodzajowe są najczęściej używane z kolekcji i metod, które działają na nich.</span><span class="sxs-lookup"><span data-stu-id="27bb4-106">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="27bb4-107">Obszar <xref:System.Collections.Generic> nazw zawiera kilka klas kolekcji ogólnej.</span><span class="sxs-lookup"><span data-stu-id="27bb4-107">The <xref:System.Collections.Generic> namespace contains several generic-based collection classes.</span></span> <span data-ttu-id="27bb4-108">Kolekcje nierodzajowe, <xref:System.Collections.ArrayList> takie jak nie są zalecane i są obsługiwane do celów zgodności.</span><span class="sxs-lookup"><span data-stu-id="27bb4-108">The non-generic collections, such as <xref:System.Collections.ArrayList> are not recommended and are maintained for compatibility purposes.</span></span> <span data-ttu-id="27bb4-109">Aby uzyskać więcej informacji, zobacz [Generykwi w .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="27bb4-109">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>

<span data-ttu-id="27bb4-110">Oczywiście można również utworzyć niestandardowe typy ogólne i metody, aby zapewnić własne uogólnione rozwiązania i wzorce projektowe, które są bezpieczne dla typu i wydajne.</span><span class="sxs-lookup"><span data-stu-id="27bb4-110">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="27bb4-111">W poniższym przykładzie kodu przedstawiono prostą klasę ogólnej listy połączonej do celów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="27bb4-111">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="27bb4-112">(W większości przypadków należy <xref:System.Collections.Generic.List%601> użyć klasy dostarczonej przez bibliotekę klas .NET Framework zamiast tworzyć własne). Parametr `T` type jest używany w kilku lokalizacjach, w których typ betonu zwykle używany do wskazania typu elementu przechowywanego na liście.</span><span class="sxs-lookup"><span data-stu-id="27bb4-112">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="27bb4-113">Jest on używany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="27bb4-113">It is used in the following ways:</span></span>

- <span data-ttu-id="27bb4-114">Jako typ parametru metody `AddHead` w metodzie.</span><span class="sxs-lookup"><span data-stu-id="27bb4-114">As the type of a method parameter in the `AddHead` method.</span></span>
- <span data-ttu-id="27bb4-115">Jako typ zwracany `Data` właściwości w `Node` klasie zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="27bb4-115">As the return type of the `Data` property in the nested `Node` class.</span></span>
- <span data-ttu-id="27bb4-116">Jako typ członka prywatnego `data` w klasie zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="27bb4-116">As the type of the private member `data` in the nested class.</span></span>

 <span data-ttu-id="27bb4-117">Należy `T` zauważyć, że jest `Node` dostępna dla klasy zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="27bb4-117">Note that `T` is available to the nested `Node` class.</span></span> <span data-ttu-id="27bb4-118">Gdy `GenericList<T>` jest tworzony z rodzaju betonu, `GenericList<int>`na przykład `T` jako , `int`każde wystąpienie zostanie zastąpione .</span><span class="sxs-lookup"><span data-stu-id="27bb4-118">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

<span data-ttu-id="27bb4-119">W poniższym przykładzie kodu pokazano, jak kod klienta używa klasy ogólnej `GenericList<T>` do tworzenia listy liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="27bb4-119">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="27bb4-120">Po prostu zmieniając argument typu, następujący kod można łatwo zmodyfikować, aby utworzyć listy ciągów lub innego typu niestandardowego:</span><span class="sxs-lookup"><span data-stu-id="27bb4-120">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a><span data-ttu-id="27bb4-121">Ogólny przegląd</span><span class="sxs-lookup"><span data-stu-id="27bb4-121">Generics overview</span></span>

- <span data-ttu-id="27bb4-122">Użyj typów ogólnych, aby zmaksymalizować ponowne użycie kodu, bezpieczeństwo typów i wydajność.</span><span class="sxs-lookup"><span data-stu-id="27bb4-122">Use generic types to maximize code reuse, type safety, and performance.</span></span>
- <span data-ttu-id="27bb4-123">Najczęstszym zastosowaniem typów ogólnych jest tworzenie klas kolekcji.</span><span class="sxs-lookup"><span data-stu-id="27bb4-123">The most common use of generics is to create collection classes.</span></span>
- <span data-ttu-id="27bb4-124">Biblioteka klas .NET Framework zawiera kilka nowych <xref:System.Collections.Generic> klas kolekcji rodzajowych w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="27bb4-124">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="27bb4-125">Powinny one być używane, gdy jest <xref:System.Collections.ArrayList> to <xref:System.Collections> możliwe, zamiast klas, takich jak w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="27bb4-125">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>
- <span data-ttu-id="27bb4-126">Można utworzyć własne interfejsy ogólne, klasy, metody, zdarzenia i delegatów.</span><span class="sxs-lookup"><span data-stu-id="27bb4-126">You can create your own generic interfaces, classes, methods, events, and delegates.</span></span>
- <span data-ttu-id="27bb4-127">Klasy ogólne mogą być ograniczone, aby umożliwić dostęp do metod dla określonych typów danych.</span><span class="sxs-lookup"><span data-stu-id="27bb4-127">Generic classes may be constrained to enable access to methods on particular data types.</span></span>
- <span data-ttu-id="27bb4-128">Informacje o typach, które są używane w typie danych ogólnych można uzyskać w czasie wykonywania przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="27bb4-128">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>

## <a name="related-sections"></a><span data-ttu-id="27bb4-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="27bb4-129">Related sections</span></span>

- [<span data-ttu-id="27bb4-130">Parametry typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="27bb4-130">Generic Type Parameters</span></span>](generic-type-parameters.md)
- [<span data-ttu-id="27bb4-131">Ograniczenia dotyczące parametrów typu</span><span class="sxs-lookup"><span data-stu-id="27bb4-131">Constraints on Type Parameters</span></span>](constraints-on-type-parameters.md)
- [<span data-ttu-id="27bb4-132">Klasy ogólne</span><span class="sxs-lookup"><span data-stu-id="27bb4-132">Generic Classes</span></span>](generic-classes.md)
- [<span data-ttu-id="27bb4-133">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="27bb4-133">Generic Interfaces</span></span>](generic-interfaces.md)
- [<span data-ttu-id="27bb4-134">Metody ogólne</span><span class="sxs-lookup"><span data-stu-id="27bb4-134">Generic Methods</span></span>](generic-methods.md)
- [<span data-ttu-id="27bb4-135">Delegaci ogólni</span><span class="sxs-lookup"><span data-stu-id="27bb4-135">Generic Delegates</span></span>](generic-delegates.md)
- [<span data-ttu-id="27bb4-136">Różnice między szablonami C++ i typami ogólnymi C#</span><span class="sxs-lookup"><span data-stu-id="27bb4-136">Differences Between C++ Templates and C# Generics</span></span>](differences-between-cpp-templates-and-csharp-generics.md)
- [<span data-ttu-id="27bb4-137">Typy ogólne i odbicie</span><span class="sxs-lookup"><span data-stu-id="27bb4-137">Generics and Reflection</span></span>](generics-and-reflection.md)
- [<span data-ttu-id="27bb4-138">Typy ogólne w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="27bb4-138">Generics in the Run Time</span></span>](generics-in-the-run-time.md)

## <a name="c-language-specification"></a><span data-ttu-id="27bb4-139">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="27bb4-139">C# language specification</span></span>

<span data-ttu-id="27bb4-140">Aby uzyskać więcej informacji, zobacz [Specyfikacja języka C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="27bb4-140">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="27bb4-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27bb4-141">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="27bb4-142">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="27bb4-142">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="27bb4-143">Typy</span><span class="sxs-lookup"><span data-stu-id="27bb4-143">Types</span></span>](../types/index.md)
- [<span data-ttu-id="27bb4-144">\<>typuparam</span><span class="sxs-lookup"><span data-stu-id="27bb4-144">\<typeparam></span></span>](../xmldoc/typeparam.md)
- [<span data-ttu-id="27bb4-145">\<typparamref></span><span class="sxs-lookup"><span data-stu-id="27bb4-145">\<typeparamref></span></span>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="27bb4-146">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="27bb4-146">Generics in .NET</span></span>](../../../standard/generics/index.md)
