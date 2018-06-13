---
title: Operator == (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: f8356320817771cb559192c1ce720a80bf33bbf9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273390"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="cf02f-102">Operator == (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cf02f-102">== Operator (C# Reference)</span></span>
<span data-ttu-id="cf02f-103">Dla wstępnie zdefiniowanych typów wartości, operator równości (`==`) zwraca wartość true, jeśli wartości argumentów są takie same, `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="cf02f-103">For predefined value types, the equality operator (`==`) returns true if the values of its operands are equal, `false` otherwise.</span></span> <span data-ttu-id="cf02f-104">Dla odwołania do typów innych niż [ciąg](../../../csharp/language-reference/keywords/string.md), `==` zwraca `true` Jeśli swoich argumentów, dwóch odwołują się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="cf02f-104">For reference types other than [string](../../../csharp/language-reference/keywords/string.md), `==` returns `true` if its two operands refer to the same object.</span></span> <span data-ttu-id="cf02f-105">Aby uzyskać `string` typu `==` porównuje wartości ciągów.</span><span class="sxs-lookup"><span data-stu-id="cf02f-105">For the `string` type, `==` compares the values of the strings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf02f-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cf02f-106">Remarks</span></span>  
 <span data-ttu-id="cf02f-107">Typy wartości zdefiniowane przez użytkownika można przeciążać `==` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="cf02f-107">User-defined value types can overload the `==` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="cf02f-108">Dlatego można typy odwołań zdefiniowanych przez użytkownika, mimo że domyślnie `==` zachowuje się jak opisano powyżej dla obu typów odniesienia wstępnie zdefiniowane i zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cf02f-108">So can user-defined reference types, although by default `==` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="cf02f-109">Jeśli `==` jest przeciążony [! =](../../../csharp/language-reference/operators/not-equal-operator.md) również musi być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="cf02f-109">If `==` is overloaded, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="cf02f-110">Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="cf02f-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf02f-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf02f-111">Example</span></span>  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cf02f-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf02f-112">See Also</span></span>  
 [<span data-ttu-id="cf02f-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="cf02f-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="cf02f-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cf02f-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cf02f-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="cf02f-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
