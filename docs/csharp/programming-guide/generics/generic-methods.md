---
title: Metody ogólne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 0fb5267e6324d3dffd1ad5a72ef3718c8cdd08b8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552908"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="90123-102">Metody ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="90123-102">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="90123-103">Metody ogólnej to metoda, która jest zadeklarowana za pomocą parametrów typu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="90123-103">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]  
  
 <span data-ttu-id="90123-104">Poniższy przykład kodu przedstawia sposób wywołania metody przy użyciu `int` dla argumentu typu:</span><span class="sxs-lookup"><span data-stu-id="90123-104">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]  
  
 <span data-ttu-id="90123-105">Można również pominąć argument typu, a kompilator wywnioskuje go.</span><span class="sxs-lookup"><span data-stu-id="90123-105">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="90123-106">Następujące wywołanie do `Swap` jest odpowiednikiem poprzedniego wywołania:</span><span class="sxs-lookup"><span data-stu-id="90123-106">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]  
  
 <span data-ttu-id="90123-107">Te same reguły wnioskowania o typie dotyczą metod statycznych i metod wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="90123-107">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="90123-108">Kompilator może wywnioskować parametry typu, na podstawie argumentów metody, które są przekazywane w; Nie można go wywnioskować parametrów typu tylko z ograniczeniem lub wartość zwracana.</span><span class="sxs-lookup"><span data-stu-id="90123-108">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="90123-109">Wnioskowanie o typie w związku z tym nie działa z metod, które nie mają parametrów.</span><span class="sxs-lookup"><span data-stu-id="90123-109">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="90123-110">Wnioskowanie o typie występuje w czasie kompilacji, zanim kompilator próbuje rozpoznać podpisy przeciążonej metody.</span><span class="sxs-lookup"><span data-stu-id="90123-110">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="90123-111">Kompilator stosuje logikę wnioskowania typu, do wszystkich metod ogólnych, które mają taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="90123-111">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="90123-112">W kroku rozdzielczość przeciążenia kompilator zawiera tylko metod ogólnych na których wnioskowanie o typie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="90123-112">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="90123-113">W obrębie klasy ogólnej metody nieogólnego mieli dostęp do parametrów typu na poziomie klasy, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="90123-113">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]  
  
 <span data-ttu-id="90123-114">Jeśli zdefiniujesz metody rodzajowej, która przyjmuje te same parametry typu jako klasa zawierająca, kompilator generuje ostrzeżenie CS0693, ponieważ w zakresie metody argument podany dla wewnętrzny `T` ukrywa argument podany dla zewnętrznego `T`.</span><span class="sxs-lookup"><span data-stu-id="90123-114">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning CS0693 because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="90123-115">Jeśli wymagana jest elastyczność wywoływania metody rodzajowej klasy z argumentami typu innych niż podany przy wywołaniu metody wystąpienia klasy, rozważ podanie inny identyfikator dla parametru typu metody, jak pokazano na `GenericList2<T>` poniżej przykład.</span><span class="sxs-lookup"><span data-stu-id="90123-115">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]  
  
 <span data-ttu-id="90123-116">Użyj ograniczeń, aby włączyć bardziej wyspecjalizowane operacje dotyczące parametrów typu w metodzie.</span><span class="sxs-lookup"><span data-stu-id="90123-116">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="90123-117">Ta wersja `Swap<T>`teraz nazwanego `SwapIfGreater<T>`, należy używać tylko z argumentami typu, które implementują <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="90123-117">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]  
  
 <span data-ttu-id="90123-118">Metody ogólne mogą być przeciążane na kilka parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="90123-118">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="90123-119">Na przykład następujące metody mogą wszystkie znajdować się w tej samej klasy:</span><span class="sxs-lookup"><span data-stu-id="90123-119">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="90123-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="90123-120">C# Language Specification</span></span>  
 <span data-ttu-id="90123-121">Aby uzyskać więcej informacji, zobacz [Specyfikacja języka C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="90123-121">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90123-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90123-122">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="90123-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="90123-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="90123-124">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="90123-124">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [<span data-ttu-id="90123-125">Metody</span><span class="sxs-lookup"><span data-stu-id="90123-125">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
