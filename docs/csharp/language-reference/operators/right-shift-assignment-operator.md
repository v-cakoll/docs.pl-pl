---
title: '>>= — operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 8cc341c14ee1b90fde2abb369c187e57b4ce5c00
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278983"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="bb121-102">>> = — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="bb121-102">>>= operator (C# Reference)</span></span>

<span data-ttu-id="bb121-103">Operator przypisania przesunięcia w prawo.</span><span class="sxs-lookup"><span data-stu-id="bb121-103">The right-shift assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb121-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb121-104">Remarks</span></span>

<span data-ttu-id="bb121-105">Wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="bb121-105">An expression of the form</span></span>

```csharp
x >>= y
```

<span data-ttu-id="bb121-106">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="bb121-106">is evaluated as</span></span>

```csharp
x = x >> y
```

<span data-ttu-id="bb121-107">z tą różnicą, że `x` jest obliczone tylko raz.</span><span class="sxs-lookup"><span data-stu-id="bb121-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="bb121-108">[Operator >>](right-shift-operator.md) przesuwa `x` w prawo o liczbę bitów określoną przez `y`.</span><span class="sxs-lookup"><span data-stu-id="bb121-108">The [>> operator](right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>

<span data-ttu-id="bb121-109">Operatora [ nie można przeciążyć bezpośrednio, ale ](right-shift-operator.md)operator >>[ (zobacz ](../keywords/operator.md)operator) może zostać przeciążony w typach danych zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bb121-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](right-shift-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="bb121-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb121-110">Example</span></span>

[!code-csharp[csRefOperators#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#11)]

## <a name="see-also"></a><span data-ttu-id="bb121-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb121-111">See also</span></span>

- [<span data-ttu-id="bb121-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bb121-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bb121-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bb121-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bb121-114">C#Operatory</span><span class="sxs-lookup"><span data-stu-id="bb121-114">C# operators</span></span>](index.md)