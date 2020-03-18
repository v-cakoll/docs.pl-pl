---
title: niezaznaczone słowo kluczowe — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 6dad0dfd508fb390dd0a52d1b48d70b4c5725513
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713004"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="cb93f-102">unchecked (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cb93f-102">unchecked (C# Reference)</span></span>

<span data-ttu-id="cb93f-103">Słowo `unchecked` kluczowe służy do pomijania sprawdzania przepełnienia dla operacji arytmetycznych typu integralnego i konwersji.</span><span class="sxs-lookup"><span data-stu-id="cb93f-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="cb93f-104">W kontekście niezaznaczone, jeśli wyrażenie tworzy wartość, która znajduje się poza zakresem typu docelowego, przepełnienie nie jest oflagowane.</span><span class="sxs-lookup"><span data-stu-id="cb93f-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="cb93f-105">Na przykład, ponieważ obliczenia w poniższym `unchecked` przykładzie są wykonywane w bloku lub wyrażeniu, fakt, że `int1` wynik jest zbyt duży dla liczby całkowitej jest ignorowany i jest przypisywany wartość -2,147,483,639.</span><span class="sxs-lookup"><span data-stu-id="cb93f-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

<span data-ttu-id="cb93f-106">Jeśli `unchecked` środowisko zostanie usunięte, wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cb93f-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="cb93f-107">Przepełnienie można wykryć w czasie kompilacji, ponieważ wszystkie warunki wyrażenia są stałe.</span><span class="sxs-lookup"><span data-stu-id="cb93f-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>

<span data-ttu-id="cb93f-108">Wyrażenia zawierające terminy niestałe są domyślnie niezaznaczone w czasie kompilacji i czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cb93f-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="cb93f-109">Zobacz [sprawdzone informacje](checked.md) dotyczące włączania sprawdzonego środowiska.</span><span class="sxs-lookup"><span data-stu-id="cb93f-109">See [checked](checked.md) for information about enabling a checked environment.</span></span>

<span data-ttu-id="cb93f-110">Ponieważ sprawdzanie przepełnienia zajmuje czas, użycie niezaznaczonego kodu w sytuacjach, gdy nie ma niebezpieczeństwa przepełnienia może zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="cb93f-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="cb93f-111">Jednak jeśli przepełnienie jest możliwe, należy użyć sprawdzonego środowiska.</span><span class="sxs-lookup"><span data-stu-id="cb93f-111">However, if overflow is a possibility, a checked environment should be used.</span></span>

## <a name="example"></a><span data-ttu-id="cb93f-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb93f-112">Example</span></span>

<span data-ttu-id="cb93f-113">W tym przykładzie pokazano, jak używać słowa kluczowego. `unchecked`</span><span class="sxs-lookup"><span data-stu-id="cb93f-113">This sample shows how to use the `unchecked` keyword.</span></span>

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="cb93f-114">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cb93f-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="cb93f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb93f-115">See also</span></span>

- [<span data-ttu-id="cb93f-116">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="cb93f-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cb93f-117">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="cb93f-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cb93f-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="cb93f-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="cb93f-119">Checked i Unchecked</span><span class="sxs-lookup"><span data-stu-id="cb93f-119">Checked and Unchecked</span></span>](checked-and-unchecked.md)
- [<span data-ttu-id="cb93f-120">Sprawdzane</span><span class="sxs-lookup"><span data-stu-id="cb93f-120">checked</span></span>](checked.md)
