---
title: "as (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4f2964f32a4139ffeb6d51b761f1176a57c5be6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="as-c-reference"></a><span data-ttu-id="3ab97-102">as (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3ab97-102">as (C# Reference)</span></span>
<span data-ttu-id="3ab97-103">Można użyć `as` operator do wykonania niektórych typów konwersji między typami zgodne odwołanie lub [typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="3ab97-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="3ab97-104">Poniższy kod przedstawia przykład.</span><span class="sxs-lookup"><span data-stu-id="3ab97-104">The following code shows an example.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="3ab97-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ab97-105">Remarks</span></span>  
 <span data-ttu-id="3ab97-106">`as` Operator przypomina operacji rzutowania.</span><span class="sxs-lookup"><span data-stu-id="3ab97-106">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="3ab97-107">Jednak jeśli konwersja nie jest możliwe, `as` zwraca `null` zamiast generowanie wyjątków.</span><span class="sxs-lookup"><span data-stu-id="3ab97-107">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="3ab97-108">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="3ab97-108">Consider the following example:</span></span>  
  
```  
expression as type  
```  
  
 <span data-ttu-id="3ab97-109">Kod jest odpowiednikiem następującego wyrażenia z wyjątkiem `expression` zmiennej jest oceniane tylko jeden raz.</span><span class="sxs-lookup"><span data-stu-id="3ab97-109">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="3ab97-110">Należy pamiętać, że `as` operator wykonuje konwersji odwołania, konwersji wartości null i konwersje boxing.</span><span class="sxs-lookup"><span data-stu-id="3ab97-110">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="3ab97-111">`as` Operatora nie można wykonać innych konwersji, takich jak konwersje zdefiniowane przez użytkownika, których należy zamiast tego można wykonać za pomocą wyrażenia rzutowania.</span><span class="sxs-lookup"><span data-stu-id="3ab97-111">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ab97-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ab97-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="3ab97-113">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3ab97-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3ab97-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ab97-114">See Also</span></span>  
 [<span data-ttu-id="3ab97-115">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="3ab97-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3ab97-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3ab97-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3ab97-117">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="3ab97-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3ab97-118">jest</span><span class="sxs-lookup"><span data-stu-id="3ab97-118">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="3ab97-119">?: — Operator</span><span class="sxs-lookup"><span data-stu-id="3ab97-119">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
 [<span data-ttu-id="3ab97-120">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="3ab97-120">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
