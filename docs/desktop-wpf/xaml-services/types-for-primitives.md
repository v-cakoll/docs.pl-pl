---
title: Typy wbudowane dla wspólnych elementów podstawowych języka XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: 3bd486ee66c5f9a32621416638bb7575025f7dee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071837"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="83d62-102">Wbudowane typy dla wspólnych elementów pierwotnych języka XAML</span><span class="sxs-lookup"><span data-stu-id="83d62-102">Built-in types for common XAML language primitives</span></span>

<span data-ttu-id="83d62-103">XAML 2009 wprowadza obsługę języka XAML dla kilku typów danych, które są często używane prymitywy w czasie wykonywania języka wspólnego (CLR) i w innych językach programowania.</span><span class="sxs-lookup"><span data-stu-id="83d62-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="83d62-104">XAML 2009 `x:Object`dodaje obsługę tych prymitywów: `x:Single` `x:Double`, `x:Int16` `x:Boolean` `x:Int32`, `x:Int64` `x:Char` `x:TimeSpan`, `x:Uri` `x:String`, `x:Decimal`, , , , , , , , , , `x:Byte`, i`x:Array`</span><span class="sxs-lookup"><span data-stu-id="83d62-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>

## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="83d62-105">Poprzednie techniki ujednolicenia języka w znacznikach XAML</span><span class="sxs-lookup"><span data-stu-id="83d62-105">Previous Techniques for Language Primitives in XAML Markup</span></span>

 <span data-ttu-id="83d62-106">W XAML dla poprzednich wersji WPF można odwoływać się do ćwierczy języka CLR mapując zestawu i przestrzeni nazw, które zawierały klasę definicji pierwotnej CLR dla programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="83d62-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="83d62-107">Większość z nich znajduje się w <xref:System> mscorlib zestawu i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="83d62-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="83d62-108">Na przykład, <xref:System.Int32>aby użyć , można zadeklarować następujące mapowanie (z przykładowym użyciem pokazanym później):</span><span class="sxs-lookup"><span data-stu-id="83d62-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>

```xaml
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Application.Resources>
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>
  </Application.Resources>
</Application>
```

## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="83d62-109">Podstawowe wersje językowe XAML 2009</span><span class="sxs-lookup"><span data-stu-id="83d62-109">XAML 2009 Language Primitives</span></span>

<span data-ttu-id="83d62-110">Zgodnie z konwencją są wyświetlane prymitywy języka dla języka XAML `x:` i wszystkie inne elementy języka XAML, w tym prefiks.</span><span class="sxs-lookup"><span data-stu-id="83d62-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="83d62-111">W ten sposób elementy języka XAML są zwykle używane w rzeczywistych znaczników.</span><span class="sxs-lookup"><span data-stu-id="83d62-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="83d62-112">Ta konwencja jest stosowana w dokumentacji koncepcyjnej dla XAML w WPF, a także w specyfikacji XAML.</span><span class="sxs-lookup"><span data-stu-id="83d62-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>

### <a name="xobject"></a><span data-ttu-id="83d62-113">x:Obiekt</span><span class="sxs-lookup"><span data-stu-id="83d62-113">x:Object</span></span>

<span data-ttu-id="83d62-114">W przypadku podkładu `x:Object` CLR prymityw odpowiada <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="83d62-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>

<span data-ttu-id="83d62-115">Ten pierwotny nie jest zwykle używany w znacznikach aplikacji, ale może być przydatne w niektórych scenariuszach, takich jak sprawdzanie możliwości przypisania w systemie typu XAML.</span><span class="sxs-lookup"><span data-stu-id="83d62-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>

### <a name="xboolean"></a><span data-ttu-id="83d62-116">x:Wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="83d62-116">x:Boolean</span></span>

<span data-ttu-id="83d62-117">W przypadku podkładu `x:Boolean` CLR prymityw odpowiada <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="83d62-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>

<span data-ttu-id="83d62-118">XAML analizuje wartości `x:Boolean` jako bez uwzględniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="83d62-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="83d62-119">Należy `x:Bool` pamiętać, że nie jest akceptowaną alternatywą.</span><span class="sxs-lookup"><span data-stu-id="83d62-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="83d62-120">Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje MS-XAML\] 5.2.17 i 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="83d62-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xchar"></a><span data-ttu-id="83d62-121">x:Znak</span><span class="sxs-lookup"><span data-stu-id="83d62-121">x:Char</span></span>

<span data-ttu-id="83d62-122">W przypadku podkładu `x:Char` CLR prymityw odpowiada <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="83d62-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>

<span data-ttu-id="83d62-123">Typy ciągów i znaków mają interakcję z ogólnym kodowaniem pliku na poziomie XML.</span><span class="sxs-lookup"><span data-stu-id="83d62-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="83d62-124">Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje MS-XAML\] 5.2.7 i 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="83d62-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xstring"></a><span data-ttu-id="83d62-125">x:Ciąg znaków</span><span class="sxs-lookup"><span data-stu-id="83d62-125">x:String</span></span>

<span data-ttu-id="83d62-126">W przypadku podkładu `x:String` CLR prymityw odpowiada <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="83d62-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>

<span data-ttu-id="83d62-127">Typy ciągów i znaków mają interakcję z ogólnym kodowaniem pliku na poziomie XML.</span><span class="sxs-lookup"><span data-stu-id="83d62-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="83d62-128">Definicja specyfikacji języka XAML umożliwia [ \[opisanie sekcji\] MS-XAML 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="83d62-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xdecimal"></a><span data-ttu-id="83d62-129">x:Dziesiętne</span><span class="sxs-lookup"><span data-stu-id="83d62-129">x:Decimal</span></span>

<span data-ttu-id="83d62-130">W przypadku podkładu `x:Decimal` CLR prymityw odpowiada <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="83d62-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>

<span data-ttu-id="83d62-131">Analizowanie XAML jest z `en-US` natury wykonywane w ramach kultury.</span><span class="sxs-lookup"><span data-stu-id="83d62-131">XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="83d62-132">W `en-US` obszarze kultura poprawny separator dla składników dziesiętnych`.`jest zawsze kropka ( ) niezależnie od ustawień kultury środowiska deweloperskiego lub ostatecznego celu klienta, w którym XAML jest ładowany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="83d62-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>

<span data-ttu-id="83d62-133">Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje\] MS-XAML 5.2.14 i 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="83d62-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xsingle"></a><span data-ttu-id="83d62-134">x:Pojedynczy</span><span class="sxs-lookup"><span data-stu-id="83d62-134">x:Single</span></span>

<span data-ttu-id="83d62-135">W przypadku podkładu `x:Single` CLR prymityw odpowiada <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="83d62-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>

<span data-ttu-id="83d62-136">Oprócz wartości liczbowych składnia tekstu zezwala `x:Single` również na `Infinity`tokeny `-Infinity` `NaN`, i .</span><span class="sxs-lookup"><span data-stu-id="83d62-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="83d62-137">Te tokeny są traktowane jako rozróżniane wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="83d62-137">These tokens are treated as case sensitive.</span></span>

<span data-ttu-id="83d62-138">`x:Single`może obsługiwać wartości w formie notacji naukowej, jeśli `e` `E`pierwszy znak w składni tekstu jest lub .</span><span class="sxs-lookup"><span data-stu-id="83d62-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>

<span data-ttu-id="83d62-139">Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje MS-XAML\] 5.2.8 i 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="83d62-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xdouble"></a><span data-ttu-id="83d62-140">x:Podwójne</span><span class="sxs-lookup"><span data-stu-id="83d62-140">x:Double</span></span>

<span data-ttu-id="83d62-141">W przypadku podkładu `x:Double` CLR prymityw odpowiada <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="83d62-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>

<span data-ttu-id="83d62-142">Oprócz wartości liczbowych składnia tekstu zezwala `x:Double` na `Infinity`tokeny `-Infinity`, `NaN`i .</span><span class="sxs-lookup"><span data-stu-id="83d62-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="83d62-143">Te tokeny są traktowane jako rozróżniane wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="83d62-143">These tokens are treated as case sensitive.</span></span>

<span data-ttu-id="83d62-144">`x:Double`może obsługiwać wartości w formie notacji naukowej.</span><span class="sxs-lookup"><span data-stu-id="83d62-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="83d62-145">Użyj znaku `e` `E` lub wprowadzić część wykładniczą.</span><span class="sxs-lookup"><span data-stu-id="83d62-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>

<span data-ttu-id="83d62-146">Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje MS-XAML\] 5.2.9 i 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="83d62-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint16"></a><span data-ttu-id="83d62-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="83d62-147">x:Int16</span></span>

<span data-ttu-id="83d62-148">W przypadku kopii `x:Int16` CLR wartość pierwotna odpowiada <xref:System.Int16> i `x:Int16` jest traktowana jako podpisana.</span><span class="sxs-lookup"><span data-stu-id="83d62-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="83d62-149">W języku XAML brak składni tekstu plus (`+`) jest implikowany jako wartość podpisana dodatnia.</span><span class="sxs-lookup"><span data-stu-id="83d62-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="83d62-150">Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje\] MS-XAML 5.2.11 i 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="83d62-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint32"></a><span data-ttu-id="83d62-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="83d62-151">x:Int32</span></span>

<span data-ttu-id="83d62-152">W przypadku podkładu `x:Int32` CLR prymityw odpowiada <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="83d62-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="83d62-153">`x:Int32`traktowane jako podpisane.</span><span class="sxs-lookup"><span data-stu-id="83d62-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="83d62-154">W języku XAML brak składni tekstu plus (`+`) jest implikowany jako wartość podpisana dodatnia.</span><span class="sxs-lookup"><span data-stu-id="83d62-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="83d62-155">Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje\] MS-XAML 5.2.12 i 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="83d62-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint64"></a><span data-ttu-id="83d62-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="83d62-156">x:Int64</span></span>

<span data-ttu-id="83d62-157">W przypadku podkładu `x:Int64` CLR prymityw odpowiada <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="83d62-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="83d62-158">`x:Int64`traktowane jako podpisane.</span><span class="sxs-lookup"><span data-stu-id="83d62-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="83d62-159">W języku XAML brak składni tekstu plus (`+`) jest implikowany jako wartość podpisana dodatnia.</span><span class="sxs-lookup"><span data-stu-id="83d62-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="83d62-160">Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje\] MS-XAML 5.2.13 i 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="83d62-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xtimespan"></a><span data-ttu-id="83d62-161">x:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="83d62-161">x:TimeSpan</span></span>

<span data-ttu-id="83d62-162">W przypadku podkładu `x:TimeSpan` CLR prymityw odpowiada <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="83d62-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>

<span data-ttu-id="83d62-163">Analizowanie XAML dla formatu daty czasu `en-US` jest z natury wykonywane w ramach kultury.</span><span class="sxs-lookup"><span data-stu-id="83d62-163">XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>

<span data-ttu-id="83d62-164">Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje MS-XAML\] 5.2.16 i 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="83d62-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xuri"></a><span data-ttu-id="83d62-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="83d62-165">x:Uri</span></span>

<span data-ttu-id="83d62-166">W przypadku podkładu `x:Uri` CLR prymityw odpowiada <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="83d62-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>

<span data-ttu-id="83d62-167">Sprawdzanie protokołów nie jest częścią definicji XAML dla `x:Uri`.</span><span class="sxs-lookup"><span data-stu-id="83d62-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>

<span data-ttu-id="83d62-168">Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje\] MS-XAML 5.2.15 i 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="83d62-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xbyte"></a><span data-ttu-id="83d62-169">x:Bajt</span><span class="sxs-lookup"><span data-stu-id="83d62-169">x:Byte</span></span>

<span data-ttu-id="83d62-170">W przypadku podkładu `x:Byte` CLR prymityw odpowiada <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="83d62-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="83d62-171"><xref:System.Byte>  /  A `x:Byte` jest traktowany jako niepodpisany.</span><span class="sxs-lookup"><span data-stu-id="83d62-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>

<span data-ttu-id="83d62-172">Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje\] MS-XAML 5.2.10 i 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="83d62-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xarray"></a><span data-ttu-id="83d62-173">x:Tablica</span><span class="sxs-lookup"><span data-stu-id="83d62-173">x:Array</span></span>

<span data-ttu-id="83d62-174">W przypadku podkładu `x:Array` CLR prymityw odpowiada <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="83d62-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>

<span data-ttu-id="83d62-175">Tablicę można zdefiniować w języku XAML 2006 przy użyciu składni rozszerzenia znaczników; jednak składnia XAML 2009 jest pierwotnym językiem zdefiniowanym przez język, który nie wymaga uzyskiwania dostępu do rozszerzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="83d62-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="83d62-176">Aby uzyskać więcej informacji na temat obsługi protokołu XAML 2006, zobacz [x:Array Markup Extension](xarray-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="83d62-176">For more information about XAML 2006 support, see [x:Array Markup Extension](xarray-markup-extension.md).</span></span>

<span data-ttu-id="83d62-177">Definicja specyfikacji języka XAML umożliwia [ \[opisanie rozdziałów\] 5.2.18 dotyczących języka MS-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="83d62-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="wpf-support"></a><span data-ttu-id="83d62-178">Obsługa WPF</span><span class="sxs-lookup"><span data-stu-id="83d62-178">WPF Support</span></span>

<span data-ttu-id="83d62-179">W WPF WPF można użyć XAML 2009 funkcje, ale tylko dla XAML, który nie jest skompilowany znaczników.</span><span class="sxs-lookup"><span data-stu-id="83d62-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="83d62-180">Markup-skompilowany XAML dla WPF i BAML formie XAML obecnie nie obsługują XAML 2009 słów kluczowych i funkcji.</span><span class="sxs-lookup"><span data-stu-id="83d62-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

<span data-ttu-id="83d62-181">Scenariusz, w którym można użyć funkcji XAML 2009 wraz z WPF jest, jeśli autor luźne XAML, a <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>następnie załadować ten kod XAML do środowiska uruchomieniowego WPF i wykres obiektu z .</span><span class="sxs-lookup"><span data-stu-id="83d62-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="83d62-182">WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> WPF <xref:System.Windows.Markup.XamlReader.Load%2A> i jego można przetwarzać XAML 2009 słowa kluczowe języka i funkcje w prawidłowej reprezentacji wykresu obiektu.</span><span class="sxs-lookup"><span data-stu-id="83d62-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
