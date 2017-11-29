---
title: "Literały (F#)"
description: "Poznaj typy literału w języku programowania w języku F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4b1d6e9d-f933-4cd4-966d-d643152c27e4
ms.openlocfilehash: 6bb1f233b6846e226c4e73aee00b8cf77735fe2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="literals"></a><span data-ttu-id="7397a-104">Literały</span><span class="sxs-lookup"><span data-stu-id="7397a-104">Literals</span></span>

> [!NOTE]
<span data-ttu-id="7397a-105">Interfejs API łącza odwołań w tym artykule spowoduje przejście do MSDN (na razie).</span><span class="sxs-lookup"><span data-stu-id="7397a-105">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="7397a-106">Ten temat zawiera tabelę, która przedstawia sposób określić typ literału w języku F #.</span><span class="sxs-lookup"><span data-stu-id="7397a-106">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="7397a-107">Typy literału</span><span class="sxs-lookup"><span data-stu-id="7397a-107">Literal Types</span></span>
<span data-ttu-id="7397a-108">W poniższej tabeli przedstawiono typy literału w języku F #.</span><span class="sxs-lookup"><span data-stu-id="7397a-108">The following table shows the literal types in F#.</span></span> <span data-ttu-id="7397a-109">Znaki, które reprezentują cyfr w formacie szesnastkowym nie jest rozróżniana; znaki, które identyfikują typ jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="7397a-109">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="7397a-110">Typ</span><span class="sxs-lookup"><span data-stu-id="7397a-110">Type</span></span>|<span data-ttu-id="7397a-111">Opis</span><span class="sxs-lookup"><span data-stu-id="7397a-111">Description</span></span>|<span data-ttu-id="7397a-112">Sufiks lub prefiksu</span><span class="sxs-lookup"><span data-stu-id="7397a-112">Suffix or prefix</span></span>|<span data-ttu-id="7397a-113">Przykłady</span><span class="sxs-lookup"><span data-stu-id="7397a-113">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="7397a-114">sbyte</span><span class="sxs-lookup"><span data-stu-id="7397a-114">sbyte</span></span>|<span data-ttu-id="7397a-115">8-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="7397a-115">signed 8-bit integer</span></span>|<span data-ttu-id="7397a-116">t</span><span class="sxs-lookup"><span data-stu-id="7397a-116">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="7397a-117">byte</span><span class="sxs-lookup"><span data-stu-id="7397a-117">byte</span></span>|<span data-ttu-id="7397a-118">bez znaku 8-bitową liczbą naturalnych</span><span class="sxs-lookup"><span data-stu-id="7397a-118">unsigned 8-bit natural number</span></span>|<span data-ttu-id="7397a-119">UY</span><span class="sxs-lookup"><span data-stu-id="7397a-119">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="7397a-120">Int16</span><span class="sxs-lookup"><span data-stu-id="7397a-120">int16</span></span>|<span data-ttu-id="7397a-121">16-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="7397a-121">signed 16-bit integer</span></span>|<span data-ttu-id="7397a-122">s</span><span class="sxs-lookup"><span data-stu-id="7397a-122">s</span></span>|`86s`|
|<span data-ttu-id="7397a-123">UInt16</span><span class="sxs-lookup"><span data-stu-id="7397a-123">uint16</span></span>|<span data-ttu-id="7397a-124">niepodpisane 16-bitową liczbę naturalnych</span><span class="sxs-lookup"><span data-stu-id="7397a-124">unsigned 16-bit natural number</span></span>|<span data-ttu-id="7397a-125">US</span><span class="sxs-lookup"><span data-stu-id="7397a-125">us</span></span>|`86us`|
|<span data-ttu-id="7397a-126">int</span><span class="sxs-lookup"><span data-stu-id="7397a-126">int</span></span><br /><br /><span data-ttu-id="7397a-127">Int32</span><span class="sxs-lookup"><span data-stu-id="7397a-127">int32</span></span>|<span data-ttu-id="7397a-128">32-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="7397a-128">signed 32-bit integer</span></span>|<span data-ttu-id="7397a-129">l lub Brak</span><span class="sxs-lookup"><span data-stu-id="7397a-129">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="7397a-130">uint</span><span class="sxs-lookup"><span data-stu-id="7397a-130">uint</span></span><br /><br /><span data-ttu-id="7397a-131">UInt32</span><span class="sxs-lookup"><span data-stu-id="7397a-131">uint32</span></span>|<span data-ttu-id="7397a-132">niepodpisane 32-bitową liczbą naturalnych</span><span class="sxs-lookup"><span data-stu-id="7397a-132">unsigned 32-bit natural number</span></span>|<span data-ttu-id="7397a-133">u lub ul</span><span class="sxs-lookup"><span data-stu-id="7397a-133">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="7397a-134">unativeint —</span><span class="sxs-lookup"><span data-stu-id="7397a-134">unativeint</span></span>|<span data-ttu-id="7397a-135">wskaźnik natywny jako wartość bez znaku naturalnych</span><span class="sxs-lookup"><span data-stu-id="7397a-135">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="7397a-136">Wyrejestruj</span><span class="sxs-lookup"><span data-stu-id="7397a-136">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="7397a-137">Int64</span><span class="sxs-lookup"><span data-stu-id="7397a-137">int64</span></span>|<span data-ttu-id="7397a-138">64-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="7397a-138">signed 64-bit integer</span></span>|<span data-ttu-id="7397a-139">L</span><span class="sxs-lookup"><span data-stu-id="7397a-139">L</span></span>|`86L`|
|<span data-ttu-id="7397a-140">UInt64 —</span><span class="sxs-lookup"><span data-stu-id="7397a-140">uint64</span></span>|<span data-ttu-id="7397a-141">Liczba naturalnego 64-bitowa bez znaku</span><span class="sxs-lookup"><span data-stu-id="7397a-141">unsigned 64-bit natural number</span></span>|<span data-ttu-id="7397a-142">UL</span><span class="sxs-lookup"><span data-stu-id="7397a-142">UL</span></span>|`86UL`|
|<span data-ttu-id="7397a-143">pojedynczy, float32</span><span class="sxs-lookup"><span data-stu-id="7397a-143">single, float32</span></span>|<span data-ttu-id="7397a-144">32-bitowych liczb zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="7397a-144">32-bit floating point number</span></span>|<span data-ttu-id="7397a-145">F lub f</span><span class="sxs-lookup"><span data-stu-id="7397a-145">F or f</span></span>|<span data-ttu-id="7397a-146">`4.14F`lub`4.14f`</span><span class="sxs-lookup"><span data-stu-id="7397a-146">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="7397a-147">LF</span><span class="sxs-lookup"><span data-stu-id="7397a-147">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="7397a-148">float; podwójne</span><span class="sxs-lookup"><span data-stu-id="7397a-148">float; double</span></span>|<span data-ttu-id="7397a-149">64-bitowych liczb zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="7397a-149">64-bit floating point number</span></span>|<span data-ttu-id="7397a-150">brak</span><span class="sxs-lookup"><span data-stu-id="7397a-150">none</span></span>|<span data-ttu-id="7397a-151">`4.14`lub `2.3E+32` lub`2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="7397a-151">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="7397a-152">LF</span><span class="sxs-lookup"><span data-stu-id="7397a-152">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="7397a-153">bigint</span><span class="sxs-lookup"><span data-stu-id="7397a-153">bigint</span></span>|<span data-ttu-id="7397a-154">innymi reprezentacja 64-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="7397a-154">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="7397a-155">I</span><span class="sxs-lookup"><span data-stu-id="7397a-155">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="7397a-156">decimal</span><span class="sxs-lookup"><span data-stu-id="7397a-156">decimal</span></span>|<span data-ttu-id="7397a-157">liczbę ułamkową reprezentowane jako punkt stałym lub Liczba wymierna</span><span class="sxs-lookup"><span data-stu-id="7397a-157">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="7397a-158">M lub m</span><span class="sxs-lookup"><span data-stu-id="7397a-158">M or m</span></span>|<span data-ttu-id="7397a-159">`0.7833M`lub`0.7833m`</span><span class="sxs-lookup"><span data-stu-id="7397a-159">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="7397a-160">Char</span><span class="sxs-lookup"><span data-stu-id="7397a-160">Char</span></span>|<span data-ttu-id="7397a-161">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="7397a-161">Unicode character</span></span>|<span data-ttu-id="7397a-162">brak</span><span class="sxs-lookup"><span data-stu-id="7397a-162">none</span></span>|`'a'`|
|<span data-ttu-id="7397a-163">String</span><span class="sxs-lookup"><span data-stu-id="7397a-163">String</span></span>|<span data-ttu-id="7397a-164">Ciąg w formacie Unicode</span><span class="sxs-lookup"><span data-stu-id="7397a-164">Unicode string</span></span>|<span data-ttu-id="7397a-165">brak</span><span class="sxs-lookup"><span data-stu-id="7397a-165">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="7397a-166">lub</span><span class="sxs-lookup"><span data-stu-id="7397a-166">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="7397a-167">lub</span><span class="sxs-lookup"><span data-stu-id="7397a-167">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="7397a-168">lub</span><span class="sxs-lookup"><span data-stu-id="7397a-168">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="7397a-169">Zobacz też [ciągów](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="7397a-169">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="7397a-170">byte</span><span class="sxs-lookup"><span data-stu-id="7397a-170">byte</span></span>|<span data-ttu-id="7397a-171">Znaków ASCII</span><span class="sxs-lookup"><span data-stu-id="7397a-171">ASCII character</span></span>|<span data-ttu-id="7397a-172">B</span><span class="sxs-lookup"><span data-stu-id="7397a-172">B</span></span>|`'a'B`|
|<span data-ttu-id="7397a-173">Byte]</span><span class="sxs-lookup"><span data-stu-id="7397a-173">byte[]</span></span>|<span data-ttu-id="7397a-174">Ciąg ASCII</span><span class="sxs-lookup"><span data-stu-id="7397a-174">ASCII string</span></span>|<span data-ttu-id="7397a-175">B</span><span class="sxs-lookup"><span data-stu-id="7397a-175">B</span></span>|`"text"B`|
|<span data-ttu-id="7397a-176">String lub byte]</span><span class="sxs-lookup"><span data-stu-id="7397a-176">String or byte[]</span></span>|<span data-ttu-id="7397a-177">ciągu dosłownego wyrażenia</span><span class="sxs-lookup"><span data-stu-id="7397a-177">verbatim string</span></span>|<span data-ttu-id="7397a-178">@ prefiksu</span><span class="sxs-lookup"><span data-stu-id="7397a-178">@ prefix</span></span>|<span data-ttu-id="7397a-179">`@"\\server\share"`(Unicode)</span><span class="sxs-lookup"><span data-stu-id="7397a-179">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="7397a-180">`@"\\server\share"B`(ASCII)</span><span class="sxs-lookup"><span data-stu-id="7397a-180">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="7397a-181">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7397a-181">Remarks</span></span>
<span data-ttu-id="7397a-182">Ciągów Unicode może zawierać jawnych kodowania, którą można określić za pomocą `\u` następuje szesnastkowy kod 16-bitowy lub kodowania UTF-32, którą można określić za pomocą `\U` następuje 32-bitowy kod szesnastkowe, który reprezentuje Unicode Para zastępcza.</span><span class="sxs-lookup"><span data-stu-id="7397a-182">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="7397a-183">Począwszy od F # 3.1, można użyć `+` logowanie się łączenie literałów ciągu.</span><span class="sxs-lookup"><span data-stu-id="7397a-183">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="7397a-184">Można również użyć operatora testu koniunkcji lub (`|||`) operatora łączenia wyliczenia flag.</span><span class="sxs-lookup"><span data-stu-id="7397a-184">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="7397a-185">Na przykład następujący kod jest dozwolony w F # 3.1:</span><span class="sxs-lookup"><span data-stu-id="7397a-185">For example, the following code is legal in F# 3.1:</span></span>

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

<span data-ttu-id="7397a-186">Korzystanie z innych operatory bitowe nie jest dozwolona.</span><span class="sxs-lookup"><span data-stu-id="7397a-186">The use of other bitwise operators isn't allowed.</span></span>


## <a name="named-literals"></a><span data-ttu-id="7397a-187">Literały nazwanego</span><span class="sxs-lookup"><span data-stu-id="7397a-187">Named Literals</span></span>
<span data-ttu-id="7397a-188">Wartości, które mają być stałymi może być oznaczony przez [literału](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7397a-188">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="7397a-189">Ten atrybut ma wpływ powoduje wartość ma zostać skompilowana jako stała.</span><span class="sxs-lookup"><span data-stu-id="7397a-189">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="7397a-190">W wyrażeniach dopasowywania do wzorca identyfikatory, które zaczynają się od małych liter zawsze są traktowane jako zmienne, które mają być powiązane, a nie jako literały, dlatego należy zwykle należy używać początkowe wersaliki podczas definiowania literały.</span><span class="sxs-lookup"><span data-stu-id="7397a-190">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="7397a-191">Liczby całkowite w innych bazach</span><span class="sxs-lookup"><span data-stu-id="7397a-191">Integers In Other Bases</span></span>

<span data-ttu-id="7397a-192">Liczb całkowitych ze znakiem 32-bitowych można również określić za pomocą szesnastkowych, ósemkowe lub binarne `0x`, `0o` lub `0b` odpowiednio prefiksu.</span><span class="sxs-lookup"><span data-stu-id="7397a-192">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="7397a-193">Podkreślenia w literałach numerycznych</span><span class="sxs-lookup"><span data-stu-id="7397a-193">Underscores in Numeric Literals</span></span>

<span data-ttu-id="7397a-194">Począwszy od 4.1 F # można oddzielić cyfr znakiem podkreślenia (`_`).</span><span class="sxs-lookup"><span data-stu-id="7397a-194">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="7397a-195">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7397a-195">See Also</span></span>

[<span data-ttu-id="7397a-196">Core.literalattribute — klasa</span><span class="sxs-lookup"><span data-stu-id="7397a-196">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
