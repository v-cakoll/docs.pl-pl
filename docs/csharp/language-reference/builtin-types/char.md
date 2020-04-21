---
title: typ znaku - odwołanie do języka C#
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: a07cae6e607bb6cda965240c669c655207632298
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739066"
---
# <a name="char-c-reference"></a><span data-ttu-id="e3563-102">char (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="e3563-102">char (C# reference)</span></span>

<span data-ttu-id="e3563-103">Słowo `char` kluczowe typu jest aliasem <xref:System.Char?displayProperty=nameWithType> typu struktury .NET, który reprezentuje znak Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="e3563-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="e3563-104">Typ</span><span class="sxs-lookup"><span data-stu-id="e3563-104">Type</span></span>|<span data-ttu-id="e3563-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="e3563-105">Range</span></span>|<span data-ttu-id="e3563-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="e3563-106">Size</span></span>|<span data-ttu-id="e3563-107">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="e3563-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="e3563-108">U+0000 do U+FFFF</span><span class="sxs-lookup"><span data-stu-id="e3563-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="e3563-109">16 bitów</span><span class="sxs-lookup"><span data-stu-id="e3563-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="e3563-110">Domyślną wartością `char` typu `\0`jest , czyli U + 0000.</span><span class="sxs-lookup"><span data-stu-id="e3563-110">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="e3563-111">Typ [ciągu](reference-types.md#the-string-type) reprezentuje tekst jako `char` sekwencję wartości.</span><span class="sxs-lookup"><span data-stu-id="e3563-111">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="e3563-112">Literały</span><span class="sxs-lookup"><span data-stu-id="e3563-112">Literals</span></span>

<span data-ttu-id="e3563-113">Można określić `char` wartość za pomocą:</span><span class="sxs-lookup"><span data-stu-id="e3563-113">You can specify a `char` value with:</span></span>

- <span data-ttu-id="e3563-114">literał znakowy.</span><span class="sxs-lookup"><span data-stu-id="e3563-114">a character literal.</span></span>
- <span data-ttu-id="e3563-115">sekwencji unicode ucieczki, `\u` po którym następuje cztery symbole szesnastkowe reprezentacji kodu znaku.</span><span class="sxs-lookup"><span data-stu-id="e3563-115">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="e3563-116">szesnastkowej sekwencji `\x` ucieczki, po której następuje szesnastkowa reprezentacja kodu znaku.</span><span class="sxs-lookup"><span data-stu-id="e3563-116">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

<span data-ttu-id="e3563-117">Jak pokazano w poprzednim przykładzie, można również rzutować wartość `char` kodu znaku do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="e3563-117">As the preceding example shows, you can also cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="e3563-118">W przypadku sekwencji unikowej Unicode należy określić wszystkie cztery cyfry szesnastkowe.</span><span class="sxs-lookup"><span data-stu-id="e3563-118">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="e3563-119">Oznacza to, `\u006A` że jest prawidłową sekwencją ucieczki, podczas gdy `\u06A` i `\u6A` nie są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="e3563-119">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="e3563-120">W przypadku szesnastkowej sekwencji ucieczki można pominąć zera wiodące.</span><span class="sxs-lookup"><span data-stu-id="e3563-120">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="e3563-121">Oznacza to, `\x006A` `\x06A`że `\x6A` , i sekwencje ucieczki są prawidłowe i odpowiadają tej samej postaci.</span><span class="sxs-lookup"><span data-stu-id="e3563-121">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="e3563-122">Konwersje</span><span class="sxs-lookup"><span data-stu-id="e3563-122">Conversions</span></span>

<span data-ttu-id="e3563-123">Typ `char` jest niejawnie konwertowany na `int` `uint`następujące `long`typy `ulong` [integralne:](integral-numeric-types.md) `ushort`, , , i .</span><span class="sxs-lookup"><span data-stu-id="e3563-123">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="e3563-124">Jest również niejawnie wymienialny na [wbudowane zmiennoprzecinkowe](floating-point-numeric-types.md) typy liczbowe: `float`, `double`, i `decimal`.</span><span class="sxs-lookup"><span data-stu-id="e3563-124">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="e3563-125">Jest jawnie wymienialny `sbyte`na `byte`typy i `short` integralne.</span><span class="sxs-lookup"><span data-stu-id="e3563-125">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="e3563-126">Nie ma żadnych konwersji niejawnych `char` z innych typów do typu.</span><span class="sxs-lookup"><span data-stu-id="e3563-126">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="e3563-127">Jednak każdy [integralny](integral-numeric-types.md) lub [zmiennoprzecinowy](floating-point-numeric-types.md) typ `char`liczbowy jest jawnie wymienialny na .</span><span class="sxs-lookup"><span data-stu-id="e3563-127">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e3563-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e3563-128">C# language specification</span></span>

<span data-ttu-id="e3563-129">Aby uzyskać więcej informacji, zobacz integralną [sekcję typów](~/_csharplang/spec/types.md#integral-types) [specyfikacji języka języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="e3563-129">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3563-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3563-130">See also</span></span>

- [<span data-ttu-id="e3563-131">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e3563-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e3563-132">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="e3563-132">Value types</span></span>](value-types.md)
- [<span data-ttu-id="e3563-133">Ciągi</span><span class="sxs-lookup"><span data-stu-id="e3563-133">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [<span data-ttu-id="e3563-134">Kodowanie znaków na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="e3563-134">Character encoding in .NET</span></span>](../../../standard/base-types/character-encoding-introduction.md)
