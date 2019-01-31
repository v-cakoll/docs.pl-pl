---
title: << = — operator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: 0a005efa19be24f9adbf9031f562a30f9c1b0e34
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258737"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d13de-102">\<\<= — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="d13de-102">\<\<= operator (C# Reference)</span></span>

<span data-ttu-id="d13de-103">Operator przypisania przesunięcia w lewo.</span><span class="sxs-lookup"><span data-stu-id="d13de-103">The left-shift assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="d13de-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d13de-104">Remarks</span></span>

<span data-ttu-id="d13de-105">Wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="d13de-105">An expression of the form</span></span>

```csharp
x <<= y
```

<span data-ttu-id="d13de-106">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="d13de-106">is evaluated as</span></span>

```csharp
x = x << y
```

<span data-ttu-id="d13de-107">z tą różnicą, że `x` jest obliczone tylko raz.</span><span class="sxs-lookup"><span data-stu-id="d13de-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="d13de-108">[Operator <<](left-shift-operator.md) przesuwa `x` w lewo o liczbę bitów określoną przez `y`.</span><span class="sxs-lookup"><span data-stu-id="d13de-108">The [<< operator](left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>

<span data-ttu-id="d13de-109">Operatora `<<=` nie można przeciążyć bezpośrednio, ale [operator <<](left-shift-operator.md) (zobacz [operator](../keywords/operator.md)) może zostać przeciążony w typach danych zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d13de-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](left-shift-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="d13de-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="d13de-110">Example</span></span>

[!code-csharp[csRefOperators#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#12)]

## <a name="see-also"></a><span data-ttu-id="d13de-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d13de-111">See also</span></span>

- [<span data-ttu-id="d13de-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d13de-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d13de-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d13de-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d13de-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="d13de-114">C# Operators</span></span>](index.md)
