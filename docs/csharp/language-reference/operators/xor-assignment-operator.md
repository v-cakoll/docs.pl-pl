---
title: Operator ^= (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: b868f2cdbfa8a80f89a12e6194a30154481f0b07
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172376"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0f24d-102">Operator ^= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0f24d-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="0f24d-103">Operator przypisania OR wyłączne.</span><span class="sxs-lookup"><span data-stu-id="0f24d-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f24d-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0f24d-104">Remarks</span></span>  
 <span data-ttu-id="0f24d-105">Wyrażenie w postaci</span><span class="sxs-lookup"><span data-stu-id="0f24d-105">An expression of the form</span></span>  
  
```csharp  
x ^= y  
```  
  
 <span data-ttu-id="0f24d-106">jest szacowana jako</span><span class="sxs-lookup"><span data-stu-id="0f24d-106">is evaluated as</span></span>  
  
```csharp  
x = x ^ y  
```  
  
 <span data-ttu-id="0f24d-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="0f24d-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="0f24d-108">[^ — Operator](../../../csharp/language-reference/operators/xor-operator.md) wykonuje OR wyłączne operacji na całkowite operandy i logicznego OR wyłączne na [bool](../../../csharp/language-reference/keywords/bool.md) argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="0f24d-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="0f24d-109">^ = — Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [^ — operator](../../../csharp/language-reference/operators/xor-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="0f24d-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f24d-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f24d-110">Example</span></span>  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0f24d-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f24d-111">See Also</span></span>  
 [<span data-ttu-id="0f24d-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="0f24d-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0f24d-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0f24d-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0f24d-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="0f24d-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
