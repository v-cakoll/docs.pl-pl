---
title: / — Operator (odwołanie w C#)
ms.date: 04/04/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: 9d0bbff1fd9f4ab3c93c879d12ccd5fde1187b44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272574"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="dc5df-102">/ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="dc5df-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="dc5df-103">Operator dzielenia (`/`) dzieli jego pierwszym argumentem przez jego drugi argument operacji.</span><span class="sxs-lookup"><span data-stu-id="dc5df-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="dc5df-104">Wszystkie typy liczbowe ma wstępnie zdefiniowane operatory dzielenia.</span><span class="sxs-lookup"><span data-stu-id="dc5df-104">All numeric types have predefined division operators.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="dc5df-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc5df-105">Remarks</span></span>  
 <span data-ttu-id="dc5df-106">Typy definiowane przez użytkownika można przeciążać `/` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="dc5df-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="dc5df-107">Przeciążenie `/` operator niejawnie overloads [/ = — operator](division-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="dc5df-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="dc5df-108">Służy do dzielenia dwie liczb całkowitych, wynik jest zawsze liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="dc5df-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="dc5df-109">Na przykład wynik 7 / 3 to 2.</span><span class="sxs-lookup"><span data-stu-id="dc5df-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="dc5df-110">Pozwala to nie należy mylić z dzielenia floored jako `/` operator Zaokrągla wartość w kierunku zera: -7 / 3 -2.</span><span class="sxs-lookup"><span data-stu-id="dc5df-110">This is not to be confused with floored division, as the `/` operator rounds towards zero: -7 / 3 is -2.</span></span>  
  
 <span data-ttu-id="dc5df-111">Aby uzyskać iloraz jako Liczba wymierna, użyj `float`, `double`, lub `decimal` typów.</span><span class="sxs-lookup"><span data-stu-id="dc5df-111">To obtain a quotient as a rational number, use the `float`, `double`, or `decimal` types.</span></span> <span data-ttu-id="dc5df-112">Istnieje wiele sposobów, aby dokonać konwersji między [wbudowane typy liczbowe](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span><span class="sxs-lookup"><span data-stu-id="dc5df-112">There are many ways to convert between [built in numeric types](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span></span>  
  
 <span data-ttu-id="dc5df-113">Aby określić pozostałą, użyj [operator reszty](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span><span class="sxs-lookup"><span data-stu-id="dc5df-113">To determine the remainder, use the [remainder operator](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc5df-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc5df-114">Example</span></span>  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="dc5df-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc5df-115">See Also</span></span>  
 [<span data-ttu-id="dc5df-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="dc5df-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="dc5df-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="dc5df-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="dc5df-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="dc5df-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
