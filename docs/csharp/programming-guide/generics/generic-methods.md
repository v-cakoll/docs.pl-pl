---
title: Metody ogólne — przewodnik programowania języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 5f066ca39c97b70554886e423c37c4ee47d49158
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712198"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="22a11-102">Metody ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="22a11-102">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="22a11-103">Metoda ogólna jest metodą, która jest zadeklarowana z parametrami typu, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="22a11-103">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 <span data-ttu-id="22a11-104">Poniższy przykład kodu pokazuje jeden sposób wywołania metody przy użyciu `int` argumentu typu:</span><span class="sxs-lookup"><span data-stu-id="22a11-104">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 <span data-ttu-id="22a11-105">Można również pominąć argument typu i kompilator wywnioskuje go.</span><span class="sxs-lookup"><span data-stu-id="22a11-105">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="22a11-106">Następujące wywołanie `Swap` jest równoważne z poprzednim wywołaniem:</span><span class="sxs-lookup"><span data-stu-id="22a11-106">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 <span data-ttu-id="22a11-107">Te same reguły wnioskowania o typie mają zastosowanie do metod statycznych i metod wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="22a11-107">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="22a11-108">Kompilator można wywnioskować parametry typu na podstawie argumentów metody, które można przekazać w; nie można wywnioskować parametrów typu tylko z ograniczenia lub wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="22a11-108">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="22a11-109">W związku z tym wnioskowanie o typie nie działa z metodami, które nie mają parametrów.</span><span class="sxs-lookup"><span data-stu-id="22a11-109">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="22a11-110">Wnioskowanie o typie występuje w czasie kompilacji, zanim kompilator spróbuje rozwiązać przeciążone podpisy metody.</span><span class="sxs-lookup"><span data-stu-id="22a11-110">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="22a11-111">Kompilator stosuje logikę wnioskowania o typie do wszystkich metod ogólnych, które mają tę samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="22a11-111">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="22a11-112">W kroku rozpoznawania przeciążenia kompilator zawiera tylko te metody ogólne, na których wnioskowanie typu powiodło się.</span><span class="sxs-lookup"><span data-stu-id="22a11-112">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="22a11-113">W klasie ogólnej metody nieogólne mogą uzyskiwać dostęp do parametrów typu na poziomie klasy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="22a11-113">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 <span data-ttu-id="22a11-114">Jeśli zdefiniujesz metodę rodzajową, która przyjmuje parametry tego samego typu, co klasa zawierająca, kompilator generuje ostrzeżenie `T` [CS0693,](../../misc/cs0693.md) ponieważ w zakresie metody argument podany dla wewnętrznej ukrywa argument dostarczony dla zewnętrznego `T`.</span><span class="sxs-lookup"><span data-stu-id="22a11-114">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning [CS0693](../../misc/cs0693.md) because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="22a11-115">Jeśli potrzebujesz elastyczności wywoływania metody klasy ogólnej z argumentami typu innymi niż te podane, gdy klasa została uprzedzona, należy `GenericList2<T>` rozważyć podanie innego identyfikatora parametru typu metody, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="22a11-115">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 <span data-ttu-id="22a11-116">Użyj ograniczeń, aby włączyć bardziej wyspecjalizowane operacje parametrów typu w metodach.</span><span class="sxs-lookup"><span data-stu-id="22a11-116">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="22a11-117">Ta wersja `Swap<T>`, `SwapIfGreater<T>`teraz o nazwie , może <xref:System.IComparable%601>być używana tylko z argumentami typu, które implementują .</span><span class="sxs-lookup"><span data-stu-id="22a11-117">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 <span data-ttu-id="22a11-118">Metody ogólne mogą być przeciążone na kilka parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="22a11-118">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="22a11-119">Na przykład wszystkie następujące metody mogą znajdować się w tej samej klasie:</span><span class="sxs-lookup"><span data-stu-id="22a11-119">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="22a11-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="22a11-120">C# Language Specification</span></span>  
 <span data-ttu-id="22a11-121">Aby uzyskać więcej informacji, zobacz [Specyfikacja języka C#](~/_csharplang/spec/classes.md#methods).</span><span class="sxs-lookup"><span data-stu-id="22a11-121">For more information, see the [C# Language Specification](~/_csharplang/spec/classes.md#methods).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a11-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22a11-122">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="22a11-123">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="22a11-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="22a11-124">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="22a11-124">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="22a11-125">Metody</span><span class="sxs-lookup"><span data-stu-id="22a11-125">Methods</span></span>](../classes-and-structs/methods.md)
