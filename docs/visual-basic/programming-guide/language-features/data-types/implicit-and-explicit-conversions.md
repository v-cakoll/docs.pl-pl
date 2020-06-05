---
title: Konwersje jawne i niejawne
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
ms.openlocfilehash: 2858dafd2531bd846ad89672348d103f385c4511
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393834"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="77d6e-102">Konwersje jawne i niejawne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77d6e-102">Implicit and Explicit Conversions (Visual Basic)</span></span>

<span data-ttu-id="77d6e-103">*Niejawna konwersja* nie wymaga żadnej specjalnej składni w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="77d6e-103">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="77d6e-104">W poniższym przykładzie Visual Basic niejawnie konwertuje wartość `k` do wartości zmiennoprzecinkowej o pojedynczej precyzji przed przypisaniem do `q` .</span><span class="sxs-lookup"><span data-stu-id="77d6e-104">In the following example, Visual Basic implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>

```vb
Dim k As Integer
Dim q As Double
' Integer widens to Double, so you can do this with Option Strict On.
k = 432
q = k
```

<span data-ttu-id="77d6e-105">*Jawna konwersja* używa słowa kluczowego konwersji typu.</span><span class="sxs-lookup"><span data-stu-id="77d6e-105">An *explicit conversion* uses a type conversion keyword.</span></span> <span data-ttu-id="77d6e-106">Visual Basic udostępnia kilka takich słów kluczowych, które przekształcają wyrażenie w nawiasy z żądanym typem danych.</span><span class="sxs-lookup"><span data-stu-id="77d6e-106">Visual Basic provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="77d6e-107">Te słowa kluczowe działają podobnie do funkcji, ale kompilator generuje kod wewnętrznie, więc wykonywanie jest nieco szybsze niż w przypadku wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="77d6e-107">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>

<span data-ttu-id="77d6e-108">W poniższym rozszerzeniu poprzedniego przykładu `CInt` słowo kluczowe konwertuje wartość z `q` powrotem na liczbę całkowitą przed przypisaniem do `k` .</span><span class="sxs-lookup"><span data-stu-id="77d6e-108">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>

```vb
' q had been assigned the value 432 from k.
q = Math.Sqrt(q)
k = CInt(q)
' k now has the value 21 (rounded square root of 432).
```

## <a name="conversion-keywords"></a><span data-ttu-id="77d6e-109">Słowa kluczowe konwersji</span><span class="sxs-lookup"><span data-stu-id="77d6e-109">Conversion Keywords</span></span>

<span data-ttu-id="77d6e-110">W poniższej tabeli przedstawiono dostępne słowa kluczowe konwersji.</span><span class="sxs-lookup"><span data-stu-id="77d6e-110">The following table shows the available conversion keywords.</span></span>

|<span data-ttu-id="77d6e-111">Słowo kluczowe konwersji typu</span><span class="sxs-lookup"><span data-stu-id="77d6e-111">Type conversion keyword</span></span>|<span data-ttu-id="77d6e-112">Konwertuje wyrażenie na typ danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-112">Converts an expression to data type</span></span>|<span data-ttu-id="77d6e-113">Dozwolone typy danych wyrażenia do przekonwertowania</span><span class="sxs-lookup"><span data-stu-id="77d6e-113">Allowable data types of expression to be converted</span></span>|
|---|---|---|
|`CBool`|[<span data-ttu-id="77d6e-114">Boolean, typ danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-114">Boolean Data Type</span></span>](../../../language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="77d6e-115">Dowolny typ liczbowy (w `Byte` tym `SByte` typy, i wyliczane), `String` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="77d6e-115">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|
|`CByte`|[<span data-ttu-id="77d6e-116">Byte, typ danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-116">Byte Data Type</span></span>](../../../language-reference/data-types/byte-data-type.md)|<span data-ttu-id="77d6e-117">Dowolny typ liczbowy ( `SByte` w tym i typy wyliczeniowe),, `Boolean` `String` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="77d6e-117">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CChar`|[<span data-ttu-id="77d6e-118">Char, typ danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-118">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)|<span data-ttu-id="77d6e-119">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="77d6e-119">`String`, `Object`</span></span>|
|`CDate`|[<span data-ttu-id="77d6e-120">Date, typ danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-120">Date Data Type</span></span>](../../../language-reference/data-types/date-data-type.md)|<span data-ttu-id="77d6e-121">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="77d6e-121">`String`, `Object`</span></span>|
|`CDbl`|[<span data-ttu-id="77d6e-122">Double, typ danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-122">Double Data Type</span></span>](../../../language-reference/data-types/double-data-type.md)|<span data-ttu-id="77d6e-123">Dowolny typ liczbowy (w `Byte` tym `SByte` typy wyliczeniowe),, `Boolean` , `String``Object`</span><span class="sxs-lookup"><span data-stu-id="77d6e-123">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CDec`|[<span data-ttu-id="77d6e-124">Decimal, typ danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-124">Decimal Data Type</span></span>](../../../language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="77d6e-125">Dowolny typ liczbowy (w `Byte` tym `SByte` typy wyliczeniowe),, `Boolean` , `String``Object`</span><span class="sxs-lookup"><span data-stu-id="77d6e-125">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CInt`|[<span data-ttu-id="77d6e-126">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-126">Integer Data Type</span></span>](../../../language-reference/data-types/integer-data-type.md)|<span data-ttu-id="77d6e-127">Dowolny typ liczbowy (w `Byte` tym `SByte` typy wyliczeniowe),, `Boolean` , `String``Object`</span><span class="sxs-lookup"><span data-stu-id="77d6e-127">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CLng`|[<span data-ttu-id="77d6e-128">Long, typ danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-128">Long Data Type</span></span>](../../../language-reference/data-types/long-data-type.md)|<span data-ttu-id="77d6e-129">Dowolny typ liczbowy (w `Byte` tym `SByte` typy wyliczeniowe),, `Boolean` , `String``Object`</span><span class="sxs-lookup"><span data-stu-id="77d6e-129">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CObj`|[<span data-ttu-id="77d6e-130">Object — typ danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-130">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)|<span data-ttu-id="77d6e-131">Dowolny typ</span><span class="sxs-lookup"><span data-stu-id="77d6e-131">Any type</span></span>|
|`CSByte`|[<span data-ttu-id="77d6e-132">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-132">SByte Data Type</span></span>](../../../language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="77d6e-133">Dowolny typ liczbowy ( `Byte` w tym i typy wyliczeniowe),, `Boolean` `String` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="77d6e-133">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CShort`|[<span data-ttu-id="77d6e-134">Short, typ danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-134">Short Data Type</span></span>](../../../language-reference/data-types/short-data-type.md)|<span data-ttu-id="77d6e-135">Dowolny typ liczbowy (w `Byte` tym `SByte` typy wyliczeniowe),, `Boolean` , `String``Object`</span><span class="sxs-lookup"><span data-stu-id="77d6e-135">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CSng`|[<span data-ttu-id="77d6e-136">Single, typ danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-136">Single Data Type</span></span>](../../../language-reference/data-types/single-data-type.md)|<span data-ttu-id="77d6e-137">Dowolny typ liczbowy (w `Byte` tym `SByte` typy wyliczeniowe),, `Boolean` , `String``Object`</span><span class="sxs-lookup"><span data-stu-id="77d6e-137">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CStr`|[<span data-ttu-id="77d6e-138">Typ danych ciągu</span><span class="sxs-lookup"><span data-stu-id="77d6e-138">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)|<span data-ttu-id="77d6e-139">Dowolny typ liczbowy (w `Byte` tym `SByte` typy wyliczeniowe), `Boolean` , `Char` , `Char` Array, `Date` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="77d6e-139">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|
|`CType`|<span data-ttu-id="77d6e-140">Typ określony po przecinku ( `,` )</span><span class="sxs-lookup"><span data-stu-id="77d6e-140">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="77d6e-141">Podczas konwertowania na *Typ danych podstawowych* (włącznie z tablicą typu elementarnego) te same typy, które są dozwolone dla odpowiedniego słowa kluczowego konwersji</span><span class="sxs-lookup"><span data-stu-id="77d6e-141">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="77d6e-142">Podczas konwertowania na *Typ danych złożonych*, interfejsy, które implementuje, oraz klasy, z których dziedziczy</span><span class="sxs-lookup"><span data-stu-id="77d6e-142">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="77d6e-143">Podczas konwertowania na klasę lub strukturę, w której jest przeciążona `CType` , ta klasa lub struktura</span><span class="sxs-lookup"><span data-stu-id="77d6e-143">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|
|`CUInt`|[<span data-ttu-id="77d6e-144">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-144">UInteger Data Type</span></span>](../../../language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="77d6e-145">Dowolny typ liczbowy (w `Byte` tym `SByte` typy wyliczeniowe),, `Boolean` , `String``Object`</span><span class="sxs-lookup"><span data-stu-id="77d6e-145">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CULng`|[<span data-ttu-id="77d6e-146">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-146">ULong Data Type</span></span>](../../../language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="77d6e-147">Dowolny typ liczbowy (w `Byte` tym `SByte` typy wyliczeniowe),, `Boolean` , `String``Object`</span><span class="sxs-lookup"><span data-stu-id="77d6e-147">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CUShort`|[<span data-ttu-id="77d6e-148">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-148">UShort Data Type</span></span>](../../../language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="77d6e-149">Dowolny typ liczbowy (w `Byte` tym `SByte` typy wyliczeniowe),, `Boolean` , `String``Object`</span><span class="sxs-lookup"><span data-stu-id="77d6e-149">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|

## <a name="the-ctype-function"></a><span data-ttu-id="77d6e-150">Funkcja CType</span><span class="sxs-lookup"><span data-stu-id="77d6e-150">The CType Function</span></span>

<span data-ttu-id="77d6e-151">[Funkcja CType](../../../language-reference/functions/ctype-function.md) działa na dwóch argumentach.</span><span class="sxs-lookup"><span data-stu-id="77d6e-151">The [CType Function](../../../language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="77d6e-152">Pierwszy jest wyrażeniem, które ma zostać przekonwertowane, a drugi to docelowy typ danych lub Klasa obiektu.</span><span class="sxs-lookup"><span data-stu-id="77d6e-152">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="77d6e-153">Należy zauważyć, że pierwszy argument musi być wyrażeniem, a nie typem.</span><span class="sxs-lookup"><span data-stu-id="77d6e-153">Note that the first argument must be an expression, not a type.</span></span>

<span data-ttu-id="77d6e-154">`CType`jest *funkcją wbudowaną*, co oznacza, że skompilowany kod wykonuje konwersję, często bez generowania wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="77d6e-154">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="77d6e-155">Zwiększa to wydajność.</span><span class="sxs-lookup"><span data-stu-id="77d6e-155">This improves performance.</span></span>

<span data-ttu-id="77d6e-156">Aby porównać z `CType` innymi słowami kluczowymi konwersji, zobacz [operator DirectCast](../../../language-reference/operators/directcast-operator.md) i [operator TryCast](../../../language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="77d6e-156">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../language-reference/operators/trycast-operator.md).</span></span>

### <a name="elementary-types"></a><span data-ttu-id="77d6e-157">Typy elementarne</span><span class="sxs-lookup"><span data-stu-id="77d6e-157">Elementary Types</span></span>

<span data-ttu-id="77d6e-158">Poniższy przykład ilustruje użycie `CType` .</span><span class="sxs-lookup"><span data-stu-id="77d6e-158">The following example demonstrates the use of `CType`.</span></span>

```vb
k = CType(q, Integer)
' The following statement coerces w to the specific object class Label.
f = CType(w, Label)
```

### <a name="composite-types"></a><span data-ttu-id="77d6e-159">Typy złożone</span><span class="sxs-lookup"><span data-stu-id="77d6e-159">Composite Types</span></span>

<span data-ttu-id="77d6e-160">Można użyć `CType` do przekonwertowania wartości na złożone typy danych, a także do typów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="77d6e-160">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="77d6e-161">Można go również użyć do przekształcenia klasy Object na typ jednego z jego interfejsów, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="77d6e-161">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>

```vb
' Assume class cZone implements interface iZone.
Dim h As Object
' The first argument to CType must be an expression, not a type.
Dim cZ As cZone
' The following statement coerces a cZone object to its interface iZone.
h = CType(cZ, iZone)
```

### <a name="array-types"></a><span data-ttu-id="77d6e-162">Typy tablic</span><span class="sxs-lookup"><span data-stu-id="77d6e-162">Array Types</span></span>

<span data-ttu-id="77d6e-163">`CType`można również skonwertować typy danych tablicy, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="77d6e-163">`CType` can also convert array data types, as in the following example.</span></span>

```vb
Dim v() As classV
Dim obArray() As Object
' Assume some object array has been assigned to obArray.
' Check for run-time type compatibility.
If TypeOf obArray Is classV()
    ' obArray can be converted to classV.
    v = CType(obArray, classV())
End If
```

<span data-ttu-id="77d6e-164">Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz [konwersje tablic](array-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="77d6e-164">For more information and an example, see [Array Conversions](array-conversions.md).</span></span>

### <a name="types-defining-ctype"></a><span data-ttu-id="77d6e-165">Typy definiujące CType</span><span class="sxs-lookup"><span data-stu-id="77d6e-165">Types Defining CType</span></span>

<span data-ttu-id="77d6e-166">Można zdefiniować `CType` dla zdefiniowanej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="77d6e-166">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="77d6e-167">Pozwala to na konwertowanie wartości do i z typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="77d6e-167">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="77d6e-168">Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz [jak: definiowanie operatora konwersji](../procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="77d6e-168">For more information and an example, see [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>

> [!NOTE]
> <span data-ttu-id="77d6e-169">Wartości używane ze słowem kluczowym konwersji muszą być prawidłowe dla docelowego typu danych lub wystąpił błąd.</span><span class="sxs-lookup"><span data-stu-id="77d6e-169">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="77d6e-170">Na przykład, jeśli spróbujesz skonwertować `Long` do `Integer` , wartość `Long` musi znajdować się w zakresie prawidłowym dla `Integer` typu danych.</span><span class="sxs-lookup"><span data-stu-id="77d6e-170">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>

> [!CAUTION]
> <span data-ttu-id="77d6e-171">Określanie, `CType` aby konwertować z jednego typu klasy na inny błąd w czasie wykonywania, jeśli typ źródłowy nie pochodzi od typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="77d6e-171">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="77d6e-172">Taka awaria zgłasza <xref:System.InvalidCastException> wyjątek.</span><span class="sxs-lookup"><span data-stu-id="77d6e-172">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>

<span data-ttu-id="77d6e-173">Jeśli jednak jeden z typów jest zdefiniowaną strukturą lub klasą, a jeśli zdefiniowano ją `CType` w tej strukturze lub klasy, konwersja może się powieść, jeśli spełnia wymagania `CType` .</span><span class="sxs-lookup"><span data-stu-id="77d6e-173">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="77d6e-174">Zobacz [jak: definiowanie operatora konwersji](../procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="77d6e-174">See [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>

<span data-ttu-id="77d6e-175">Wykonywanie jawnej konwersji jest również znane jako *rzutowanie* wyrażenia do danego typu danych lub klasy obiektu.</span><span class="sxs-lookup"><span data-stu-id="77d6e-175">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>

## <a name="see-also"></a><span data-ttu-id="77d6e-176">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77d6e-176">See also</span></span>

- [<span data-ttu-id="77d6e-177">Konwersje plików w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77d6e-177">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="77d6e-178">Konwertowanie między ciągami a innymi typami danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-178">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="77d6e-179">Porady: konwertowanie obiektu do innego typu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77d6e-179">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="77d6e-180">Struktury</span><span class="sxs-lookup"><span data-stu-id="77d6e-180">Structures</span></span>](structures.md)
- [<span data-ttu-id="77d6e-181">Typy danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-181">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="77d6e-182">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="77d6e-182">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="77d6e-183">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="77d6e-183">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
