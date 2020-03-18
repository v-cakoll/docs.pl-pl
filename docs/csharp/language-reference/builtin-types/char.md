---
title: typ char - odwołanie do języka C#
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: c4e29e6437edfe549b36a04a2050f63caa0d3d2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846525"
---
# <a name="char-c-reference"></a><span data-ttu-id="0b3f2-102">char (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="0b3f2-102">char (C# reference)</span></span>

<span data-ttu-id="0b3f2-103">Słowo `char` kluczowe type jest aliasem <xref:System.Char?displayProperty=nameWithType> dla typu struktury .NET, który reprezentuje znak Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="0b3f2-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="0b3f2-104">Typ</span><span class="sxs-lookup"><span data-stu-id="0b3f2-104">Type</span></span>|<span data-ttu-id="0b3f2-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="0b3f2-105">Range</span></span>|<span data-ttu-id="0b3f2-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="0b3f2-106">Size</span></span>|<span data-ttu-id="0b3f2-107">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="0b3f2-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="0b3f2-108">Od U+0000 do U+FFFF</span><span class="sxs-lookup"><span data-stu-id="0b3f2-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="0b3f2-109">16 bitów</span><span class="sxs-lookup"><span data-stu-id="0b3f2-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="0b3f2-110">Domyślną wartością `char` tego `\0`typu jest , czyli U +0000.</span><span class="sxs-lookup"><span data-stu-id="0b3f2-110">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="0b3f2-111">Typ [ciągu](reference-types.md#the-string-type) reprezentuje tekst jako `char` sekwencję wartości.</span><span class="sxs-lookup"><span data-stu-id="0b3f2-111">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="0b3f2-112">Literały</span><span class="sxs-lookup"><span data-stu-id="0b3f2-112">Literals</span></span>

<span data-ttu-id="0b3f2-113">Można określić `char` wartość z:</span><span class="sxs-lookup"><span data-stu-id="0b3f2-113">You can specify a `char` value with:</span></span>

- <span data-ttu-id="0b3f2-114">literał postaci.</span><span class="sxs-lookup"><span data-stu-id="0b3f2-114">a character literal.</span></span>
- <span data-ttu-id="0b3f2-115">sekwencji ucieczki Unicode, `\u` po której następuje czterosymboliczna szesnastkowa reprezentacja kodu znaku.</span><span class="sxs-lookup"><span data-stu-id="0b3f2-115">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="0b3f2-116">sekwencji ucieczki szesnastkowej, po której następuje `\x` szesnastkowe przedstawienie kodu znaku.</span><span class="sxs-lookup"><span data-stu-id="0b3f2-116">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

<span data-ttu-id="0b3f2-117">Jak pokazano w poprzednim przykładzie, można również rzutować wartość `char` kodu znaku do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="0b3f2-117">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="0b3f2-118">W przypadku sekwencji ucieczki Unicode należy określić wszystkie cztery cyfry szesnastkowe.</span><span class="sxs-lookup"><span data-stu-id="0b3f2-118">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="0b3f2-119">Oznacza to, że `\u006A` jest prawidłową sekwencją ucieczki, podczas gdy `\u06A` i `\u6A` nie są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="0b3f2-119">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="0b3f2-120">W przypadku sekwencji ucieczki szesnastkowej można pominąć zera wiodące.</span><span class="sxs-lookup"><span data-stu-id="0b3f2-120">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="0b3f2-121">Oznacza to, `\x006A` `\x06A`że `\x6A` sekwencje , i escape są prawidłowe i odpowiadają temu samemu znakowi.</span><span class="sxs-lookup"><span data-stu-id="0b3f2-121">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="0b3f2-122">Konwersje</span><span class="sxs-lookup"><span data-stu-id="0b3f2-122">Conversions</span></span>

<span data-ttu-id="0b3f2-123">Typ `char` jest niejawnie konwertowalny na następujące `int` `uint`typy `long` `ulong` [całki:](integral-numeric-types.md) `ushort`, , , i .</span><span class="sxs-lookup"><span data-stu-id="0b3f2-123">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="0b3f2-124">Jest również niejawnie konwertowalny na wbudowane typy liczbowe `float` `double` `decimal` [zmiennoprzecinkowe:](floating-point-numeric-types.md) , , i .</span><span class="sxs-lookup"><span data-stu-id="0b3f2-124">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="0b3f2-125">Jest jawnie konwertowalne `sbyte`do `byte`, `short` i typy integralne.</span><span class="sxs-lookup"><span data-stu-id="0b3f2-125">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="0b3f2-126">Nie ma żadnych niejawnych konwersji `char` z innych typów do typu.</span><span class="sxs-lookup"><span data-stu-id="0b3f2-126">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="0b3f2-127">Jednak każdy [typ liczbowy typu integralnego](integral-numeric-types.md) lub [zmiennoprzecinkowego](floating-point-numeric-types.md) jest jawnie konwertowalny na `char`.</span><span class="sxs-lookup"><span data-stu-id="0b3f2-127">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0b3f2-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0b3f2-128">C# language specification</span></span>

<span data-ttu-id="0b3f2-129">Aby uzyskać więcej informacji, zobacz [integralne typy](~/_csharplang/spec/types.md#integral-types) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="0b3f2-129">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0b3f2-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b3f2-130">See also</span></span>

- [<span data-ttu-id="0b3f2-131">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0b3f2-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0b3f2-132">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="0b3f2-132">Value types</span></span>](value-types.md)
- [<span data-ttu-id="0b3f2-133">Ciągi</span><span class="sxs-lookup"><span data-stu-id="0b3f2-133">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
