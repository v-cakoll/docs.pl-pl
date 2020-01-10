---
title: gdy kontekstowe słowo C# kluczowe-odwołanie
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 6a61c42ba2d01e84ffae376bf95c99877437be85
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712835"
---
# <a name="when-c-reference"></a><span data-ttu-id="be2ae-102">When (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="be2ae-102">when (C# Reference)</span></span>

<span data-ttu-id="be2ae-103">Możesz użyć słowa kluczowego `when` kontekstowego, aby określić warunek filtru w dwóch kontekstach:</span><span class="sxs-lookup"><span data-stu-id="be2ae-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="be2ae-104">W instrukcji `catch` bloku [try/catch](try-catch.md) lub [try/catch/finally](try-catch-finally.md) .</span><span class="sxs-lookup"><span data-stu-id="be2ae-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="be2ae-105">W etykiecie `case` instrukcji [Switch](switch.md) .</span><span class="sxs-lookup"><span data-stu-id="be2ae-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="be2ae-106">`when` w instrukcji `catch`</span><span class="sxs-lookup"><span data-stu-id="be2ae-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="be2ae-107">Począwszy od C# 6, `when` może być użyty w instrukcji `catch`, aby określić warunek, który musi mieć wartość true dla programu obsługi określonego wyjątku do wykonania.</span><span class="sxs-lookup"><span data-stu-id="be2ae-107">Starting with C# 6, `when` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="be2ae-108">Jego składnia to:</span><span class="sxs-lookup"><span data-stu-id="be2ae-108">Its syntax is:</span></span>

```csharp
catch (ExceptionType [e]) when (expr)
```

<span data-ttu-id="be2ae-109">gdzie *Expr* jest wyrażeniem, którego wynikiem jest wartość logiczna.</span><span class="sxs-lookup"><span data-stu-id="be2ae-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="be2ae-110">Jeśli zwróci `true`, program obsługi wyjątków zostanie wykonany; Jeśli `false`, nie jest.</span><span class="sxs-lookup"><span data-stu-id="be2ae-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span>

<span data-ttu-id="be2ae-111">Poniższy przykład używa słowa kluczowego `when`, aby warunkowo wykonywać procedury obsługi dla <xref:System.Net.Http.HttpRequestException> w zależności od tekstu komunikatu o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="be2ae-111">The following example uses the `when` keyword to conditionally execute handlers for an <xref:System.Net.Http.HttpRequestException> depending on the text of the exception message.</span></span>

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a><span data-ttu-id="be2ae-112">`when` w instrukcji `switch`</span><span class="sxs-lookup"><span data-stu-id="be2ae-112">`when` in a `switch` statement</span></span>

<span data-ttu-id="be2ae-113">Począwszy od C# 7,0, etykiety `case` nie muszą już być wykluczane wzajemnie, a kolejność, w której `case` etykiety pojawiają się w instrukcji `switch` może ustalić, który blok przełącznika jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="be2ae-113">Starting with C# 7.0, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="be2ae-114">Za pomocą słowa kluczowego `when` można określić warunek filtru, który powoduje, że skojarzona z nim etykieta Case ma wartość true tylko wtedy, gdy warunek filtru ma również wartość true.</span><span class="sxs-lookup"><span data-stu-id="be2ae-114">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="be2ae-115">Jego składnia to:</span><span class="sxs-lookup"><span data-stu-id="be2ae-115">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```

<span data-ttu-id="be2ae-116">gdzie *Expr* jest wzorcem stałej lub wzorcem typu, który jest porównywany z wyrażeniem Match, a *warunek when* jest dowolnym wyrażeniem logicznym.</span><span class="sxs-lookup"><span data-stu-id="be2ae-116">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span>

<span data-ttu-id="be2ae-117">Poniższy przykład używa słowa kluczowego `when` do testowania `Shape` obiektów, które mają powierzchnię zero, a także do testowania dla różnych `Shape` obiektów, które mają obszar większy niż zero.</span><span class="sxs-lookup"><span data-stu-id="be2ae-117">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span>

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a><span data-ttu-id="be2ae-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be2ae-118">See also</span></span>

- [<span data-ttu-id="be2ae-119">Switch, instrukcja</span><span class="sxs-lookup"><span data-stu-id="be2ae-119">switch statement</span></span>](switch.md)
- [<span data-ttu-id="be2ae-120">Instrukcja try/catch</span><span class="sxs-lookup"><span data-stu-id="be2ae-120">try/catch statement</span></span>](try-catch.md)
- [<span data-ttu-id="be2ae-121">Instrukcja try/catch/finally</span><span class="sxs-lookup"><span data-stu-id="be2ae-121">try/catch/finally statement</span></span>](try-catch-finally.md)
