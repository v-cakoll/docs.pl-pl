---
title: '&gt;&gt; Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: fc3d683f212c71620049ec6adee3d20bd5c1437c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239998"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="53435-102">&gt;&gt; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="53435-102">&gt;&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="53435-103">Operator przesunięcia w prawo (`>>`) przenosi pierwszy argument operacji w prawo o liczbę bitów określoną przez drugim argumentem operacji.</span><span class="sxs-lookup"><span data-stu-id="53435-103">The right-shift operator (`>>`) shifts its first operand right by the number of bits specified by its second operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53435-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53435-104">Remarks</span></span>  
 <span data-ttu-id="53435-105">Jeśli pierwszy argument jest [int](../../../csharp/language-reference/keywords/int.md) lub [uint](../../../csharp/language-reference/keywords/uint.md) (32-bitowy), licznik przesunięć oblicza mniej znaczące bity pięć, drugi operand (drugi operand & 0x1f).</span><span class="sxs-lookup"><span data-stu-id="53435-105">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand (second operand & 0x1f).</span></span>  
  
 <span data-ttu-id="53435-106">Jeśli pierwszy argument jest [długie](../../../csharp/language-reference/keywords/long.md) lub [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bitowy), licznik przesunięć oblicza mniej znaczące bity sześć, drugi operand (drugi operand & 0x3f).</span><span class="sxs-lookup"><span data-stu-id="53435-106">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand (second operand & 0x3f).</span></span>  
  
 <span data-ttu-id="53435-107">Jeśli pierwszy argument jest [int](../../../csharp/language-reference/keywords/int.md) lub [długie](../../../csharp/language-reference/keywords/long.md), prawy shift jest arytmetycznego przesunięcia (wyższego rzędu pusty bity są ustawione na bit znaku).</span><span class="sxs-lookup"><span data-stu-id="53435-107">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [long](../../../csharp/language-reference/keywords/long.md), the right-shift is an arithmetic shift (high-order empty bits are set to the sign bit).</span></span> <span data-ttu-id="53435-108">Jeśli pierwszy operand jest typu [uint](../../../csharp/language-reference/keywords/uint.md) lub [ulong](../../../csharp/language-reference/keywords/ulong.md), prawy shift to Przesunięcie logiczne (bity wyższego rzędu są wypełnione przez zera).</span><span class="sxs-lookup"><span data-stu-id="53435-108">If the first operand is of type [uint](../../../csharp/language-reference/keywords/uint.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md), the right-shift is a logical shift (high-order bits are zero-filled).</span></span>  
  
 <span data-ttu-id="53435-109">Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia `>>` operator; typ pierwszy operand musi być typu zdefiniowanego przez użytkownika, a typ drugiego argumentu operacji musi być [int](../../../csharp/language-reference/keywords/int.md). Aby uzyskać więcej informacji, zobacz [operator](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="53435-109">User-defined types can overload the `>>` operator; the type of the first operand must be the user-defined type, and the type of the second operand must be [int](../../../csharp/language-reference/keywords/int.md). For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="53435-110">Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="53435-110">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53435-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="53435-111">Example</span></span>  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="53435-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53435-112">See Also</span></span>

- [<span data-ttu-id="53435-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="53435-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="53435-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="53435-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="53435-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="53435-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
