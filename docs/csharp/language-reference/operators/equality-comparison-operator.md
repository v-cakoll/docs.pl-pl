---
title: Operator == (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca22846325968519a1f7625461867c0d83a1a9f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d1aad-102">Operator == (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d1aad-102">== Operator (C# Reference)</span></span>
<span data-ttu-id="d1aad-103">Dla wstępnie zdefiniowanych typów wartości, operator równości (`==`) zwraca wartość true, jeśli wartości argumentów są takie same, `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="d1aad-103">For predefined value types, the equality operator (`==`) returns true if the values of its operands are equal, `false` otherwise.</span></span> <span data-ttu-id="d1aad-104">Dla odwołania do typów innych niż [ciąg](../../../csharp/language-reference/keywords/string.md), `==` zwraca `true` Jeśli swoich argumentów, dwóch odwołują się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="d1aad-104">For reference types other than [string](../../../csharp/language-reference/keywords/string.md), `==` returns `true` if its two operands refer to the same object.</span></span> <span data-ttu-id="d1aad-105">Aby uzyskać `string` typu `==` porównuje wartości ciągów.</span><span class="sxs-lookup"><span data-stu-id="d1aad-105">For the `string` type, `==` compares the values of the strings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1aad-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1aad-106">Remarks</span></span>  
 <span data-ttu-id="d1aad-107">Typy wartości zdefiniowane przez użytkownika można przeciążać `==` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="d1aad-107">User-defined value types can overload the `==` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="d1aad-108">Dlatego można typy odwołań zdefiniowanych przez użytkownika, mimo że domyślnie `==` zachowuje się jak opisano powyżej dla obu typów odniesienia wstępnie zdefiniowane i zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d1aad-108">So can user-defined reference types, although by default `==` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="d1aad-109">Jeśli `==` jest przeciążony [! =](../../../csharp/language-reference/operators/not-equal-operator.md) również musi być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="d1aad-109">If `==` is overloaded, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="d1aad-110">Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="d1aad-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1aad-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1aad-111">Example</span></span>  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d1aad-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1aad-112">See Also</span></span>  
 [<span data-ttu-id="d1aad-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="d1aad-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d1aad-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d1aad-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d1aad-115">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="d1aad-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
