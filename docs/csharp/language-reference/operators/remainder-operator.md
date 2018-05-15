---
title: Operator % (odwołanie w C#)
ms.date: 04/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: b906feb22aaec97e58da562b615baae01f3e0719
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c8a1a-102">Operator % (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c8a1a-102">% Operator (C# Reference)</span></span>
<span data-ttu-id="c8a1a-103">Operator reszty (`%`) oblicza resztę po podzieleniu jego pierwszym argumentem przez jego sekundy.</span><span class="sxs-lookup"><span data-stu-id="c8a1a-103">The remainder operator (`%`) computes the remainder after dividing its first operand by its second.</span></span> <span data-ttu-id="c8a1a-104">Wszystkie typy liczbowe ma wstępnie zdefiniowane operatory resztę.</span><span class="sxs-lookup"><span data-stu-id="c8a1a-104">All numeric types have predefined remainder operators.</span></span> 
  
## <a name="remarks"></a><span data-ttu-id="c8a1a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8a1a-105">Remarks</span></span>  
 <span data-ttu-id="c8a1a-106">Formuła `a % b` zawsze zwróci wartość z zakresu `(-b, b)`, wyłącznego (nigdy nie może zwrócić `b` lub `-b`), przechowywania znak dzielna.</span><span class="sxs-lookup"><span data-stu-id="c8a1a-106">The formula `a % b` will always return a value on the range `(-b, b)`, exclusive (it can never return `b` or `-b`), keeping the sign of the dividend.</span></span> <span data-ttu-id="c8a1a-107">Dla dzielenie liczby całkowitej operator reszty spełnia reguły `a % b = a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="c8a1a-107">For integer division, the remainder operator satisfies the rule `a % b = a - (a / b) * b`.</span></span>
  
 <span data-ttu-id="c8a1a-108">Pozwala to nie należy mylić z canonical modulo, które spełniają reguły podobne, lecz z floored dzielenia i zwraca wartości zakresu `[0, b)`.</span><span class="sxs-lookup"><span data-stu-id="c8a1a-108">This is not to be confused with canonical modulus, which satisfies a similar rule but with floored division and returns values on the range `[0, b)`.</span></span> <span data-ttu-id="c8a1a-109">C# nie ma operator modulo kanonicznej.</span><span class="sxs-lookup"><span data-stu-id="c8a1a-109">C# does not have an operator for canonical modulus.</span></span> <span data-ttu-id="c8a1a-110">Jednak zachowanie jest takie same dla dywidendy dodatnią.</span><span class="sxs-lookup"><span data-stu-id="c8a1a-110">However, the behavior is the same for positive dividends.</span></span>
  
 <span data-ttu-id="c8a1a-111">Typy definiowane przez użytkownika można przeciążać `%` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="c8a1a-111">User-defined types can overload the `%` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="c8a1a-112">Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="c8a1a-112">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8a1a-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8a1a-113">Example</span></span>  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/remainder-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="c8a1a-114">Komentarze</span><span class="sxs-lookup"><span data-stu-id="c8a1a-114">Comments</span></span>  
 <span data-ttu-id="c8a1a-115">Należy pamiętać, błędów zaokrąglania skojarzonych z typu double.</span><span class="sxs-lookup"><span data-stu-id="c8a1a-115">Note the round-off errors associated with the double type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8a1a-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8a1a-116">See Also</span></span>  
 [<span data-ttu-id="c8a1a-117">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="c8a1a-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c8a1a-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c8a1a-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c8a1a-119">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="c8a1a-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
