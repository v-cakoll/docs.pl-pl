---
title: Literały
description: Dowiedz się więcej o typach literałów w języku F# programowania.
ms.date: 06/28/2019
ms.openlocfilehash: 9792a24ac28eb402e35e78574cd6a2bf9526734d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041032"
---
# <a name="literals"></a><span data-ttu-id="f6d2f-103">Literały</span><span class="sxs-lookup"><span data-stu-id="f6d2f-103">Literals</span></span>

> [!NOTE]
> <span data-ttu-id="f6d2f-104">Linki do odwołań do interfejsów API w tym artykule przeprowadzą Cię do subskrypcji MSDN (dla tej pory).</span><span class="sxs-lookup"><span data-stu-id="f6d2f-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="f6d2f-105">Ten temat zawiera tabelę, w której pokazano, jak określić typ literału w F#.</span><span class="sxs-lookup"><span data-stu-id="f6d2f-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="f6d2f-106">Typy literałów</span><span class="sxs-lookup"><span data-stu-id="f6d2f-106">Literal Types</span></span>

<span data-ttu-id="f6d2f-107">W poniższej tabeli przedstawiono typy literałów w F#.</span><span class="sxs-lookup"><span data-stu-id="f6d2f-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="f6d2f-108">Znaki reprezentujące cyfry w notacji szesnastkowej nie uwzględniają wielkości liter. w znakach identyfikujących typ rozróżniana jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="f6d2f-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="f6d2f-109">Typ</span><span class="sxs-lookup"><span data-stu-id="f6d2f-109">Type</span></span>|<span data-ttu-id="f6d2f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f6d2f-110">Description</span></span>|<span data-ttu-id="f6d2f-111">Sufiks lub prefiks</span><span class="sxs-lookup"><span data-stu-id="f6d2f-111">Suffix or prefix</span></span>|<span data-ttu-id="f6d2f-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f6d2f-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="f6d2f-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="f6d2f-113">sbyte</span></span>|<span data-ttu-id="f6d2f-114">8-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="f6d2f-114">signed 8-bit integer</span></span>|<span data-ttu-id="f6d2f-115">t</span><span class="sxs-lookup"><span data-stu-id="f6d2f-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="f6d2f-116">byte</span><span class="sxs-lookup"><span data-stu-id="f6d2f-116">byte</span></span>|<span data-ttu-id="f6d2f-117">8-bitowa niepodpisana liczba naturalna</span><span class="sxs-lookup"><span data-stu-id="f6d2f-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="f6d2f-118">uy</span><span class="sxs-lookup"><span data-stu-id="f6d2f-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="f6d2f-119">Int16</span><span class="sxs-lookup"><span data-stu-id="f6d2f-119">int16</span></span>|<span data-ttu-id="f6d2f-120">16-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="f6d2f-120">signed 16-bit integer</span></span>|<span data-ttu-id="f6d2f-121">s</span><span class="sxs-lookup"><span data-stu-id="f6d2f-121">s</span></span>|`86s`|
|<span data-ttu-id="f6d2f-122">UInt16</span><span class="sxs-lookup"><span data-stu-id="f6d2f-122">uint16</span></span>|<span data-ttu-id="f6d2f-123">16-bitowa liczba naturalna bez znaku</span><span class="sxs-lookup"><span data-stu-id="f6d2f-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="f6d2f-124">Prześlij</span><span class="sxs-lookup"><span data-stu-id="f6d2f-124">us</span></span>|`86us`|
|<span data-ttu-id="f6d2f-125">int</span><span class="sxs-lookup"><span data-stu-id="f6d2f-125">int</span></span><br /><br /><span data-ttu-id="f6d2f-126">Elementem</span><span class="sxs-lookup"><span data-stu-id="f6d2f-126">int32</span></span>|<span data-ttu-id="f6d2f-127">32-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="f6d2f-127">signed 32-bit integer</span></span>|<span data-ttu-id="f6d2f-128">l lub brak</span><span class="sxs-lookup"><span data-stu-id="f6d2f-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="f6d2f-129">uint</span><span class="sxs-lookup"><span data-stu-id="f6d2f-129">uint</span></span><br /><br /><span data-ttu-id="f6d2f-130">równ</span><span class="sxs-lookup"><span data-stu-id="f6d2f-130">uint32</span></span>|<span data-ttu-id="f6d2f-131">niepodpisany 32-bit liczby naturalnej</span><span class="sxs-lookup"><span data-stu-id="f6d2f-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="f6d2f-132">u lub ul</span><span class="sxs-lookup"><span data-stu-id="f6d2f-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="f6d2f-133">nativeint —</span><span class="sxs-lookup"><span data-stu-id="f6d2f-133">nativeint</span></span>|<span data-ttu-id="f6d2f-134">natywny wskaźnik do podpisanej liczby naturalnej</span><span class="sxs-lookup"><span data-stu-id="f6d2f-134">native pointer to a signed natural number</span></span>|<span data-ttu-id="f6d2f-135">n</span><span class="sxs-lookup"><span data-stu-id="f6d2f-135">n</span></span>|`123n`|
|<span data-ttu-id="f6d2f-136">unativeint —</span><span class="sxs-lookup"><span data-stu-id="f6d2f-136">unativeint</span></span>|<span data-ttu-id="f6d2f-137">natywny wskaźnik jako niepodpisany numer naturalny</span><span class="sxs-lookup"><span data-stu-id="f6d2f-137">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="f6d2f-138">odinstalować</span><span class="sxs-lookup"><span data-stu-id="f6d2f-138">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="f6d2f-139">Int64</span><span class="sxs-lookup"><span data-stu-id="f6d2f-139">int64</span></span>|<span data-ttu-id="f6d2f-140">64-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="f6d2f-140">signed 64-bit integer</span></span>|<span data-ttu-id="f6d2f-141">L</span><span class="sxs-lookup"><span data-stu-id="f6d2f-141">L</span></span>|`86L`|
|<span data-ttu-id="f6d2f-142">UInt64</span><span class="sxs-lookup"><span data-stu-id="f6d2f-142">uint64</span></span>|<span data-ttu-id="f6d2f-143">niepodpisany 64-bit liczby naturalnej</span><span class="sxs-lookup"><span data-stu-id="f6d2f-143">unsigned 64-bit natural number</span></span>|<span data-ttu-id="f6d2f-144">UL</span><span class="sxs-lookup"><span data-stu-id="f6d2f-144">UL</span></span>|`86UL`|
|<span data-ttu-id="f6d2f-145">Single, float32</span><span class="sxs-lookup"><span data-stu-id="f6d2f-145">single, float32</span></span>|<span data-ttu-id="f6d2f-146">32-bitowa liczba zmiennoprzecinkowa</span><span class="sxs-lookup"><span data-stu-id="f6d2f-146">32-bit floating point number</span></span>|<span data-ttu-id="f6d2f-147">F lub f</span><span class="sxs-lookup"><span data-stu-id="f6d2f-147">F or f</span></span>|<span data-ttu-id="f6d2f-148">`4.14F` lub `4.14f`</span><span class="sxs-lookup"><span data-stu-id="f6d2f-148">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="f6d2f-149">wiersza</span><span class="sxs-lookup"><span data-stu-id="f6d2f-149">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="f6d2f-150">float Double</span><span class="sxs-lookup"><span data-stu-id="f6d2f-150">float; double</span></span>|<span data-ttu-id="f6d2f-151">64-bitowa liczba zmiennoprzecinkowa</span><span class="sxs-lookup"><span data-stu-id="f6d2f-151">64-bit floating point number</span></span>|<span data-ttu-id="f6d2f-152">brak</span><span class="sxs-lookup"><span data-stu-id="f6d2f-152">none</span></span>|<span data-ttu-id="f6d2f-153">`4.14` lub `2.3E+32` lub `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="f6d2f-153">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="f6d2f-154">WIERSZA</span><span class="sxs-lookup"><span data-stu-id="f6d2f-154">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="f6d2f-155">bigint</span><span class="sxs-lookup"><span data-stu-id="f6d2f-155">bigint</span></span>|<span data-ttu-id="f6d2f-156">Liczba całkowita nieograniczona do 64-bitowej reprezentacji</span><span class="sxs-lookup"><span data-stu-id="f6d2f-156">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="f6d2f-157">I</span><span class="sxs-lookup"><span data-stu-id="f6d2f-157">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="f6d2f-158">decimal</span><span class="sxs-lookup"><span data-stu-id="f6d2f-158">decimal</span></span>|<span data-ttu-id="f6d2f-159">Liczba ułamkowa reprezentowana jako stały punkt lub liczba wymierna</span><span class="sxs-lookup"><span data-stu-id="f6d2f-159">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="f6d2f-160">M lub m</span><span class="sxs-lookup"><span data-stu-id="f6d2f-160">M or m</span></span>|<span data-ttu-id="f6d2f-161">`0.7833M` lub `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="f6d2f-161">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="f6d2f-162">Char</span><span class="sxs-lookup"><span data-stu-id="f6d2f-162">Char</span></span>|<span data-ttu-id="f6d2f-163">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="f6d2f-163">Unicode character</span></span>|<span data-ttu-id="f6d2f-164">brak</span><span class="sxs-lookup"><span data-stu-id="f6d2f-164">none</span></span>|<span data-ttu-id="f6d2f-165">`'a'` lub `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="f6d2f-165">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="f6d2f-166">String</span><span class="sxs-lookup"><span data-stu-id="f6d2f-166">String</span></span>|<span data-ttu-id="f6d2f-167">Ciąg Unicode</span><span class="sxs-lookup"><span data-stu-id="f6d2f-167">Unicode string</span></span>|<span data-ttu-id="f6d2f-168">brak</span><span class="sxs-lookup"><span data-stu-id="f6d2f-168">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="f6d2f-169">lub</span><span class="sxs-lookup"><span data-stu-id="f6d2f-169">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="f6d2f-170">lub</span><span class="sxs-lookup"><span data-stu-id="f6d2f-170">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="f6d2f-171">lub</span><span class="sxs-lookup"><span data-stu-id="f6d2f-171">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="f6d2f-172">Zobacz również [ciągi](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="f6d2f-172">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="f6d2f-173">byte</span><span class="sxs-lookup"><span data-stu-id="f6d2f-173">byte</span></span>|<span data-ttu-id="f6d2f-174">Znak ASCII</span><span class="sxs-lookup"><span data-stu-id="f6d2f-174">ASCII character</span></span>|<span data-ttu-id="f6d2f-175">B</span><span class="sxs-lookup"><span data-stu-id="f6d2f-175">B</span></span>|`'a'B`|
|<span data-ttu-id="f6d2f-176">Byte []</span><span class="sxs-lookup"><span data-stu-id="f6d2f-176">byte[]</span></span>|<span data-ttu-id="f6d2f-177">Ciąg ASCII</span><span class="sxs-lookup"><span data-stu-id="f6d2f-177">ASCII string</span></span>|<span data-ttu-id="f6d2f-178">B</span><span class="sxs-lookup"><span data-stu-id="f6d2f-178">B</span></span>|`"text"B`|
|<span data-ttu-id="f6d2f-179">Ciąg lub Byte []</span><span class="sxs-lookup"><span data-stu-id="f6d2f-179">String or byte[]</span></span>|<span data-ttu-id="f6d2f-180">ciąg Verbatim</span><span class="sxs-lookup"><span data-stu-id="f6d2f-180">verbatim string</span></span>|<span data-ttu-id="f6d2f-181">@ prefix</span><span class="sxs-lookup"><span data-stu-id="f6d2f-181">@ prefix</span></span>|<span data-ttu-id="f6d2f-182">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="f6d2f-182">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="f6d2f-183">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="f6d2f-183">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="f6d2f-184">Nazwane literały</span><span class="sxs-lookup"><span data-stu-id="f6d2f-184">Named literals</span></span>

<span data-ttu-id="f6d2f-185">Wartości, które mają być stałymi, mogą być oznaczone atrybutem [literału](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) .</span><span class="sxs-lookup"><span data-stu-id="f6d2f-185">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="f6d2f-186">Ten atrybut ma wpływ na sposób kompilowania wartości jako stałej.</span><span class="sxs-lookup"><span data-stu-id="f6d2f-186">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="f6d2f-187">W wyrażeniach dopasowania wzorców identyfikatory zaczynające się od małych liter są zawsze traktowane jako zmienne do powiązania, a nie jako literały, więc zazwyczaj należy używać początkowych wersalików podczas definiowania literałów.</span><span class="sxs-lookup"><span data-stu-id="f6d2f-187">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

```fsharp
[<Literal>]
let SomeJson = """{"numbers":[1,2,3,4,5]}"""

[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

## <a name="remarks"></a><span data-ttu-id="f6d2f-188">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6d2f-188">Remarks</span></span>

<span data-ttu-id="f6d2f-189">Ciągi Unicode mogą zawierać jawne kodowania, które można określić przy użyciu `\u`, po którym następuje 16-bitowy kod szesnastkowy (0000-FFFF) lub kodowanie UTF-32, które można określić przy użyciu `\U`, a następnie kod szesnastkowy 32-bitowy, który reprezentuje dowolny Unicode punkt kodu (00000000-0010FFFF).</span><span class="sxs-lookup"><span data-stu-id="f6d2f-189">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="f6d2f-190">Użycie innych operatorów bitowych innych niż `|||` nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="f6d2f-190">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="f6d2f-191">Liczby całkowite w innych bazach</span><span class="sxs-lookup"><span data-stu-id="f6d2f-191">Integers in other bases</span></span>

<span data-ttu-id="f6d2f-192">Podpisane 32-bitowe liczby całkowite można także określić w formacie szesnastkowym, ósemkowym lub binarnym przy użyciu odpowiednio prefiksu `0x`, `0o` lub `0b`.</span><span class="sxs-lookup"><span data-stu-id="f6d2f-192">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="f6d2f-193">Znaki podkreślenia w literałach numerycznych</span><span class="sxs-lookup"><span data-stu-id="f6d2f-193">Underscores in numeric literals</span></span>

<span data-ttu-id="f6d2f-194">Możesz oddzielić cyfry znakiem podkreślenia (`_`).</span><span class="sxs-lookup"><span data-stu-id="f6d2f-194">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="f6d2f-195">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6d2f-195">See also</span></span>

- [<span data-ttu-id="f6d2f-196">Core. LiteralAttribute — Klasa</span><span class="sxs-lookup"><span data-stu-id="f6d2f-196">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
