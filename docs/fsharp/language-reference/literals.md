---
title: Literały (F#)
description: Dowiedz się więcej o typy literałów w F# języka programowania.
ms.date: 05/16/2016
ms.openlocfilehash: 7a531cd63c5a4dc1123834d481fc998216b0d82d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131342"
---
# <a name="literals"></a><span data-ttu-id="7dff7-103">Literały</span><span class="sxs-lookup"><span data-stu-id="7dff7-103">Literals</span></span>

> [!NOTE]
> <span data-ttu-id="7dff7-104">Łączy dokumentacja interfejsu API, w tym artykule spowoduje przejście do MSDN (na razie).</span><span class="sxs-lookup"><span data-stu-id="7dff7-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="7dff7-105">Ten temat zawiera tabelę, która pokazuje sposób określania rodzaju literału w F#.</span><span class="sxs-lookup"><span data-stu-id="7dff7-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="7dff7-106">Typy literałów</span><span class="sxs-lookup"><span data-stu-id="7dff7-106">Literal Types</span></span>

<span data-ttu-id="7dff7-107">W poniższej tabeli przedstawiono typy literałów w F#.</span><span class="sxs-lookup"><span data-stu-id="7dff7-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="7dff7-108">Znaki, które reprezentują cyfr w zapisie szesnastkowym nie jest rozróżniana wielkość liter; znaki, które identyfikują typ jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="7dff7-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="7dff7-109">Typ</span><span class="sxs-lookup"><span data-stu-id="7dff7-109">Type</span></span>|<span data-ttu-id="7dff7-110">Opis</span><span class="sxs-lookup"><span data-stu-id="7dff7-110">Description</span></span>|<span data-ttu-id="7dff7-111">Prefiks lub sufiks</span><span class="sxs-lookup"><span data-stu-id="7dff7-111">Suffix or prefix</span></span>|<span data-ttu-id="7dff7-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="7dff7-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="7dff7-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="7dff7-113">sbyte</span></span>|<span data-ttu-id="7dff7-114">8-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="7dff7-114">signed 8-bit integer</span></span>|<span data-ttu-id="7dff7-115">t</span><span class="sxs-lookup"><span data-stu-id="7dff7-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="7dff7-116">byte</span><span class="sxs-lookup"><span data-stu-id="7dff7-116">byte</span></span>|<span data-ttu-id="7dff7-117">niepodpisane 8-bitowa liczba naturalna</span><span class="sxs-lookup"><span data-stu-id="7dff7-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="7dff7-118">UY</span><span class="sxs-lookup"><span data-stu-id="7dff7-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="7dff7-119">Int16</span><span class="sxs-lookup"><span data-stu-id="7dff7-119">int16</span></span>|<span data-ttu-id="7dff7-120">16-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="7dff7-120">signed 16-bit integer</span></span>|<span data-ttu-id="7dff7-121">s</span><span class="sxs-lookup"><span data-stu-id="7dff7-121">s</span></span>|`86s`|
|<span data-ttu-id="7dff7-122">UInt16</span><span class="sxs-lookup"><span data-stu-id="7dff7-122">uint16</span></span>|<span data-ttu-id="7dff7-123">Liczba naturalna bez znaku 16-bitowych</span><span class="sxs-lookup"><span data-stu-id="7dff7-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="7dff7-124">USA</span><span class="sxs-lookup"><span data-stu-id="7dff7-124">us</span></span>|`86us`|
|<span data-ttu-id="7dff7-125">int</span><span class="sxs-lookup"><span data-stu-id="7dff7-125">int</span></span><br /><br /><span data-ttu-id="7dff7-126">int32</span><span class="sxs-lookup"><span data-stu-id="7dff7-126">int32</span></span>|<span data-ttu-id="7dff7-127">32-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="7dff7-127">signed 32-bit integer</span></span>|<span data-ttu-id="7dff7-128">l lub Brak</span><span class="sxs-lookup"><span data-stu-id="7dff7-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="7dff7-129">uint</span><span class="sxs-lookup"><span data-stu-id="7dff7-129">uint</span></span><br /><br /><span data-ttu-id="7dff7-130">uint32</span><span class="sxs-lookup"><span data-stu-id="7dff7-130">uint32</span></span>|<span data-ttu-id="7dff7-131">niepodpisane 32-bitowa liczba naturalna</span><span class="sxs-lookup"><span data-stu-id="7dff7-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="7dff7-132">u lub ul</span><span class="sxs-lookup"><span data-stu-id="7dff7-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="7dff7-133">unativeint —</span><span class="sxs-lookup"><span data-stu-id="7dff7-133">unativeint</span></span>|<span data-ttu-id="7dff7-134">wskaźnik natywny jako liczba naturalna bez znaku</span><span class="sxs-lookup"><span data-stu-id="7dff7-134">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="7dff7-135">NZ</span><span class="sxs-lookup"><span data-stu-id="7dff7-135">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="7dff7-136">int64</span><span class="sxs-lookup"><span data-stu-id="7dff7-136">int64</span></span>|<span data-ttu-id="7dff7-137">64-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="7dff7-137">signed 64-bit integer</span></span>|<span data-ttu-id="7dff7-138">L</span><span class="sxs-lookup"><span data-stu-id="7dff7-138">L</span></span>|`86L`|
|<span data-ttu-id="7dff7-139">uint64</span><span class="sxs-lookup"><span data-stu-id="7dff7-139">uint64</span></span>|<span data-ttu-id="7dff7-140">niepodpisane 64-bitowa liczba naturalna</span><span class="sxs-lookup"><span data-stu-id="7dff7-140">unsigned 64-bit natural number</span></span>|<span data-ttu-id="7dff7-141">UL</span><span class="sxs-lookup"><span data-stu-id="7dff7-141">UL</span></span>|`86UL`|
|<span data-ttu-id="7dff7-142">pojedynczy, float32</span><span class="sxs-lookup"><span data-stu-id="7dff7-142">single, float32</span></span>|<span data-ttu-id="7dff7-143">32-bitowych liczb zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="7dff7-143">32-bit floating point number</span></span>|<span data-ttu-id="7dff7-144">F lub f</span><span class="sxs-lookup"><span data-stu-id="7dff7-144">F or f</span></span>|<span data-ttu-id="7dff7-145">`4.14F` lub `4.14f`</span><span class="sxs-lookup"><span data-stu-id="7dff7-145">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="7dff7-146">LF</span><span class="sxs-lookup"><span data-stu-id="7dff7-146">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="7dff7-147">float; podwójne</span><span class="sxs-lookup"><span data-stu-id="7dff7-147">float; double</span></span>|<span data-ttu-id="7dff7-148">64-bitowych liczb zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="7dff7-148">64-bit floating point number</span></span>|<span data-ttu-id="7dff7-149">brak</span><span class="sxs-lookup"><span data-stu-id="7dff7-149">none</span></span>|<span data-ttu-id="7dff7-150">`4.14` lub `2.3E+32` lub `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="7dff7-150">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="7dff7-151">LF</span><span class="sxs-lookup"><span data-stu-id="7dff7-151">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="7dff7-152">bigint</span><span class="sxs-lookup"><span data-stu-id="7dff7-152">bigint</span></span>|<span data-ttu-id="7dff7-153">Liczba całkowita nie ogranicza się do reprezentacja 64-bitowa</span><span class="sxs-lookup"><span data-stu-id="7dff7-153">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="7dff7-154">I</span><span class="sxs-lookup"><span data-stu-id="7dff7-154">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="7dff7-155">decimal</span><span class="sxs-lookup"><span data-stu-id="7dff7-155">decimal</span></span>|<span data-ttu-id="7dff7-156">liczba ułamkowa reprezentowana jako stały punktu lub Liczba wymierna</span><span class="sxs-lookup"><span data-stu-id="7dff7-156">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="7dff7-157">M lub m</span><span class="sxs-lookup"><span data-stu-id="7dff7-157">M or m</span></span>|<span data-ttu-id="7dff7-158">`0.7833M` lub `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="7dff7-158">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="7dff7-159">Char</span><span class="sxs-lookup"><span data-stu-id="7dff7-159">Char</span></span>|<span data-ttu-id="7dff7-160">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="7dff7-160">Unicode character</span></span>|<span data-ttu-id="7dff7-161">brak</span><span class="sxs-lookup"><span data-stu-id="7dff7-161">none</span></span>|`'a'`|
|<span data-ttu-id="7dff7-162">String</span><span class="sxs-lookup"><span data-stu-id="7dff7-162">String</span></span>|<span data-ttu-id="7dff7-163">Ciąg Unicode</span><span class="sxs-lookup"><span data-stu-id="7dff7-163">Unicode string</span></span>|<span data-ttu-id="7dff7-164">brak</span><span class="sxs-lookup"><span data-stu-id="7dff7-164">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="7dff7-165">lub</span><span class="sxs-lookup"><span data-stu-id="7dff7-165">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="7dff7-166">lub</span><span class="sxs-lookup"><span data-stu-id="7dff7-166">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="7dff7-167">lub</span><span class="sxs-lookup"><span data-stu-id="7dff7-167">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="7dff7-168">Zobacz też [ciągi](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="7dff7-168">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="7dff7-169">byte</span><span class="sxs-lookup"><span data-stu-id="7dff7-169">byte</span></span>|<span data-ttu-id="7dff7-170">Znak ASCII</span><span class="sxs-lookup"><span data-stu-id="7dff7-170">ASCII character</span></span>|<span data-ttu-id="7dff7-171">B</span><span class="sxs-lookup"><span data-stu-id="7dff7-171">B</span></span>|`'a'B`|
|<span data-ttu-id="7dff7-172">byte[]</span><span class="sxs-lookup"><span data-stu-id="7dff7-172">byte[]</span></span>|<span data-ttu-id="7dff7-173">Ciąg ASCII</span><span class="sxs-lookup"><span data-stu-id="7dff7-173">ASCII string</span></span>|<span data-ttu-id="7dff7-174">B</span><span class="sxs-lookup"><span data-stu-id="7dff7-174">B</span></span>|`"text"B`|
|<span data-ttu-id="7dff7-175">Ciąg lub bajt]</span><span class="sxs-lookup"><span data-stu-id="7dff7-175">String or byte[]</span></span>|<span data-ttu-id="7dff7-176">Ciąg Verbatim</span><span class="sxs-lookup"><span data-stu-id="7dff7-176">verbatim string</span></span>|<span data-ttu-id="7dff7-177">@ prefiksu</span><span class="sxs-lookup"><span data-stu-id="7dff7-177">@ prefix</span></span>|<span data-ttu-id="7dff7-178">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="7dff7-178">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="7dff7-179">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="7dff7-179">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="7dff7-180">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7dff7-180">Remarks</span></span>

<span data-ttu-id="7dff7-181">Ciągi Unicode mogą zawierać jawne kodowania, które można określić za pomocą `\u` następuje 16-bitowych kodów szesnastkowych lub kodowania UTF-32, które można określić za pomocą `\U` następuje kod szesnastkowy 32-bitowy, który reprezentuje Unicode Para zastępcza.</span><span class="sxs-lookup"><span data-stu-id="7dff7-181">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="7dff7-182">Począwszy od programu F# 3.1, można użyć `+` Zaloguj się połączyć literały ciągów znaków.</span><span class="sxs-lookup"><span data-stu-id="7dff7-182">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="7dff7-183">Możesz również użyć operatora testu koniunkcji lub (`|||`) operator, aby łączyć flagi wyliczeń.</span><span class="sxs-lookup"><span data-stu-id="7dff7-183">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="7dff7-184">Na przykład, poniższy kod jest niedozwolony w F# 3.1:</span><span class="sxs-lookup"><span data-stu-id="7dff7-184">For example, the following code is legal in F# 3.1:</span></span>

```fsharp
[<Literal>]
let literal1 = "a" + "b"

[<Literal>]
let fileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let literal2 = 1 ||| 64

[<Literal>]
let literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

<span data-ttu-id="7dff7-185">Nie jest dozwolone używanie innych operatorów bitowych.</span><span class="sxs-lookup"><span data-stu-id="7dff7-185">The use of other bitwise operators isn't allowed.</span></span>

## <a name="named-literals"></a><span data-ttu-id="7dff7-186">Nazwane literały</span><span class="sxs-lookup"><span data-stu-id="7dff7-186">Named Literals</span></span>

<span data-ttu-id="7dff7-187">Wartości, które mają być stałymi mogą być oznaczone [literału](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7dff7-187">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="7dff7-188">Ten atrybut jest w stanie sprawić, że wartość zostanie skompilowana jako stała.</span><span class="sxs-lookup"><span data-stu-id="7dff7-188">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="7dff7-189">W wyrażeniach dopasowania do wzorca identyfikatory, które zaczynają się od małych liter są zawsze traktowane jako zmienne do powiązania, a nie jako literały, więc należy generalnie używać początkowych wielkich liter podczas definiowania literałów.</span><span class="sxs-lookup"><span data-stu-id="7dff7-189">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="7dff7-190">Liczby całkowite w innych bazach</span><span class="sxs-lookup"><span data-stu-id="7dff7-190">Integers In Other Bases</span></span>

<span data-ttu-id="7dff7-191">Liczby całkowite ze znakiem 32-bitowych można również określić szesnastkową, ósemkowej lub binarny przy użyciu `0x`, `0o` lub `0b` odpowiednio prefiksu.</span><span class="sxs-lookup"><span data-stu-id="7dff7-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="7dff7-192">Podkreślenia w literałach numerycznych</span><span class="sxs-lookup"><span data-stu-id="7dff7-192">Underscores in Numeric Literals</span></span>

<span data-ttu-id="7dff7-193">Począwszy od F# 4.1, można oddzielić cyfr od znaku podkreślenia (`_`).</span><span class="sxs-lookup"><span data-stu-id="7dff7-193">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="7dff7-194">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7dff7-194">See also</span></span>

- [<span data-ttu-id="7dff7-195">Core.literalattribute — klasa</span><span class="sxs-lookup"><span data-stu-id="7dff7-195">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
