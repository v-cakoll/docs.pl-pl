---
title: Funkcje konwersji typu
ms.date: 10/24/2018
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: 3924da6ccbfea00668370f2fbcf4baf289be80db
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349970"
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="6a17f-102">Funkcje konwersji typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a17f-102">Type Conversion Functions (Visual Basic)</span></span>

<span data-ttu-id="6a17f-103">Te funkcje są kompilowane w tekście, co oznacza, że kod konwersji jest częścią kodu, który szacuje wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="6a17f-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="6a17f-104">Czasami nie istnieje wywołanie procedury w celu wykonania konwersji, co zwiększa wydajność.</span><span class="sxs-lookup"><span data-stu-id="6a17f-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="6a17f-105">Każda funkcja przekształca wyrażenie na określony typ danych.</span><span class="sxs-lookup"><span data-stu-id="6a17f-105">Each function coerces an expression to a specific data type.</span></span>

## <a name="syntax"></a><span data-ttu-id="6a17f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a17f-106">Syntax</span></span>

```vb
CBool(expression)
CByte(expression)
CChar(expression)
CDate(expression)
CDbl(expression)
CDec(expression)
CInt(expression)
CLng(expression)
CObj(expression)
CSByte(expression)
CShort(expression)
CSng(expression)
CStr(expression)
CUInt(expression)
CULng(expression)
CUShort(expression)
```

## <a name="part"></a><span data-ttu-id="6a17f-107">Części</span><span class="sxs-lookup"><span data-stu-id="6a17f-107">Part</span></span>

`expression`  
<span data-ttu-id="6a17f-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="6a17f-108">Required.</span></span> <span data-ttu-id="6a17f-109">Dowolne wyrażenie typu danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="6a17f-109">Any expression of the source data type.</span></span>

## <a name="return-value-data-type"></a><span data-ttu-id="6a17f-110">Typ danych wartości zwracanej</span><span class="sxs-lookup"><span data-stu-id="6a17f-110">Return Value Data Type</span></span>

<span data-ttu-id="6a17f-111">Nazwa funkcji określa typ danych zwracanej wartości, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="6a17f-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>

|<span data-ttu-id="6a17f-112">Nazwa funkcji</span><span class="sxs-lookup"><span data-stu-id="6a17f-112">Function name</span></span>|<span data-ttu-id="6a17f-113">Zwraca typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-113">Return data type</span></span>|<span data-ttu-id="6a17f-114">Zakres dla argumentu `expression`</span><span class="sxs-lookup"><span data-stu-id="6a17f-114">Range for `expression` argument</span></span>|
|-------------------|----------------------|-------------------------------------|
|`CBool`|[<span data-ttu-id="6a17f-115">Boolean, typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="6a17f-116">Dowolny prawidłowy `Char` lub `String` lub wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="6a17f-116">Any valid `Char` or `String` or numeric expression.</span></span>|
|`CByte`|[<span data-ttu-id="6a17f-117">Byte, typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="6a17f-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) do <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (bez znaku); części ułamkowe są zaokrąglane. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6a17f-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) through <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="6a17f-119">Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność konwersji zmiennoprzecinkowej na wartość typu Byte z funkcją `CByte`; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6a17f-119">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to byte conversion with the `CByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="6a17f-120">Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="6a17f-120">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CChar`|[<span data-ttu-id="6a17f-121">Char, typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-121">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="6a17f-122">Dowolne prawidłowe wyrażenie `Char` lub `String`; konwertowany jest tylko pierwszy znak `String`; wartość może być równa 0 – 65535 (bez znaku).</span><span class="sxs-lookup"><span data-stu-id="6a17f-122">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|
|`CDate`|[<span data-ttu-id="6a17f-123">Date, typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-123">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="6a17f-124">Dowolna prawidłowa reprezentacja daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="6a17f-124">Any valid representation of a date and time.</span></span>|
|`CDbl`|[<span data-ttu-id="6a17f-125">Double, typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-125">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="6a17f-126">-1.79769313486231570 e + 308 do-4.94065645841246544 E-324 dla wartości ujemnych; 4.94065645841246544 e-324 za pośrednictwem 1.79769313486231570 E + 308 dla wartości dodatnich.</span><span class="sxs-lookup"><span data-stu-id="6a17f-126">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|
|`CDec`|[<span data-ttu-id="6a17f-127">Decimal, typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-127">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="6a17f-128">+/-79228162514264337593543950335 dla liczb o zerowej skali, czyli liczb bez miejsc dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="6a17f-128">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="6a17f-129">W przypadku liczb z 28 miejscami dziesiętnymi zakresem jest +/-7.9228162514264337593543950335.</span><span class="sxs-lookup"><span data-stu-id="6a17f-129">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="6a17f-130">Najmniejsza możliwa liczba różna od zera to 0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="6a17f-130">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|
|`CInt`|[<span data-ttu-id="6a17f-131">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="6a17f-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2 147 483 648) do <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2 147 483 647); części ułamkowe są zaokrąglane. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6a17f-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) through <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2,147,483,647); fractional parts are rounded.<sup>1</sup></span></span> <br/><br/><span data-ttu-id="6a17f-133">Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność konwersji zmiennoprzecinkowej na liczbę całkowitą przy użyciu funkcji `CInt`; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6a17f-133">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to integer conversion with the `CInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="6a17f-134">Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="6a17f-134">See the [CInt Example](#cint-example) section for an example.</span></span> |
|`CLng`|[<span data-ttu-id="6a17f-135">Long, typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-135">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="6a17f-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-zakresu od) za <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9 223 372 036 854 775 807); części ułamkowe są zaokrąglane. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6a17f-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) through <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="6a17f-137">Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność operacji zmiennoprzecinkowych do 64-bitowej konwersji liczb całkowitych za pomocą funkcji `CLng`; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6a17f-137">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 64-bit integer conversion with the `CLng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="6a17f-138">Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="6a17f-138">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CObj`|[<span data-ttu-id="6a17f-139">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-139">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="6a17f-140">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="6a17f-140">Any valid expression.</span></span>|
|`CSByte`|[<span data-ttu-id="6a17f-141">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-141">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="6a17f-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) do <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); części ułamkowe są zaokrąglane. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6a17f-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) through <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="6a17f-143">Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność przeprowadzenia zmiennoprzecinkowej konwersji bajtów z funkcją `CSByte`; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6a17f-143">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to signed byte conversion with the `CSByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="6a17f-144">Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="6a17f-144">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CShort`|[<span data-ttu-id="6a17f-145">Short, typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-145">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="6a17f-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32 768) do <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32 767); części ułamkowe są zaokrąglane. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6a17f-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) through <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="6a17f-147">Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność konwersji zmiennoprzecinkowej na 16-bitową liczbę całkowitą przy użyciu funkcji `CShort`; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6a17f-147">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 16-bit integer conversion with the `CShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="6a17f-148">Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="6a17f-148">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CSng`|[<span data-ttu-id="6a17f-149">Single, typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-149">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="6a17f-150">-3.402823 e + 38 do-1.401298 E-45 dla wartości ujemnych; 1.401298 e-45 za pośrednictwem 3.402823 E + 38 w przypadku wartości dodatnich.</span><span class="sxs-lookup"><span data-stu-id="6a17f-150">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|
|`CStr`|[<span data-ttu-id="6a17f-151">String, typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-151">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="6a17f-152">Zwraca dla `CStr` zależą od argumentu `expression`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-152">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="6a17f-153">Zobacz [wartości zwracane dla funkcji CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="6a17f-153">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|
|`CUInt`|[<span data-ttu-id="6a17f-154">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-154">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="6a17f-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) do <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4 294 967 295) (bez znaku); części ułamkowe są zaokrąglane. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6a17f-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="6a17f-156">Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność konwersji zmiennoprzecinkowej do niepodpisanej liczby całkowitej przy użyciu funkcji `CUInt`; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6a17f-156">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned integer conversion with the `CUInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="6a17f-157">Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="6a17f-157">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CULng`|[<span data-ttu-id="6a17f-158">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-158">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="6a17f-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) do <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18446744073709551615 są) (bez znaku); części ułamkowe są zaokrąglane. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6a17f-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="6a17f-160">Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność operacji zmiennoprzecinkowych do konwersji długich liczb całkowitych bez znaku przy użyciu funkcji `CULng`; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6a17f-160">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned long integer conversion with the `CULng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="6a17f-161">Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="6a17f-161">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CUShort`|[<span data-ttu-id="6a17f-162">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="6a17f-162">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="6a17f-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) do <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65 535) (bez znaku); części ułamkowe są zaokrąglane. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6a17f-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="6a17f-164">Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność zmiennoprzecinkowej niepodpisanej 16-bitowej konwersji liczb całkowitych za pomocą funkcji `CUShort`; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6a17f-164">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned 16-bit integer conversion with the `CUShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="6a17f-165">Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="6a17f-165">See the [CInt Example](#cint-example) section for an example.</span></span>|

<span data-ttu-id="6a17f-166"><sup>1</sup> części ułamkowe mogą podlegać specjalnemu typowi zaokrąglania wywołanemu przez *Bank*.</span><span class="sxs-lookup"><span data-stu-id="6a17f-166"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="6a17f-167">Aby uzyskać więcej informacji, zobacz "uwagi".</span><span class="sxs-lookup"><span data-stu-id="6a17f-167">See "Remarks" for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a17f-168">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a17f-168">Remarks</span></span>

<span data-ttu-id="6a17f-169">Jako regułę należy użyć funkcji konwersji typu Visual Basic w preferencjach do metod .NET Framework, takich jak `ToString()`, w klasie <xref:System.Convert> lub w strukturze lub klasie poszczególnych typów.</span><span class="sxs-lookup"><span data-stu-id="6a17f-169">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="6a17f-170">Funkcje Visual Basic są przeznaczone do optymalnej interakcji z kodem Visual Basic, a także sprawiają, że kod źródłowy jest krótszy i łatwiejszy do odczytania.</span><span class="sxs-lookup"><span data-stu-id="6a17f-170">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="6a17f-171">Ponadto metody konwersji .NET Framework nie zawsze generują te same wyniki co funkcje Visual Basic, na przykład podczas konwertowania `Boolean` na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-171">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="6a17f-172">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="6a17f-172">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

<span data-ttu-id="6a17f-173">Począwszy od Visual Basic 15,8, wydajność konwersji zmiennoprzecinkowej na liczbę całkowitą jest optymalizowana po przejściu <xref:System.Single> lub <xref:System.Double> wartości zwróconej przez następujące metody do jednej z funkcji konwersji liczb całkowitych (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span><span class="sxs-lookup"><span data-stu-id="6a17f-173">Starting with Visual Basic 15.8, the performance of floating-point-to-integer conversion is optimized when you pass the <xref:System.Single> or <xref:System.Double> value returned by the following methods to one of the integer conversion functions (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

<span data-ttu-id="6a17f-174">Ta optymalizacja umożliwia kod, który wykonuje dużą liczbę konwersji liczb całkowitych do dwukrotnego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="6a17f-174">This optimization allows code that does a large number of integer conversions to run up to twice as fast.</span></span> <span data-ttu-id="6a17f-175">Poniższy przykład ilustruje te zoptymalizowane konwersje zmiennoprzecinkowe do liczby całkowitej:</span><span class="sxs-lookup"><span data-stu-id="6a17f-175">The following example illustrates these optimized floating-point-to-integer conversions:</span></span>

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a><span data-ttu-id="6a17f-176">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="6a17f-176">Behavior</span></span>

- <span data-ttu-id="6a17f-177">**Wymuszanie.**</span><span class="sxs-lookup"><span data-stu-id="6a17f-177">**Coercion.**</span></span> <span data-ttu-id="6a17f-178">Ogólnie rzecz biorąc, można użyć funkcji konwersji typu danych, aby przekształcić wynik operacji do określonego typu danych, a nie domyślnego typu danych.</span><span class="sxs-lookup"><span data-stu-id="6a17f-178">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="6a17f-179">Na przykład użyj `CDec`, aby wymusić arytmetyczną liczbę dziesiętną w przypadkach, gdy zwykle odbywa się przeprowadzenie arytmetycznej pojedynczej precyzji, podwójnej precyzji lub liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="6a17f-179">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>

- <span data-ttu-id="6a17f-180">**Konwersje zakończone niepowodzeniem.**</span><span class="sxs-lookup"><span data-stu-id="6a17f-180">**Failed Conversions.**</span></span> <span data-ttu-id="6a17f-181">Jeśli `expression` przeniesiona do funkcji znajduje się poza zakresem typu danych, do którego ma zostać przekonwertowane, występuje <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="6a17f-181">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>

- <span data-ttu-id="6a17f-182">**Części ułamkowe.**</span><span class="sxs-lookup"><span data-stu-id="6a17f-182">**Fractional Parts.**</span></span> <span data-ttu-id="6a17f-183">W przypadku konwersji niecałkowitej wartości na typ całkowity, funkcje konwersji liczb całkowitych (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`i `CUShort`) Usuń część ułamkową i Zaokrąglij wartość do najbliższej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="6a17f-183">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>

     <span data-ttu-id="6a17f-184">Jeśli część ułamkowa ma wartość dokładnie 0,5, funkcja konwersji liczb całkowitych zaokrągli ją do najbliższej parzystej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="6a17f-184">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="6a17f-185">Na przykład 0,5 zaokrągla do 0, i 1,5 i 2,5 oba do 2.</span><span class="sxs-lookup"><span data-stu-id="6a17f-185">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="6a17f-186">Jest to czasami nazywane *zaokrąglaniem w banku*, a jego celem jest zrekompensowanie odchylenia, które może wystąpić w przypadku dodawania wielu takich liczb jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="6a17f-186">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>

     <span data-ttu-id="6a17f-187">`CInt` i `CLng` różnią się od funkcji <xref:Microsoft.VisualBasic.Conversion.Int%2A> i <xref:Microsoft.VisualBasic.Conversion.Fix%2A>, które obcinają, a nie zaokrąglają część ułamkową liczby.</span><span class="sxs-lookup"><span data-stu-id="6a17f-187">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="6a17f-188">Ponadto `Fix` i `Int` zawsze zwracają wartość tego samego typu danych podczas przekazywania.</span><span class="sxs-lookup"><span data-stu-id="6a17f-188">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>

- <span data-ttu-id="6a17f-189">**Konwersje daty/godziny.**</span><span class="sxs-lookup"><span data-stu-id="6a17f-189">**Date/Time Conversions.**</span></span> <span data-ttu-id="6a17f-190">Użyj funkcji <xref:Microsoft.VisualBasic.Information.IsDate%2A>, aby określić, czy wartość może zostać przekonwertowana na datę i godzinę.</span><span class="sxs-lookup"><span data-stu-id="6a17f-190">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="6a17f-191">`CDate` rozpoznaje literały daty i literały czasowe, ale nie wartości numeryczne.</span><span class="sxs-lookup"><span data-stu-id="6a17f-191">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="6a17f-192">Aby przekonwertować wartość Visual Basic 6,0 `Date` na wartość `Date` w Visual Basic 2005 lub nowszej wersji, można użyć metody <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6a17f-192">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="6a17f-193">**Neutralne wartości daty/godziny.**</span><span class="sxs-lookup"><span data-stu-id="6a17f-193">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="6a17f-194">[Typ danych Data](../../../visual-basic/language-reference/data-types/date-data-type.md) zawsze zawiera informacje o dacie i godzinie.</span><span class="sxs-lookup"><span data-stu-id="6a17f-194">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="6a17f-195">Na potrzeby konwersji typów Visual Basic uznaje, że 1/1/0001 (1 stycznia roku 1) jest *wartością neutralną* dla daty oraz 00:00:00 (północy) jako wartość neutralną czasu.</span><span class="sxs-lookup"><span data-stu-id="6a17f-195">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="6a17f-196">Jeśli przekonwertujesz wartość `Date` na ciąg, `CStr` nie zawiera neutralnych wartości w ciągu wynikiem.</span><span class="sxs-lookup"><span data-stu-id="6a17f-196">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="6a17f-197">Na przykład w przypadku konwersji `#January 1, 0001 9:30:00#` na ciąg, wynikiem jest "9:30:00 AM"; Informacje o dacie są pomijane.</span><span class="sxs-lookup"><span data-stu-id="6a17f-197">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="6a17f-198">Jednak informacje o dacie są nadal obecne w oryginalnej wartości `Date` i mogą być odzyskiwane za pomocą funkcji, takich jak funkcja <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span><span class="sxs-lookup"><span data-stu-id="6a17f-198">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>

- <span data-ttu-id="6a17f-199">**Czułość kultury.**</span><span class="sxs-lookup"><span data-stu-id="6a17f-199">**Culture Sensitivity.**</span></span> <span data-ttu-id="6a17f-200">Funkcje konwersji typów obejmujące ciągi wykonują konwersje w oparciu o bieżące ustawienia kultury dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6a17f-200">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="6a17f-201">Na przykład `CDate` rozpoznaje formaty dat zgodnie z ustawieniami regionalnymi systemu.</span><span class="sxs-lookup"><span data-stu-id="6a17f-201">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="6a17f-202">Musisz podać dzień, miesiąc i rok w prawidłowej kolejności dla ustawień regionalnych lub Data może nie być interpretowana poprawnie.</span><span class="sxs-lookup"><span data-stu-id="6a17f-202">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="6a17f-203">Format daty długiej nie jest rozpoznawany, jeśli zawiera ciąg dni tygodnia, taki jak "Środa".</span><span class="sxs-lookup"><span data-stu-id="6a17f-203">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>

     <span data-ttu-id="6a17f-204">Jeśli konieczne jest przekonwertowanie na lub z ciągu reprezentującego wartość w formacie innym niż określony przez ustawienia regionalne, nie można użyć funkcji konwersji typu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6a17f-204">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="6a17f-205">Aby to zrobić, użyj metod `ToString(IFormatProvider)` i `Parse(String, IFormatProvider)` typu tej wartości.</span><span class="sxs-lookup"><span data-stu-id="6a17f-205">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="6a17f-206">Na przykład użyj <xref:System.Double.Parse%2A?displayProperty=nameWithType> podczas konwertowania ciągu na `Double`i użyj <xref:System.Double.ToString%2A?displayProperty=nameWithType> podczas konwertowania wartości typu `Double` na ciąg.</span><span class="sxs-lookup"><span data-stu-id="6a17f-206">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>

## <a name="ctype-function"></a><span data-ttu-id="6a17f-207">CType — Funkcja</span><span class="sxs-lookup"><span data-stu-id="6a17f-207">CType Function</span></span>

<span data-ttu-id="6a17f-208">[Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md) przyjmuje drugi argument, `typename`i przekształcenie `expression` do `typename`, gdzie `typename` może być dowolnym typem danych, strukturą, klasą lub interfejsem, do którego istnieje prawidłowa konwersja.</span><span class="sxs-lookup"><span data-stu-id="6a17f-208">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>

<span data-ttu-id="6a17f-209">Aby porównać `CType` z innymi słowami kluczowymi konwersji typu, zobacz [operator DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) i [operator TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="6a17f-209">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>

## <a name="cbool-example"></a><span data-ttu-id="6a17f-210">Przykład CBool</span><span class="sxs-lookup"><span data-stu-id="6a17f-210">CBool Example</span></span>

<span data-ttu-id="6a17f-211">W poniższym przykładzie zastosowano funkcję `CBool`, aby przekonwertować wyrażenia na `Boolean` wartości.</span><span class="sxs-lookup"><span data-stu-id="6a17f-211">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="6a17f-212">Jeśli wyrażenie daje w wyniku wartość różną od zera, `CBool` zwraca `True`; w przeciwnym razie zwraca `False`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-212">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>

[!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]

## <a name="cbyte-example"></a><span data-ttu-id="6a17f-213">Przykład CByte</span><span class="sxs-lookup"><span data-stu-id="6a17f-213">CByte Example</span></span>

<span data-ttu-id="6a17f-214">W poniższym przykładzie zastosowano funkcję `CByte`, aby przekonwertować wyrażenie na `Byte`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-214">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>

[!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]

## <a name="cchar-example"></a><span data-ttu-id="6a17f-215">Przykład CChar</span><span class="sxs-lookup"><span data-stu-id="6a17f-215">CChar Example</span></span>

<span data-ttu-id="6a17f-216">Poniższy przykład używa funkcji `CChar`, aby skonwertować pierwszy znak wyrażenia `String` na typ `Char`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-216">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>

[!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]

<span data-ttu-id="6a17f-217">Argument wejściowy do `CChar` musi być typu danych `Char` lub `String`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-217">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="6a17f-218">Nie można użyć `CChar` do przekonwertowania liczby na znak, ponieważ `CChar` nie może akceptować typu danych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="6a17f-218">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="6a17f-219">Poniższy przykład pobiera liczbę reprezentującą punkt kodu (kod znaku) i konwertuje ją na odpowiedni znak.</span><span class="sxs-lookup"><span data-stu-id="6a17f-219">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="6a17f-220">Używa funkcji <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> w celu uzyskania ciągu cyfr, `CInt` do przekonwertowania ciągu na typ `Integer`i `ChrW` do przekonwertowania liczby na typ `Char`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-220">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>

[!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]

## <a name="cdate-example"></a><span data-ttu-id="6a17f-221">Przykład CDate</span><span class="sxs-lookup"><span data-stu-id="6a17f-221">CDate Example</span></span>

<span data-ttu-id="6a17f-222">W poniższym przykładzie zastosowano funkcję `CDate`, aby przekonwertować ciągi na `Date` wartości.</span><span class="sxs-lookup"><span data-stu-id="6a17f-222">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="6a17f-223">Ogólnie rzecz biorąc, stałe kodowanie i godziny w postaci ciągów (jak pokazano w tym przykładzie) nie są zalecane.</span><span class="sxs-lookup"><span data-stu-id="6a17f-223">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="6a17f-224">Używaj literałów daty i literałów czasowych, takich jak #Feb 12, 1969 # i #4:45:23 PM #, zamiast.</span><span class="sxs-lookup"><span data-stu-id="6a17f-224">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>

[!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]

## <a name="cdbl-example"></a><span data-ttu-id="6a17f-225">Przykład CDbl</span><span class="sxs-lookup"><span data-stu-id="6a17f-225">CDbl Example</span></span>

[!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]

## <a name="cdec-example"></a><span data-ttu-id="6a17f-226">Przykład CDec</span><span class="sxs-lookup"><span data-stu-id="6a17f-226">CDec Example</span></span>

<span data-ttu-id="6a17f-227">W poniższym przykładzie została użyta funkcja `CDec` do przekonwertowania wartości liczbowej na `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-227">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>

[!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]

## <a name="cint-example"></a><span data-ttu-id="6a17f-228">Przykład CInt</span><span class="sxs-lookup"><span data-stu-id="6a17f-228">CInt Example</span></span>

<span data-ttu-id="6a17f-229">Poniższy przykład używa funkcji `CInt`, aby przekonwertować wartość na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-229">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>

[!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]

## <a name="clng-example"></a><span data-ttu-id="6a17f-230">Przykład CLng</span><span class="sxs-lookup"><span data-stu-id="6a17f-230">CLng Example</span></span>

<span data-ttu-id="6a17f-231">Poniższy przykład używa funkcji `CLng`, aby konwertować wartości na `Long`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-231">The following example uses the `CLng` function to convert values to `Long`.</span></span>

[!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]

## <a name="cobj-example"></a><span data-ttu-id="6a17f-232">Przykład CObj</span><span class="sxs-lookup"><span data-stu-id="6a17f-232">CObj Example</span></span>

<span data-ttu-id="6a17f-233">W poniższym przykładzie została użyta funkcja `CObj` do przekonwertowania wartości liczbowej na `Object`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-233">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="6a17f-234">Sama zmienna `Object` zawiera tylko wskaźnik z czterema bajtami, który wskazuje na przypisaną do `Double` wartość.</span><span class="sxs-lookup"><span data-stu-id="6a17f-234">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>

[!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]

## <a name="csbyte-example"></a><span data-ttu-id="6a17f-235">Przykład CSByte</span><span class="sxs-lookup"><span data-stu-id="6a17f-235">CSByte Example</span></span>

<span data-ttu-id="6a17f-236">W poniższym przykładzie została użyta funkcja `CSByte` do przekonwertowania wartości liczbowej na `SByte`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-236">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>

[!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]

## <a name="cshort-example"></a><span data-ttu-id="6a17f-237">Przykład CShort</span><span class="sxs-lookup"><span data-stu-id="6a17f-237">CShort Example</span></span>

<span data-ttu-id="6a17f-238">W poniższym przykładzie została użyta funkcja `CShort` do przekonwertowania wartości liczbowej na `Short`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-238">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>

[!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]

## <a name="csng-example"></a><span data-ttu-id="6a17f-239">Przykład CSng</span><span class="sxs-lookup"><span data-stu-id="6a17f-239">CSng Example</span></span>

<span data-ttu-id="6a17f-240">Poniższy przykład używa funkcji `CSng`, aby konwertować wartości na `Single`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-240">The following example uses the `CSng` function to convert values to `Single`.</span></span>

[!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]

## <a name="cstr-example"></a><span data-ttu-id="6a17f-241">Przykład CStr</span><span class="sxs-lookup"><span data-stu-id="6a17f-241">CStr Example</span></span>

<span data-ttu-id="6a17f-242">W poniższym przykładzie została użyta funkcja `CStr` do przekonwertowania wartości liczbowej na `String`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-242">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>

[!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]

<span data-ttu-id="6a17f-243">Poniższy przykład używa funkcji `CStr`, aby przekonwertować wartości `Date` na wartości `String`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-243">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>

[!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]

<span data-ttu-id="6a17f-244">`CStr` zawsze renderuje `Date` wartość w standardowym formacie skróconym dla bieżących ustawień regionalnych, na przykład "6/15/2003 4:35:47 PM".</span><span class="sxs-lookup"><span data-stu-id="6a17f-244">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="6a17f-245">Jednak `CStr` pomija *wartości neutralnych* 1/1/0001 dla daty i 00:00:00 przez czas.</span><span class="sxs-lookup"><span data-stu-id="6a17f-245">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>

<span data-ttu-id="6a17f-246">Aby uzyskać więcej szczegółów na temat wartości zwracanych przez `CStr`, zobacz [zwracają wartości dla funkcji CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="6a17f-246">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>

## <a name="cuint-example"></a><span data-ttu-id="6a17f-247">Przykład CUInt</span><span class="sxs-lookup"><span data-stu-id="6a17f-247">CUInt Example</span></span>

<span data-ttu-id="6a17f-248">W poniższym przykładzie została użyta funkcja `CUInt` do przekonwertowania wartości liczbowej na `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-248">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>

[!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]

## <a name="culng-example"></a><span data-ttu-id="6a17f-249">Przykład CULng</span><span class="sxs-lookup"><span data-stu-id="6a17f-249">CULng Example</span></span>

<span data-ttu-id="6a17f-250">W poniższym przykładzie została użyta funkcja `CULng` do przekonwertowania wartości liczbowej na `ULong`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-250">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>

[!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]

## <a name="cushort-example"></a><span data-ttu-id="6a17f-251">Przykład CUShort</span><span class="sxs-lookup"><span data-stu-id="6a17f-251">CUShort Example</span></span>

<span data-ttu-id="6a17f-252">W poniższym przykładzie została użyta funkcja `CUShort` do przekonwertowania wartości liczbowej na `UShort`.</span><span class="sxs-lookup"><span data-stu-id="6a17f-252">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>

[!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]

## <a name="see-also"></a><span data-ttu-id="6a17f-253">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a17f-253">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="6a17f-254">Funkcje konwersji</span><span class="sxs-lookup"><span data-stu-id="6a17f-254">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="6a17f-255">Konwersje typów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6a17f-255">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
