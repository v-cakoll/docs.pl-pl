---
title: '&gt;&gt;Operator (odwołanie w C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7c2eddf06d7b8417c9fcb0fed395b2bf51e07144
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="50871-102">&gt;&gt;Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="50871-102">&gt;&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="50871-103">Operator przesunięcia w prawo (`>>`) przesuwa jego pierwszy argument operacji po prawej przez liczbę bitów określony przez jego drugi argument operacji.</span><span class="sxs-lookup"><span data-stu-id="50871-103">The right-shift operator (`>>`) shifts its first operand right by the number of bits specified by its second operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50871-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50871-104">Remarks</span></span>  
 <span data-ttu-id="50871-105">Jeśli pierwszy argument operacji jest [int](../../../csharp/language-reference/keywords/int.md) lub [uint](../../../csharp/language-reference/keywords/uint.md) (32-bitowy), licznik przesunięć oblicza znaczącymi bitami pięć bitów drugi argument operacji (drugi operand & 0x1f).</span><span class="sxs-lookup"><span data-stu-id="50871-105">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand (second operand & 0x1f).</span></span>  
  
 <span data-ttu-id="50871-106">Jeśli pierwszy argument operacji jest [długi](../../../csharp/language-reference/keywords/long.md) lub [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bitowy), licznik przesunięć oblicza za pomocą liczby bitów sześciu znaczącymi bitami drugi operand (drugi operand & 0x3f).</span><span class="sxs-lookup"><span data-stu-id="50871-106">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand (second operand & 0x3f).</span></span>  
  
 <span data-ttu-id="50871-107">Jeśli pierwszy argument operacji jest [int](../../../csharp/language-reference/keywords/int.md) lub [długi](../../../csharp/language-reference/keywords/long.md), prawy klawisz shift jest arytmetyczne przesunięcie (pusta bardziej znaczących bitów ustawiono bitu znaku).</span><span class="sxs-lookup"><span data-stu-id="50871-107">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [long](../../../csharp/language-reference/keywords/long.md), the right-shift is an arithmetic shift (high-order empty bits are set to the sign bit).</span></span> <span data-ttu-id="50871-108">Jeśli pierwszy argument operacji jest typu [uint](../../../csharp/language-reference/keywords/uint.md) lub [ulong](../../../csharp/language-reference/keywords/ulong.md), prawy klawisz shift jest Przesunięcie logiczne (bardziej znaczących bitów są wypełnione zero).</span><span class="sxs-lookup"><span data-stu-id="50871-108">If the first operand is of type [uint](../../../csharp/language-reference/keywords/uint.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md), the right-shift is a logical shift (high-order bits are zero-filled).</span></span>  
  
 <span data-ttu-id="50871-109">Typy definiowane przez użytkownika można przeciążać `>>` operator; typ pierwszego argumentu musi być typu zdefiniowanego przez użytkownika, a typ drugiego argumentu operacji musi być [int](../../../csharp/language-reference/keywords/int.md). Aby uzyskać więcej informacji, zobacz [operator](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="50871-109">User-defined types can overload the `>>` operator; the type of the first operand must be the user-defined type, and the type of the second operand must be [int](../../../csharp/language-reference/keywords/int.md). For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="50871-110">Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="50871-110">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50871-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="50871-111">Example</span></span>  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="50871-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50871-112">See Also</span></span>  
 [<span data-ttu-id="50871-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="50871-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="50871-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="50871-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="50871-115">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="50871-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
