---
title: Literały
description: Dowiedz się więcej o typy literałów w F# języka programowania.
ms.date: 05/16/2016
ms.openlocfilehash: dfc02f0ff8ac3ad8600be5f3b6c9359f02bd25be
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612455"
---
# <a name="literals"></a><span data-ttu-id="a36b9-103">Literały</span><span class="sxs-lookup"><span data-stu-id="a36b9-103">Literals</span></span>

> [!NOTE]
> <span data-ttu-id="a36b9-104">Łączy dokumentacja interfejsu API, w tym artykule spowoduje przejście do MSDN (na razie).</span><span class="sxs-lookup"><span data-stu-id="a36b9-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="a36b9-105">Ten temat zawiera tabelę, która pokazuje sposób określania rodzaju literału w F#.</span><span class="sxs-lookup"><span data-stu-id="a36b9-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="a36b9-106">Typy literałów</span><span class="sxs-lookup"><span data-stu-id="a36b9-106">Literal Types</span></span>

<span data-ttu-id="a36b9-107">W poniższej tabeli przedstawiono typy literałów w F#.</span><span class="sxs-lookup"><span data-stu-id="a36b9-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="a36b9-108">Znaki, które reprezentują cyfr w zapisie szesnastkowym nie jest rozróżniana wielkość liter; znaki, które identyfikują typ jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="a36b9-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="a36b9-109">Typ</span><span class="sxs-lookup"><span data-stu-id="a36b9-109">Type</span></span>|<span data-ttu-id="a36b9-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a36b9-110">Description</span></span>|<span data-ttu-id="a36b9-111">Prefiks lub sufiks</span><span class="sxs-lookup"><span data-stu-id="a36b9-111">Suffix or prefix</span></span>|<span data-ttu-id="a36b9-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a36b9-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="a36b9-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="a36b9-113">sbyte</span></span>|<span data-ttu-id="a36b9-114">8-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="a36b9-114">signed 8-bit integer</span></span>|<span data-ttu-id="a36b9-115">t</span><span class="sxs-lookup"><span data-stu-id="a36b9-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="a36b9-116">byte</span><span class="sxs-lookup"><span data-stu-id="a36b9-116">byte</span></span>|<span data-ttu-id="a36b9-117">niepodpisane 8-bitowa liczba naturalna</span><span class="sxs-lookup"><span data-stu-id="a36b9-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="a36b9-118">UY</span><span class="sxs-lookup"><span data-stu-id="a36b9-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="a36b9-119">Int16</span><span class="sxs-lookup"><span data-stu-id="a36b9-119">int16</span></span>|<span data-ttu-id="a36b9-120">16-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="a36b9-120">signed 16-bit integer</span></span>|<span data-ttu-id="a36b9-121">s</span><span class="sxs-lookup"><span data-stu-id="a36b9-121">s</span></span>|`86s`|
|<span data-ttu-id="a36b9-122">UInt16</span><span class="sxs-lookup"><span data-stu-id="a36b9-122">uint16</span></span>|<span data-ttu-id="a36b9-123">Liczba naturalna bez znaku 16-bitowych</span><span class="sxs-lookup"><span data-stu-id="a36b9-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="a36b9-124">USA</span><span class="sxs-lookup"><span data-stu-id="a36b9-124">us</span></span>|`86us`|
|<span data-ttu-id="a36b9-125">int</span><span class="sxs-lookup"><span data-stu-id="a36b9-125">int</span></span><br /><br /><span data-ttu-id="a36b9-126">int32</span><span class="sxs-lookup"><span data-stu-id="a36b9-126">int32</span></span>|<span data-ttu-id="a36b9-127">32-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="a36b9-127">signed 32-bit integer</span></span>|<span data-ttu-id="a36b9-128">l lub Brak</span><span class="sxs-lookup"><span data-stu-id="a36b9-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="a36b9-129">uint</span><span class="sxs-lookup"><span data-stu-id="a36b9-129">uint</span></span><br /><br /><span data-ttu-id="a36b9-130">uint32</span><span class="sxs-lookup"><span data-stu-id="a36b9-130">uint32</span></span>|<span data-ttu-id="a36b9-131">niepodpisane 32-bitowa liczba naturalna</span><span class="sxs-lookup"><span data-stu-id="a36b9-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="a36b9-132">u lub ul</span><span class="sxs-lookup"><span data-stu-id="a36b9-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="a36b9-133">unativeint —</span><span class="sxs-lookup"><span data-stu-id="a36b9-133">unativeint</span></span>|<span data-ttu-id="a36b9-134">wskaźnik natywny jako liczba naturalna bez znaku</span><span class="sxs-lookup"><span data-stu-id="a36b9-134">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="a36b9-135">NZ</span><span class="sxs-lookup"><span data-stu-id="a36b9-135">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="a36b9-136">int64</span><span class="sxs-lookup"><span data-stu-id="a36b9-136">int64</span></span>|<span data-ttu-id="a36b9-137">64-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="a36b9-137">signed 64-bit integer</span></span>|<span data-ttu-id="a36b9-138">L</span><span class="sxs-lookup"><span data-stu-id="a36b9-138">L</span></span>|`86L`|
|<span data-ttu-id="a36b9-139">uint64</span><span class="sxs-lookup"><span data-stu-id="a36b9-139">uint64</span></span>|<span data-ttu-id="a36b9-140">niepodpisane 64-bitowa liczba naturalna</span><span class="sxs-lookup"><span data-stu-id="a36b9-140">unsigned 64-bit natural number</span></span>|<span data-ttu-id="a36b9-141">UL</span><span class="sxs-lookup"><span data-stu-id="a36b9-141">UL</span></span>|`86UL`|
|<span data-ttu-id="a36b9-142">pojedynczy, float32</span><span class="sxs-lookup"><span data-stu-id="a36b9-142">single, float32</span></span>|<span data-ttu-id="a36b9-143">32-bitowych liczb zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="a36b9-143">32-bit floating point number</span></span>|<span data-ttu-id="a36b9-144">F lub f</span><span class="sxs-lookup"><span data-stu-id="a36b9-144">F or f</span></span>|<span data-ttu-id="a36b9-145">`4.14F` lub `4.14f`</span><span class="sxs-lookup"><span data-stu-id="a36b9-145">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="a36b9-146">LF</span><span class="sxs-lookup"><span data-stu-id="a36b9-146">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="a36b9-147">float; podwójne</span><span class="sxs-lookup"><span data-stu-id="a36b9-147">float; double</span></span>|<span data-ttu-id="a36b9-148">64-bitowych liczb zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="a36b9-148">64-bit floating point number</span></span>|<span data-ttu-id="a36b9-149">brak</span><span class="sxs-lookup"><span data-stu-id="a36b9-149">none</span></span>|<span data-ttu-id="a36b9-150">`4.14` lub `2.3E+32` lub `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="a36b9-150">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="a36b9-151">LF</span><span class="sxs-lookup"><span data-stu-id="a36b9-151">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="a36b9-152">bigint</span><span class="sxs-lookup"><span data-stu-id="a36b9-152">bigint</span></span>|<span data-ttu-id="a36b9-153">Liczba całkowita nie ogranicza się do reprezentacja 64-bitowa</span><span class="sxs-lookup"><span data-stu-id="a36b9-153">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="a36b9-154">I</span><span class="sxs-lookup"><span data-stu-id="a36b9-154">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="a36b9-155">decimal</span><span class="sxs-lookup"><span data-stu-id="a36b9-155">decimal</span></span>|<span data-ttu-id="a36b9-156">liczba ułamkowa reprezentowana jako stały punktu lub Liczba wymierna</span><span class="sxs-lookup"><span data-stu-id="a36b9-156">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="a36b9-157">M lub m</span><span class="sxs-lookup"><span data-stu-id="a36b9-157">M or m</span></span>|<span data-ttu-id="a36b9-158">`0.7833M` lub `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="a36b9-158">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="a36b9-159">Char</span><span class="sxs-lookup"><span data-stu-id="a36b9-159">Char</span></span>|<span data-ttu-id="a36b9-160">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="a36b9-160">Unicode character</span></span>|<span data-ttu-id="a36b9-161">brak</span><span class="sxs-lookup"><span data-stu-id="a36b9-161">none</span></span>|`'a'`|
|<span data-ttu-id="a36b9-162">String</span><span class="sxs-lookup"><span data-stu-id="a36b9-162">String</span></span>|<span data-ttu-id="a36b9-163">Ciąg Unicode</span><span class="sxs-lookup"><span data-stu-id="a36b9-163">Unicode string</span></span>|<span data-ttu-id="a36b9-164">brak</span><span class="sxs-lookup"><span data-stu-id="a36b9-164">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="a36b9-165">lub</span><span class="sxs-lookup"><span data-stu-id="a36b9-165">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="a36b9-166">lub</span><span class="sxs-lookup"><span data-stu-id="a36b9-166">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="a36b9-167">lub</span><span class="sxs-lookup"><span data-stu-id="a36b9-167">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="a36b9-168">Zobacz też [ciągi](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="a36b9-168">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="a36b9-169">byte</span><span class="sxs-lookup"><span data-stu-id="a36b9-169">byte</span></span>|<span data-ttu-id="a36b9-170">Znak ASCII</span><span class="sxs-lookup"><span data-stu-id="a36b9-170">ASCII character</span></span>|<span data-ttu-id="a36b9-171">B</span><span class="sxs-lookup"><span data-stu-id="a36b9-171">B</span></span>|`'a'B`|
|<span data-ttu-id="a36b9-172">byte[]</span><span class="sxs-lookup"><span data-stu-id="a36b9-172">byte[]</span></span>|<span data-ttu-id="a36b9-173">Ciąg ASCII</span><span class="sxs-lookup"><span data-stu-id="a36b9-173">ASCII string</span></span>|<span data-ttu-id="a36b9-174">B</span><span class="sxs-lookup"><span data-stu-id="a36b9-174">B</span></span>|`"text"B`|
|<span data-ttu-id="a36b9-175">Ciąg lub bajt]</span><span class="sxs-lookup"><span data-stu-id="a36b9-175">String or byte[]</span></span>|<span data-ttu-id="a36b9-176">Ciąg Verbatim</span><span class="sxs-lookup"><span data-stu-id="a36b9-176">verbatim string</span></span>|<span data-ttu-id="a36b9-177">@ prefiksu</span><span class="sxs-lookup"><span data-stu-id="a36b9-177">@ prefix</span></span>|<span data-ttu-id="a36b9-178">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="a36b9-178">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="a36b9-179">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="a36b9-179">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="a36b9-180">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a36b9-180">Remarks</span></span>

<span data-ttu-id="a36b9-181">Ciągi Unicode mogą zawierać jawne kodowania, które można określić za pomocą `\u` następuje 16-bitowych kodów szesnastkowych lub kodowania UTF-32, które można określić za pomocą `\U` następuje kod szesnastkowy 32-bitowy, który reprezentuje Unicode Para zastępcza.</span><span class="sxs-lookup"><span data-stu-id="a36b9-181">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="a36b9-182">Począwszy od programu F# 3.1, można użyć `+` Zaloguj się połączyć literały ciągów znaków.</span><span class="sxs-lookup"><span data-stu-id="a36b9-182">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="a36b9-183">Możesz również użyć operatora testu koniunkcji lub (`|||`) operator, aby łączyć flagi wyliczeń.</span><span class="sxs-lookup"><span data-stu-id="a36b9-183">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="a36b9-184">Na przykład, poniższy kod jest niedozwolony w F# 3.1:</span><span class="sxs-lookup"><span data-stu-id="a36b9-184">For example, the following code is legal in F# 3.1:</span></span>

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

<span data-ttu-id="a36b9-185">Nie jest dozwolone używanie innych operatorów bitowych.</span><span class="sxs-lookup"><span data-stu-id="a36b9-185">The use of other bitwise operators isn't allowed.</span></span>

## <a name="named-literals"></a><span data-ttu-id="a36b9-186">Nazwane literały</span><span class="sxs-lookup"><span data-stu-id="a36b9-186">Named Literals</span></span>

<span data-ttu-id="a36b9-187">Wartości, które mają być stałymi mogą być oznaczone [literału](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a36b9-187">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="a36b9-188">Ten atrybut jest w stanie sprawić, że wartość zostanie skompilowana jako stała.</span><span class="sxs-lookup"><span data-stu-id="a36b9-188">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="a36b9-189">W wyrażeniach dopasowania do wzorca identyfikatory, które zaczynają się od małych liter są zawsze traktowane jako zmienne do powiązania, a nie jako literały, więc należy generalnie używać początkowych wielkich liter podczas definiowania literałów.</span><span class="sxs-lookup"><span data-stu-id="a36b9-189">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="a36b9-190">Liczby całkowite w innych bazach</span><span class="sxs-lookup"><span data-stu-id="a36b9-190">Integers In Other Bases</span></span>

<span data-ttu-id="a36b9-191">Liczby całkowite ze znakiem 32-bitowych można również określić szesnastkową, ósemkowej lub binarny przy użyciu `0x`, `0o` lub `0b` odpowiednio prefiksu.</span><span class="sxs-lookup"><span data-stu-id="a36b9-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="a36b9-192">Podkreślenia w literałach numerycznych</span><span class="sxs-lookup"><span data-stu-id="a36b9-192">Underscores in Numeric Literals</span></span>

<span data-ttu-id="a36b9-193">Począwszy od F# 4.1, można oddzielić cyfr od znaku podkreślenia (`_`).</span><span class="sxs-lookup"><span data-stu-id="a36b9-193">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="a36b9-194">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a36b9-194">See also</span></span>

- [<span data-ttu-id="a36b9-195">Core.literalattribute — klasa</span><span class="sxs-lookup"><span data-stu-id="a36b9-195">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)