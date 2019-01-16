---
title: ^ = — operator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: 12189d6469a9716d3b7ebcffef23423a75692d1a
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333554"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4bbac-102">^ = — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="4bbac-102">^= operator (C# Reference)</span></span>

<span data-ttu-id="4bbac-103">Operator przypisania OR wyłączne.</span><span class="sxs-lookup"><span data-stu-id="4bbac-103">The exclusive-OR assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="4bbac-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4bbac-104">Remarks</span></span>

<span data-ttu-id="4bbac-105">Wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="4bbac-105">An expression of the form</span></span>

```csharp
x ^= y
```

<span data-ttu-id="4bbac-106">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="4bbac-106">is evaluated as</span></span>

```csharp
x = x ^ y
```

<span data-ttu-id="4bbac-107">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="4bbac-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="4bbac-108">[^ — Operator](xor-operator.md) wykonuje OR wyłączne operacja bitowa na operandach typu całkowitego i logiczne OR wyłączne na [bool](../keywords/bool.md) argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="4bbac-108">The [^ operator](xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../keywords/bool.md) operands.</span></span>

<span data-ttu-id="4bbac-109">^ = — Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [^ — operator](xor-operator.md) (zobacz [operator](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="4bbac-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](xor-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="4bbac-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="4bbac-110">Example</span></span>

[!code-csharp[csRefOperators#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#23)]

## <a name="see-also"></a><span data-ttu-id="4bbac-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4bbac-111">See also</span></span>

- [<span data-ttu-id="4bbac-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4bbac-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4bbac-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4bbac-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4bbac-114">C#Operatory</span><span class="sxs-lookup"><span data-stu-id="4bbac-114">C# operators</span></span>](index.md)