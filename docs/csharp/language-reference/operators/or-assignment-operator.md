---
title: '| = — operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: f4f7806c8679af400a371decd0c367929b3fb81d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333268"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="40e1d-102">| = — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="40e1d-102">|= operator (C# Reference)</span></span>

<span data-ttu-id="40e1d-103">Operator przypisania OR.</span><span class="sxs-lookup"><span data-stu-id="40e1d-103">The OR assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="40e1d-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40e1d-104">Remarks</span></span>

<span data-ttu-id="40e1d-105">Wyrażenie używające operatora przypisania `|=`, takie jak</span><span class="sxs-lookup"><span data-stu-id="40e1d-105">An expression using the `|=` assignment operator, such as</span></span>

```csharp
x |= y
```

<span data-ttu-id="40e1d-106">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="40e1d-106">is equivalent to</span></span>

```csharp
x = x | y
```

<span data-ttu-id="40e1d-107">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="40e1d-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="40e1d-108">[ &#124; Operator](or-operator.md) wykonuje bitowe logicznej operacji lub w przypadku argumentów operacji typu całkowitego i operator logiczny lub w przypadku argumentów bool operacji.</span><span class="sxs-lookup"><span data-stu-id="40e1d-108">The [&#124; operator](or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>

<span data-ttu-id="40e1d-109">`|=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [ &#124; operator](or-operator.md) (zobacz [operator](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="40e1d-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](or-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="40e1d-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="40e1d-110">Example</span></span>

[!code-csharp[csRefOperators#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#10)]

## <a name="see-also"></a><span data-ttu-id="40e1d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40e1d-111">See also</span></span>

- [<span data-ttu-id="40e1d-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="40e1d-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="40e1d-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="40e1d-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="40e1d-114">C#Operatory</span><span class="sxs-lookup"><span data-stu-id="40e1d-114">C# operators</span></span>](index.md)