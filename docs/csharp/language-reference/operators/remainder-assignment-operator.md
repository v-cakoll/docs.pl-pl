---
title: Operator %= (odwołanie w C#)
ms.date: 04/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: 009c162b13fab05ba349d0535fe8dfae206502f3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507940"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0e2b5-102">Operator %= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0e2b5-102">%= Operator (C# Reference)</span></span>
<span data-ttu-id="0e2b5-103">Operator przypisania reszty.</span><span class="sxs-lookup"><span data-stu-id="0e2b5-103">The remainder assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e2b5-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e2b5-104">Remarks</span></span>  
 <span data-ttu-id="0e2b5-105">Wyrażenie używające operatora przypisania `%=`, takie jak</span><span class="sxs-lookup"><span data-stu-id="0e2b5-105">An expression using the `%=` assignment operator, such as</span></span>  
  
```csharp  
x %= y  
```  
  
 <span data-ttu-id="0e2b5-106">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="0e2b5-106">is equivalent to</span></span>  
  
```csharp  
x = x % y  
```  
  
 <span data-ttu-id="0e2b5-107">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="0e2b5-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="0e2b5-108">[% — Operator](../../../csharp/language-reference/operators/remainder-operator.md) wstępnie zdefiniowany dla typów liczbowych do obliczania pozostałej po dzielenia.</span><span class="sxs-lookup"><span data-stu-id="0e2b5-108">The [% operator](../../../csharp/language-reference/operators/remainder-operator.md) is predefined for numeric types to compute the remainder after division.</span></span>  
  
 <span data-ttu-id="0e2b5-109">`%=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [operatora %](../../../csharp/language-reference/operators/remainder-operator.md) (zobacz [— operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="0e2b5-109">The `%=` operator cannot be overloaded directly, but user-defined types can overload the [% operator](../../../csharp/language-reference/operators/remainder-operator.md) (see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e2b5-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e2b5-110">Example</span></span>  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0e2b5-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e2b5-111">See Also</span></span>

- [<span data-ttu-id="0e2b5-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0e2b5-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="0e2b5-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0e2b5-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0e2b5-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="0e2b5-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
