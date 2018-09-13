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
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44707195"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c8634-102">|= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c8634-102">|= Operator (C# Reference)</span></span>
<span data-ttu-id="c8634-103">Operator przypisania OR.</span><span class="sxs-lookup"><span data-stu-id="c8634-103">The OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8634-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8634-104">Remarks</span></span>  
 <span data-ttu-id="c8634-105">Wyrażenie używające operatora przypisania `|=`, takie jak</span><span class="sxs-lookup"><span data-stu-id="c8634-105">An expression using the `|=` assignment operator, such as</span></span>  
  
```csharp  
x |= y  
```  
  
 <span data-ttu-id="c8634-106">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="c8634-106">is equivalent to</span></span>  
  
```csharp  
x = x | y  
```  
  
 <span data-ttu-id="c8634-107">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="c8634-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="c8634-108">[ &#124; Operator](../../../csharp/language-reference/operators/or-operator.md) wykonuje bitowe logicznej operacji lub w przypadku argumentów operacji typu całkowitego i operator logiczny lub w przypadku argumentów bool operacji.</span><span class="sxs-lookup"><span data-stu-id="c8634-108">The [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>  
  
 <span data-ttu-id="c8634-109">`|=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [ &#124; operator](../../../csharp/language-reference/operators/or-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="c8634-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8634-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8634-110">Example</span></span>  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c8634-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8634-111">See Also</span></span>

- [<span data-ttu-id="c8634-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c8634-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c8634-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c8634-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c8634-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="c8634-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
