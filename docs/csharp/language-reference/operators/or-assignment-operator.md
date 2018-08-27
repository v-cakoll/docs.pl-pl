---
title: '|= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: fe56005ce94656b5e8a075cddfb91dc0da096cf7
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929917"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="17235-102">|= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="17235-102">|= Operator (C# Reference)</span></span>
<span data-ttu-id="17235-103">Operator przypisania OR.</span><span class="sxs-lookup"><span data-stu-id="17235-103">The OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17235-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17235-104">Remarks</span></span>  
 <span data-ttu-id="17235-105">Wyrażenie używające operatora przypisania `|=`, takie jak</span><span class="sxs-lookup"><span data-stu-id="17235-105">An expression using the `|=` assignment operator, such as</span></span>  
  
```csharp  
x |= y  
```  
  
 <span data-ttu-id="17235-106">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="17235-106">is equivalent to</span></span>  
  
```csharp  
x = x | y  
```  
  
 <span data-ttu-id="17235-107">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="17235-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="17235-108">[ &#124; Operator](../../../csharp/language-reference/operators/or-operator.md) wykonuje bitowe logicznej operacji lub w przypadku argumentów operacji typu całkowitego i operator logiczny lub w przypadku argumentów bool operacji.</span><span class="sxs-lookup"><span data-stu-id="17235-108">The [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>  
  
 <span data-ttu-id="17235-109">`|=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [ &#124; operator](../../../csharp/language-reference/operators/or-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="17235-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="17235-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="17235-110">Example</span></span>  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="17235-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17235-111">See Also</span></span>

- [<span data-ttu-id="17235-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="17235-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="17235-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="17235-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="17235-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="17235-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
