---
title: ^ — Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: 5cc3cd2cfc932646e5b2dd6ec034555b07582379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8feef-102">^ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8feef-102">^ Operator (C# Reference)</span></span>
<span data-ttu-id="8feef-103">Binarny `^` operatory są wstępnie zdefiniowane dla typów całkowitych i `bool`.</span><span class="sxs-lookup"><span data-stu-id="8feef-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="8feef-104">W przypadku typów całkowitych `^` oblicza bitowej OR wyłączne argumentów.</span><span class="sxs-lookup"><span data-stu-id="8feef-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="8feef-105">Dla `bool` argumentów operacji, `^` oblicza logicznej wyłącznie — lub z argumentów; wynik jest `true` tylko wtedy, gdy jest dokładnie jeden z argumentów `true`.</span><span class="sxs-lookup"><span data-stu-id="8feef-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8feef-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8feef-106">Remarks</span></span>  
 <span data-ttu-id="8feef-107">Typy definiowane przez użytkownika można przeciążać `^` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="8feef-107">User-defined types can overload the `^` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="8feef-108">Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="8feef-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8feef-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="8feef-109">Example</span></span>  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 <span data-ttu-id="8feef-110">Do obliczenia `0xf8 ^ 0x3f` w poprzednim przykładzie wykonuje bitowej OR wyłączne następujących dwóch wartości binarnych, które odpowiadają wartości szesnastkowe F8 i 3F:</span><span class="sxs-lookup"><span data-stu-id="8feef-110">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>  
  
 `1111 1000`  
  
 `0011 1111`  
  
 <span data-ttu-id="8feef-111">Wynik OR wyłączne jest `1100 0111`, która jest w formacie szesnastkowym C7.</span><span class="sxs-lookup"><span data-stu-id="8feef-111">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8feef-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8feef-112">See Also</span></span>  
 [<span data-ttu-id="8feef-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="8feef-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8feef-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8feef-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8feef-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="8feef-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
