---
title: '&lt;&lt;= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: c689aeccdf3ad6cc6c672cc101a4f0aa92f19791
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406977"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="f8f41-102">&lt;&lt;= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f8f41-102">&lt;&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="f8f41-103">Operator przypisania przesunięcia w lewo.</span><span class="sxs-lookup"><span data-stu-id="f8f41-103">The left-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8f41-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8f41-104">Remarks</span></span>  
 <span data-ttu-id="f8f41-105">Wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="f8f41-105">An expression of the form</span></span>  
  
```csharp  
x <<= y  
```  
  
 <span data-ttu-id="f8f41-106">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="f8f41-106">is evaluated as</span></span>  
  
```csharp  
x = x << y  
```  
  
 <span data-ttu-id="f8f41-107">z tą różnicą, że `x` jest obliczone tylko raz.</span><span class="sxs-lookup"><span data-stu-id="f8f41-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f8f41-108">[Operator <<](../../../csharp/language-reference/operators/left-shift-operator.md) przesuwa `x` w lewo o liczbę bitów określoną przez `y`.</span><span class="sxs-lookup"><span data-stu-id="f8f41-108">The [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>  
  
 <span data-ttu-id="f8f41-109">Operatora `<<=` nie można przeciążyć bezpośrednio, ale [operator <<](../../../csharp/language-reference/operators/left-shift-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)) może zostać przeciążony w typach danych zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f8f41-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8f41-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8f41-110">Example</span></span>  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f8f41-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8f41-111">See Also</span></span>

- [<span data-ttu-id="f8f41-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f8f41-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="f8f41-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f8f41-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f8f41-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="f8f41-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
