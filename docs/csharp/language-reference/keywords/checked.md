---
title: zaznaczone — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 5ce9291fd047dfa9c69048887ccbd878819f2de8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662015"
---
# <a name="checked-c-reference"></a><span data-ttu-id="11cb3-102">checked (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="11cb3-102">checked (C# Reference)</span></span>

<span data-ttu-id="11cb3-103">`checked` Słowo kluczowe jest używane, aby jawnie włączyć sprawdzanie typu całkowitego operacjach arytmetycznych i konwersjach przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="11cb3-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="11cb3-104">Domyślnie wyrażenie, które zawiera tylko wartości stałych powoduje błąd kompilatora, jeśli wyrażenie generują wartość, która znajduje się poza zakresem typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="11cb3-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="11cb3-105">Jeśli wyrażenie zawiera co najmniej jedną wartość niebędącą stałą, kompilator nie może wykryć przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="11cb3-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="11cb3-106">Obliczenie wyrażenia przypisane do `i2` w poniższym przykładzie nie powoduje błędu kompilatora.</span><span class="sxs-lookup"><span data-stu-id="11cb3-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

<span data-ttu-id="11cb3-107">Domyślnie te wyrażenia niestałe nie są sprawdzane na przepełnienie w czasie wykonywania albo, a nie zgłaszaj wyjątków przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="11cb3-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="11cb3-108">Poprzedni przykład wyświetla-2,147,483,639 jako suma dwie dodatnie liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="11cb3-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>

<span data-ttu-id="11cb3-109">Sprawdzanie przepełnienia może włączyć opcje kompilatora, konfiguracji środowiska i użyciem `checked` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="11cb3-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="11cb3-110">W poniższych przykładach pokazano sposób użycia `checked` wyrażenie lub `checked` bloku, aby wykryć przepełnienia, który jest wytwarzany przez poprzednie sum w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="11cb3-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="11cb3-111">Oba przykłady zgłosić wyjątek przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="11cb3-111">Both examples raise an overflow exception.</span></span>

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

<span data-ttu-id="11cb3-112">[Unchecked](../../../csharp/language-reference/keywords/unchecked.md) — słowo kluczowe może służyć do uniemożliwić sprawdzanie przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="11cb3-112">The [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword can be used to prevent overflow checking.</span></span>

## <a name="example"></a><span data-ttu-id="11cb3-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="11cb3-113">Example</span></span>

<span data-ttu-id="11cb3-114">Ten przykład ilustruje sposób używania `checked` umożliwiające przepełnienie sprawdzanie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="11cb3-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="11cb3-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="11cb3-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="11cb3-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11cb3-116">See also</span></span>

- [<span data-ttu-id="11cb3-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="11cb3-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="11cb3-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="11cb3-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="11cb3-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="11cb3-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="11cb3-120">Checked i Unchecked</span><span class="sxs-lookup"><span data-stu-id="11cb3-120">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)
- [<span data-ttu-id="11cb3-121">unchecked</span><span class="sxs-lookup"><span data-stu-id="11cb3-121">unchecked</span></span>](../../../csharp/language-reference/keywords/unchecked.md)
