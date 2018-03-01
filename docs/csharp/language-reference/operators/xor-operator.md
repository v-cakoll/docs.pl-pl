---
title: "^ — Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4ccd32ea8abd8ca3252380083eafecad2b572ed7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="b82c9-102">^ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="b82c9-102">^ Operator (C# Reference)</span></span>
<span data-ttu-id="b82c9-103">Binarny `^` operatory są wstępnie zdefiniowane dla typów całkowitych i `bool`.</span><span class="sxs-lookup"><span data-stu-id="b82c9-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="b82c9-104">W przypadku typów całkowitych `^` oblicza bitowej OR wyłączne argumentów.</span><span class="sxs-lookup"><span data-stu-id="b82c9-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="b82c9-105">Dla `bool` argumentów operacji, `^` oblicza logicznej wyłącznie — lub z argumentów; wynik jest `true` tylko wtedy, gdy jest dokładnie jeden z argumentów `true`.</span><span class="sxs-lookup"><span data-stu-id="b82c9-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b82c9-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b82c9-106">Remarks</span></span>  
 <span data-ttu-id="b82c9-107">Typy definiowane przez użytkownika można przeciążać `^` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="b82c9-107">User-defined types can overload the `^` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="b82c9-108">Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="b82c9-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b82c9-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="b82c9-109">Example</span></span>  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 <span data-ttu-id="b82c9-110">Do obliczenia `0xf8 ^ 0x3f` w poprzednim przykładzie wykonuje bitowej OR wyłączne następujących dwóch wartości binarnych, które odpowiadają wartości szesnastkowe F8 i 3F:</span><span class="sxs-lookup"><span data-stu-id="b82c9-110">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>  
  
 `1111 1000`  
  
 `0011 1111`  
  
 <span data-ttu-id="b82c9-111">Wynik OR wyłączne jest `1100 0111`, która jest w formacie szesnastkowym C7.</span><span class="sxs-lookup"><span data-stu-id="b82c9-111">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b82c9-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b82c9-112">See Also</span></span>  
 [<span data-ttu-id="b82c9-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="b82c9-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b82c9-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b82c9-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b82c9-115">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="b82c9-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
