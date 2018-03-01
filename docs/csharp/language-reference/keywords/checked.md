---
title: "checked (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0ae77894cdc94e41dfa281b92ed3304e0dc25731
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="checked-c-reference"></a><span data-ttu-id="05586-102">checked (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="05586-102">checked (C# Reference)</span></span>
<span data-ttu-id="05586-103">`checked` Słowo kluczowe jest używane do jawnie włączyć sprawdzanie operacji arytmetycznych typem całkowitym i konwersje przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="05586-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="05586-104">Domyślnie wyrażenie, które zawiera tylko wartości stałych powoduje wystąpi błąd kompilatora, jeśli wyrażenie zwraca wartość, która jest poza zakresem typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="05586-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="05586-105">Jeśli wyrażenie zawiera jedną lub więcej wartości niż stała, kompilator nie wykrywa przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="05586-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="05586-106">Obliczenie wyrażenia przypisane do `i2` w poniższym przykładzie nie powoduje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="05586-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 <span data-ttu-id="05586-107">Domyślnie wyrażenia te z systemem innym niż stała nie są sprawdzane dla przepełnienie w czasie wykonywania albo, a nie wywołuj wyjątków przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="05586-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="05586-108">Poprzedni przykład przedstawia-2,147,483,639 jako suma wartości dwie dodatnie liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="05586-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>  
  
 <span data-ttu-id="05586-109">Sprawdzanie przepełnienia można włączyć opcji kompilatora, konfiguracji środowiska lub użycie `checked` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="05586-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="05586-110">W poniższych przykładach pokazano, jak używać `checked` wyrażenie lub `checked` bloku, aby wykryć przepełnienie, wytworzonego przez poprzednie sum w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="05586-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="05586-111">Oba przykłady zgłosić wyjątek przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="05586-111">Both examples raise an overflow exception.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 <span data-ttu-id="05586-112">[Niezaznaczone](../../../csharp/language-reference/keywords/unchecked.md) — słowo kluczowe może służyć do zapobiec sprawdzanie przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="05586-112">The [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword can be used to prevent overflow checking.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05586-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="05586-113">Example</span></span>  
 <span data-ttu-id="05586-114">Ten przykład przedstawia sposób użycia `checked` umożliwiające przepełnienie sprawdzenie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="05586-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="05586-115">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="05586-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="05586-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05586-116">See Also</span></span>  
 [<span data-ttu-id="05586-117">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="05586-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="05586-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="05586-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="05586-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="05586-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="05586-120">Zaznaczony i niezaznaczony</span><span class="sxs-lookup"><span data-stu-id="05586-120">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [<span data-ttu-id="05586-121">unchecked</span><span class="sxs-lookup"><span data-stu-id="05586-121">unchecked</span></span>](../../../csharp/language-reference/keywords/unchecked.md)
