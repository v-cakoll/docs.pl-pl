---
title: '&amp;= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: 092f46ddd8ca52e2d705200768c93a3473f1520f
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="b03aa-102">&amp;= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="b03aa-102">&amp;= Operator (C# Reference)</span></span>
<span data-ttu-id="b03aa-103">Operator przypisania AND.</span><span class="sxs-lookup"><span data-stu-id="b03aa-103">The AND assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b03aa-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b03aa-104">Remarks</span></span>  
 <span data-ttu-id="b03aa-105">Za pomocą wyrażenia `&=` operator przypisania, takich jak</span><span class="sxs-lookup"><span data-stu-id="b03aa-105">An expression using the `&=` assignment operator, such as</span></span>  
  
```csharp  
x &= y  
```  
  
 <span data-ttu-id="b03aa-106">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="b03aa-106">is equivalent to</span></span>  
  
```csharp  
x = x & y  
```  
  
 <span data-ttu-id="b03aa-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="b03aa-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="b03aa-108">[& — Operator](../../../csharp/language-reference/operators/and-operator.md) dokonuje logicznego operacji i na całkowite argumenty i logiczny AND `bool` argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="b03aa-108">The [& operator](../../../csharp/language-reference/operators/and-operator.md) performs a bitwise logical AND operation on integral operands and logical AND on `bool` operands.</span></span>  
  
 <span data-ttu-id="b03aa-109">`&=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać plik binarny [& — operator](../../../csharp/language-reference/operators/and-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="b03aa-109">The `&=` operator cannot be overloaded directly, but user-defined types can overload the binary [& operator](../../../csharp/language-reference/operators/and-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b03aa-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="b03aa-110">Example</span></span>  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b03aa-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b03aa-111">See Also</span></span>  
 [<span data-ttu-id="b03aa-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="b03aa-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b03aa-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b03aa-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b03aa-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="b03aa-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
