---
title: char — słowo C# kluczowe-odwołanie
ms.custom: seodec18
ms.date: 10/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 1b9f8d1bb205a6cbfe521830a11bd8878ccde991
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771800"
---
# <a name="char-c-reference"></a><span data-ttu-id="9d008-102">char (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="9d008-102">char (C# reference)</span></span>

<span data-ttu-id="9d008-103">Słowo kluczowe typu `char` jest aliasem dla typu struktury <xref:System.Char?displayProperty=nameWithType> .NET, który reprezentuje znak Unicode UTF-16:</span><span class="sxs-lookup"><span data-stu-id="9d008-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character:</span></span>

|<span data-ttu-id="9d008-104">Typ</span><span class="sxs-lookup"><span data-stu-id="9d008-104">Type</span></span>|<span data-ttu-id="9d008-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="9d008-105">Range</span></span>|<span data-ttu-id="9d008-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="9d008-106">Size</span></span>|<span data-ttu-id="9d008-107">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="9d008-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="9d008-108">U + 0000 do U + FFFF</span><span class="sxs-lookup"><span data-stu-id="9d008-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="9d008-109">16 bitów</span><span class="sxs-lookup"><span data-stu-id="9d008-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="9d008-110">Literały</span><span class="sxs-lookup"><span data-stu-id="9d008-110">Literals</span></span>

<span data-ttu-id="9d008-111">Stałe typu `char` mogą być zapisywane jako literały znakowe, szesnastkowe sekwencje ucieczki lub reprezentację Unicode.</span><span class="sxs-lookup"><span data-stu-id="9d008-111">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="9d008-112">Można również rzutować kod znaku całkowitego na odpowiadającą wartość `char`.</span><span class="sxs-lookup"><span data-stu-id="9d008-112">You can also cast an integral character code into the corresponding `char` value.</span></span> <span data-ttu-id="9d008-113">W poniższym przykładzie cztery elementy tablicy `char` są inicjowane przy użyciu tego samego znaku `X`:</span><span class="sxs-lookup"><span data-stu-id="9d008-113">In the following example, the four elements of an array of `char` are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="9d008-114">Konwersje</span><span class="sxs-lookup"><span data-stu-id="9d008-114">Conversions</span></span>

<span data-ttu-id="9d008-115">Typ `char` jest niejawnie konwertowany na następujące typy [całkowite](../builtin-types/integral-numeric-types.md) : `ushort`, `int`, `uint`, `long` i `ulong`.</span><span class="sxs-lookup"><span data-stu-id="9d008-115">The `char` type is implicitly convertible to the following [integral](../builtin-types/integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="9d008-116">Jest on również niejawnie konwertowany na wbudowane typy liczbowe [zmiennoprzecinkowe](../builtin-types/floating-point-numeric-types.md) : `float`, `double` i `decimal`.</span><span class="sxs-lookup"><span data-stu-id="9d008-116">It's also implicitly convertible to the built-in [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="9d008-117">Jest on jawnie konwertowany na `sbyte`, `byte` i `short` typów całkowitych.</span><span class="sxs-lookup"><span data-stu-id="9d008-117">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="9d008-118">Brak niejawnych konwersji z innych typów na typ `char`.</span><span class="sxs-lookup"><span data-stu-id="9d008-118">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="9d008-119">Jednak każdy typ liczbowy [całkowitego](../builtin-types/integral-numeric-types.md) lub [zmiennoprzecinkowego](../builtin-types/floating-point-numeric-types.md) jest jawnie konwertowany do `char`.</span><span class="sxs-lookup"><span data-stu-id="9d008-119">However, any [integral](../builtin-types/integral-numeric-types.md) or [floating-point](../builtin-types/floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9d008-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9d008-120">C# language specification</span></span>

<span data-ttu-id="9d008-121">Aby uzyskać więcej informacji, zobacz sekcję [Typy całkowite](~/_csharplang/spec/types.md#integral-types) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="9d008-121">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d008-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d008-122">See also</span></span>

- [<span data-ttu-id="9d008-123">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="9d008-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9d008-124">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9d008-124">C# keywords</span></span>](./index.md)
- [<span data-ttu-id="9d008-125">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="9d008-125">Built-in types table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="9d008-126">Ciągi</span><span class="sxs-lookup"><span data-stu-id="9d008-126">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Char?displayProperty=nameWithType>
