---
title: as (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: aee80b3262ccd9432d7c311dddec47185b66d05f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45648397"
---
# <a name="as-c-reference"></a><span data-ttu-id="74589-102">as (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="74589-102">as (C# Reference)</span></span>
<span data-ttu-id="74589-103">Możesz użyć `as` operator pod kątem niektórych typów konwersje między typami zgodne odwołanie lub [typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="74589-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="74589-104">Poniższy kod przedstawia przykład.</span><span class="sxs-lookup"><span data-stu-id="74589-104">The following code shows an example.</span></span>  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]
  
## <a name="remarks"></a><span data-ttu-id="74589-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="74589-105">Remarks</span></span>  
 <span data-ttu-id="74589-106">`as` Operator przypomina operacji rzutowania.</span><span class="sxs-lookup"><span data-stu-id="74589-106">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="74589-107">Jednakże, jeśli konwersja nie jest możliwe, `as` zwraca `null` zamiast zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="74589-107">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="74589-108">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="74589-108">Consider the following example:</span></span>  
  
```csharp  
expression as type  
```  
  
 <span data-ttu-id="74589-109">Kod jest odpowiednikiem następujące wyrażenie, chyba że `expression` zmienna jest oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="74589-109">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="74589-110">Należy pamiętać, że `as` operator wykonuje konwersje odwołań, konwersje dopuszcza wartości null i opakowywanie konwersji.</span><span class="sxs-lookup"><span data-stu-id="74589-110">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="74589-111">`as` Operator nie może wykonywać inne konwersji, takie jak konwersje zdefiniowane przez użytkownika, które należy zamiast tego przeprowadzić za pomocą wyrażenia cast.</span><span class="sxs-lookup"><span data-stu-id="74589-111">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74589-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="74589-112">Example</span></span>  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a><span data-ttu-id="74589-113">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="74589-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="74589-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74589-114">See Also</span></span>  
- [<span data-ttu-id="74589-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="74589-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="74589-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="74589-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="74589-117">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="74589-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="74589-118">is</span><span class="sxs-lookup"><span data-stu-id="74589-118">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
- [<span data-ttu-id="74589-119">?:, operator</span><span class="sxs-lookup"><span data-stu-id="74589-119">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
- [<span data-ttu-id="74589-120">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="74589-120">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
