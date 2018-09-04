---
title: Operator ~ (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 8af25217f9e7e66796192783a0b8e3415604dc90
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510114"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a5abd-102">Operator ~ (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a5abd-102">~ Operator (C# Reference)</span></span>
<span data-ttu-id="a5abd-103">Operator `~` wykonuje operację dopełnienia bitowego na jego argumencie operacji, która powoduje odwrócenie każdego z bitów.</span><span class="sxs-lookup"><span data-stu-id="a5abd-103">The `~` operator performs a bitwise complement operation on its operand, which has the effect of reversing each bit.</span></span> <span data-ttu-id="a5abd-104">Operatory dopełnienia bitowego są wstępnie zdefiniowane dla następujących typów: [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długi](../../../csharp/language-reference/keywords/long.md), i [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="a5abd-104">Bitwise complement operators are predefined for [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), and [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5abd-105">Symbol `~` służy również do deklarowania finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="a5abd-105">The `~` symbol also is used to declare finalizers.</span></span> <span data-ttu-id="a5abd-106">Aby uzyskać więcej informacji, zobacz [finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="a5abd-106">For more information, see [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5abd-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5abd-107">Remarks</span></span>  
 <span data-ttu-id="a5abd-108">Typy definiowane przez użytkownika mogą przeciążać operator `~`.</span><span class="sxs-lookup"><span data-stu-id="a5abd-108">User-defined types can overload the `~` operator.</span></span> <span data-ttu-id="a5abd-109">Aby uzyskać więcej informacji, zobacz [operator](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="a5abd-109">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="a5abd-110">Operacje na typach całkowitych są zazwyczaj dozwolone na wyliczeniach.</span><span class="sxs-lookup"><span data-stu-id="a5abd-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5abd-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5abd-111">Example</span></span>  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a5abd-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5abd-112">See Also</span></span>

- [<span data-ttu-id="a5abd-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a5abd-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a5abd-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a5abd-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a5abd-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="a5abd-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="a5abd-116">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="a5abd-116">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
