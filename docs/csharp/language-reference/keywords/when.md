---
title: gdy kontekstowego słowa kluczowego - C# odwołania
ms.custom: seodec18
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: a8f64da0ab603830972035f1c2cd3a0b1eaadaff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660219"
---
# <a name="when-c-reference"></a><span data-ttu-id="66893-102">gdy (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="66893-102">when (C# Reference)</span></span>

<span data-ttu-id="66893-103">Możesz użyć `when` kontekstowe słowo kluczowe, aby określić warunek filtru w dwóch kontekstów:</span><span class="sxs-lookup"><span data-stu-id="66893-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="66893-104">W `catch` instrukcja [bloku try/catch](try-catch.md) lub [try/catch/finally](try-catch-finally.md) bloku.</span><span class="sxs-lookup"><span data-stu-id="66893-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="66893-105">W `case` etykieta [Przełącz](switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="66893-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="66893-106">`when` w `catch` — instrukcja</span><span class="sxs-lookup"><span data-stu-id="66893-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="66893-107">Począwszy od C# 6, `when` mogą być używane w `catch` instrukcję, aby określić warunek, który musi mieć wartość true dla programu obsługi dla określonego wyjątku do wykonania.</span><span class="sxs-lookup"><span data-stu-id="66893-107">Starting with C# 6, `when` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="66893-108">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="66893-108">Its syntax is:</span></span>

```csharp
catch (ExceptionType [e]) when (expr)
```

<span data-ttu-id="66893-109">gdzie *expr* jest wyrażeniem, którego wynikiem jest wartość typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="66893-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="66893-110">Jeśli zostanie zwrócona `true`, uruchamia program obsługi wyjątku; Jeśli `false`, nie ma.</span><span class="sxs-lookup"><span data-stu-id="66893-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span>

<span data-ttu-id="66893-111">W poniższym przykładzie użyto `when` — słowo kluczowe warunkowo wykonanie procedury obsługi dla <xref:System.Net.Http.HttpRequestException> w zależności od tekstu komunikat o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="66893-111">The following example uses the `when` keyword to conditionally execute handlers for an <xref:System.Net.Http.HttpRequestException> depending on the text of the exception message.</span></span>

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a><span data-ttu-id="66893-112">`when` w `switch` — instrukcja</span><span class="sxs-lookup"><span data-stu-id="66893-112">`when` in a `switch` statement</span></span>

<span data-ttu-id="66893-113">Począwszy od C# 7.0, `case` etykiety już nie muszą być wzajemnie wyłącznie i kolejność, w której `case` etykiety pojawiają się w `switch` instrukcji można określić, które blok "switch" wykonuje.</span><span class="sxs-lookup"><span data-stu-id="66893-113">Starting with C# 7.0, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="66893-114">`when` — Słowo kluczowe może służyć do określania warunku filtru, który powoduje, że jego skojarzony etykiety case PRAWDA, tylko wtedy, gdy warunek filtru jest również wartość true.</span><span class="sxs-lookup"><span data-stu-id="66893-114">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="66893-115">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="66893-115">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```

<span data-ttu-id="66893-116">gdzie *expr* wzór stałej lub wzorzec typ, który jest porównywany z wyrażenie dopasowania i *kiedy warunek* jest dowolne wyrażenie logiczne.</span><span class="sxs-lookup"><span data-stu-id="66893-116">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span>

<span data-ttu-id="66893-117">W poniższym przykładzie użyto `when` — słowo kluczowe do testowania `Shape` obiektów, które mają obszar o wartości zero, a także do testowania różnych `Shape` obiektów, które mają obszar jest większy od zera.</span><span class="sxs-lookup"><span data-stu-id="66893-117">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span>

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a><span data-ttu-id="66893-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66893-118">See also</span></span>

- [<span data-ttu-id="66893-119">Switch — instrukcja</span><span class="sxs-lookup"><span data-stu-id="66893-119">switch statement</span></span>](switch.md)
- [<span data-ttu-id="66893-120">Instrukcja try/catch</span><span class="sxs-lookup"><span data-stu-id="66893-120">try/catch statement</span></span>](try-catch.md)
- [<span data-ttu-id="66893-121">instrukcji try/catch/finally</span><span class="sxs-lookup"><span data-stu-id="66893-121">try/catch/finally statement</span></span>](try-catch-finally.md)