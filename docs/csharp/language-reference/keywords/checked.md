---
title: zaznaczone słowo kluczowe - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 5963bb85ef4b61c1dc478667fb0e2e5438f3e4ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713707"
---
# <a name="checked-c-reference"></a><span data-ttu-id="05158-102">checked (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="05158-102">checked (C# Reference)</span></span>

<span data-ttu-id="05158-103">Słowo `checked` kluczowe służy do jawnego włączania sprawdzania przepełnienia dla operacji arytmetycznych typu integralnego i konwersji.</span><span class="sxs-lookup"><span data-stu-id="05158-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="05158-104">Domyślnie wyrażenie, które zawiera tylko wartości stałe powoduje błąd kompilatora, jeśli wyrażenie tworzy wartość, która znajduje się poza zakresem typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="05158-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="05158-105">Jeśli wyrażenie zawiera co najmniej jedną niestałą wartość, kompilator nie wykrywa przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="05158-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="05158-106">Ocena wyrażenia przypisanego `i2` do w poniższym przykładzie nie powoduje błędu kompilatora.</span><span class="sxs-lookup"><span data-stu-id="05158-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

<span data-ttu-id="05158-107">Domyślnie te wyrażenia niestałe nie są sprawdzane pod kątem przepełnienia w czasie wykonywania i nie zgłaszają wyjątków przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="05158-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="05158-108">W poprzednim przykładzie jest wyświetlana wartość -2,147,483,639 jako suma dwóch dodatnich liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="05158-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>

<span data-ttu-id="05158-109">Sprawdzanie przepełnienia można włączyć za pomocą opcji kompilatora, konfiguracji środowiska lub użycia słowa kluczowego. `checked`</span><span class="sxs-lookup"><span data-stu-id="05158-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="05158-110">W poniższych przykładach pokazano, jak użyć `checked` wyrażenia lub `checked` bloku do wykrywania przepełnienia, który jest produkowany przez poprzednią sumę w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="05158-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="05158-111">Oba przykłady zgłaszają wyjątek przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="05158-111">Both examples raise an overflow exception.</span></span>

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

<span data-ttu-id="05158-112">[Niezaznaczone](./unchecked.md) słowo kluczowe może służyć do zapobiegania sprawdzaniu przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="05158-112">The [unchecked](./unchecked.md) keyword can be used to prevent overflow checking.</span></span>

## <a name="example"></a><span data-ttu-id="05158-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="05158-113">Example</span></span>

<span data-ttu-id="05158-114">W tym przykładzie `checked` pokazano, jak włączyć sprawdzanie przepełnienia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="05158-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="05158-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="05158-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="05158-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05158-116">See also</span></span>

- [<span data-ttu-id="05158-117">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="05158-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="05158-118">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="05158-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="05158-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="05158-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="05158-120">Checked i Unchecked</span><span class="sxs-lookup"><span data-stu-id="05158-120">Checked and Unchecked</span></span>](./checked-and-unchecked.md)
- [<span data-ttu-id="05158-121">unchecked</span><span class="sxs-lookup"><span data-stu-id="05158-121">unchecked</span></span>](./unchecked.md)
