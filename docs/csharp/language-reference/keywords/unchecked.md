---
title: "unchecked (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords: unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c05e7cb742d8e8f5a7804656a5ec13548d0498b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="8b2aa-102">unchecked (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8b2aa-102">unchecked (C# Reference)</span></span>
<span data-ttu-id="8b2aa-103">`unchecked` Słowo kluczowe jest używane do pomijania sprawdzania przepełnienia dla operacji arytmetycznych typem całkowitym i konwersje.</span><span class="sxs-lookup"><span data-stu-id="8b2aa-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="8b2aa-104">W kontekście zaznaczenie opcji Jeśli wyrażenie zwraca wartość, która jest poza zakresem typu docelowego przeciążenia nie jest oznaczony.</span><span class="sxs-lookup"><span data-stu-id="8b2aa-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="8b2aa-105">Na przykład obliczeń w poniższym przykładzie jest wykonywana w `unchecked` bloku lub wyrażenie, fakt, że wynik jest za duża dla typu integer jest ignorowana, a `int1` jest przypisywana wartość-2,147,483,639.</span><span class="sxs-lookup"><span data-stu-id="8b2aa-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 <span data-ttu-id="8b2aa-106">Jeśli `unchecked` środowiska zostanie usunięty, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8b2aa-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="8b2aa-107">Mogą być wykrywane przepełnienie w czasie kompilacji, ponieważ wszystkie warunki wyrażenie stałe.</span><span class="sxs-lookup"><span data-stu-id="8b2aa-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>  
  
 <span data-ttu-id="8b2aa-108">Wyrażeń, które zawierają postanowienia z systemem innym niż stała jest zaznaczony domyślnie w czasie kompilacji i czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8b2aa-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="8b2aa-109">Zobacz [zaznaczone](../../../csharp/language-reference/keywords/checked.md) informacji na temat włączania zaznaczone środowiska.</span><span class="sxs-lookup"><span data-stu-id="8b2aa-109">See [checked](../../../csharp/language-reference/keywords/checked.md) for information about enabling a checked environment.</span></span>  
  
 <span data-ttu-id="8b2aa-110">Ponieważ sprawdzania przepełnienia jest czasochłonne, użycie niezaznaczone kodu w sytuacjach, gdy istnieje niebezpieczeństwo z przepełnienie może zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="8b2aa-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="8b2aa-111">Jednak jeśli przepełnienia jest możliwość, można użyć środowiska zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="8b2aa-111">However, if overflow is a possibility, a checked environment should be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b2aa-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="8b2aa-112">Example</span></span>  
 <span data-ttu-id="8b2aa-113">Ten przykład przedstawia sposób użycia `unchecked` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="8b2aa-113">This sample shows how to use the `unchecked` keyword.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8b2aa-114">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8b2aa-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8b2aa-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b2aa-115">See Also</span></span>  
 [<span data-ttu-id="8b2aa-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="8b2aa-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8b2aa-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8b2aa-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8b2aa-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="8b2aa-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="8b2aa-119">Zaznaczony i niezaznaczony</span><span class="sxs-lookup"><span data-stu-id="8b2aa-119">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [<span data-ttu-id="8b2aa-120">zaznaczone</span><span class="sxs-lookup"><span data-stu-id="8b2aa-120">checked</span></span>](../../../csharp/language-reference/keywords/checked.md)
