---
title: Operator ^= (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: d6546f23ffb6dee792339a7e3863bf58ae668d58
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857235"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ea045-102">Operator ^= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ea045-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="ea045-103">Operator przypisania OR wyłączne.</span><span class="sxs-lookup"><span data-stu-id="ea045-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea045-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea045-104">Remarks</span></span>  
 <span data-ttu-id="ea045-105">Wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="ea045-105">An expression of the form</span></span>  
  
```csharp  
x ^= y  
```  
  
 <span data-ttu-id="ea045-106">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="ea045-106">is evaluated as</span></span>  
  
```csharp  
x = x ^ y  
```  
  
 <span data-ttu-id="ea045-107">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="ea045-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="ea045-108">[^ — Operator](../../../csharp/language-reference/operators/xor-operator.md) wykonuje OR wyłączne operacja bitowa na operandach typu całkowitego i logiczne OR wyłączne na [bool](../../../csharp/language-reference/keywords/bool.md) argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="ea045-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="ea045-109">^ = — Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [^ — operator](../../../csharp/language-reference/operators/xor-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="ea045-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea045-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea045-110">Example</span></span>  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ea045-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea045-111">See Also</span></span>

- [<span data-ttu-id="ea045-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ea045-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="ea045-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ea045-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ea045-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="ea045-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
