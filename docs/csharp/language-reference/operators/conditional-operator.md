---
title: '?: — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 3e45ff6eaaefa5829c3ed9415abe1a12b7a1d069
ms.sourcegitcommit: 4bca8f7e172fd019ef437a4803bf5895c6bc4781
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2018
ms.locfileid: "50980625"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a4108-102">?: — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a4108-102">?: Operator (C# Reference)</span></span>

<span data-ttu-id="a4108-103">Operator warunkowy (`?:`), powszechnie znane jako trójargumentowy operator warunkowy zwraca jedną z dwóch wartości w zależności od wartości wyrażenia logicznego.</span><span class="sxs-lookup"><span data-stu-id="a4108-103">The conditional operator (`?:`), commonly known as the ternary conditional operator, returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="a4108-104">Poniżej przedstawiono składnię operatora warunkowego.</span><span class="sxs-lookup"><span data-stu-id="a4108-104">Following is the syntax for the conditional operator.</span></span>  

```csharp
condition ? first_expression : second_expression;  
```

<span data-ttu-id="a4108-105">Począwszy od C# 7.2, `first_expression` i `second_expression` Moje można [ `ref` wyrażeń](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md):</span><span class="sxs-lookup"><span data-stu-id="a4108-105">Beginning with C# 7.2, the `first_expression` and `second_expression` my be [`ref` expressions](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md):</span></span>

```csharp
ref condition ? ref first_expression : ref second_expression;  
```

<span data-ttu-id="a4108-106">Wynik może być przypisana do `ref` lub `ref readonly` zmiennej lub zmiennej za pomocą modyfikatora ani.</span><span class="sxs-lookup"><span data-stu-id="a4108-106">The result may be assigned to a `ref` or `ref readonly` variable, or to a variable with neither modifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="a4108-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a4108-107">Remarks</span></span>

<span data-ttu-id="a4108-108">`condition` Musi zwrócić `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="a4108-108">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="a4108-109">Jeśli `condition` jest `true`, `first_expression` jest obliczane i staje się wynik.</span><span class="sxs-lookup"><span data-stu-id="a4108-109">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="a4108-110">Jeśli `condition` jest `false`, `second_expression` jest obliczane i staje się wynik.</span><span class="sxs-lookup"><span data-stu-id="a4108-110">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="a4108-111">Obliczane jest tylko jedno z dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="a4108-111">Only one of the two expressions is evaluated.</span></span> <span data-ttu-id="a4108-112">Jest to szczególnie ważne dla wyrażeń, których wynikiem jest `ref`, ponieważ następujące jest prawidłowy:</span><span class="sxs-lookup"><span data-stu-id="a4108-112">This is particularly important for expressions where the result is a `ref`, as the following is valid:</span></span>

```csharp
ref (storage != null) ? ref storage[3] : ref defaultValue;
```

<span data-ttu-id="a4108-113">Odwołanie do `storage` nie jest oceniany, jeśli `storage` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="a4108-113">The reference to `storage` is not evaluated when `storage` is null.</span></span>

<span data-ttu-id="a4108-114">Gdy wynik jest wartością typu `first_expression` i `second_expression` musi być w tej samej lub występują musi być niejawna konwersja z jednego typu na drugi.</span><span class="sxs-lookup"><span data-stu-id="a4108-114">When the result is a value, the type of `first_expression` and `second_expression` must be the same, or there must be an implicit conversion from one type to the other.</span></span> <span data-ttu-id="a4108-115">Jeśli wynik jest `ref`, typ `first_expression` i `second_expression` musi być taka sama.</span><span class="sxs-lookup"><span data-stu-id="a4108-115">When the result is a `ref`, the type of `first_expression` and `second_expression` must be the same.</span></span>

<span data-ttu-id="a4108-116">Można wyrazić obliczenia, które w przeciwnym razie może wymagać `if-else` konstruowania bardziej zwięzłym, używając operatora warunkowego.</span><span class="sxs-lookup"><span data-stu-id="a4108-116">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="a4108-117">Na przykład w poniższym kodzie użyto najpierw `if` instrukcji, a następnie operator warunkowy w celu zaklasyfikowania liczby całkowitej jako dodatnia lub ujemna.</span><span class="sxs-lookup"><span data-stu-id="a4108-117">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>

```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```

<span data-ttu-id="a4108-118">Operator warunkowy ma łączność do prawej strony.</span><span class="sxs-lookup"><span data-stu-id="a4108-118">The conditional operator is right-associative.</span></span> <span data-ttu-id="a4108-119">Wyrażenie `a ? b : c ? d : e` jest oceniane jako `a ? b : (c ? d : e)`, nie jako `(a ? b : c) ? d : e`.</span><span class="sxs-lookup"><span data-stu-id="a4108-119">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
<span data-ttu-id="a4108-120">Operatorów warunkowych nie można przeciążać.</span><span class="sxs-lookup"><span data-stu-id="a4108-120">The conditional operator cannot be overloaded.</span></span>
  
## <a name="example"></a><span data-ttu-id="a4108-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="a4108-121">Example</span></span>

<span data-ttu-id="a4108-122">Operator warunkowy, którego wynikiem jest wartość można znaleźć w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a4108-122">The following example shows the conditional operator whose result is a value:</span></span>

[!code-csharp[csRefOperators?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

<span data-ttu-id="a4108-123">Alternatywne pokazuje operatora warunkowego, gdy wynik jest odwołaniem:</span><span class="sxs-lookup"><span data-stu-id="a4108-123">The following alternative shows the conditional operator where the result is a reference:</span></span>

[!code-csharp[csRefOperatorsRef?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

## <a name="see-also"></a><span data-ttu-id="a4108-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4108-124">See Also</span></span>

- [<span data-ttu-id="a4108-125">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a4108-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a4108-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a4108-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a4108-127">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="a4108-127">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="a4108-128">if-else</span><span class="sxs-lookup"><span data-stu-id="a4108-128">if-else</span></span>](../../../csharp/language-reference/keywords/if-else.md)  
- <span data-ttu-id="a4108-129">[Operatory ?. i ?[]](../../../csharp/language-reference/operators/null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="a4108-129">[?. and ?[] Operators](../../../csharp/language-reference/operators/null-conditional-operators.md)</span></span>  
- [<span data-ttu-id="a4108-130">??, operator</span><span class="sxs-lookup"><span data-stu-id="a4108-130">?? Operator</span></span>](../../../csharp/language-reference/operators/null-coalescing-operator.md)
