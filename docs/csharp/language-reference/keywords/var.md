---
title: var - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: ff8348a725f43fa8789c73fa58549da26126369c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712887"
---
# <a name="var-c-reference"></a><span data-ttu-id="ef42a-102">var (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ef42a-102">var (C# Reference)</span></span>

<span data-ttu-id="ef42a-103">Począwszy od języka Visual C# 3.0 zmienne, które są zadeklarowane w zakresie metody może mieć niejawne "typ" `var`.</span><span class="sxs-lookup"><span data-stu-id="ef42a-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="ef42a-104">Niejawnie wpisane zmiennej lokalnej jest silnie wpisany tak, jakby zadeklarowano typ samodzielnie, ale kompilator określa typ.</span><span class="sxs-lookup"><span data-stu-id="ef42a-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="ef42a-105">Następujące dwie deklaracje `i` są funkcjonalnie równoważne:</span><span class="sxs-lookup"><span data-stu-id="ef42a-105">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

<span data-ttu-id="ef42a-106">Aby uzyskać więcej informacji, zobacz [Niejawnie wpisane zmienne lokalne](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) i [relacje typu w operacjach kwerend LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="ef42a-106">For more information, see [Implicitly Typed Local Variables](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="ef42a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef42a-107">Example</span></span>

<span data-ttu-id="ef42a-108">W poniższym przykładzie przedstawiono dwa wyrażenia kwerendy.</span><span class="sxs-lookup"><span data-stu-id="ef42a-108">The following example shows two query expressions.</span></span> <span data-ttu-id="ef42a-109">W pierwszym wyrażeniu `var` użycie jest dozwolone, ale nie jest wymagane, ponieważ typ wyniku `IEnumerable<string>`kwerendy można wyraźnie podać jako .</span><span class="sxs-lookup"><span data-stu-id="ef42a-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="ef42a-110">Jednak w drugim wyrażeniu `var` umożliwia wynik jest kolekcją typów anonimowych, a nazwa tego typu nie jest dostępna z wyjątkiem samego kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ef42a-110">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="ef42a-111">Użycie `var` eliminuje wymóg, aby utworzyć nową klasę dla wyniku.</span><span class="sxs-lookup"><span data-stu-id="ef42a-111">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="ef42a-112">Należy zauważyć, że `foreach` w przykładzie `item` #2 zmienna iteracji musi być również wpisywany niejawnie.</span><span class="sxs-lookup"><span data-stu-id="ef42a-112">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="ef42a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef42a-113">See also</span></span>

- [<span data-ttu-id="ef42a-114">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="ef42a-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ef42a-115">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="ef42a-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ef42a-116">Jawnie wpisana zmienna lokalna</span><span class="sxs-lookup"><span data-stu-id="ef42a-116">Implicitly Typed Local Variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
