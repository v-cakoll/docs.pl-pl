---
title: typ znaku — C# odwołanie
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 3b2eec4f0e17aa329fe3865fb3ef453ee030c6a7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451165"
---
# <a name="char-c-reference"></a><span data-ttu-id="ca4ef-102">char (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="ca4ef-102">char (C# reference)</span></span>

<span data-ttu-id="ca4ef-103">Słowo kluczowe typu `char` jest aliasem dla typu struktury <xref:System.Char?displayProperty=nameWithType> .NET, który reprezentuje znak Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="ca4ef-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="ca4ef-104">Typ</span><span class="sxs-lookup"><span data-stu-id="ca4ef-104">Type</span></span>|<span data-ttu-id="ca4ef-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="ca4ef-105">Range</span></span>|<span data-ttu-id="ca4ef-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="ca4ef-106">Size</span></span>|<span data-ttu-id="ca4ef-107">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="ca4ef-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="ca4ef-108">U + 0000 do U + FFFF</span><span class="sxs-lookup"><span data-stu-id="ca4ef-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="ca4ef-109">16 bitów</span><span class="sxs-lookup"><span data-stu-id="ca4ef-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="ca4ef-110">Typ [String](reference-types.md#the-string-type) reprezentuje tekst jako sekwencję wartości `char`.</span><span class="sxs-lookup"><span data-stu-id="ca4ef-110">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="ca4ef-111">Literały</span><span class="sxs-lookup"><span data-stu-id="ca4ef-111">Literals</span></span>

<span data-ttu-id="ca4ef-112">Możesz określić wartość `char` przy użyciu:</span><span class="sxs-lookup"><span data-stu-id="ca4ef-112">You can specify a `char` value with:</span></span>

- <span data-ttu-id="ca4ef-113">literał znakowy.</span><span class="sxs-lookup"><span data-stu-id="ca4ef-113">a character literal.</span></span>
- <span data-ttu-id="ca4ef-114">sekwencja unikowa Unicode, która jest `\u` po którym następuje dwusymbolowa reprezentacja kodu znaku w postaci szesnastkowej.</span><span class="sxs-lookup"><span data-stu-id="ca4ef-114">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="ca4ef-115">szesnastkowa sekwencja ucieczki, która jest `\x` po której następuje reprezentacja szesnastkowa kodu znaku.</span><span class="sxs-lookup"><span data-stu-id="ca4ef-115">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](~/samples/csharp/language-reference/builtin-types/CharType.cs#Literals)]

<span data-ttu-id="ca4ef-116">Jak pokazano w powyższym przykładzie, można także rzutować wartość kodu znaku na odpowiadającą wartość `char`.</span><span class="sxs-lookup"><span data-stu-id="ca4ef-116">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="ca4ef-117">W przypadku sekwencji unikowej Unicode należy określić wszystkie cztery cyfry szesnastkowe.</span><span class="sxs-lookup"><span data-stu-id="ca4ef-117">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="ca4ef-118">Oznacza to, że `\u006A` jest prawidłową sekwencją ucieczki, podczas gdy `\u06A` i `\u6A` są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="ca4ef-118">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="ca4ef-119">W przypadku szesnastkowej sekwencji ucieczki można pominąć zera wiodące.</span><span class="sxs-lookup"><span data-stu-id="ca4ef-119">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="ca4ef-120">Oznacza to, że `\x006A`, `\x06A`i `\x6A` sekwencje ucieczki są prawidłowe i odpowiadają temu samemu znakowi.</span><span class="sxs-lookup"><span data-stu-id="ca4ef-120">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="ca4ef-121">Konwersje</span><span class="sxs-lookup"><span data-stu-id="ca4ef-121">Conversions</span></span>

<span data-ttu-id="ca4ef-122">Typ `char` jest niejawnie konwertowany na następujące typy [całkowite](integral-numeric-types.md) : `ushort`, `int`, `uint`, `long`i `ulong`.</span><span class="sxs-lookup"><span data-stu-id="ca4ef-122">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="ca4ef-123">Jest on również niejawnie konwertowany na wbudowane typy liczbowe [zmiennoprzecinkowe](floating-point-numeric-types.md) : `float`, `double`i `decimal`.</span><span class="sxs-lookup"><span data-stu-id="ca4ef-123">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="ca4ef-124">Jest on jawnie konwertowany na `sbyte`, `byte`i `short` typów całkowitych.</span><span class="sxs-lookup"><span data-stu-id="ca4ef-124">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="ca4ef-125">Brak niejawnych konwersji z innych typów na typ `char`.</span><span class="sxs-lookup"><span data-stu-id="ca4ef-125">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="ca4ef-126">Jednak każdy typ liczbowy [całkowitego](integral-numeric-types.md) lub [zmiennoprzecinkowego](floating-point-numeric-types.md) jest jawnie konwertowany do `char`.</span><span class="sxs-lookup"><span data-stu-id="ca4ef-126">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ca4ef-127">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ca4ef-127">C# language specification</span></span>

<span data-ttu-id="ca4ef-128">Aby uzyskać więcej informacji, zobacz sekcję [Typy całkowite](~/_csharplang/spec/types.md#integral-types) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ca4ef-128">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ca4ef-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca4ef-129">See also</span></span>

- [<span data-ttu-id="ca4ef-130">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="ca4ef-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ca4ef-131">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="ca4ef-131">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="ca4ef-132">Ciągi</span><span class="sxs-lookup"><span data-stu-id="ca4ef-132">Strings</span></span>](../../programming-guide/strings/index.md)
