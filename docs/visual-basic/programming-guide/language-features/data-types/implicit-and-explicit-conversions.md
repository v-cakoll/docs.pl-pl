---
title: Konwersje jawne i niejawne (Visual Basic)
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
ms.openlocfilehash: 82ff710629089cd14c7e982b4afa4301d0790811
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834000"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="f4ce6-102">Konwersje jawne i niejawne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4ce6-102">Implicit and Explicit Conversions (Visual Basic)</span></span>
<span data-ttu-id="f4ce6-103">*Niejawna konwersja* nie wymaga żadnych specjalnej składni w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-103">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="f4ce6-104">W poniższym przykładzie Visual Basic niejawnie konwertuje wartość `k` na wartość zmiennoprzecinkową o pojedynczej dokładności przed przypisaniem go do `q`.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-104">In the following example, Visual Basic implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 <span data-ttu-id="f4ce6-105">*Jawną konwersję* używa słowa kluczowego konwersji typu.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-105">An *explicit conversion* uses a type conversion keyword.</span></span> <span data-ttu-id="f4ce6-106">Visual Basic oferuje kilka takich słowa kluczowe, które coerce — wyrażenia w nawiasach do danych żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-106">Visual Basic provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="f4ce6-107">Te słowa kluczowe zachowywać się jak functions, ale kompilator generuje kod inline, dzięki czemu wykonanie jest nieznacznie wyższa niż w przypadku wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-107">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>  
  
 <span data-ttu-id="f4ce6-108">Następujące rozszerzenia powyższego przykładu `CInt` — słowo kluczowe konwertuje wartość `q` do liczby całkowitej przed przypisaniem go do `k`.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-108">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a><span data-ttu-id="f4ce6-109">Słowa kluczowe konwersji</span><span class="sxs-lookup"><span data-stu-id="f4ce6-109">Conversion Keywords</span></span>  
 <span data-ttu-id="f4ce6-110">W poniższej tabeli przedstawiono słowa kluczowe konwersji dostępne.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-110">The following table shows the available conversion keywords.</span></span>  
  
|<span data-ttu-id="f4ce6-111">Konwersja typu — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="f4ce6-111">Type conversion keyword</span></span>|<span data-ttu-id="f4ce6-112">Konwertuje wyrażenie na typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-112">Converts an expression to data type</span></span>|<span data-ttu-id="f4ce6-113">Typy danych wyrażenia, które ma zostać przekonwertowany</span><span class="sxs-lookup"><span data-stu-id="f4ce6-113">Allowable data types of expression to be converted</span></span>|  
|---|---|---|  
|`CBool`|[<span data-ttu-id="f4ce6-114">Boolean, typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-114">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="f4ce6-115">Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="f4ce6-115">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|  
|`CByte`|[<span data-ttu-id="f4ce6-116">Byte, typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-116">Byte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="f4ce6-117">Dowolnego typu liczbowego (w tym `SByte` i są wyliczone typów), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="f4ce6-117">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CChar`|[<span data-ttu-id="f4ce6-118">Char, typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-118">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="f4ce6-119">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="f4ce6-119">`String`, `Object`</span></span>|  
|`CDate`|[<span data-ttu-id="f4ce6-120">Date, typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-120">Date Data Type</span></span>](../../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="f4ce6-121">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="f4ce6-121">`String`, `Object`</span></span>|  
|`CDbl`|[<span data-ttu-id="f4ce6-122">Double, typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-122">Double Data Type</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="f4ce6-123">Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="f4ce6-123">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CDec`|[<span data-ttu-id="f4ce6-124">Decimal, typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-124">Decimal Data Type</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="f4ce6-125">Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="f4ce6-125">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CInt`|[<span data-ttu-id="f4ce6-126">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-126">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="f4ce6-127">Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="f4ce6-127">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CLng`|[<span data-ttu-id="f4ce6-128">Long, typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-128">Long Data Type</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="f4ce6-129">Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="f4ce6-129">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CObj`|[<span data-ttu-id="f4ce6-130">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-130">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="f4ce6-131">Dowolnego typu</span><span class="sxs-lookup"><span data-stu-id="f4ce6-131">Any type</span></span>|  
|`CSByte`|[<span data-ttu-id="f4ce6-132">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-132">SByte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="f4ce6-133">Dowolnego typu liczbowego (w tym `Byte` i są wyliczone typów), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="f4ce6-133">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CShort`|[<span data-ttu-id="f4ce6-134">Short, typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-134">Short Data Type</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="f4ce6-135">Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="f4ce6-135">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CSng`|[<span data-ttu-id="f4ce6-136">Single, typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-136">Single Data Type</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="f4ce6-137">Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="f4ce6-137">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CStr`|[<span data-ttu-id="f4ce6-138">String, typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-138">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="f4ce6-139">Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `Char`, `Char` tablicy, `Date`, `Object`</span><span class="sxs-lookup"><span data-stu-id="f4ce6-139">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|  
|`CType`|<span data-ttu-id="f4ce6-140">Określony typ po przecinku (`,`)</span><span class="sxs-lookup"><span data-stu-id="f4ce6-140">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="f4ce6-141">Podczas konwertowania na *typu danych podstawowych* (łącznie z tablicy typu podstawowego) typy takie same jak dozwolone dla odpowiedniej konwersji — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="f4ce6-141">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="f4ce6-142">Podczas konwertowania na *złożonego typu danych*, interfejsy implementuje i klasy, z których dziedziczy</span><span class="sxs-lookup"><span data-stu-id="f4ce6-142">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="f4ce6-143">Podczas konwertowania na klasy lub struktury, na którym przeciążają `CType`, tej klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="f4ce6-143">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|  
|`CUInt`|[<span data-ttu-id="f4ce6-144">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-144">UInteger Data Type</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="f4ce6-145">Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="f4ce6-145">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CULng`|[<span data-ttu-id="f4ce6-146">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-146">ULong Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="f4ce6-147">Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="f4ce6-147">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CUShort`|[<span data-ttu-id="f4ce6-148">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-148">UShort Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="f4ce6-149">Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="f4ce6-149">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
  
## <a name="the-ctype-function"></a><span data-ttu-id="f4ce6-150">CType — funkcja</span><span class="sxs-lookup"><span data-stu-id="f4ce6-150">The CType Function</span></span>  
 <span data-ttu-id="f4ce6-151">[Funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md) działa na dwóch argumentów.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-151">The [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="f4ce6-152">Pierwszy jest wyrażeniem, które ma zostać przekonwertowany, a drugą jest wartość klasy docelowej danych typu lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-152">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="f4ce6-153">Należy pamiętać, że pierwszy argument musi być wyrażeniem, nie typu.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-153">Note that the first argument must be an expression, not a type.</span></span>  
  
 <span data-ttu-id="f4ce6-154">`CType` jest *funkcja śródwierszowa*, co oznacza skompilowany kod sprawia, że konwersja, często bez generowania funkcję wywołania.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-154">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="f4ce6-155">Poprawia to wydajność.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-155">This improves performance.</span></span>  
  
 <span data-ttu-id="f4ce6-156">Porównanie `CType` przy użyciu innych typów słowa kluczowe konwersji, zobacz [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) i [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f4ce6-156">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
### <a name="elementary-types"></a><span data-ttu-id="f4ce6-157">Typy podstawowe</span><span class="sxs-lookup"><span data-stu-id="f4ce6-157">Elementary Types</span></span>  
 <span data-ttu-id="f4ce6-158">W poniższym przykładzie pokazano użycie `CType`.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-158">The following example demonstrates the use of `CType`.</span></span>  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a><span data-ttu-id="f4ce6-159">Typy złożone</span><span class="sxs-lookup"><span data-stu-id="f4ce6-159">Composite Types</span></span>  
 <span data-ttu-id="f4ce6-160">Możesz użyć `CType` można przekonwertować wartości na złożone typy danych jak również do typów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-160">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="f4ce6-161">Można również użyć do zmuszania klasy obiektu na typ jednego z jego interfejsów, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-161">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a><span data-ttu-id="f4ce6-162">Typy tablic</span><span class="sxs-lookup"><span data-stu-id="f4ce6-162">Array Types</span></span>  
 <span data-ttu-id="f4ce6-163">`CType` można także przekonwertować typy danych tablicy, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-163">`CType` can also convert array data types, as in the following example.</span></span>  
  
```  
Dim v() As classV  
Dim obArray() As Object  
' Assume some object array has been assigned to obArray.  
' Check for run-time type compatibility.  
If TypeOf obArray Is classV()  
    ' obArray can be converted to classV.  
    v = CType(obArray, classV())  
End If  
```  
  
 <span data-ttu-id="f4ce6-164">Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [konwersje tablicę](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="f4ce6-164">For more information and an example, see [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span></span>  
  
### <a name="types-defining-ctype"></a><span data-ttu-id="f4ce6-165">Typy Definiowanie CType</span><span class="sxs-lookup"><span data-stu-id="f4ce6-165">Types Defining CType</span></span>  
 <span data-ttu-id="f4ce6-166">Można zdefiniować `CType` dla klasy lub struktury, które zostały zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-166">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="f4ce6-167">Dzięki temu można przekonwertować wartości do i z typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-167">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="f4ce6-168">Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [jak: Definiowanie operatora konwersji](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f4ce6-168">For more information and an example, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4ce6-169">Wartości używane ze słowem kluczowym konwersji muszą być prawidłowe dla docelowego typu danych lub wystąpienia błędu.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-169">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="f4ce6-170">Na przykład, jeśli użytkownik spróbuje przekonwertować `Long` do `Integer`, wartość `Long` należy do prawidłowego zakresu dla `Integer` typu danych.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-170">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f4ce6-171">Określanie `CType` umożliwia przekonwertowanie z jedną klasę do innego kończy się niepowodzeniem w czasie wykonywania, jeśli typ źródłowy nie pochodzi od typu miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-171">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="f4ce6-172">Taka awaria zgłasza <xref:System.InvalidCastException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-172">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="f4ce6-173">Jednak jeśli jeden z typów struktury lub klasy, które zostały zdefiniowane i zdefiniowaniu `CType` dla tej struktury lub klasy, konwersja może powieść, jeśli spełnia on wymagania Twojej `CType`.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-173">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="f4ce6-174">Zobacz [jak: Definiowanie operatora konwersji](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f4ce6-174">See [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
 <span data-ttu-id="f4ce6-175">Wykonywania konwersji jawnej jest także znana jako *rzutowania* wyrażenia klasy danych danego typu lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-175">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4ce6-176">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4ce6-176">See also</span></span>

- [<span data-ttu-id="f4ce6-177">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f4ce6-177">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="f4ce6-178">Konwertowanie między ciągami a innymi typami danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-178">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="f4ce6-179">Instrukcje: Konwertowanie obiektu na inny typ w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f4ce6-179">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="f4ce6-180">Struktury</span><span class="sxs-lookup"><span data-stu-id="f4ce6-180">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="f4ce6-181">Typy danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-181">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="f4ce6-182">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="f4ce6-182">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="f4ce6-183">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="f4ce6-183">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
