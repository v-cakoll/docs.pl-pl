---
title: / — Operator (odwołanie w C#)
ms.date: 04/04/2018
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
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5b17d122e3e3f75012e084903b6f8975fb53d46c
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d9da3-102">/ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d9da3-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="d9da3-103">Operator dzielenia (`/`) dzieli jego pierwszym argumentem przez jego drugi argument operacji.</span><span class="sxs-lookup"><span data-stu-id="d9da3-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="d9da3-104">Wszystkie typy liczbowe ma wstępnie zdefiniowane operatory dzielenia.</span><span class="sxs-lookup"><span data-stu-id="d9da3-104">All numeric types have predefined division operators.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="d9da3-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9da3-105">Remarks</span></span>  
 <span data-ttu-id="d9da3-106">Typy definiowane przez użytkownika można przeciążać `/` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="d9da3-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="d9da3-107">Przeciążenie `/` operator niejawnie overloads [/ = — operator](division-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="d9da3-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="d9da3-108">Służy do dzielenia dwie liczb całkowitych, wynik jest zawsze liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="d9da3-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="d9da3-109">Na przykład wynik 7 / 3 to 2.</span><span class="sxs-lookup"><span data-stu-id="d9da3-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="d9da3-110">Pozwala to nie należy mylić z dzielenia floored jako `/` operator Zaokrągla wartość w kierunku zera: -7 / 3 -2.</span><span class="sxs-lookup"><span data-stu-id="d9da3-110">This is not to be confused with floored division, as the `/` operator rounds towards zero: -7 / 3 is -2.</span></span>  
  
 <span data-ttu-id="d9da3-111">Aby uzyskać iloraz jako Liczba wymierna, użyj `float`, `double`, lub `decimal` typów.</span><span class="sxs-lookup"><span data-stu-id="d9da3-111">To obtain a quotient as a rational number, use the `float`, `double`, or `decimal` types.</span></span> <span data-ttu-id="d9da3-112">Istnieje wiele sposobów, aby dokonać konwersji między [wbudowane typy liczbowe](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span><span class="sxs-lookup"><span data-stu-id="d9da3-112">There are many ways to convert between [built in numeric types](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span></span>  
  
 <span data-ttu-id="d9da3-113">Aby określić pozostałą, użyj [operator reszty](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span><span class="sxs-lookup"><span data-stu-id="d9da3-113">To determine the remainder, use the [remainder operator](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9da3-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9da3-114">Example</span></span>  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d9da3-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9da3-115">See Also</span></span>  
 [<span data-ttu-id="d9da3-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="d9da3-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d9da3-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d9da3-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d9da3-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="d9da3-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
