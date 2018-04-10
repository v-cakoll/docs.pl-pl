---
title: gdy (odwołanie w C#)
ms.date: 03/07/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f453d9f4b443d7adeeb0ab628b4ddad1a0116e49
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
 # <a name="when-c-reference"></a><span data-ttu-id="9238a-102">gdy (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9238a-102">when (C# Reference)</span></span>

<span data-ttu-id="9238a-103">Można użyć `when` kontekstowe słowo kluczowe do określenia warunku filtru w dwóch kontekstów:</span><span class="sxs-lookup"><span data-stu-id="9238a-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="9238a-104">W `catch` instrukcja [bloku try/catch](try-catch.md) lub [try/catch/finally](try-catch-finally.md) bloku.</span><span class="sxs-lookup"><span data-stu-id="9238a-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="9238a-105">W `case` etykietę [przełącznika](switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9238a-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="9238a-106">`when`w `catch` — instrukcja</span><span class="sxs-lookup"><span data-stu-id="9238a-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="9238a-107">Począwszy od języka C# 6, `When` mogą być używane w `catch` instrukcji do określenia warunku, który musi mieć wartość true dla programu obsługi dla określonego wyjątku do wykonania.</span><span class="sxs-lookup"><span data-stu-id="9238a-107">Starting with C# 6, `When` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="9238a-108">Składnia to:</span><span class="sxs-lookup"><span data-stu-id="9238a-108">Its syntax is:</span></span>

```csharp
catch ExceptionType [e] when (expr)
```
<span data-ttu-id="9238a-109">gdzie *wyrażenie* to wyrażenie, którego wynikiem jest wartość logiczna.</span><span class="sxs-lookup"><span data-stu-id="9238a-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="9238a-110">Jeśli zmienna zwraca `true`, obsługa wyjątków wykonuje; Jeśli `false`, nie ma.</span><span class="sxs-lookup"><span data-stu-id="9238a-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span> 

<span data-ttu-id="9238a-111">W poniższym przykładzie użyto `when` — słowo kluczowe warunkowo wykonać obsługi <xref:System.Net.Http.HttpRequestException> w zależności od tekst komunikat o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="9238a-111">The following example uses the `when` keyword to conditionally execute handlers for an <xref:System.Net.Http.HttpRequestException> depending on the text of the exception message.</span></span>

 [!code-csharp[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]  
  
## <a name="when-in-a-switch-statement"></a><span data-ttu-id="9238a-112">`when`w `switch` — instrukcja</span><span class="sxs-lookup"><span data-stu-id="9238a-112">`when` in a `switch` statement</span></span>

<span data-ttu-id="9238a-113">Począwszy od 7, `case` etykiety już muszą być wykluczają się wzajemnie, a w kolejności `case` etykiety są wyświetlane w `switch` instrukcji można określić, który blok przełącznika wykonuje.</span><span class="sxs-lookup"><span data-stu-id="9238a-113">Starting with 7, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="9238a-114">`when` — Słowo kluczowe może służyć do określenia warunku filtru, który powoduje, że jego skojarzony etykiety case mieć wartość true tylko wtedy, gdy warunek filtru również ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="9238a-114">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="9238a-115">Składnia to:</span><span class="sxs-lookup"><span data-stu-id="9238a-115">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```
<span data-ttu-id="9238a-116">gdzie *wyrażenie* jest stałe wzorzec lub wzorzec typu, który jest porównywany wyrażenie dopasowania i *warunek when* jest wyrażenia logicznego.</span><span class="sxs-lookup"><span data-stu-id="9238a-116">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span> 

<span data-ttu-id="9238a-117">W poniższym przykładzie użyto `when` — słowo kluczowe w celu zbadania `Shape` obiektów, które mają obszar zero, a także aby przetestować dla różnych `Shape` obiektów, które mają obszar większa od zera.</span><span class="sxs-lookup"><span data-stu-id="9238a-117">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span> 

 [!code-csharp[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]  

## <a name="see-also"></a><span data-ttu-id="9238a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9238a-118">See also</span></span> 
  [<span data-ttu-id="9238a-119">Switch — instrukcja</span><span class="sxs-lookup"><span data-stu-id="9238a-119">switch statement</span></span>](switch.md)  
  [<span data-ttu-id="9238a-120">try/catch — instrukcja</span><span class="sxs-lookup"><span data-stu-id="9238a-120">try/catch statement</span></span>](try-catch.md)  
  [<span data-ttu-id="9238a-121">instrukcji try/catch/finally</span><span class="sxs-lookup"><span data-stu-id="9238a-121">try/catch/finally statement</span></span>](try-catch-finally.md) 

