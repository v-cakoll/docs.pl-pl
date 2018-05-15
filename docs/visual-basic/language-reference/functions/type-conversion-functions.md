---
title: Funkcje konwersji typu (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: c9222bdb31f4fd7c792d5a50c100067e29e9d537
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="8b4ac-102">Funkcje konwersji typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b4ac-102">Type Conversion Functions (Visual Basic)</span></span>
<span data-ttu-id="8b4ac-103">Te funkcje są skompilowaną wbudowaną, co oznacza, że kod konwersji jest częścią kodu, który wylicza wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="8b4ac-104">Czasami nie istnieje żadne wywołanie procedury do wykonania konwersji, co zwiększa wydajność.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="8b4ac-105">Każda funkcja przekształca wyrażenie określonego typu danych.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-105">Each function coerces an expression to a specific data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b4ac-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b4ac-106">Syntax</span></span>  
  
```  
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
  
## <a name="part"></a><span data-ttu-id="8b4ac-107">Część</span><span class="sxs-lookup"><span data-stu-id="8b4ac-107">Part</span></span>  
 `expression`  
 <span data-ttu-id="8b4ac-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-108">Required.</span></span> <span data-ttu-id="8b4ac-109">Dowolne wyrażenie typu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-109">Any expression of the source data type.</span></span>  
  
## <a name="return-value-data-type"></a><span data-ttu-id="8b4ac-110">Zwraca typ danych wartości</span><span class="sxs-lookup"><span data-stu-id="8b4ac-110">Return Value Data Type</span></span>  
 <span data-ttu-id="8b4ac-111">Nazwa funkcji określa typ danych wartości, która zwraca, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>  
  
|<span data-ttu-id="8b4ac-112">Nazwa funkcji</span><span class="sxs-lookup"><span data-stu-id="8b4ac-112">Function name</span></span>|<span data-ttu-id="8b4ac-113">Zwracany typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-113">Return data type</span></span>|<span data-ttu-id="8b4ac-114">Zakres dla `expression` argumentu</span><span class="sxs-lookup"><span data-stu-id="8b4ac-114">Range for `expression` argument</span></span>|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[<span data-ttu-id="8b4ac-115">Boolean, typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="8b4ac-116">Wszystkie prawidłowe `Char` lub `String` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-116">Any valid `Char` or `String` or numeric expression.</span></span>|  
|`CByte`|[<span data-ttu-id="8b4ac-117">Byte, typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="8b4ac-118">0 do 255 (bez znaku); są zaokrąglane ułamkowych części. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8b4ac-118">0 through 255 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CChar`|[<span data-ttu-id="8b4ac-119">Char, typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-119">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="8b4ac-120">Wszystkie prawidłowe `Char` lub `String` wyrażenia, tylko pierwszy znak `String` konwersji; możliwe wartości od 0 do 65535 (bez znaku).</span><span class="sxs-lookup"><span data-stu-id="8b4ac-120">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|  
|`CDate`|[<span data-ttu-id="8b4ac-121">Date, typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-121">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="8b4ac-122">Wszystkie prawidłowe reprezentacja daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-122">Any valid representation of a date and time.</span></span>|  
|`CDbl`|[<span data-ttu-id="8b4ac-123">Double, typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-123">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="8b4ac-124">-1.79769313486231570E + 308 do - 4.94065645841246544E-324 dla wartości ujemnych; 4.94065645841246544E-324 za pośrednictwem 1.79769313486231570E + 308 do wartości dodatnie.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-124">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|  
|`CDec`|[<span data-ttu-id="8b4ac-125">Decimal, typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-125">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="8b4ac-126">+/-79,228,162,514,264,337,593,543,950,335 162 514 liczb, czyli liczby bez miejsc dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-126">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="8b4ac-127">W przypadku numerów 28 miejsc dziesiętnych zakres jest +/-7.9228162514264337593543950335.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-127">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="8b4ac-128">Najmniejsza możliwa liczba niezerowa to 0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="8b4ac-128">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|  
|`CInt`|[<span data-ttu-id="8b4ac-129">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-129">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="8b4ac-130">-2,147,483,648 do 2 147 483 647; są zaokrąglane ułamkowych części. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8b4ac-130">-2,147,483,648 through 2,147,483,647; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CLng`|[<span data-ttu-id="8b4ac-131">Long, typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-131">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="8b4ac-132">-9,223,372,036,854,775,808 za pośrednictwem 9,223,372,036,854,775,807; są zaokrąglane ułamkowych części. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8b4ac-132">-9,223,372,036,854,775,808 through 9,223,372,036,854,775,807; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CObj`|[<span data-ttu-id="8b4ac-133">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-133">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="8b4ac-134">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-134">Any valid expression.</span></span>|  
|`CSByte`|[<span data-ttu-id="8b4ac-135">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-135">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="8b4ac-136">-128 do 127; są zaokrąglane ułamkowych części. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8b4ac-136">-128 through 127; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CShort`|[<span data-ttu-id="8b4ac-137">Short, typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-137">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="8b4ac-138">-32 768 do 32 767; są zaokrąglane ułamkowych części. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8b4ac-138">-32,768 through 32,767; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CSng`|[<span data-ttu-id="8b4ac-139">Single, typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-139">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="8b4ac-140">-3.402823E + 38 do - 1, 401298E-45 dla wartości ujemnych; 1, 401298E-45 za pośrednictwem 3.402823E + 38 dla wartości dodatnie.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-140">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|  
|`CStr`|[<span data-ttu-id="8b4ac-141">String, typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-141">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="8b4ac-142">Zwraca `CStr` są zależne od `expression` argumentu.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-142">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="8b4ac-143">Zobacz [zwracane wartości dla funkcji CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="8b4ac-143">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|  
|`CUInt`|[<span data-ttu-id="8b4ac-144">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-144">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="8b4ac-145">od 0 do 4 294 967 295 (bez znaku); są zaokrąglane ułamkowych części. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8b4ac-145">0 through 4,294,967,295 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CULng`|[<span data-ttu-id="8b4ac-146">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-146">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="8b4ac-147">od 0 do 18,446,744,073,709,551,615 (bez znaku); są zaokrąglane ułamkowych części. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8b4ac-147">0 through 18,446,744,073,709,551,615 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CUShort`|[<span data-ttu-id="8b4ac-148">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="8b4ac-148">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="8b4ac-149">od 0 do 65 535 (bez znaku); są zaokrąglane ułamkowych części. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8b4ac-149">0 through 65,535 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
  
 <span data-ttu-id="8b4ac-150"><sup>1</sup> ułamkowych części mogą podlegać specjalny typ zaokrąglania wywołane *zaokrąglenie do zaokrąglania*.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-150"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="8b4ac-151">Aby uzyskać więcej informacji, zobacz "Uwagi".</span><span class="sxs-lookup"><span data-stu-id="8b4ac-151">See "Remarks" for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b4ac-152">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b4ac-152">Remarks</span></span>  
 <span data-ttu-id="8b4ac-153">Jako regułę, należy używać funkcje konwersji typu Visual Basic, zamiast metod .NET Framework takie jak `ToString()`, albo na <xref:System.Convert> klasy lub na poszczególnych typ struktury lub klasy.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-153">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="8b4ac-154">Funkcje Visual Basic są przeznaczone do optymalnego interakcji z kodu języka Visual Basic, a także umożliwiają kod źródłowy krótsze i łatwiejsze do odczytu.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-154">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="8b4ac-155">Ponadto metody konwersji .NET Framework nie zawsze utworzyć takie same wyniki jako funkcje języka Visual Basic, na przykład podczas konwertowania `Boolean` do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-155">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="8b4ac-156">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="8b4ac-156">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="8b4ac-157">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="8b4ac-157">Behavior</span></span>  
  
-   <span data-ttu-id="8b4ac-158">**Koercja.**</span><span class="sxs-lookup"><span data-stu-id="8b4ac-158">**Coercion.**</span></span> <span data-ttu-id="8b4ac-159">Ogólnie rzecz biorąc można użyć funkcji konwersji typu danych konwersji wynik operacji do określonego typu danych niż domyślny typ danych.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-159">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="8b4ac-160">Na przykład użyć `CDec` wymusić dziesiętną arytmetyczne w przypadkach, gdy pojedynczej precyzji, podwójnej precyzji lub liczba całkowita arytmetyczne zwykle nastąpiłoby.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-160">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>  
  
-   <span data-ttu-id="8b4ac-161">**Konwersje nie powiodło się.**</span><span class="sxs-lookup"><span data-stu-id="8b4ac-161">**Failed Conversions.**</span></span> <span data-ttu-id="8b4ac-162">Jeśli `expression` przekazany do funkcji jest poza zakresem typu danych, których ma zostać przekonwertowany, <xref:System.OverflowException> występuje.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-162">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>  
  
-   <span data-ttu-id="8b4ac-163">**Ułamkowych części.**</span><span class="sxs-lookup"><span data-stu-id="8b4ac-163">**Fractional Parts.**</span></span> <span data-ttu-id="8b4ac-164">Podczas konwertowania wartości nonintegral typem całkowitym typ, liczbę całkowitą funkcji konwersji (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, i `CUShort`) Usuń ułamkowych części i zaokrąglona do najbliższej liczby całkowitej wartość.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-164">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>  
  
     <span data-ttu-id="8b4ac-165">Jeśli część ułamkowa jest dokładnie 0,5, funkcje konwersji całkowitą zaokrąglona do najbliższej parzystej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-165">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="8b4ac-166">Na przykład 0,5 zaokrągla wartość 0 i w wersji 1.5 i 2.5, który zarówno zaokrąglona do 2.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-166">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="8b4ac-167">Jest to czasem nazywane *zaokrąglenie do zaokrąglania*, a jej celem jest kompensacji odchylenia, który może narastać, dodając takiej liczby razem.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-167">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>  
  
     <span data-ttu-id="8b4ac-168">`CInt` i `CLng` różnią się od <xref:Microsoft.VisualBasic.Conversion.Int%2A> i <xref:Microsoft.VisualBasic.Conversion.Fix%2A> funkcji, które truncate, zamiast zaokrąglona ułamkową część liczby.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-168">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="8b4ac-169">Ponadto `Fix` i `Int` zawsze zwraca wartość typu danych podczas przemieszczania w.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-169">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>  
  
-   <span data-ttu-id="8b4ac-170">**Data/Godzina konwersji.**</span><span class="sxs-lookup"><span data-stu-id="8b4ac-170">**Date/Time Conversions.**</span></span> <span data-ttu-id="8b4ac-171">Użyj <xref:Microsoft.VisualBasic.Information.IsDate%2A> funkcji, aby określić, jeśli można przekonwertować wartości na datę i godzinę.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-171">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="8b4ac-172">`CDate` rozpoznaje literałów dat i godzin, ale wartości liczbowych nie.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-172">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="8b4ac-173">Aby przekonwertować Visual Basic 6.0 `Date` do wartości `Date` wartość w języku Visual Basic 2005 lub nowszym, można użyć <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> — metoda.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-173">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="8b4ac-174">**Neutralna wartości daty/godziny.**</span><span class="sxs-lookup"><span data-stu-id="8b4ac-174">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="8b4ac-175">[Date — typ danych](../../../visual-basic/language-reference/data-types/date-data-type.md) zawsze zawiera informacje zarówno datę i godzinę.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-175">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="8b4ac-176">W celu konwersji typu, Visual Basic uważa 1/1/0001 (1 stycznia 1 roku) *neutralne wartość* daty i 00:00:00 (północ) jako neutralny wartość po raz.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-176">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="8b4ac-177">W przypadku przekonwertowania `Date` wartość na ciąg `CStr` nie ma wartości neutralne w ciągu wynikowym.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-177">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="8b4ac-178">Na przykład, jeśli przekonwertujesz `#January 1, 0001 9:30:00#` na ciąg, wynikiem jest "9:30:00 AM"; informacje o dacie jest pomijane.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-178">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="8b4ac-179">Jednak informacje o dacie jest nadal znajdują się w oryginalnym `Date` wartości i może zostać przywrócona z funkcji takich jak <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> funkcji.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-179">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>  
  
-   <span data-ttu-id="8b4ac-180">**Czułość kultury.**</span><span class="sxs-lookup"><span data-stu-id="8b4ac-180">**Culture Sensitivity.**</span></span> <span data-ttu-id="8b4ac-181">Funkcje konwersji typu obejmującego ciągów wykonaj konwersje w oparciu o bieżące ustawienia kultury dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-181">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="8b4ac-182">Na przykład `CDate` rozpoznaje formaty daty zgodnie z ustawieniem ustawień regionalnych systemu.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-182">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="8b4ac-183">Należy podać dzień, miesiąc i rok w odpowiedniej kolejności dla ustawień regionalnych użytkownika lub daty może nie być prawidłowo interpretowane.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-183">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="8b4ac-184">Nie rozpoznano formatu daty długiej, jeśli zawiera ciąg dzień tygodnia, takie jak "Środa".</span><span class="sxs-lookup"><span data-stu-id="8b4ac-184">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>  
  
     <span data-ttu-id="8b4ac-185">Jeśli chcesz przekonwertować z reprezentacji ciągu wartości w formacie innym niż określony przez ustawienia regionalne lub nie można użyć funkcje konwersji typu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-185">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="8b4ac-186">Aby to zrobić, użyj `ToString(IFormatProvider)` i `Parse(String, IFormatProvider)` metod z typem tej wartości.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-186">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="8b4ac-187">Na przykład użyć <xref:System.Double.Parse%2A?displayProperty=nameWithType> podczas konwertowania ciągu na `Double`i użyj <xref:System.Double.ToString%2A?displayProperty=nameWithType> podczas konwertowania wartości typu `Double` na ciąg.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-187">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>  
  
## <a name="ctype-function"></a><span data-ttu-id="8b4ac-188">CType — Funkcja</span><span class="sxs-lookup"><span data-stu-id="8b4ac-188">CType Function</span></span>  
 <span data-ttu-id="8b4ac-189">[CType — funkcja](../../../visual-basic/language-reference/functions/ctype-function.md) przyjmuje drugi argument, `typename`i przekształca wynik dane `expression` do `typename`, gdzie `typename` może być typu danych, struktury, klasy lub interfejsu, do którego istnieje prawidłowa konwersja.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-189">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>  
  
 <span data-ttu-id="8b4ac-190">Porównanie `CType` z innych typów słowa kluczowe konwersji, zobacz [operatora DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) i [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="8b4ac-190">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
## <a name="cbool-example"></a><span data-ttu-id="8b4ac-191">Przykład CBool</span><span class="sxs-lookup"><span data-stu-id="8b4ac-191">CBool Example</span></span>  
 <span data-ttu-id="8b4ac-192">W poniższym przykładzie użyto `CBool` funkcji konwersji wyrażenia do `Boolean` wartości.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-192">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="8b4ac-193">Jeśli wyrażenie ma wartość różną od zera `CBool` zwraca `True`; w przeciwnym razie zwraca `False`.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-193">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## <a name="cbyte-example"></a><span data-ttu-id="8b4ac-194">Przykład CByte</span><span class="sxs-lookup"><span data-stu-id="8b4ac-194">CByte Example</span></span>  
 <span data-ttu-id="8b4ac-195">W poniższym przykładzie użyto `CByte` funkcji konwersji wyrażenia do `Byte`.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-195">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## <a name="cchar-example"></a><span data-ttu-id="8b4ac-196">Przykład CChar</span><span class="sxs-lookup"><span data-stu-id="8b4ac-196">CChar Example</span></span>  
 <span data-ttu-id="8b4ac-197">W poniższym przykładzie użyto `CChar` funkcji konwersji pierwszego znaku `String` wyrażenie `Char` typu.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-197">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 <span data-ttu-id="8b4ac-198">Argument wejściowy `CChar` musi być typu danych `Char` lub `String`.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-198">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="8b4ac-199">Nie można użyć `CChar` do konwertowania wartości na znak, ponieważ `CChar` nie może akceptować dane typu liczbowego.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-199">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="8b4ac-200">Poniższy przykład uzyskuje liczba reprezentująca punkt kodu (kod znaku) i konwertuje ją na odpowiedni znak.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-200">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="8b4ac-201">Używa <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> funkcji, aby uzyskać ciąg cyfr, `CInt` można przekonwertować ciągu na typ `Integer`, i `ChrW` do konwertowanie liczby na typ `Char`.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-201">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## <a name="cdate-example"></a><span data-ttu-id="8b4ac-202">Przykład CDate</span><span class="sxs-lookup"><span data-stu-id="8b4ac-202">CDate Example</span></span>  
 <span data-ttu-id="8b4ac-203">W poniższym przykładzie użyto `CDate` funkcji konwersji ciągów na `Date` wartości.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-203">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="8b4ac-204">Ogólnie rzecz biorąc kodować dat i godzin jako ciągi (jak pokazano w tym przykładzie) nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-204">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="8b4ac-205">Użyj literałów dat i godzin, takie jak #Feb 12, 1969 # i # 4:45:23 PM #, zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-205">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## <a name="cdbl-example"></a><span data-ttu-id="8b4ac-206">Przykład CDbl</span><span class="sxs-lookup"><span data-stu-id="8b4ac-206">CDbl Example</span></span>  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## <a name="cdec-example"></a><span data-ttu-id="8b4ac-207">Przykład CDec</span><span class="sxs-lookup"><span data-stu-id="8b4ac-207">CDec Example</span></span>  
 <span data-ttu-id="8b4ac-208">W poniższym przykładzie użyto `CDec` funkcji konwersji wartość liczbową `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-208">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## <a name="cint-example"></a><span data-ttu-id="8b4ac-209">Przykład CInt</span><span class="sxs-lookup"><span data-stu-id="8b4ac-209">CInt Example</span></span>  
 <span data-ttu-id="8b4ac-210">W poniższym przykładzie użyto `CInt` funkcji można przekonwertować wartości na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-210">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  
  
## <a name="clng-example"></a><span data-ttu-id="8b4ac-211">Przykład CLng</span><span class="sxs-lookup"><span data-stu-id="8b4ac-211">CLng Example</span></span>  
 <span data-ttu-id="8b4ac-212">W poniższym przykładzie użyto `CLng` funkcji można przekonwertować wartości na `Long`.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-212">The following example uses the `CLng` function to convert values to `Long`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## <a name="cobj-example"></a><span data-ttu-id="8b4ac-213">Przykład CObj</span><span class="sxs-lookup"><span data-stu-id="8b4ac-213">CObj Example</span></span>  
 <span data-ttu-id="8b4ac-214">W poniższym przykładzie użyto `CObj` funkcji konwersji wartość liczbową `Object`.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-214">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="8b4ac-215">`Object` Samej zmiennej zawierają tylko wskaźnik 4 bajtowych, która wskazuje na `Double` wartość przypisana do niego.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-215">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## <a name="csbyte-example"></a><span data-ttu-id="8b4ac-216">Przykład CSByte</span><span class="sxs-lookup"><span data-stu-id="8b4ac-216">CSByte Example</span></span>  
 <span data-ttu-id="8b4ac-217">W poniższym przykładzie użyto `CSByte` funkcji konwersji wartość liczbową `SByte`.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-217">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## <a name="cshort-example"></a><span data-ttu-id="8b4ac-218">Przykład CShort</span><span class="sxs-lookup"><span data-stu-id="8b4ac-218">CShort Example</span></span>  
 <span data-ttu-id="8b4ac-219">W poniższym przykładzie użyto `CShort` funkcji konwersji wartość liczbową `Short`.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-219">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## <a name="csng-example"></a><span data-ttu-id="8b4ac-220">Przykład CSng</span><span class="sxs-lookup"><span data-stu-id="8b4ac-220">CSng Example</span></span>  
 <span data-ttu-id="8b4ac-221">W poniższym przykładzie użyto `CSng` funkcji można przekonwertować wartości na `Single`.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-221">The following example uses the `CSng` function to convert values to `Single`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## <a name="cstr-example"></a><span data-ttu-id="8b4ac-222">Przykład CStr</span><span class="sxs-lookup"><span data-stu-id="8b4ac-222">CStr Example</span></span>  
 <span data-ttu-id="8b4ac-223">W poniższym przykładzie użyto `CStr` funkcji konwersji wartość liczbową `String`.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-223">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 <span data-ttu-id="8b4ac-224">W poniższym przykładzie użyto `CStr` funkcji konwersji `Date` wartości do `String` wartości.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-224">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 <span data-ttu-id="8b4ac-225">`CStr` zawsze renderuje `Date` wartość w standardowym formacie krótkiej dla bieżących ustawień regionalnych, na przykład "15-6-2003 4:35:47 PM".</span><span class="sxs-lookup"><span data-stu-id="8b4ac-225">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="8b4ac-226">Jednak `CStr` pomija *niezależnym od wartości* z 1/1/0001 daty i 00:00:00 czasu.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-226">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>  
  
 <span data-ttu-id="8b4ac-227">Aby uzyskać więcej szczegółów na wartości zwracanych przez `CStr`, zobacz [zwracać wartości dla funkcji CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="8b4ac-227">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>  
  
## <a name="cuint-example"></a><span data-ttu-id="8b4ac-228">Przykład CUInt</span><span class="sxs-lookup"><span data-stu-id="8b4ac-228">CUInt Example</span></span>  
 <span data-ttu-id="8b4ac-229">W poniższym przykładzie użyto `CUInt` funkcji konwersji wartość liczbową `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-229">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## <a name="culng-example"></a><span data-ttu-id="8b4ac-230">Przykład CULng</span><span class="sxs-lookup"><span data-stu-id="8b4ac-230">CULng Example</span></span>  
 <span data-ttu-id="8b4ac-231">W poniższym przykładzie użyto `CULng` funkcji konwersji wartość liczbową `ULong`.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-231">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## <a name="cushort-example"></a><span data-ttu-id="8b4ac-232">Przykład CUShort</span><span class="sxs-lookup"><span data-stu-id="8b4ac-232">CUShort Example</span></span>  
 <span data-ttu-id="8b4ac-233">W poniższym przykładzie użyto `CUShort` funkcji konwersji wartość liczbową `UShort`.</span><span class="sxs-lookup"><span data-stu-id="8b4ac-233">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#18](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8b4ac-234">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b4ac-234">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 <xref:Microsoft.VisualBasic.Strings.Format%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Oct%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Str%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [<span data-ttu-id="8b4ac-235">Funkcje konwersji</span><span class="sxs-lookup"><span data-stu-id="8b4ac-235">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [<span data-ttu-id="8b4ac-236">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8b4ac-236">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
