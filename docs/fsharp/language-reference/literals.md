---
title: Literały
description: Dowiedz się więcej o typy literałów w F# języka programowania.
ms.date: 06/28/2019
ms.openlocfilehash: 0c9ced0b505817a161ca39c6c9f853f94cedf410
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610153"
---
# <a name="literals"></a><span data-ttu-id="e25d2-103">Literały</span><span class="sxs-lookup"><span data-stu-id="e25d2-103">Literals</span></span>

> [!NOTE]
> <span data-ttu-id="e25d2-104">Łączy dokumentacja interfejsu API, w tym artykule spowoduje przejście do MSDN (na razie).</span><span class="sxs-lookup"><span data-stu-id="e25d2-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="e25d2-105">Ten temat zawiera tabelę, która pokazuje sposób określania rodzaju literału w F#.</span><span class="sxs-lookup"><span data-stu-id="e25d2-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="e25d2-106">Typy literałów</span><span class="sxs-lookup"><span data-stu-id="e25d2-106">Literal Types</span></span>

<span data-ttu-id="e25d2-107">W poniższej tabeli przedstawiono typy literałów w F#.</span><span class="sxs-lookup"><span data-stu-id="e25d2-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="e25d2-108">Znaki, które reprezentują cyfr w zapisie szesnastkowym nie jest rozróżniana wielkość liter; znaki, które identyfikują typ jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="e25d2-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="e25d2-109">Typ</span><span class="sxs-lookup"><span data-stu-id="e25d2-109">Type</span></span>|<span data-ttu-id="e25d2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="e25d2-110">Description</span></span>|<span data-ttu-id="e25d2-111">Prefiks lub sufiks</span><span class="sxs-lookup"><span data-stu-id="e25d2-111">Suffix or prefix</span></span>|<span data-ttu-id="e25d2-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e25d2-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="e25d2-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="e25d2-113">sbyte</span></span>|<span data-ttu-id="e25d2-114">8-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="e25d2-114">signed 8-bit integer</span></span>|<span data-ttu-id="e25d2-115">t</span><span class="sxs-lookup"><span data-stu-id="e25d2-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="e25d2-116">byte</span><span class="sxs-lookup"><span data-stu-id="e25d2-116">byte</span></span>|<span data-ttu-id="e25d2-117">niepodpisane 8-bitowa liczba naturalna</span><span class="sxs-lookup"><span data-stu-id="e25d2-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="e25d2-118">UY</span><span class="sxs-lookup"><span data-stu-id="e25d2-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="e25d2-119">Int16</span><span class="sxs-lookup"><span data-stu-id="e25d2-119">int16</span></span>|<span data-ttu-id="e25d2-120">16-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="e25d2-120">signed 16-bit integer</span></span>|<span data-ttu-id="e25d2-121">s</span><span class="sxs-lookup"><span data-stu-id="e25d2-121">s</span></span>|`86s`|
|<span data-ttu-id="e25d2-122">UInt16</span><span class="sxs-lookup"><span data-stu-id="e25d2-122">uint16</span></span>|<span data-ttu-id="e25d2-123">Liczba naturalna bez znaku 16-bitowych</span><span class="sxs-lookup"><span data-stu-id="e25d2-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="e25d2-124">us</span><span class="sxs-lookup"><span data-stu-id="e25d2-124">us</span></span>|`86us`|
|<span data-ttu-id="e25d2-125">int</span><span class="sxs-lookup"><span data-stu-id="e25d2-125">int</span></span><br /><br /><span data-ttu-id="e25d2-126">int32</span><span class="sxs-lookup"><span data-stu-id="e25d2-126">int32</span></span>|<span data-ttu-id="e25d2-127">32-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="e25d2-127">signed 32-bit integer</span></span>|<span data-ttu-id="e25d2-128">l lub Brak</span><span class="sxs-lookup"><span data-stu-id="e25d2-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="e25d2-129">uint</span><span class="sxs-lookup"><span data-stu-id="e25d2-129">uint</span></span><br /><br /><span data-ttu-id="e25d2-130">uint32</span><span class="sxs-lookup"><span data-stu-id="e25d2-130">uint32</span></span>|<span data-ttu-id="e25d2-131">niepodpisane 32-bitowa liczba naturalna</span><span class="sxs-lookup"><span data-stu-id="e25d2-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="e25d2-132">u lub ul</span><span class="sxs-lookup"><span data-stu-id="e25d2-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="e25d2-133">nativeint —</span><span class="sxs-lookup"><span data-stu-id="e25d2-133">nativeint</span></span>|<span data-ttu-id="e25d2-134">wskaźnik natywny podpisem numer naturalnym</span><span class="sxs-lookup"><span data-stu-id="e25d2-134">native pointer to a signed natural number</span></span>|<span data-ttu-id="e25d2-135">n</span><span class="sxs-lookup"><span data-stu-id="e25d2-135">n</span></span>|`123n`|
|<span data-ttu-id="e25d2-136">unativeint —</span><span class="sxs-lookup"><span data-stu-id="e25d2-136">unativeint</span></span>|<span data-ttu-id="e25d2-137">wskaźnik natywny jako liczba naturalna bez znaku</span><span class="sxs-lookup"><span data-stu-id="e25d2-137">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="e25d2-138">NZ</span><span class="sxs-lookup"><span data-stu-id="e25d2-138">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="e25d2-139">int64</span><span class="sxs-lookup"><span data-stu-id="e25d2-139">int64</span></span>|<span data-ttu-id="e25d2-140">64-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="e25d2-140">signed 64-bit integer</span></span>|<span data-ttu-id="e25d2-141">L</span><span class="sxs-lookup"><span data-stu-id="e25d2-141">L</span></span>|`86L`|
|<span data-ttu-id="e25d2-142">uint64</span><span class="sxs-lookup"><span data-stu-id="e25d2-142">uint64</span></span>|<span data-ttu-id="e25d2-143">niepodpisane 64-bitowa liczba naturalna</span><span class="sxs-lookup"><span data-stu-id="e25d2-143">unsigned 64-bit natural number</span></span>|<span data-ttu-id="e25d2-144">UL</span><span class="sxs-lookup"><span data-stu-id="e25d2-144">UL</span></span>|`86UL`|
|<span data-ttu-id="e25d2-145">pojedynczy, float32</span><span class="sxs-lookup"><span data-stu-id="e25d2-145">single, float32</span></span>|<span data-ttu-id="e25d2-146">32-bitowych liczb zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="e25d2-146">32-bit floating point number</span></span>|<span data-ttu-id="e25d2-147">F lub f</span><span class="sxs-lookup"><span data-stu-id="e25d2-147">F or f</span></span>|<span data-ttu-id="e25d2-148">`4.14F` lub `4.14f`</span><span class="sxs-lookup"><span data-stu-id="e25d2-148">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="e25d2-149">lf</span><span class="sxs-lookup"><span data-stu-id="e25d2-149">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="e25d2-150">float; podwójne</span><span class="sxs-lookup"><span data-stu-id="e25d2-150">float; double</span></span>|<span data-ttu-id="e25d2-151">64-bitowych liczb zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="e25d2-151">64-bit floating point number</span></span>|<span data-ttu-id="e25d2-152">brak</span><span class="sxs-lookup"><span data-stu-id="e25d2-152">none</span></span>|<span data-ttu-id="e25d2-153">`4.14` lub `2.3E+32` lub `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="e25d2-153">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="e25d2-154">LF</span><span class="sxs-lookup"><span data-stu-id="e25d2-154">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="e25d2-155">bigint</span><span class="sxs-lookup"><span data-stu-id="e25d2-155">bigint</span></span>|<span data-ttu-id="e25d2-156">Liczba całkowita nie ogranicza się do reprezentacja 64-bitowa</span><span class="sxs-lookup"><span data-stu-id="e25d2-156">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="e25d2-157">I</span><span class="sxs-lookup"><span data-stu-id="e25d2-157">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="e25d2-158">decimal</span><span class="sxs-lookup"><span data-stu-id="e25d2-158">decimal</span></span>|<span data-ttu-id="e25d2-159">liczba ułamkowa reprezentowana jako stały punktu lub Liczba wymierna</span><span class="sxs-lookup"><span data-stu-id="e25d2-159">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="e25d2-160">M lub m</span><span class="sxs-lookup"><span data-stu-id="e25d2-160">M or m</span></span>|<span data-ttu-id="e25d2-161">`0.7833M` lub `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="e25d2-161">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="e25d2-162">Char</span><span class="sxs-lookup"><span data-stu-id="e25d2-162">Char</span></span>|<span data-ttu-id="e25d2-163">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="e25d2-163">Unicode character</span></span>|<span data-ttu-id="e25d2-164">brak</span><span class="sxs-lookup"><span data-stu-id="e25d2-164">none</span></span>|`'a'`|
|<span data-ttu-id="e25d2-165">String</span><span class="sxs-lookup"><span data-stu-id="e25d2-165">String</span></span>|<span data-ttu-id="e25d2-166">Ciąg Unicode</span><span class="sxs-lookup"><span data-stu-id="e25d2-166">Unicode string</span></span>|<span data-ttu-id="e25d2-167">brak</span><span class="sxs-lookup"><span data-stu-id="e25d2-167">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="e25d2-168">lub</span><span class="sxs-lookup"><span data-stu-id="e25d2-168">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="e25d2-169">lub</span><span class="sxs-lookup"><span data-stu-id="e25d2-169">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="e25d2-170">lub</span><span class="sxs-lookup"><span data-stu-id="e25d2-170">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="e25d2-171">Zobacz też [ciągi](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="e25d2-171">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="e25d2-172">byte</span><span class="sxs-lookup"><span data-stu-id="e25d2-172">byte</span></span>|<span data-ttu-id="e25d2-173">Znak ASCII</span><span class="sxs-lookup"><span data-stu-id="e25d2-173">ASCII character</span></span>|<span data-ttu-id="e25d2-174">B</span><span class="sxs-lookup"><span data-stu-id="e25d2-174">B</span></span>|`'a'B`|
|<span data-ttu-id="e25d2-175">byte[]</span><span class="sxs-lookup"><span data-stu-id="e25d2-175">byte[]</span></span>|<span data-ttu-id="e25d2-176">Ciąg ASCII</span><span class="sxs-lookup"><span data-stu-id="e25d2-176">ASCII string</span></span>|<span data-ttu-id="e25d2-177">B</span><span class="sxs-lookup"><span data-stu-id="e25d2-177">B</span></span>|`"text"B`|
|<span data-ttu-id="e25d2-178">Ciąg lub bajt]</span><span class="sxs-lookup"><span data-stu-id="e25d2-178">String or byte[]</span></span>|<span data-ttu-id="e25d2-179">Ciąg Verbatim</span><span class="sxs-lookup"><span data-stu-id="e25d2-179">verbatim string</span></span>|<span data-ttu-id="e25d2-180">@ prefiksu</span><span class="sxs-lookup"><span data-stu-id="e25d2-180">@ prefix</span></span>|<span data-ttu-id="e25d2-181">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="e25d2-181">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="e25d2-182">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="e25d2-182">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="e25d2-183">Nazwane literały</span><span class="sxs-lookup"><span data-stu-id="e25d2-183">Named literals</span></span>

<span data-ttu-id="e25d2-184">Wartości, które mają być stałymi mogą być oznaczone [literału](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e25d2-184">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="e25d2-185">Ten atrybut jest w stanie sprawić, że wartość zostanie skompilowana jako stała.</span><span class="sxs-lookup"><span data-stu-id="e25d2-185">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="e25d2-186">W wyrażeniach dopasowania do wzorca identyfikatory, które zaczynają się od małych liter są zawsze traktowane jako zmienne do powiązania, a nie jako literały, więc należy generalnie używać początkowych wielkich liter podczas definiowania literałów.</span><span class="sxs-lookup"><span data-stu-id="e25d2-186">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="e25d2-187">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e25d2-187">Remarks</span></span>

<span data-ttu-id="e25d2-188">Ciągi Unicode mogą zawierać jawne kodowania, które można określić za pomocą `\u` następuje 16-bitowych kodów szesnastkowych (FFFF 0000 -) lub kodowania UTF-32, które można określić za pomocą `\U` następuje kod szesnastkowy 32-bitowy, który reprezentuje wszelkie punkt kodu Unicode (00000000 - 0010FFFF).</span><span class="sxs-lookup"><span data-stu-id="e25d2-188">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="e25d2-189">Używanie innych operatorów bitowych inne niż `|||` nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="e25d2-189">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="e25d2-190">Liczby całkowite w innych bazach</span><span class="sxs-lookup"><span data-stu-id="e25d2-190">Integers in other bases</span></span>

<span data-ttu-id="e25d2-191">Liczby całkowite ze znakiem 32-bitowych można również określić szesnastkową, ósemkowej lub binarny przy użyciu `0x`, `0o` lub `0b` odpowiednio prefiksu.</span><span class="sxs-lookup"><span data-stu-id="e25d2-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="e25d2-192">Podkreślenia w literałach numerycznych</span><span class="sxs-lookup"><span data-stu-id="e25d2-192">Underscores in numeric literals</span></span>

<span data-ttu-id="e25d2-193">Możesz oddzielić cyfr znaku podkreślenia (`_`).</span><span class="sxs-lookup"><span data-stu-id="e25d2-193">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="e25d2-194">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e25d2-194">See also</span></span>

- [<span data-ttu-id="e25d2-195">Core.literalattribute — klasa</span><span class="sxs-lookup"><span data-stu-id="e25d2-195">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
