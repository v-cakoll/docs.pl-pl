---
title: "Operator -- (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4eb68143103d44defeac7191e7c4ce7d1ee90e9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="---operator-c-reference"></a><span data-ttu-id="4c4a0-102">Operator -- (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4c4a0-102">-- Operator (C# Reference)</span></span>
<span data-ttu-id="4c4a0-103">Operator dekrementacji (`--`) zmniejsza jej argument operacji o 1.</span><span class="sxs-lookup"><span data-stu-id="4c4a0-103">The decrement operator (`--`) decrements its operand by 1.</span></span> <span data-ttu-id="4c4a0-104">Operator dekrementacji może występować przed lub po jej argument: `--variable` i `variable--`.</span><span class="sxs-lookup"><span data-stu-id="4c4a0-104">The decrement operator can appear before or after its operand: `--variable` and `variable--`.</span></span> <span data-ttu-id="4c4a0-105">Pierwszy formularz jest operacją dekrementacja prefiks.</span><span class="sxs-lookup"><span data-stu-id="4c4a0-105">The first form is a prefix decrement operation.</span></span> <span data-ttu-id="4c4a0-106">Wynikiem operacji jest wartość operandu "po" została zmniejszona.</span><span class="sxs-lookup"><span data-stu-id="4c4a0-106">The result of the operation is the value of the operand "after" it has been decremented.</span></span> <span data-ttu-id="4c4a0-107">Drugi formularz jest operacją dekrementacja przyrostek.</span><span class="sxs-lookup"><span data-stu-id="4c4a0-107">The second form is a postfix decrement operation.</span></span> <span data-ttu-id="4c4a0-108">Wynik operacji jest wartość operandu "przed" została zmniejszona.</span><span class="sxs-lookup"><span data-stu-id="4c4a0-108">The result of the operation is the value of the operand "before" it has been decremented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c4a0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c4a0-109">Remarks</span></span>  
 <span data-ttu-id="4c4a0-110">Typy numeryczne i wyliczenia mają wstępnie zdefiniowane dekrementacji.</span><span class="sxs-lookup"><span data-stu-id="4c4a0-110">Numeric and enumeration types have predefined decrement operators.</span></span>  
  
 <span data-ttu-id="4c4a0-111">Typy definiowane przez użytkownika można przeciążać `--` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="4c4a0-111">User-defined types can overload the `--` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="4c4a0-112">Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="4c4a0-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c4a0-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="4c4a0-113">Example</span></span>  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4c4a0-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c4a0-114">See Also</span></span>  
 [<span data-ttu-id="4c4a0-115">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="4c4a0-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4c4a0-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4c4a0-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4c4a0-117">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="4c4a0-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
