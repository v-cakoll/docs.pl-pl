---
title: '&lt;&lt;= — Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: f49c6360d6fee3f6d612aee51446545f25cd7d18
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239176"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="12a99-102">&lt;&lt;= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="12a99-102">&lt;&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="12a99-103">Operator przypisania przesunięcia w lewo.</span><span class="sxs-lookup"><span data-stu-id="12a99-103">The left-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12a99-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="12a99-104">Remarks</span></span>  
 <span data-ttu-id="12a99-105">Wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="12a99-105">An expression of the form</span></span>  
  
```csharp  
x <<= y  
```  
  
 <span data-ttu-id="12a99-106">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="12a99-106">is evaluated as</span></span>  
  
```csharp  
x = x << y  
```  
  
 <span data-ttu-id="12a99-107">z tą różnicą, że `x` jest obliczone tylko raz.</span><span class="sxs-lookup"><span data-stu-id="12a99-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="12a99-108">[Operator <<](../../../csharp/language-reference/operators/left-shift-operator.md) przesuwa `x` w lewo o liczbę bitów określoną przez `y`.</span><span class="sxs-lookup"><span data-stu-id="12a99-108">The [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>  
  
 <span data-ttu-id="12a99-109">Operatora `<<=` nie można przeciążyć bezpośrednio, ale [operator <<](../../../csharp/language-reference/operators/left-shift-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)) może zostać przeciążony w typach danych zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="12a99-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="12a99-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="12a99-110">Example</span></span>  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="12a99-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12a99-111">See Also</span></span>

- [<span data-ttu-id="12a99-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="12a99-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="12a99-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="12a99-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="12a99-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="12a99-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
