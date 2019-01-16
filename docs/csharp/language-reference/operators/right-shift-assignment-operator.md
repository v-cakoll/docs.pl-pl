---
title: '&gt;&gt;= — operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 02a9559a5c4086eeed09094c15c3620366ffad8c
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333695"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="b12f0-102">&gt;&gt;= — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="b12f0-102">&gt;&gt;= operator (C# Reference)</span></span>

<span data-ttu-id="b12f0-103">Operator przypisania przesunięcia w prawo.</span><span class="sxs-lookup"><span data-stu-id="b12f0-103">The right-shift assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="b12f0-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b12f0-104">Remarks</span></span>

<span data-ttu-id="b12f0-105">Wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="b12f0-105">An expression of the form</span></span>

```csharp
x >>= y
```

<span data-ttu-id="b12f0-106">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="b12f0-106">is evaluated as</span></span>

```csharp
x = x >> y
```

<span data-ttu-id="b12f0-107">z tą różnicą, że `x` jest obliczone tylko raz.</span><span class="sxs-lookup"><span data-stu-id="b12f0-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="b12f0-108">[Operator >>](right-shift-operator.md) przesuwa `x` w prawo o liczbę bitów określoną przez `y`.</span><span class="sxs-lookup"><span data-stu-id="b12f0-108">The [>> operator](right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>

<span data-ttu-id="b12f0-109">Operatora [ nie można przeciążyć bezpośrednio, ale ](right-shift-operator.md)operator >>[ (zobacz ](../keywords/operator.md)operator) może zostać przeciążony w typach danych zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b12f0-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](right-shift-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="b12f0-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="b12f0-110">Example</span></span>

[!code-csharp[csRefOperators#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#11)]

## <a name="see-also"></a><span data-ttu-id="b12f0-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b12f0-111">See also</span></span>

- [<span data-ttu-id="b12f0-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b12f0-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b12f0-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b12f0-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b12f0-114">C#Operatory</span><span class="sxs-lookup"><span data-stu-id="b12f0-114">C# operators</span></span>](index.md)