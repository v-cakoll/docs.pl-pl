---
title: "/ — Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9e12e5c472266ea75d3f572a2091bd0784ea5dcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a5a97-102">/ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a5a97-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="a5a97-103">Operator dzielenia (`/`) dzieli jego pierwszym argumentem przez jego drugi argument operacji.</span><span class="sxs-lookup"><span data-stu-id="a5a97-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="a5a97-104">Wszystkie typy liczbowe ma wstępnie zdefiniowane operatory dzielenia.</span><span class="sxs-lookup"><span data-stu-id="a5a97-104">All numeric types have predefined division operators.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5a97-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5a97-105">Remarks</span></span>  
 <span data-ttu-id="a5a97-106">Typy definiowane przez użytkownika można przeciążać `/` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="a5a97-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="a5a97-107">Przeciążenie `/` operator niejawnie overloads [/ = — operator](division-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="a5a97-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="a5a97-108">Służy do dzielenia dwie liczb całkowitych, wynik jest zawsze liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="a5a97-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="a5a97-109">Na przykład wynik 7 / 3 to 2.</span><span class="sxs-lookup"><span data-stu-id="a5a97-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="a5a97-110">Aby określić w pozostałej części 7 / 3, użycie operator reszty ([%](../../../csharp/language-reference/operators/modulus-operator.md)).</span><span class="sxs-lookup"><span data-stu-id="a5a97-110">To determine the remainder of 7 / 3, use the remainder operator ([%](../../../csharp/language-reference/operators/modulus-operator.md)).</span></span> <span data-ttu-id="a5a97-111">Aby uzyskać iloraz jako Liczba wymierna lub ułamek, nadaj dzielna lub dzielnik typu `float` lub typ `double`.</span><span class="sxs-lookup"><span data-stu-id="a5a97-111">To obtain a quotient as a rational number or fraction, give the dividend or divisor type `float` or type `double`.</span></span> <span data-ttu-id="a5a97-112">Typ można przypisać niejawnie Jeśli express dzielna lub dzielnik jako wartości dziesiętnej poprzez umieszczenie cyfrę z prawej strony punktu dziesiętnego, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a5a97-112">You can assign the type implicitly if you express the dividend or divisor as a decimal by putting a digit to the right side of the decimal point, as the following example shows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5a97-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5a97-113">Example</span></span>  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a5a97-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5a97-114">See Also</span></span>  
 [<span data-ttu-id="a5a97-115">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="a5a97-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a5a97-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a5a97-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a5a97-117">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="a5a97-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
