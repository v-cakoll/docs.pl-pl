---
title: Literały (F#)
description: 'Poznaj typy literału w języku programowania w języku F #.'
ms.date: 05/16/2016
ms.openlocfilehash: f28ca0ae7a0b092bbc039d23625b883faffd241c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564342"
---
# <a name="literals"></a><span data-ttu-id="f06ee-103">Literały</span><span class="sxs-lookup"><span data-stu-id="f06ee-103">Literals</span></span>

> [!NOTE]
<span data-ttu-id="f06ee-104">Interfejs API łącza odwołań w tym artykule spowoduje przejście do MSDN (na razie).</span><span class="sxs-lookup"><span data-stu-id="f06ee-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="f06ee-105">Ten temat zawiera tabelę, która przedstawia sposób określić typ literału w języku F #.</span><span class="sxs-lookup"><span data-stu-id="f06ee-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="f06ee-106">Typy literału</span><span class="sxs-lookup"><span data-stu-id="f06ee-106">Literal Types</span></span>
<span data-ttu-id="f06ee-107">W poniższej tabeli przedstawiono typy literału w języku F #.</span><span class="sxs-lookup"><span data-stu-id="f06ee-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="f06ee-108">Znaki, które reprezentują cyfr w formacie szesnastkowym nie jest rozróżniana; znaki, które identyfikują typ jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="f06ee-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="f06ee-109">Typ</span><span class="sxs-lookup"><span data-stu-id="f06ee-109">Type</span></span>|<span data-ttu-id="f06ee-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f06ee-110">Description</span></span>|<span data-ttu-id="f06ee-111">Sufiks lub prefiksu</span><span class="sxs-lookup"><span data-stu-id="f06ee-111">Suffix or prefix</span></span>|<span data-ttu-id="f06ee-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f06ee-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="f06ee-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="f06ee-113">sbyte</span></span>|<span data-ttu-id="f06ee-114">8-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="f06ee-114">signed 8-bit integer</span></span>|<span data-ttu-id="f06ee-115">t</span><span class="sxs-lookup"><span data-stu-id="f06ee-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="f06ee-116">byte</span><span class="sxs-lookup"><span data-stu-id="f06ee-116">byte</span></span>|<span data-ttu-id="f06ee-117">bez znaku 8-bitową liczbą naturalnych</span><span class="sxs-lookup"><span data-stu-id="f06ee-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="f06ee-118">UY</span><span class="sxs-lookup"><span data-stu-id="f06ee-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="f06ee-119">Int16</span><span class="sxs-lookup"><span data-stu-id="f06ee-119">int16</span></span>|<span data-ttu-id="f06ee-120">16-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="f06ee-120">signed 16-bit integer</span></span>|<span data-ttu-id="f06ee-121">s</span><span class="sxs-lookup"><span data-stu-id="f06ee-121">s</span></span>|`86s`|
|<span data-ttu-id="f06ee-122">UInt16</span><span class="sxs-lookup"><span data-stu-id="f06ee-122">uint16</span></span>|<span data-ttu-id="f06ee-123">niepodpisane 16-bitową liczbę naturalnych</span><span class="sxs-lookup"><span data-stu-id="f06ee-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="f06ee-124">US</span><span class="sxs-lookup"><span data-stu-id="f06ee-124">us</span></span>|`86us`|
|<span data-ttu-id="f06ee-125">int</span><span class="sxs-lookup"><span data-stu-id="f06ee-125">int</span></span><br /><br /><span data-ttu-id="f06ee-126">int32</span><span class="sxs-lookup"><span data-stu-id="f06ee-126">int32</span></span>|<span data-ttu-id="f06ee-127">32-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="f06ee-127">signed 32-bit integer</span></span>|<span data-ttu-id="f06ee-128">l lub Brak</span><span class="sxs-lookup"><span data-stu-id="f06ee-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="f06ee-129">uint</span><span class="sxs-lookup"><span data-stu-id="f06ee-129">uint</span></span><br /><br /><span data-ttu-id="f06ee-130">uint32</span><span class="sxs-lookup"><span data-stu-id="f06ee-130">uint32</span></span>|<span data-ttu-id="f06ee-131">niepodpisane 32-bitową liczbą naturalnych</span><span class="sxs-lookup"><span data-stu-id="f06ee-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="f06ee-132">u lub ul</span><span class="sxs-lookup"><span data-stu-id="f06ee-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="f06ee-133">unativeint —</span><span class="sxs-lookup"><span data-stu-id="f06ee-133">unativeint</span></span>|<span data-ttu-id="f06ee-134">wskaźnik natywny jako wartość bez znaku naturalnych</span><span class="sxs-lookup"><span data-stu-id="f06ee-134">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="f06ee-135">Wyrejestruj</span><span class="sxs-lookup"><span data-stu-id="f06ee-135">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="f06ee-136">int64</span><span class="sxs-lookup"><span data-stu-id="f06ee-136">int64</span></span>|<span data-ttu-id="f06ee-137">64-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="f06ee-137">signed 64-bit integer</span></span>|<span data-ttu-id="f06ee-138">L</span><span class="sxs-lookup"><span data-stu-id="f06ee-138">L</span></span>|`86L`|
|<span data-ttu-id="f06ee-139">uint64</span><span class="sxs-lookup"><span data-stu-id="f06ee-139">uint64</span></span>|<span data-ttu-id="f06ee-140">Liczba naturalnego 64-bitowa bez znaku</span><span class="sxs-lookup"><span data-stu-id="f06ee-140">unsigned 64-bit natural number</span></span>|<span data-ttu-id="f06ee-141">UL</span><span class="sxs-lookup"><span data-stu-id="f06ee-141">UL</span></span>|`86UL`|
|<span data-ttu-id="f06ee-142">pojedynczy, float32</span><span class="sxs-lookup"><span data-stu-id="f06ee-142">single, float32</span></span>|<span data-ttu-id="f06ee-143">32-bitowych liczb zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="f06ee-143">32-bit floating point number</span></span>|<span data-ttu-id="f06ee-144">F lub f</span><span class="sxs-lookup"><span data-stu-id="f06ee-144">F or f</span></span>|<span data-ttu-id="f06ee-145">`4.14F` lub `4.14f`</span><span class="sxs-lookup"><span data-stu-id="f06ee-145">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="f06ee-146">LF</span><span class="sxs-lookup"><span data-stu-id="f06ee-146">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="f06ee-147">float; podwójne</span><span class="sxs-lookup"><span data-stu-id="f06ee-147">float; double</span></span>|<span data-ttu-id="f06ee-148">64-bitowych liczb zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="f06ee-148">64-bit floating point number</span></span>|<span data-ttu-id="f06ee-149">brak</span><span class="sxs-lookup"><span data-stu-id="f06ee-149">none</span></span>|<span data-ttu-id="f06ee-150">`4.14` lub `2.3E+32` lub `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="f06ee-150">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="f06ee-151">LF</span><span class="sxs-lookup"><span data-stu-id="f06ee-151">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="f06ee-152">bigint</span><span class="sxs-lookup"><span data-stu-id="f06ee-152">bigint</span></span>|<span data-ttu-id="f06ee-153">innymi reprezentacja 64-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="f06ee-153">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="f06ee-154">I</span><span class="sxs-lookup"><span data-stu-id="f06ee-154">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="f06ee-155">decimal</span><span class="sxs-lookup"><span data-stu-id="f06ee-155">decimal</span></span>|<span data-ttu-id="f06ee-156">liczbę ułamkową reprezentowane jako punkt stałym lub Liczba wymierna</span><span class="sxs-lookup"><span data-stu-id="f06ee-156">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="f06ee-157">M lub m</span><span class="sxs-lookup"><span data-stu-id="f06ee-157">M or m</span></span>|<span data-ttu-id="f06ee-158">`0.7833M` lub `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="f06ee-158">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="f06ee-159">Char</span><span class="sxs-lookup"><span data-stu-id="f06ee-159">Char</span></span>|<span data-ttu-id="f06ee-160">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="f06ee-160">Unicode character</span></span>|<span data-ttu-id="f06ee-161">brak</span><span class="sxs-lookup"><span data-stu-id="f06ee-161">none</span></span>|`'a'`|
|<span data-ttu-id="f06ee-162">String</span><span class="sxs-lookup"><span data-stu-id="f06ee-162">String</span></span>|<span data-ttu-id="f06ee-163">Ciąg w formacie Unicode</span><span class="sxs-lookup"><span data-stu-id="f06ee-163">Unicode string</span></span>|<span data-ttu-id="f06ee-164">brak</span><span class="sxs-lookup"><span data-stu-id="f06ee-164">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="f06ee-165">lub</span><span class="sxs-lookup"><span data-stu-id="f06ee-165">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="f06ee-166">lub</span><span class="sxs-lookup"><span data-stu-id="f06ee-166">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="f06ee-167">lub</span><span class="sxs-lookup"><span data-stu-id="f06ee-167">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="f06ee-168">Zobacz też [ciągów](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="f06ee-168">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="f06ee-169">byte</span><span class="sxs-lookup"><span data-stu-id="f06ee-169">byte</span></span>|<span data-ttu-id="f06ee-170">Znaków ASCII</span><span class="sxs-lookup"><span data-stu-id="f06ee-170">ASCII character</span></span>|<span data-ttu-id="f06ee-171">B</span><span class="sxs-lookup"><span data-stu-id="f06ee-171">B</span></span>|`'a'B`|
|<span data-ttu-id="f06ee-172">byte[]</span><span class="sxs-lookup"><span data-stu-id="f06ee-172">byte[]</span></span>|<span data-ttu-id="f06ee-173">Ciąg ASCII</span><span class="sxs-lookup"><span data-stu-id="f06ee-173">ASCII string</span></span>|<span data-ttu-id="f06ee-174">B</span><span class="sxs-lookup"><span data-stu-id="f06ee-174">B</span></span>|`"text"B`|
|<span data-ttu-id="f06ee-175">String lub byte]</span><span class="sxs-lookup"><span data-stu-id="f06ee-175">String or byte[]</span></span>|<span data-ttu-id="f06ee-176">ciągu dosłownego wyrażenia</span><span class="sxs-lookup"><span data-stu-id="f06ee-176">verbatim string</span></span>|<span data-ttu-id="f06ee-177">@ prefiksu</span><span class="sxs-lookup"><span data-stu-id="f06ee-177">@ prefix</span></span>|<span data-ttu-id="f06ee-178">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="f06ee-178">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="f06ee-179">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="f06ee-179">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="f06ee-180">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f06ee-180">Remarks</span></span>
<span data-ttu-id="f06ee-181">Ciągów Unicode może zawierać jawnych kodowania, którą można określić za pomocą `\u` następuje szesnastkowy kod 16-bitowy lub kodowania UTF-32, którą można określić za pomocą `\U` następuje 32-bitowy kod szesnastkowe, który reprezentuje Unicode Para zastępcza.</span><span class="sxs-lookup"><span data-stu-id="f06ee-181">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="f06ee-182">Począwszy od F # 3.1, można użyć `+` logowanie się łączenie literałów ciągu.</span><span class="sxs-lookup"><span data-stu-id="f06ee-182">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="f06ee-183">Można również użyć operatora testu koniunkcji lub (`|||`) operatora łączenia wyliczenia flag.</span><span class="sxs-lookup"><span data-stu-id="f06ee-183">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="f06ee-184">Na przykład następujący kod jest dozwolony w F # 3.1:</span><span class="sxs-lookup"><span data-stu-id="f06ee-184">For example, the following code is legal in F# 3.1:</span></span>

```fsharp
[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

<span data-ttu-id="f06ee-185">Korzystanie z innych operatory bitowe nie jest dozwolona.</span><span class="sxs-lookup"><span data-stu-id="f06ee-185">The use of other bitwise operators isn't allowed.</span></span>


## <a name="named-literals"></a><span data-ttu-id="f06ee-186">Literały nazwanego</span><span class="sxs-lookup"><span data-stu-id="f06ee-186">Named Literals</span></span>
<span data-ttu-id="f06ee-187">Wartości, które mają być stałymi może być oznaczony przez [literału](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f06ee-187">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="f06ee-188">Ten atrybut ma wpływ powoduje wartość ma zostać skompilowana jako stała.</span><span class="sxs-lookup"><span data-stu-id="f06ee-188">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="f06ee-189">W wyrażeniach dopasowywania do wzorca identyfikatory, które zaczynają się od małych liter zawsze są traktowane jako zmienne, które mają być powiązane, a nie jako literały, dlatego należy zwykle należy używać początkowe wersaliki podczas definiowania literały.</span><span class="sxs-lookup"><span data-stu-id="f06ee-189">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="f06ee-190">Liczby całkowite w innych bazach</span><span class="sxs-lookup"><span data-stu-id="f06ee-190">Integers In Other Bases</span></span>

<span data-ttu-id="f06ee-191">Liczb całkowitych ze znakiem 32-bitowych można również określić za pomocą szesnastkowych, ósemkowe lub binarne `0x`, `0o` lub `0b` odpowiednio prefiksu.</span><span class="sxs-lookup"><span data-stu-id="f06ee-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="f06ee-192">Podkreślenia w literałach numerycznych</span><span class="sxs-lookup"><span data-stu-id="f06ee-192">Underscores in Numeric Literals</span></span>

<span data-ttu-id="f06ee-193">Począwszy od 4.1 F # można oddzielić cyfr znakiem podkreślenia (`_`).</span><span class="sxs-lookup"><span data-stu-id="f06ee-193">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="f06ee-194">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f06ee-194">See Also</span></span>

[<span data-ttu-id="f06ee-195">Core.literalattribute — klasa</span><span class="sxs-lookup"><span data-stu-id="f06ee-195">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
