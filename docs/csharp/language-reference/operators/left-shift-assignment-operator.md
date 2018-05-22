---
title: '&lt;&lt;= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: e5f3886670baa34b0360501ee15280b93fac36bc
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="3c582-102">&lt;&lt;= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3c582-102">&lt;&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="3c582-103">Operator przypisania przesunięcia w lewo.</span><span class="sxs-lookup"><span data-stu-id="3c582-103">The left-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c582-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3c582-104">Remarks</span></span>  
 <span data-ttu-id="3c582-105">Wyrażenie w postaci</span><span class="sxs-lookup"><span data-stu-id="3c582-105">An expression of the form</span></span>  
  
```csharp  
x <<= y  
```  
  
 <span data-ttu-id="3c582-106">jest wykonywane w postaci</span><span class="sxs-lookup"><span data-stu-id="3c582-106">is evaluated as</span></span>  
  
```csharp  
x = x << y  
```  
  
 <span data-ttu-id="3c582-107">z tą różnicą, że `x` jest obliczone tylko raz.</span><span class="sxs-lookup"><span data-stu-id="3c582-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="3c582-108">[Operator <<](../../../csharp/language-reference/operators/left-shift-operator.md) przesuwa `x` w lewo o liczbę bitów określoną przez `y`.</span><span class="sxs-lookup"><span data-stu-id="3c582-108">The [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>  
  
 <span data-ttu-id="3c582-109">Operatora `<<=` nie można przeciążyć bezpośrednio, ale [operator <<](../../../csharp/language-reference/operators/left-shift-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)) może zostać przeciążony w typach danych zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3c582-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c582-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="3c582-110">Example</span></span>  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3c582-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c582-111">See Also</span></span>  
 [<span data-ttu-id="3c582-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="3c582-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3c582-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3c582-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3c582-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="3c582-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
