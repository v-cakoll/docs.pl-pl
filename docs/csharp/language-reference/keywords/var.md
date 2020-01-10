---
title: WARIANCJA C# — odwołanie
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: ff8348a725f43fa8789c73fa58549da26126369c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712887"
---
# <a name="var-c-reference"></a><span data-ttu-id="73647-102">var (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="73647-102">var (C# Reference)</span></span>

<span data-ttu-id="73647-103">Począwszy od programu C# Visual 3,0, zmienne, które są zadeklarowane w zakresie metody, mogą mieć niejawny "typ" `var`.</span><span class="sxs-lookup"><span data-stu-id="73647-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="73647-104">Niejawnie wpisana zmienna lokalna jest silnie wpisana, tak jakby zadeklarowano typ samodzielnie, ale kompilator określa typ.</span><span class="sxs-lookup"><span data-stu-id="73647-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="73647-105">Następujące dwie deklaracje `i` są funkcjonalnie równoważne:</span><span class="sxs-lookup"><span data-stu-id="73647-105">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

<span data-ttu-id="73647-106">Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) i [relacje typu w operacjach zapytań LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="73647-106">For more information, see [Implicitly Typed Local Variables](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="73647-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="73647-107">Example</span></span>

<span data-ttu-id="73647-108">Poniższy przykład przedstawia dwa wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="73647-108">The following example shows two query expressions.</span></span> <span data-ttu-id="73647-109">W pierwszym wyrażeniu użycie `var` jest dozwolone, ale nie jest wymagane, ponieważ typ wyniku zapytania można jawnie określić jako `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="73647-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="73647-110">Jednak w drugim wyrażeniu `var` zezwala na zbieranie anonimowych typów, a nazwa tego typu jest niedostępna z wyjątkiem samego kompilatora.</span><span class="sxs-lookup"><span data-stu-id="73647-110">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="73647-111">Użycie `var` eliminuje wymóg tworzenia nowej klasy dla wyniku.</span><span class="sxs-lookup"><span data-stu-id="73647-111">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="73647-112">Należy zauważyć, że w przykładzie #2 Zmienna iteracji `foreach` `item` musi również być wpisana niejawnie.</span><span class="sxs-lookup"><span data-stu-id="73647-112">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="73647-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73647-113">See also</span></span>

- [<span data-ttu-id="73647-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="73647-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="73647-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="73647-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="73647-116">Jawnie wpisane zmienne lokalne</span><span class="sxs-lookup"><span data-stu-id="73647-116">Implicitly Typed Local Variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
