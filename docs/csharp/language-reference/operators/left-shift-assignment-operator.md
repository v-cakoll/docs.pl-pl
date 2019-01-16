---
title: '&lt;&lt;= — operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: 4513c4b78dea3e8102c72a43249b4a44ffa2421d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333255"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="b7242-102">&lt;&lt;= — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="b7242-102">&lt;&lt;= operator (C# Reference)</span></span>

<span data-ttu-id="b7242-103">Operator przypisania przesunięcia w lewo.</span><span class="sxs-lookup"><span data-stu-id="b7242-103">The left-shift assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7242-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7242-104">Remarks</span></span>

<span data-ttu-id="b7242-105">Wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="b7242-105">An expression of the form</span></span>

```csharp
x <<= y
```

<span data-ttu-id="b7242-106">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="b7242-106">is evaluated as</span></span>

```csharp
x = x << y
```

<span data-ttu-id="b7242-107">z tą różnicą, że `x` jest obliczone tylko raz.</span><span class="sxs-lookup"><span data-stu-id="b7242-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="b7242-108">[Operator <<](left-shift-operator.md) przesuwa `x` w lewo o liczbę bitów określoną przez `y`.</span><span class="sxs-lookup"><span data-stu-id="b7242-108">The [<< operator](left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>

<span data-ttu-id="b7242-109">Operatora `<<=` nie można przeciążyć bezpośrednio, ale [operator <<](left-shift-operator.md) (zobacz [operator](../keywords/operator.md)) może zostać przeciążony w typach danych zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b7242-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](left-shift-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="b7242-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="b7242-110">Example</span></span>

[!code-csharp[csRefOperators#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#12)]

## <a name="see-also"></a><span data-ttu-id="b7242-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7242-111">See also</span></span>

- [<span data-ttu-id="b7242-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b7242-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b7242-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b7242-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b7242-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="b7242-114">C# Operators</span></span>](index.md)
