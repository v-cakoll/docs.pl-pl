---
title: ^ — Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: b1333f9d06e2804029550e6364a225558e096431
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925301"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9402e-102">^ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9402e-102">^ Operator (C# Reference)</span></span>
<span data-ttu-id="9402e-103">Operatory binarne `^` są wstępnie zdefiniowane dla typów całkowitych i `bool`.</span><span class="sxs-lookup"><span data-stu-id="9402e-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="9402e-104">W przypadku typów całkowitych `^` oblicza bitową alternatywę rozłączną dla operandu.</span><span class="sxs-lookup"><span data-stu-id="9402e-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="9402e-105">Dla operacji na zmiennych typu `bool` `^` oblicza alternatywę rozłączną dla jej argumentów. Wynik jest `true` tylko wtedy, gdy dokładnie jeden z argumentów to `true`.</span><span class="sxs-lookup"><span data-stu-id="9402e-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9402e-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9402e-106">Remarks</span></span>  
 <span data-ttu-id="9402e-107">Typy definiowane przez użytkownika mogą przeciążać operator `^` — (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="9402e-107">User-defined types can overload the `^` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="9402e-108">Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone.</span><span class="sxs-lookup"><span data-stu-id="9402e-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9402e-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="9402e-109">Example</span></span>  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 <span data-ttu-id="9402e-110">Obliczenie `0xf8 ^ 0x3f` w poprzednim przykładzie powoduje wykonanie bitowej operacji wyłącznej OR na następnych dwóch wartościach binarnych, które odpowiadają wartościom szesnastkowym F8 i 3F:</span><span class="sxs-lookup"><span data-stu-id="9402e-110">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>  
  
 `1111 1000`  
  
 `0011 1111`  
  
 <span data-ttu-id="9402e-111">Wynik alternatywy rozłącznej to `1100 0111`, czyli C7 w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="9402e-111">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9402e-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9402e-112">See Also</span></span>

- [<span data-ttu-id="9402e-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9402e-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9402e-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9402e-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9402e-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="9402e-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
