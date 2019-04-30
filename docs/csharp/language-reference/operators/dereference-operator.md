---
title: -> — Operator - C# odwołania
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: be74f02a85aa05cdab32768ed38222fc4d9289b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660017"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="1be2e-102">-> — Operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="1be2e-102">-> Operator (C# Reference)</span></span>

<span data-ttu-id="1be2e-103">Operator dostępu do elementu członkowskiego wskaźnika `->` łączy dostępu wskaźnika pośredniego i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="1be2e-103">The pointer member access operator `->` combines pointer indirection and member access.</span></span>

<span data-ttu-id="1be2e-104">Jeśli `x` jest wskaźnikiem typu `T*` i `y` jest dostępny członek `T`, wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="1be2e-104">If `x` is a pointer of the type `T*` and `y` is an accessible member of `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="1be2e-105">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="1be2e-105">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="1be2e-106">`->` Operator wymaga [niebezpieczne](../keywords/unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="1be2e-106">The `->` operator requires [unsafe](../keywords/unsafe.md) context.</span></span>

<span data-ttu-id="1be2e-107">Aby uzyskać więcej informacji, zobacz [porady: uzyskiwanie dostępu do członka za pomocą wskaźnika](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="1be2e-107">For more information, see [How to: access a member with a pointer](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="1be2e-108">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="1be2e-108">Operator overloadability</span></span>

<span data-ttu-id="1be2e-109">Operator `->` nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="1be2e-109">The `->` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1be2e-110">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1be2e-110">C# language specification</span></span>

<span data-ttu-id="1be2e-111">Aby uzyskać więcej informacji, zobacz [dostęp do elementu członkowskiego wskaźnika](~/_csharplang/spec/unsafe-code.md#pointer-member-access) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="1be2e-111">For more information, see the [Pointer member access](~/_csharplang/spec/unsafe-code.md#pointer-member-access) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1be2e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1be2e-112">See also</span></span>

- [<span data-ttu-id="1be2e-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1be2e-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1be2e-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1be2e-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1be2e-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="1be2e-115">C# Operators</span></span>](index.md)
- [<span data-ttu-id="1be2e-116">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="1be2e-116">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
