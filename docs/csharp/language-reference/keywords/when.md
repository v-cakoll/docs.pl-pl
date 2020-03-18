---
title: gdy kontekstowe słowo kluczowe — odwołanie do języka C#
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 6a61c42ba2d01e84ffae376bf95c99877437be85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712835"
---
# <a name="when-c-reference"></a><span data-ttu-id="8e2df-102">kiedy (Odwołanie do Języka C#)</span><span class="sxs-lookup"><span data-stu-id="8e2df-102">when (C# Reference)</span></span>

<span data-ttu-id="8e2df-103">Można użyć `when` kontekstowesłowo kluczowe, aby określić warunek filtru w dwóch kontekstach:</span><span class="sxs-lookup"><span data-stu-id="8e2df-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="8e2df-104">W `catch` instrukcji [try/catch](try-catch.md) lub [try/catch/finally](try-catch-finally.md) bloku.</span><span class="sxs-lookup"><span data-stu-id="8e2df-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="8e2df-105">W `case` etykiecie [instrukcji switch.](switch.md)</span><span class="sxs-lookup"><span data-stu-id="8e2df-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="8e2df-106">`when`w `catch` oświadczeniu</span><span class="sxs-lookup"><span data-stu-id="8e2df-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="8e2df-107">Począwszy od języka `when` C# 6, może służyć w `catch` instrukcji, aby określić warunek, który musi być true dla programu obsługi dla określonego wyjątku do wykonania.</span><span class="sxs-lookup"><span data-stu-id="8e2df-107">Starting with C# 6, `when` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="8e2df-108">Jego składnia jest:</span><span class="sxs-lookup"><span data-stu-id="8e2df-108">Its syntax is:</span></span>

```csharp
catch (ExceptionType [e]) when (expr)
```

<span data-ttu-id="8e2df-109">gdzie *expr* jest wyrażeniem, które oblicza wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="8e2df-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="8e2df-110">Jeśli zwraca `true`, program obsługi wyjątków wykonuje; jeśli `false`, nie.</span><span class="sxs-lookup"><span data-stu-id="8e2df-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span>

<span data-ttu-id="8e2df-111">W poniższym `when` przykładzie użyto słowa kluczowego <xref:System.Net.Http.HttpRequestException> do warunkowo wykonywania programów obsługi dla w zależności od tekstu komunikatu o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="8e2df-111">The following example uses the `when` keyword to conditionally execute handlers for an <xref:System.Net.Http.HttpRequestException> depending on the text of the exception message.</span></span>

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a><span data-ttu-id="8e2df-112">`when`w `switch` oświadczeniu</span><span class="sxs-lookup"><span data-stu-id="8e2df-112">`when` in a `switch` statement</span></span>

<span data-ttu-id="8e2df-113">Począwszy od języka C# 7.0, etykiety nie muszą `case` się wzajemnie `switch` wykluczać, a kolejność, w jakiej etykiety pojawiają się w instrukcji można określić, `case` który blok przełącznika wykonuje.</span><span class="sxs-lookup"><span data-stu-id="8e2df-113">Starting with C# 7.0, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="8e2df-114">Słowo `when` kluczowe może służyć do określenia warunku filtru, który powoduje, że jego skojarzona etykieta sprawy jest true tylko wtedy, gdy warunek filtru jest również true.</span><span class="sxs-lookup"><span data-stu-id="8e2df-114">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="8e2df-115">Jego składnia jest:</span><span class="sxs-lookup"><span data-stu-id="8e2df-115">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```

<span data-ttu-id="8e2df-116">gdzie *expr* jest stały wzorzec lub wzorzec typu, który jest porównywany do wyrażenia dopasowania, a *gdy warunek* jest dowolne wyrażenie logiczne.</span><span class="sxs-lookup"><span data-stu-id="8e2df-116">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span>

<span data-ttu-id="8e2df-117">W poniższym `when` przykładzie użyto `Shape` słowa kluczowego do testowania obiektów, które mają `Shape` obszar zero, a także do testowania dla różnych obiektów, które mają obszar większy niż zero.</span><span class="sxs-lookup"><span data-stu-id="8e2df-117">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span>

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a><span data-ttu-id="8e2df-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e2df-118">See also</span></span>

- [<span data-ttu-id="8e2df-119">instrukcja switch</span><span class="sxs-lookup"><span data-stu-id="8e2df-119">switch statement</span></span>](switch.md)
- [<span data-ttu-id="8e2df-120">instrukcja try/catch</span><span class="sxs-lookup"><span data-stu-id="8e2df-120">try/catch statement</span></span>](try-catch.md)
- [<span data-ttu-id="8e2df-121">instrukcja try/catch/finally</span><span class="sxs-lookup"><span data-stu-id="8e2df-121">try/catch/finally statement</span></span>](try-catch-finally.md)
