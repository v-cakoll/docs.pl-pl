---
title: unchecked — C# odwołanie
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 6dad0dfd508fb390dd0a52d1b48d70b4c5725513
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713004"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="0ca8c-102">unchecked (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0ca8c-102">unchecked (C# Reference)</span></span>

<span data-ttu-id="0ca8c-103">Słowo kluczowe `unchecked` służy do pomijania sprawdzania przepełnienia dla operacji arytmetycznych i konwersji typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="0ca8c-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="0ca8c-104">W niesprawdzonym kontekście, jeśli wyrażenie generuje wartość spoza zakresu typu docelowego, przepełnienie nie jest oflagowane.</span><span class="sxs-lookup"><span data-stu-id="0ca8c-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="0ca8c-105">Na przykład, ponieważ obliczenia w poniższym przykładzie są wykonywane w bloku `unchecked` lub wyrażeniu, fakt, że wynik jest za duży dla liczby całkowitej, jest ignorowany, a `int1` ma przypisaną wartość-2 147 483 639.</span><span class="sxs-lookup"><span data-stu-id="0ca8c-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

<span data-ttu-id="0ca8c-106">Jeśli środowisko `unchecked` zostanie usunięte, wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0ca8c-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="0ca8c-107">Przepełnienie można wykryć w czasie kompilacji, ponieważ wszystkie warunki wyrażenia są stałymi.</span><span class="sxs-lookup"><span data-stu-id="0ca8c-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>

<span data-ttu-id="0ca8c-108">Wyrażenia zawierające warunki niestałe są domyślnie niezaznaczone w czasie kompilacji i w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0ca8c-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="0ca8c-109">Zobacz [zaewidencjonowano](checked.md) , aby uzyskać informacje na temat włączania sprawdzonego środowiska.</span><span class="sxs-lookup"><span data-stu-id="0ca8c-109">See [checked](checked.md) for information about enabling a checked environment.</span></span>

<span data-ttu-id="0ca8c-110">Ze względu na to, że sprawdzanie przepełnienia jest czasochłonne, użycie niesprawdzonego kodu w sytuacjach, gdy nie ma żadnych niebezpieczeństwa przepełnienia może zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="0ca8c-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="0ca8c-111">Jeśli jednak przepełnienie jest możliwe, należy użyć zaznaczonego środowiska.</span><span class="sxs-lookup"><span data-stu-id="0ca8c-111">However, if overflow is a possibility, a checked environment should be used.</span></span>

## <a name="example"></a><span data-ttu-id="0ca8c-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ca8c-112">Example</span></span>

<span data-ttu-id="0ca8c-113">Ten przykład pokazuje, jak używać słowa kluczowego `unchecked`.</span><span class="sxs-lookup"><span data-stu-id="0ca8c-113">This sample shows how to use the `unchecked` keyword.</span></span>

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="0ca8c-114">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0ca8c-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0ca8c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ca8c-115">See also</span></span>

- [<span data-ttu-id="0ca8c-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0ca8c-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0ca8c-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0ca8c-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0ca8c-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0ca8c-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0ca8c-119">Checked i Unchecked</span><span class="sxs-lookup"><span data-stu-id="0ca8c-119">Checked and Unchecked</span></span>](checked-and-unchecked.md)
- [<span data-ttu-id="0ca8c-120">checked</span><span class="sxs-lookup"><span data-stu-id="0ca8c-120">checked</span></span>](checked.md)
