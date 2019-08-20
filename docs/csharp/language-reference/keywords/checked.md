---
title: Checked słowo kluczowe C# -odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 69bd8cc95012533a6be279b04dc883a56f6f78ea
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605913"
---
# <a name="checked-c-reference"></a><span data-ttu-id="edaf1-102">checked (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="edaf1-102">checked (C# Reference)</span></span>

<span data-ttu-id="edaf1-103">`checked` Słowo kluczowe jest używane do jawnego włączania sprawdzania przepełnienia dla operacji arytmetycznych i konwersji typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="edaf1-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="edaf1-104">Domyślnie wyrażenie zawierające tylko stałe wartości powoduje błąd kompilatora, jeśli wyrażenie generuje wartość spoza zakresu typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="edaf1-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="edaf1-105">Jeśli wyrażenie zawiera jedną lub więcej wartości niestałych, kompilator nie wykrywa przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="edaf1-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="edaf1-106">Obliczenie wyrażenia przypisanego do `i2` w poniższym przykładzie nie powoduje błędu kompilatora.</span><span class="sxs-lookup"><span data-stu-id="edaf1-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

<span data-ttu-id="edaf1-107">Domyślnie te wyrażenia niestałe nie są sprawdzane w celu przepełnienia w czasie wykonywania i nie powodują wyjątków przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="edaf1-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="edaf1-108">W poprzednim przykładzie przedstawiono wartość-2 147 483 639 jako sumę dwóch dodatnich liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="edaf1-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>

<span data-ttu-id="edaf1-109">Sprawdzanie przepełnienia można włączyć przez opcje kompilatora, konfigurację środowiska lub użycie `checked` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="edaf1-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="edaf1-110">W poniższych przykładach pokazano, jak używać `checked` wyrażenia `checked` lub bloku do wykrywania przepełnienia, który jest generowany przez poprzednią sumę w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="edaf1-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="edaf1-111">Oba przykłady powodują wyjątek przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="edaf1-111">Both examples raise an overflow exception.</span></span>

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

<span data-ttu-id="edaf1-112">[Niesprawdzone](./unchecked.md) słowo kluczowe może służyć do zapobiegania sprawdzaniu przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="edaf1-112">The [unchecked](./unchecked.md) keyword can be used to prevent overflow checking.</span></span>

## <a name="example"></a><span data-ttu-id="edaf1-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="edaf1-113">Example</span></span>

<span data-ttu-id="edaf1-114">Ten przykład pokazuje, jak używać `checked` do włączania sprawdzania przepełnienia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="edaf1-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="edaf1-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="edaf1-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="edaf1-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="edaf1-116">See also</span></span>

- [<span data-ttu-id="edaf1-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="edaf1-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="edaf1-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="edaf1-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="edaf1-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="edaf1-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="edaf1-120">Checked i Unchecked</span><span class="sxs-lookup"><span data-stu-id="edaf1-120">Checked and Unchecked</span></span>](./checked-and-unchecked.md)
- [<span data-ttu-id="edaf1-121">unchecked</span><span class="sxs-lookup"><span data-stu-id="edaf1-121">unchecked</span></span>](./unchecked.md)
