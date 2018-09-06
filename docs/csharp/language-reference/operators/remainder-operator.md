---
title: Operator % (odwołanie w C#)
ms.date: 04/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: 477f2491e6d2efe6b5c327efb371843d0bf12c26
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723876"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c9345-102">Operator % (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c9345-102">% Operator (C# Reference)</span></span>
<span data-ttu-id="c9345-103">Operator reszty (`%`) oblicza pozostałą po podzieleniu swojego pierwszego operandu przez drugi jej.</span><span class="sxs-lookup"><span data-stu-id="c9345-103">The remainder operator (`%`) computes the remainder after dividing its first operand by its second.</span></span> <span data-ttu-id="c9345-104">Wszystkie typy liczbowe ma wstępnie zdefiniowane operatory resztę.</span><span class="sxs-lookup"><span data-stu-id="c9345-104">All numeric types have predefined remainder operators.</span></span> 
  
## <a name="remarks"></a><span data-ttu-id="c9345-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9345-105">Remarks</span></span>  
 <span data-ttu-id="c9345-106">Formuła `a % b` zawsze zwraca wartość w zakresie `(-b, b)`Ekskluzywna (nigdy nie może zwrócić `b` lub `-b`), utrzymywanie znak dzielna.</span><span class="sxs-lookup"><span data-stu-id="c9345-106">The formula `a % b` will always return a value on the range `(-b, b)`, exclusive (it can never return `b` or `-b`), keeping the sign of the dividend.</span></span> <span data-ttu-id="c9345-107">Dzielenie liczby całkowitej, operator reszty spełnia reguły `a % b = a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="c9345-107">For integer division, the remainder operator satisfies the rule `a % b = a - (a / b) * b`.</span></span>
  
 <span data-ttu-id="c9345-108">Nie należy mylić modulo canonical, które spełniają reguły podobne, ale floored dzielenia i zwraca wartości na zakresie `[0, b)`.</span><span class="sxs-lookup"><span data-stu-id="c9345-108">This is not to be confused with canonical modulus, which satisfies a similar rule but with floored division and returns values on the range `[0, b)`.</span></span> <span data-ttu-id="c9345-109">C# ma operator modulo kanonicznej.</span><span class="sxs-lookup"><span data-stu-id="c9345-109">C# does not have an operator for canonical modulus.</span></span> <span data-ttu-id="c9345-110">Jednak to zachowanie jest taki sam dla dywidendy dodatnią.</span><span class="sxs-lookup"><span data-stu-id="c9345-110">However, the behavior is the same for positive dividends.</span></span>
  
 <span data-ttu-id="c9345-111">Typy definiowane przez użytkownika mogą przeciążać operator `%` — (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="c9345-111">User-defined types can overload the `%` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="c9345-112">Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="c9345-112">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9345-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9345-113">Example</span></span>  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/remainder-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="c9345-114">Komentarze</span><span class="sxs-lookup"><span data-stu-id="c9345-114">Comments</span></span>  
 <span data-ttu-id="c9345-115">Należy pamiętać, błędy zaokrąglania skojarzone z typem double.</span><span class="sxs-lookup"><span data-stu-id="c9345-115">Note the round-off errors associated with the double type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9345-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9345-116">See Also</span></span>

- [<span data-ttu-id="c9345-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c9345-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c9345-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c9345-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c9345-119">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="c9345-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
