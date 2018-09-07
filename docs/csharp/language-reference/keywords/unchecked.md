---
title: unchecked (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: daccd7916a9f81f26f468ab0f64833d9537cff8e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44066925"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="fe7cf-102">unchecked (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="fe7cf-102">unchecked (C# Reference)</span></span>
<span data-ttu-id="fe7cf-103">`unchecked` Słowo kluczowe jest używane, aby pominąć sprawdzanie przepełnienia dla typu całkowitego operacje arytmetyczne i konwersje.</span><span class="sxs-lookup"><span data-stu-id="fe7cf-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="fe7cf-104">W kontekście niesprawdzanym Jeśli wyrażenie generuje wartość, która znajduje się poza zakresem typu docelowego przeciążenia nie jest oznaczony.</span><span class="sxs-lookup"><span data-stu-id="fe7cf-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="fe7cf-105">Na przykład ponieważ obliczenie w poniższym przykładzie jest wykonywane w `unchecked` bloku lub wyrażenie, fakt, że wynik jest za duży dla liczby całkowitej jest ignorowana, a `int1` jest przypisywana wartość-2,147,483,639.</span><span class="sxs-lookup"><span data-stu-id="fe7cf-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 <span data-ttu-id="fe7cf-106">Jeśli `unchecked` środowiska zostanie usunięty, pojawia się błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fe7cf-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="fe7cf-107">Ponieważ wszystkie warunki wyrażenia są stałe, można wykryć przepełnienie w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fe7cf-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>  
  
 <span data-ttu-id="fe7cf-108">Wyrażenia, które zawierają wartość niebędącą stałą warunki nie domyślnie są zaznaczone w czasie kompilacji i czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fe7cf-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="fe7cf-109">Zobacz [zaznaczone](../../../csharp/language-reference/keywords/checked.md) informacji na temat włączania środowiska zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="fe7cf-109">See [checked](../../../csharp/language-reference/keywords/checked.md) for information about enabling a checked environment.</span></span>  
  
 <span data-ttu-id="fe7cf-110">Ponieważ sprawdzania dla przepełnienia zajmuje trochę czasu, użycie unchecked kodu w sytuacjach, gdy ma zagrożenia przepełnienia może zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="fe7cf-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="fe7cf-111">Jednak jeśli przepełnienia jest możliwość, należy użyć środowiska zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="fe7cf-111">However, if overflow is a possibility, a checked environment should be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe7cf-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="fe7cf-112">Example</span></span>  
 <span data-ttu-id="fe7cf-113">Ten przykład ilustruje sposób używania `unchecked` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="fe7cf-113">This sample shows how to use the `unchecked` keyword.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="fe7cf-114">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fe7cf-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fe7cf-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe7cf-115">See Also</span></span>

- [<span data-ttu-id="fe7cf-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fe7cf-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="fe7cf-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fe7cf-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="fe7cf-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="fe7cf-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="fe7cf-119">Checked i Unchecked</span><span class="sxs-lookup"><span data-stu-id="fe7cf-119">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
- [<span data-ttu-id="fe7cf-120">checked</span><span class="sxs-lookup"><span data-stu-id="fe7cf-120">checked</span></span>](../../../csharp/language-reference/keywords/checked.md)
