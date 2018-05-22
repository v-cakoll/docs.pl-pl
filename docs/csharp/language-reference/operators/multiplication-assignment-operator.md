---
title: Operator *= (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 6bbf2142ca7e9e05010a29920da52e1439f6e882
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="79d20-102">Operator \*= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="79d20-102">\*= Operator (C# Reference)</span></span>
<span data-ttu-id="79d20-103">Operator przypisania mnożenia danych binarnych.</span><span class="sxs-lookup"><span data-stu-id="79d20-103">The binary multiplication assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79d20-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79d20-104">Remarks</span></span>  
 <span data-ttu-id="79d20-105">Wyrażenie używające operatora przypisania `*=`, takie jak</span><span class="sxs-lookup"><span data-stu-id="79d20-105">An expression using the `*=` assignment operator, such as</span></span>  
  
```csharp  
x *= y  
```  
  
 <span data-ttu-id="79d20-106">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="79d20-106">is equivalent to</span></span>  
  
```csharp  
x = x * y  
```  
  
 <span data-ttu-id="79d20-107">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="79d20-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="79d20-108">[Operator \*](../../../csharp/language-reference/operators/multiplication-operator.md) jest wstępnie zdefiniowany dla typów liczbowych do wykonania mnożenia.</span><span class="sxs-lookup"><span data-stu-id="79d20-108">The [\* operator](../../../csharp/language-reference/operators/multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>  
  
 <span data-ttu-id="79d20-109">Operator `*=` nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika mogą przeciążać [operator *](../../../csharp/language-reference/operators/multiplication-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="79d20-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="79d20-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="79d20-110">Example</span></span>  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="79d20-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79d20-111">See Also</span></span>  
 [<span data-ttu-id="79d20-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="79d20-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="79d20-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="79d20-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="79d20-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="79d20-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
