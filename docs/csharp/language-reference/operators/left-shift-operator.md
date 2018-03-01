---
title: "&lt;&lt;Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 400dbc799c68bb9e1bc00695954115f2eb6af7c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="88462-102">&lt;&lt;Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="88462-102">&lt;&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="88462-103">Operator przesunięcia w lewo (`<<`) zmiany jego pierwszym argumentem pozostawionego przez liczbę bitów określony przez jego drugi argument operacji.</span><span class="sxs-lookup"><span data-stu-id="88462-103">The left-shift operator (`<<`) shifts its first operand left by the number of bits specified by its second operand.</span></span> <span data-ttu-id="88462-104">Typ drugiego argumentu operacji musi być [int](../../../csharp/language-reference/keywords/int.md) lub typu, który ma wstępnie zdefiniowanych niejawna konwersja liczbowa na `int`.</span><span class="sxs-lookup"><span data-stu-id="88462-104">The type of the second operand must be an [int](../../../csharp/language-reference/keywords/int.md) or a type that has a predefined implicit numeric conversion to `int`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88462-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88462-105">Remarks</span></span>  
 <span data-ttu-id="88462-106">Jeśli pierwszy argument operacji jest [int](../../../csharp/language-reference/keywords/int.md) lub [uint](../../../csharp/language-reference/keywords/uint.md) (32-bitowy), licznik przesunięć oblicza znaczącymi bitami pięć bitów drugiego argumentu operacji.</span><span class="sxs-lookup"><span data-stu-id="88462-106">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand.</span></span> <span data-ttu-id="88462-107">Licznik przesunięć rzeczywistego jest bitów 0 do 31.</span><span class="sxs-lookup"><span data-stu-id="88462-107">That is, the actual shift count is 0 to 31 bits.</span></span>  
  
 <span data-ttu-id="88462-108">Jeśli pierwszy argument operacji jest [długi](../../../csharp/language-reference/keywords/long.md) lub [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bitowy), licznik przesunięć oblicza za pomocą liczby bitów sześciu znaczącymi bitami drugiego argumentu operacji.</span><span class="sxs-lookup"><span data-stu-id="88462-108">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand.</span></span> <span data-ttu-id="88462-109">Licznik przesunięć rzeczywistego jest 0 – 63 bity.</span><span class="sxs-lookup"><span data-stu-id="88462-109">That is, the actual shift count is 0 to 63 bits.</span></span>  
  
 <span data-ttu-id="88462-110">Żadnych znaczących bitów, które są nie w zakresie typ pierwszego argumentu po zmiany zostaną odrzucone i bits pusty znaczącymi bitami są wypełnione zero.</span><span class="sxs-lookup"><span data-stu-id="88462-110">Any high-order bits that are not within the range of the type of the first operand after the shift are discarded, and the low-order empty bits are zero-filled.</span></span> <span data-ttu-id="88462-111">Operacje SHIFT nigdy nie powodują przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="88462-111">Shift operations never cause overflows.</span></span>  
  
 <span data-ttu-id="88462-112">Typy definiowane przez użytkownika można przeciążać `<<` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)); typ pierwszego argumentu musi być typu zdefiniowanego przez użytkownika, a typ drugiego argumentu operacji musi być `int`.</span><span class="sxs-lookup"><span data-stu-id="88462-112">User-defined types can overload the `<<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)); the type of the first operand must be the user-defined type, and the type of the second operand must be `int`.</span></span> <span data-ttu-id="88462-113">Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="88462-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88462-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="88462-114">Example</span></span>  
 [!code-csharp[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="88462-115">Komentarze</span><span class="sxs-lookup"><span data-stu-id="88462-115">Comments</span></span>  
 <span data-ttu-id="88462-116">Należy pamiętać, że `i<<1` i `i<<33` zapewniają takiego samego wyniku, ponieważ 1 i 33 ma tego samego pięć bitów znaczącymi bitami.</span><span class="sxs-lookup"><span data-stu-id="88462-116">Note that `i<<1` and `i<<33` give the same result, because 1 and 33 have the same low-order five bits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88462-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88462-117">See Also</span></span>  
 [<span data-ttu-id="88462-118">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="88462-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="88462-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="88462-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="88462-120">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="88462-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
