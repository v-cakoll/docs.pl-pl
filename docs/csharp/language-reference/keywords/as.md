---
title: jak - C# odwołania
ms.custom: seodec18
ms.date: 10/11/2018
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: 84e599340877ce52dc6242ea259c69672915c546
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422019"
---
# <a name="as-c-reference"></a><span data-ttu-id="84886-102">as (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="84886-102">as (C# Reference)</span></span>
<span data-ttu-id="84886-103">Możesz użyć `as` operator pod kątem niektórych typów konwersje między typami zgodne odwołanie lub [typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="84886-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="84886-104">Poniższy kod przedstawia przykład.</span><span class="sxs-lookup"><span data-stu-id="84886-104">The following code shows an example.</span></span>  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]

<span data-ttu-id="84886-105">Jak pokazano w przykładzie, należy porównać wynik `as` wyrażenie `null` do sprawdzenia, jeśli konwersja zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="84886-105">As the example shows, you need to compare the result of the `as` expression with `null` to check if a conversion is successful.</span></span> <span data-ttu-id="84886-106">Począwszy od języka C# 7.0, można użyć [jest](is.md) wyrażenie zarówno do testowania, że konwersja powiedzie się i warunkowo przypisać zmiennej po pomyślnym zakończeniu konwersji.</span><span class="sxs-lookup"><span data-stu-id="84886-106">Beginning with C# 7.0, you can use the [is](is.md) expression both to test that a conversion succeeds and conditionally assign a variable when the conversion succeeds.</span></span> <span data-ttu-id="84886-107">W wielu scenariuszach, jest bardziej zwięzłe niż przy użyciu `as` operatora.</span><span class="sxs-lookup"><span data-stu-id="84886-107">In many scenarios, it's more concise than using the `as` operator.</span></span> <span data-ttu-id="84886-108">Aby uzyskać więcej informacji, zobacz [wpisz wzór](is.md#type) części [ `is` operator](is.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="84886-108">For more information, see the [Type pattern](is.md#type) section of the [`is` operator](is.md) article.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="84886-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84886-109">Remarks</span></span>  
 <span data-ttu-id="84886-110">`as` Operator przypomina operacji rzutowania.</span><span class="sxs-lookup"><span data-stu-id="84886-110">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="84886-111">Jednakże, jeśli konwersja nie jest możliwe, `as` zwraca `null` zamiast zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="84886-111">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="84886-112">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="84886-112">Consider the following example:</span></span>  
  
```csharp  
expression as type  
```  
  
 <span data-ttu-id="84886-113">Kod jest odpowiednikiem następujące wyrażenie, chyba że `expression` zmienna jest oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="84886-113">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="84886-114">Należy pamiętać, że `as` operator wykonuje konwersje odwołań, konwersje dopuszcza wartości null i opakowywanie konwersji.</span><span class="sxs-lookup"><span data-stu-id="84886-114">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="84886-115">`as` Operator nie może wykonywać inne konwersji, takie jak konwersje zdefiniowane przez użytkownika, które należy zamiast tego przeprowadzić za pomocą wyrażenia cast.</span><span class="sxs-lookup"><span data-stu-id="84886-115">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84886-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="84886-116">Example</span></span>  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a><span data-ttu-id="84886-117">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="84886-117">C# Language Specification</span></span>  

<span data-ttu-id="84886-118">Aby uzyskać więcej informacji, zobacz [jako operator](~/_csharplang/spec/expressions.md#the-as-operator) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="84886-118">For more information, see [The as operator](~/_csharplang/spec/expressions.md#the-as-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="84886-119">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="84886-119">The language specification is the definitive source for C# syntax and usage.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="84886-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84886-120">See also</span></span>

- [<span data-ttu-id="84886-121">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="84886-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="84886-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="84886-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="84886-123">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="84886-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="84886-124">is</span><span class="sxs-lookup"><span data-stu-id="84886-124">is</span></span>](../../../csharp/language-reference/keywords/is.md)
- [<span data-ttu-id="84886-125">?: operator</span><span class="sxs-lookup"><span data-stu-id="84886-125">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)
