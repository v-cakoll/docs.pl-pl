---
title: Operator ~ (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a9b0cabcb101fce8422b1390ec8c4cb3b3849631
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4003d-102">Operator ~ (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4003d-102">~ Operator (C# Reference)</span></span>
<span data-ttu-id="4003d-103">`~` Operator wykonuje operację dopełnienia bitowego na jej argument operacji ma wpływ każdy bit cofania.</span><span class="sxs-lookup"><span data-stu-id="4003d-103">The `~` operator performs a bitwise complement operation on its operand, which has the effect of reversing each bit.</span></span> <span data-ttu-id="4003d-104">Operatory bitowe dopełnienia są wstępnie zdefiniowane dla [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długi](../../../csharp/language-reference/keywords/long.md), i [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="4003d-104">Bitwise complement operators are predefined for [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), and [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4003d-105">`~` Symbol służy również do deklarowania finalizatory.</span><span class="sxs-lookup"><span data-stu-id="4003d-105">The `~` symbol also is used to declare finalizers.</span></span> <span data-ttu-id="4003d-106">Aby uzyskać więcej informacji, zobacz [finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="4003d-106">For more information, see [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4003d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4003d-107">Remarks</span></span>  
 <span data-ttu-id="4003d-108">Typy definiowane przez użytkownika można przeciążać `~` operatora.</span><span class="sxs-lookup"><span data-stu-id="4003d-108">User-defined types can overload the `~` operator.</span></span> <span data-ttu-id="4003d-109">Aby uzyskać więcej informacji, zobacz [operator](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="4003d-109">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="4003d-110">Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="4003d-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4003d-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="4003d-111">Example</span></span>  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4003d-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4003d-112">See Also</span></span>  
 [<span data-ttu-id="4003d-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="4003d-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4003d-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4003d-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4003d-115">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="4003d-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="4003d-116">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="4003d-116">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
