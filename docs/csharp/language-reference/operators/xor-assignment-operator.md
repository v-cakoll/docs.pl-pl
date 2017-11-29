---
title: "Operator ^= (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ^=_CSharpKeyword
helpviewer_keywords: ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d4de06dbfd269dc5e0f2cc5003e8981068220a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6bcfe-102">Operator ^= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6bcfe-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="6bcfe-103">Operator przypisania OR wyłączne.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bcfe-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6bcfe-104">Remarks</span></span>  
 <span data-ttu-id="6bcfe-105">Wyrażenie w postaci</span><span class="sxs-lookup"><span data-stu-id="6bcfe-105">An expression of the form</span></span>  
  
```  
x ^= y  
```  
  
 <span data-ttu-id="6bcfe-106">jest szacowana jako</span><span class="sxs-lookup"><span data-stu-id="6bcfe-106">is evaluated as</span></span>  
  
```  
x = x ^ y  
```  
  
 <span data-ttu-id="6bcfe-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="6bcfe-108">[^ — Operator](../../../csharp/language-reference/operators/xor-operator.md) wykonuje OR wyłączne operacji na całkowite operandy i logicznego OR wyłączne na [bool](../../../csharp/language-reference/keywords/bool.md) argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="6bcfe-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="6bcfe-109">^ = — Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [^ — operator](../../../csharp/language-reference/operators/xor-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="6bcfe-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bcfe-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="6bcfe-110">Example</span></span>  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6bcfe-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6bcfe-111">See Also</span></span>  
 [<span data-ttu-id="6bcfe-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="6bcfe-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6bcfe-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6bcfe-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6bcfe-114">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="6bcfe-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
