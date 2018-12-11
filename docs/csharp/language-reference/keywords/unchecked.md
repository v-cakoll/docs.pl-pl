---
title: unchecked — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 44301333f7a36e6b0baa6ea9e089d930bb485a45
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238458"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="f8a1f-102">unchecked (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f8a1f-102">unchecked (C# Reference)</span></span>

<span data-ttu-id="f8a1f-103">`unchecked` Słowo kluczowe jest używane, aby pominąć sprawdzanie przepełnienia dla typu całkowitego operacje arytmetyczne i konwersje.</span><span class="sxs-lookup"><span data-stu-id="f8a1f-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="f8a1f-104">W kontekście niesprawdzanym Jeśli wyrażenie generuje wartość, która znajduje się poza zakresem typu docelowego przeciążenia nie jest oznaczony.</span><span class="sxs-lookup"><span data-stu-id="f8a1f-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="f8a1f-105">Na przykład ponieważ obliczenie w poniższym przykładzie jest wykonywane w `unchecked` bloku lub wyrażenie, fakt, że wynik jest za duży dla liczby całkowitej jest ignorowana, a `int1` jest przypisywana wartość-2,147,483,639.</span><span class="sxs-lookup"><span data-stu-id="f8a1f-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

<span data-ttu-id="f8a1f-106">Jeśli `unchecked` środowiska zostanie usunięty, pojawia się błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f8a1f-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="f8a1f-107">Ponieważ wszystkie warunki wyrażenia są stałe, można wykryć przepełnienie w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f8a1f-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>

<span data-ttu-id="f8a1f-108">Wyrażenia, które zawierają wartość niebędącą stałą warunki nie domyślnie są zaznaczone w czasie kompilacji i czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f8a1f-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="f8a1f-109">Zobacz [zaznaczone](checked.md) informacji na temat włączania środowiska zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="f8a1f-109">See [checked](checked.md) for information about enabling a checked environment.</span></span>

<span data-ttu-id="f8a1f-110">Ponieważ sprawdzania dla przepełnienia zajmuje trochę czasu, użycie unchecked kodu w sytuacjach, gdy ma zagrożenia przepełnienia może zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="f8a1f-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="f8a1f-111">Jednak jeśli przepełnienia jest możliwość, należy użyć środowiska zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="f8a1f-111">However, if overflow is a possibility, a checked environment should be used.</span></span>

## <a name="example"></a><span data-ttu-id="f8a1f-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8a1f-112">Example</span></span>

<span data-ttu-id="f8a1f-113">Ten przykład ilustruje sposób używania `unchecked` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="f8a1f-113">This sample shows how to use the `unchecked` keyword.</span></span>

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="f8a1f-114">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f8a1f-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f8a1f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8a1f-115">See also</span></span>

- [<span data-ttu-id="f8a1f-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f8a1f-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="f8a1f-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f8a1f-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f8a1f-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="f8a1f-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f8a1f-119">Checked i Unchecked</span><span class="sxs-lookup"><span data-stu-id="f8a1f-119">Checked and Unchecked</span></span>](checked-and-unchecked.md)
- [<span data-ttu-id="f8a1f-120">checked</span><span class="sxs-lookup"><span data-stu-id="f8a1f-120">checked</span></span>](checked.md)