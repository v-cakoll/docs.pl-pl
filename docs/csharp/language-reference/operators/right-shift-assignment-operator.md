---
title: '&gt;&gt;= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: f2bac6a4320980d80a9b6c2597dcf8dc6f08ac70
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43252814"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="10ac2-102">&gt;&gt;= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="10ac2-102">&gt;&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="10ac2-103">Operator przypisania przesunięcia w prawo.</span><span class="sxs-lookup"><span data-stu-id="10ac2-103">The right-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10ac2-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="10ac2-104">Remarks</span></span>  
 <span data-ttu-id="10ac2-105">Wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="10ac2-105">An expression of the form</span></span>  
  
```csharp  
x >>= y  
```  
  
 <span data-ttu-id="10ac2-106">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="10ac2-106">is evaluated as</span></span>  
  
```csharp  
x = x >> y  
```  
  
 <span data-ttu-id="10ac2-107">z tą różnicą, że `x` jest obliczone tylko raz.</span><span class="sxs-lookup"><span data-stu-id="10ac2-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="10ac2-108">[Operator >>](../../../csharp/language-reference/operators/right-shift-operator.md) przesuwa `x` w prawo o liczbę bitów określoną przez `y`.</span><span class="sxs-lookup"><span data-stu-id="10ac2-108">The [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>  
  
 <span data-ttu-id="10ac2-109">Operatora [ nie można przeciążyć bezpośrednio, ale ](../../../csharp/language-reference/operators/right-shift-operator.md)operator >>[ (zobacz ](../../../csharp/language-reference/keywords/operator.md)operator) może zostać przeciążony w typach danych zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="10ac2-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10ac2-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="10ac2-110">Example</span></span>  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="10ac2-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10ac2-111">See Also</span></span>

- [<span data-ttu-id="10ac2-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="10ac2-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="10ac2-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="10ac2-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="10ac2-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="10ac2-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
