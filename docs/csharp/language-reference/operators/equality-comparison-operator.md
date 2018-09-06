---
title: Operator == (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: d9d7dcf3b38939e681fb51d6c674151cee78b3d0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779172"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="15bce-102">Operator == (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="15bce-102">== Operator (C# Reference)</span></span>
<span data-ttu-id="15bce-103">Dla wstępnie zdefiniowanych typów wartości, operatora równości (`==`) zwraca wartość true, jeśli wartości argumentów są takie same `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="15bce-103">For predefined value types, the equality operator (`==`) returns true if the values of its operands are equal, `false` otherwise.</span></span> <span data-ttu-id="15bce-104">Dla odwołania do typów innych niż [ciąg](../../../csharp/language-reference/keywords/string.md), `==` zwraca `true` Jeśli dwóch argumentów operacji odnoszą się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="15bce-104">For reference types other than [string](../../../csharp/language-reference/keywords/string.md), `==` returns `true` if its two operands refer to the same object.</span></span> <span data-ttu-id="15bce-105">Aby uzyskać `string` typu `==` porównuje wartości ciągów.</span><span class="sxs-lookup"><span data-stu-id="15bce-105">For the `string` type, `==` compares the values of the strings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15bce-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15bce-106">Remarks</span></span>  
 <span data-ttu-id="15bce-107">Typy wartości zdefiniowanej przez użytkownika może doprowadzić do przeciążenia `==` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="15bce-107">User-defined value types can overload the `==` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="15bce-108">Ty też typy odwołań zdefiniowanych przez użytkownika, mimo że domyślnie `==` zachowuje się jak opisano powyżej dla obu typów referencyjnych wstępnie zdefiniowanych i zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="15bce-108">So can user-defined reference types, although by default `==` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="15bce-109">Jeśli `==` jest przeciążona, [! =](../../../csharp/language-reference/operators/not-equal-operator.md) musi również być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="15bce-109">If `==` is overloaded, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="15bce-110">Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone.</span><span class="sxs-lookup"><span data-stu-id="15bce-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15bce-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="15bce-111">Example</span></span>  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="15bce-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15bce-112">See Also</span></span>

- [<span data-ttu-id="15bce-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="15bce-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="15bce-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="15bce-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="15bce-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="15bce-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
