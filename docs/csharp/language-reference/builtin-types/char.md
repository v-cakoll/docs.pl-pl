---
title: typ znaku — C# odwołanie
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: ab49b8cbddac2569d6063a5f312105bef3033e84
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552302"
---
# <a name="char-c-reference"></a><span data-ttu-id="59897-102">char (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="59897-102">char (C# reference)</span></span>

<span data-ttu-id="59897-103">Słowo kluczowe typu `char` jest aliasem dla typu struktury <xref:System.Char?displayProperty=nameWithType> .NET, który reprezentuje znak Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="59897-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="59897-104">Typ</span><span class="sxs-lookup"><span data-stu-id="59897-104">Type</span></span>|<span data-ttu-id="59897-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="59897-105">Range</span></span>|<span data-ttu-id="59897-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="59897-106">Size</span></span>|<span data-ttu-id="59897-107">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="59897-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="59897-108">U + 0000 do U + FFFF</span><span class="sxs-lookup"><span data-stu-id="59897-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="59897-109">16 bitów</span><span class="sxs-lookup"><span data-stu-id="59897-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="59897-110">Wartość domyślna typu `char` to `\0`, to oznacza, U + 0000.</span><span class="sxs-lookup"><span data-stu-id="59897-110">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="59897-111">Typ [String](reference-types.md#the-string-type) reprezentuje tekst jako sekwencję wartości `char`.</span><span class="sxs-lookup"><span data-stu-id="59897-111">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="59897-112">Literały</span><span class="sxs-lookup"><span data-stu-id="59897-112">Literals</span></span>

<span data-ttu-id="59897-113">Możesz określić wartość `char` przy użyciu:</span><span class="sxs-lookup"><span data-stu-id="59897-113">You can specify a `char` value with:</span></span>

- <span data-ttu-id="59897-114">literał znakowy.</span><span class="sxs-lookup"><span data-stu-id="59897-114">a character literal.</span></span>
- <span data-ttu-id="59897-115">sekwencja unikowa Unicode, która jest `\u` po którym następuje dwusymbolowa reprezentacja kodu znaku w postaci szesnastkowej.</span><span class="sxs-lookup"><span data-stu-id="59897-115">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="59897-116">szesnastkowa sekwencja ucieczki, która jest `\x` po której następuje reprezentacja szesnastkowa kodu znaku.</span><span class="sxs-lookup"><span data-stu-id="59897-116">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](~/samples/csharp/language-reference/builtin-types/CharType.cs#Literals)]

<span data-ttu-id="59897-117">Jak pokazano w powyższym przykładzie, można także rzutować wartość kodu znaku na odpowiadającą wartość `char`.</span><span class="sxs-lookup"><span data-stu-id="59897-117">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="59897-118">W przypadku sekwencji unikowej Unicode należy określić wszystkie cztery cyfry szesnastkowe.</span><span class="sxs-lookup"><span data-stu-id="59897-118">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="59897-119">Oznacza to, że `\u006A` jest prawidłową sekwencją ucieczki, podczas gdy `\u06A` i `\u6A` są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="59897-119">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="59897-120">W przypadku szesnastkowej sekwencji ucieczki można pominąć zera wiodące.</span><span class="sxs-lookup"><span data-stu-id="59897-120">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="59897-121">Oznacza to, że `\x006A`, `\x06A`i `\x6A` sekwencje ucieczki są prawidłowe i odpowiadają temu samemu znakowi.</span><span class="sxs-lookup"><span data-stu-id="59897-121">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="59897-122">Konwersje</span><span class="sxs-lookup"><span data-stu-id="59897-122">Conversions</span></span>

<span data-ttu-id="59897-123">Typ `char` jest niejawnie konwertowany na następujące typy [całkowite](integral-numeric-types.md) : `ushort`, `int`, `uint`, `long`i `ulong`.</span><span class="sxs-lookup"><span data-stu-id="59897-123">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="59897-124">Jest on również niejawnie konwertowany na wbudowane typy liczbowe [zmiennoprzecinkowe](floating-point-numeric-types.md) : `float`, `double`i `decimal`.</span><span class="sxs-lookup"><span data-stu-id="59897-124">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="59897-125">Jest on jawnie konwertowany na `sbyte`, `byte`i `short` typów całkowitych.</span><span class="sxs-lookup"><span data-stu-id="59897-125">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="59897-126">Brak niejawnych konwersji z innych typów na typ `char`.</span><span class="sxs-lookup"><span data-stu-id="59897-126">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="59897-127">Jednak każdy typ liczbowy [całkowitego](integral-numeric-types.md) lub [zmiennoprzecinkowego](floating-point-numeric-types.md) jest jawnie konwertowany do `char`.</span><span class="sxs-lookup"><span data-stu-id="59897-127">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="59897-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="59897-128">C# language specification</span></span>

<span data-ttu-id="59897-129">Aby uzyskać więcej informacji, zobacz sekcję [Typy całkowite](~/_csharplang/spec/types.md#integral-types) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="59897-129">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="59897-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59897-130">See also</span></span>

- [<span data-ttu-id="59897-131">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="59897-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="59897-132">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="59897-132">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="59897-133">Ciągi</span><span class="sxs-lookup"><span data-stu-id="59897-133">Strings</span></span>](../../programming-guide/strings/index.md)
