---
title: -&gt; Operator (odwołanie w C#)
ms.date: 11/26/2018
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: 178724ede105d809bd812461121a38d5a0e90517
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144133"
---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="3114b-102">-&gt; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3114b-102">-&gt; Operator (C# Reference)</span></span>

<span data-ttu-id="3114b-103">Operator dostępu do elementu członkowskiego wskaźnika `->` łączy dostępu wskaźnika pośredniego i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="3114b-103">The pointer member access operator `->` combines pointer indirection and member access.</span></span>

<span data-ttu-id="3114b-104">Jeśli `x` jest wskaźnikiem typu `T*` i `y` jest dostępny członek `T`, wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="3114b-104">If `x` is a pointer of the type `T*` and `y` is an accessible member of `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="3114b-105">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="3114b-105">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="3114b-106">`->` Operator wymaga [niebezpieczne](../keywords/unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="3114b-106">The `->` operator requires [unsafe](../keywords/unsafe.md) context.</span></span>

<span data-ttu-id="3114b-107">Aby uzyskać więcej informacji, zobacz [porady: uzyskiwanie dostępu do członka za pomocą wskaźnika](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="3114b-107">For more information, see [How to: access a member with a pointer](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="3114b-108">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="3114b-108">Operator overloadability</span></span>

<span data-ttu-id="3114b-109">Operator `->` nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="3114b-109">The `->` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3114b-110">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3114b-110">C# language specification</span></span>

<span data-ttu-id="3114b-111">Aby uzyskać więcej informacji, zobacz [dostęp do elementu członkowskiego wskaźnika](~/_csharplang/spec/unsafe-code.md#pointer-member-access) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3114b-111">For more information, see the [Pointer member access](~/_csharplang/spec/unsafe-code.md#pointer-member-access) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3114b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3114b-112">See also</span></span>

- [<span data-ttu-id="3114b-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3114b-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3114b-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3114b-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3114b-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="3114b-115">C# Operators</span></span>](index.md)
- [<span data-ttu-id="3114b-116">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="3114b-116">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
