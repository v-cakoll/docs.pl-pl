---
title: '* Operator - C# odwołania'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: a5e120d26614f1e38cc2f2db02949552140b594e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977347"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="bbbf2-102">\* — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="bbbf2-102">\* operator (C# Reference)</span></span>

<span data-ttu-id="bbbf2-103">`*` Operator jest obsługiwany w dwóch formach: operatora jednoargumentowego operatora pośredniego wskaźnika lub operatora mnożenia danych binarnych.</span><span class="sxs-lookup"><span data-stu-id="bbbf2-103">The `*` operator is supported in two forms: a unary pointer indirection operator or a binary multiplication operator.</span></span>

## <a name="pointer-indirection-operator"></a><span data-ttu-id="bbbf2-104">Operatora pośredniego wskaźnika</span><span class="sxs-lookup"><span data-stu-id="bbbf2-104">Pointer indirection operator</span></span>

<span data-ttu-id="bbbf2-105">Użyj jednoargumentowego `*` operator można uzyskać zmiennej, na który wskazuje operand typu wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="bbbf2-105">Use the unary `*` operator to obtain the variable to which an operand of a pointer type points.</span></span> <span data-ttu-id="bbbf2-106">Aby uzyskać więcej informacji, zobacz [porady: uzyskiwanie wartości zmiennej wskaźnikowej](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-value-of-a-pointer-variable.md).</span><span class="sxs-lookup"><span data-stu-id="bbbf2-106">For more information, see [How to: obtain the value of a pointer variable](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-value-of-a-pointer-variable.md).</span></span>

<span data-ttu-id="bbbf2-107">Operatora pośredniego wskaźnika `*` wymaga [niebezpieczne](../keywords/unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="bbbf2-107">The pointer indirection operator `*` requires [unsafe](../keywords/unsafe.md) context.</span></span>

## <a name="multiplication-operator"></a><span data-ttu-id="bbbf2-108">Operator mnożenia</span><span class="sxs-lookup"><span data-stu-id="bbbf2-108">Multiplication operator</span></span>

<span data-ttu-id="bbbf2-109">Dla typów liczbowych `*` operator Oblicza iloczyn argumentów:</span><span class="sxs-lookup"><span data-stu-id="bbbf2-109">For numeric types, the `*` operator computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#Multiply)]

## <a name="operator-overloadability"></a><span data-ttu-id="bbbf2-110">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="bbbf2-110">Operator overloadability</span></span>

<span data-ttu-id="bbbf2-111">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) dane binarne `*` operatora.</span><span class="sxs-lookup"><span data-stu-id="bbbf2-111">User-defined types can [overload](../keywords/operator.md) a binary `*` operator.</span></span> <span data-ttu-id="bbbf2-112">Gdy dane binarne `*` operator jest przeciążony, [operator przypisania mnożenia](multiplication-assignment-operator.md) `*=` jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="bbbf2-112">When a binary `*` operator is overloaded, the [multiplication assignment operator](multiplication-assignment-operator.md) `*=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bbbf2-113">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bbbf2-113">C# language specification</span></span>

<span data-ttu-id="bbbf2-114">Aby uzyskać więcej informacji, zobacz [operację wskaźnika pośredniego](~/_csharplang/spec/unsafe-code.md#pointer-indirection) i [operator mnożenia](~/_csharplang/spec/expressions.md#multiplication-operator) sekcje [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="bbbf2-114">For more information, see the [Pointer indirection](~/_csharplang/spec/unsafe-code.md#pointer-indirection) and [Multiplication operator](~/_csharplang/spec/expressions.md#multiplication-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bbbf2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bbbf2-115">See also</span></span>

- [<span data-ttu-id="bbbf2-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bbbf2-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bbbf2-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bbbf2-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bbbf2-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="bbbf2-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="bbbf2-119">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="bbbf2-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)