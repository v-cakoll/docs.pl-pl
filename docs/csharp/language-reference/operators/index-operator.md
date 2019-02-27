---
title: operator [] — C# odwołania
ms.custom: seodec18
ms.date: 01/10/2019
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 9088393f61d300ee76e56e320bec17b4a79bfebb
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835593"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f87d6-102">[] — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="f87d6-102">[] operator (C# Reference)</span></span>

<span data-ttu-id="f87d6-103">Nawiasy kwadratowe `[]`, są zwykle używane do dostępu do elementu tablicy, indeksator lub wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="f87d6-103">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

<span data-ttu-id="f87d6-104">Aby uzyskać więcej informacji o dostępie do elementu wskaźnika, zobacz [porady: uzyskiwanie dostępu do elementu tablicy za pomocą wskaźnika](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="f87d6-104">For more information about pointer element access, see [How to: access an array element with a pointer](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span></span>

<span data-ttu-id="f87d6-105">Nawiasy kwadratowe również służy do określania [atrybuty](../../programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="f87d6-105">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="array-access"></a><span data-ttu-id="f87d6-106">Dostęp do tablicy</span><span class="sxs-lookup"><span data-stu-id="f87d6-106">Array access</span></span>

<span data-ttu-id="f87d6-107">Poniższy przykład pokazuje, jak uzyskać dostęp do elementów tablicy:</span><span class="sxs-lookup"><span data-stu-id="f87d6-107">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Arrays)]

<span data-ttu-id="f87d6-108">Jeśli indeks tablicy jest poza granicami odpowiedniego wymiaru tablicy, <xref:System.IndexOutOfRangeException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="f87d6-108">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="f87d6-109">Jak pokazano na poprzednim przykładzie, możesz także użyć nawiasy kwadratowe w deklaracji typu tablicowego i konkretyzacji wystąpień tablicy.</span><span class="sxs-lookup"><span data-stu-id="f87d6-109">As the preceding example shows, you also use square brackets in declaration of an array type and instantiation of array instances.</span></span>

<span data-ttu-id="f87d6-110">Aby uzyskać więcej informacji na temat tablic, zobacz [tablic](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f87d6-110">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="indexer-access"></a><span data-ttu-id="f87d6-111">Dostęp indeksatora</span><span class="sxs-lookup"><span data-stu-id="f87d6-111">Indexer access</span></span>

<span data-ttu-id="f87d6-112">W poniższym przykładzie użyto .NET <xref:System.Collections.Generic.Dictionary%602> typu, aby zademonstrować dostęp indeksatora:</span><span class="sxs-lookup"><span data-stu-id="f87d6-112">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Indexers)]

<span data-ttu-id="f87d6-113">Indeksatory pozwalają na indeks wystąpienia typu zdefiniowanego przez użytkownika w podobny sposób jak indeksowanie tablicy.</span><span class="sxs-lookup"><span data-stu-id="f87d6-113">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="f87d6-114">W przeciwieństwie do tablicy wskaźników, które musi być liczbą całkowitą, argumenty indeksator może być zadeklarowana jako dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="f87d6-114">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="f87d6-115">Aby uzyskać więcej informacji na temat indeksatorów, zobacz [indeksatory](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="f87d6-115">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="f87d6-116">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="f87d6-116">Operator overloadability</span></span>

<span data-ttu-id="f87d6-117">Dostęp do elementu `[]` nie jest uważany za z możliwością przeciążenia operatora.</span><span class="sxs-lookup"><span data-stu-id="f87d6-117">Element access `[]` is not considered an overloadable operator.</span></span> <span data-ttu-id="f87d6-118">Użyj [indeksatory](../../programming-guide/indexers/index.md) do obsługi indeksowanie z typami zdefiniowanymi przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f87d6-118">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f87d6-119">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f87d6-119">C# language specification</span></span>

<span data-ttu-id="f87d6-120">Aby uzyskać więcej informacji, zobacz [dostępu do elementu](~/_csharplang/spec/expressions.md#element-access) i [wskaźnika elementu dostępu](~/_csharplang/spec/unsafe-code.md#pointer-element-access) sekcje [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f87d6-120">For more information, see the [Element access](~/_csharplang/spec/expressions.md#element-access) and [Pointer element access](~/_csharplang/spec/unsafe-code.md#pointer-element-access) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f87d6-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f87d6-121">See also</span></span>

- [<span data-ttu-id="f87d6-122">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f87d6-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f87d6-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f87d6-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f87d6-124">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="f87d6-124">C# Operators</span></span>](index.md)
- [<span data-ttu-id="f87d6-125">Tablice</span><span class="sxs-lookup"><span data-stu-id="f87d6-125">Arrays</span></span>](../../programming-guide/arrays/index.md)
- [<span data-ttu-id="f87d6-126">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="f87d6-126">Indexers</span></span>](../../programming-guide/indexers/index.md)
- [<span data-ttu-id="f87d6-127">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="f87d6-127">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="f87d6-128">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f87d6-128">Attributes</span></span>](../../programming-guide/concepts/attributes/index.md)
- <span data-ttu-id="f87d6-129">[?. i? Operatory]](null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="f87d6-129">[?. and ?[] operators](null-conditional-operators.md)</span></span>