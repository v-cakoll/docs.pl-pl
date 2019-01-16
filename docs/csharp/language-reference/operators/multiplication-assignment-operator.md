---
title: '* = — Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 2038f3b55d46f3503496275b3d25b17663b8c1db
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333437"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1a91a-102">\*= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1a91a-102">\*= Operator (C# Reference)</span></span>

<span data-ttu-id="1a91a-103">Operator przypisania mnożenia danych binarnych.</span><span class="sxs-lookup"><span data-stu-id="1a91a-103">The binary multiplication assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a91a-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a91a-104">Remarks</span></span>

<span data-ttu-id="1a91a-105">Wyrażenie używające operatora przypisania `*=`, takie jak</span><span class="sxs-lookup"><span data-stu-id="1a91a-105">An expression using the `*=` assignment operator, such as</span></span>

```csharp
x *= y
```

<span data-ttu-id="1a91a-106">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="1a91a-106">is equivalent to</span></span>

```csharp
x = x * y
```

<span data-ttu-id="1a91a-107">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="1a91a-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="1a91a-108">[ \* Operator](multiplication-operator.md) wstępnie zdefiniowany dla typów liczbowych wykonać mnożenie.</span><span class="sxs-lookup"><span data-stu-id="1a91a-108">The [\* operator](multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>

<span data-ttu-id="1a91a-109">`*=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [ \* operator](multiplication-operator.md) (zobacz [operator](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="1a91a-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [\* operator](multiplication-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="1a91a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a91a-110">Example</span></span>

[!code-csharp[csRefOperators#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#13)]

## <a name="see-also"></a><span data-ttu-id="1a91a-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a91a-111">See also</span></span>

- [<span data-ttu-id="1a91a-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1a91a-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1a91a-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1a91a-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1a91a-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="1a91a-114">C# Operators</span></span>](index.md)
