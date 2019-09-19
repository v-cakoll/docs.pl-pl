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
ms.openlocfilehash: 85fd0c04a40b9de64979e4da1459dbf8953a93bf
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053881"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="3a253-102">Typy wbudowane dla wspólnych elementów podstawowych języka XAML</span><span class="sxs-lookup"><span data-stu-id="3a253-102">Built-in Types for Common XAML Language Primitives</span></span>
<span data-ttu-id="3a253-103">XAML 2009 wprowadza obsługę poziomu języka XAML dla kilku typów danych, które są często używane jako elementy pierwotne w środowisku uruchomieniowym języka wspólnego (CLR) i w innych językach programowania.</span><span class="sxs-lookup"><span data-stu-id="3a253-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="3a253-104">KOD XAML 2009 dodaje obsługę tych elementów podstawowych: `x:Object`, `x:Boolean`, `x:Char` `x:Single` `x:Double` ,,`x:Int16`,, ,,`x:Int32`,, ,`x:TimeSpan` `x:Int64` `x:String` `x:Decimal` `x:Uri`, i`x:Byte``x:Array`</span><span class="sxs-lookup"><span data-stu-id="3a253-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="3a253-105">Poprzednie techniki dla elementów podstawowych języka w znacznikach XAML</span><span class="sxs-lookup"><span data-stu-id="3a253-105">Previous Techniques for Language Primitives in XAML Markup</span></span>  
 <span data-ttu-id="3a253-106">W języku XAML dla wcześniejszych wersji WPF można przywołać elementy podstawowe języka CLR, mapując zestaw i przestrzeń nazw, które zawierały klasę definicji pierwotnej CLR dla .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3a253-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="3a253-107">Większość z nich znajduje się w zestawie mscorlib i <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3a253-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="3a253-108">Na przykład, aby użyć <xref:System.Int32>, można zadeklarować następujące mapowanie (z przykładowym użyciem):</span><span class="sxs-lookup"><span data-stu-id="3a253-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>  
  
```xaml  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="3a253-109">Elementy podstawowe języka XAML 2009</span><span class="sxs-lookup"><span data-stu-id="3a253-109">XAML 2009 Language Primitives</span></span>  
 <span data-ttu-id="3a253-110">Zgodnie z Konwencją, są wyświetlane elementy podstawowe języka XAML i wszystkich innych elementów języka XAML, łącznie z `x:` prefiksem.</span><span class="sxs-lookup"><span data-stu-id="3a253-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="3a253-111">Jest to sposób, w jaki elementy języka XAML są zwykle używane w oznakowaniu rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="3a253-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="3a253-112">Ta konwencja jest stosowana w dokumentacji koncepcyjnej języka XAML w WPF, a także w specyfikacji języka XAML.</span><span class="sxs-lookup"><span data-stu-id="3a253-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>  
  
### <a name="xobject"></a><span data-ttu-id="3a253-113">x:Object</span><span class="sxs-lookup"><span data-stu-id="3a253-113">x:Object</span></span>  
 <span data-ttu-id="3a253-114">W przypadku środowiska CLR `x:Object` element podstawowy odpowiada. <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="3a253-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="3a253-115">Ten element podstawowy nie jest zazwyczaj używany w znacznikach aplikacji, ale może być przydatny w niektórych scenariuszach, takich jak sprawdzanie możliwości przypisywania w systemie typów XAML.</span><span class="sxs-lookup"><span data-stu-id="3a253-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>  
  
### <a name="xboolean"></a><span data-ttu-id="3a253-116">x:Boolean</span><span class="sxs-lookup"><span data-stu-id="3a253-116">x:Boolean</span></span>  
 <span data-ttu-id="3a253-117">W przypadku środowiska CLR `x:Boolean` element podstawowy odpowiada. <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="3a253-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>  
  
 <span data-ttu-id="3a253-118">Kod XAML analizuje wartości `x:Boolean` jako nieuwzględniające wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="3a253-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="3a253-119">Należy zauważyć `x:Bool` , że nie jest zaakceptowaną alternatywą.</span><span class="sxs-lookup"><span data-stu-id="3a253-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="3a253-120">Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[sekcje MS-\] XAML 5.2.17 i 5.4.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="3a253-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xchar"></a><span data-ttu-id="3a253-121">x:Char</span><span class="sxs-lookup"><span data-stu-id="3a253-121">x:Char</span></span>  
 <span data-ttu-id="3a253-122">W przypadku środowiska CLR `x:Char` element podstawowy odpowiada. <xref:System.Char></span><span class="sxs-lookup"><span data-stu-id="3a253-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>  
  
 <span data-ttu-id="3a253-123">Typy String i char mają interakcję z ogólnym kodowaniem pliku na poziomie XML.</span><span class="sxs-lookup"><span data-stu-id="3a253-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="3a253-124">Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[sekcje MS-\] XAML 5.2.7 i 5.4.1](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="3a253-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xstring"></a><span data-ttu-id="3a253-125">x:String</span><span class="sxs-lookup"><span data-stu-id="3a253-125">x:String</span></span>  
 <span data-ttu-id="3a253-126">W przypadku środowiska CLR `x:String` element podstawowy odpowiada. <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="3a253-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>  
  
 <span data-ttu-id="3a253-127">Typy String i char mają interakcję z ogólnym kodowaniem pliku na poziomie XML.</span><span class="sxs-lookup"><span data-stu-id="3a253-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="3a253-128">Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[sekcje MS-\] XAML 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="3a253-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdecimal"></a><span data-ttu-id="3a253-129">x:Decimal</span><span class="sxs-lookup"><span data-stu-id="3a253-129">x:Decimal</span></span>  
 <span data-ttu-id="3a253-130">W przypadku środowiska CLR `x:Decimal` element podstawowy odpowiada. <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="3a253-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>  
  
 <span data-ttu-id="3a253-131">Należy zauważyć, że analiza kodu XAML jest zaimplementowana w ramach `en-US` kultury.</span><span class="sxs-lookup"><span data-stu-id="3a253-131">Note that XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="3a253-132">W `en-US` obszarze kultura prawidłowy separator składników dziesiętnych jest zawsze kropką (`.`) niezależnie od ustawień kultury środowiska programistycznego lub miejsca docelowego klienta, gdzie XAML jest ładowany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3a253-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>  
  
 <span data-ttu-id="3a253-133">Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[sekcje MS-\] XAML 5.2.14 i 5.4.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="3a253-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xsingle"></a><span data-ttu-id="3a253-134">x:Single</span><span class="sxs-lookup"><span data-stu-id="3a253-134">x:Single</span></span>  
 <span data-ttu-id="3a253-135">W przypadku środowiska CLR `x:Single` element podstawowy odpowiada. <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="3a253-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>  
  
 <span data-ttu-id="3a253-136">Oprócz wartości liczbowych, składnia tekstu `x:Single` dla również zezwala na tokeny `Infinity`, `-Infinity`i `NaN`.</span><span class="sxs-lookup"><span data-stu-id="3a253-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="3a253-137">Te tokeny są traktowane jako uwzględniające wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="3a253-137">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="3a253-138">`x:Single`może obsługiwać wartości w postaci notacji naukowej, jeśli pierwszy znak w składni tekstu `e` jest `E`lub.</span><span class="sxs-lookup"><span data-stu-id="3a253-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>  
  
 <span data-ttu-id="3a253-139">Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[sekcje MS-\] XAML 5.2.8 i 5.4.2](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="3a253-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdouble"></a><span data-ttu-id="3a253-140">x:Double</span><span class="sxs-lookup"><span data-stu-id="3a253-140">x:Double</span></span>  
 <span data-ttu-id="3a253-141">W przypadku środowiska CLR `x:Double` element podstawowy odpowiada. <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="3a253-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>  
  
 <span data-ttu-id="3a253-142">Oprócz wartości liczbowych `x:Double` , składnia tekstu dla zezwala na tokeny `Infinity`, `-Infinity`i `NaN`.</span><span class="sxs-lookup"><span data-stu-id="3a253-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="3a253-143">Te tokeny są traktowane jako uwzględniające wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="3a253-143">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="3a253-144">`x:Double`może obsługiwać wartości w postaci notacji naukowej.</span><span class="sxs-lookup"><span data-stu-id="3a253-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="3a253-145">Użyj znaku `e` lub `E` , aby wprowadzić część wykładnika.</span><span class="sxs-lookup"><span data-stu-id="3a253-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>  
  
 <span data-ttu-id="3a253-146">Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[sekcje MS-\] XAML 5.2.9 i 5.4.3](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="3a253-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint16"></a><span data-ttu-id="3a253-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="3a253-147">x:Int16</span></span>  
 <span data-ttu-id="3a253-148">W przypadku tworzenia kopii zapasowych `x:Int16` CLR element podstawowy odpowiada `x:Int16` <xref:System.Int16> i jest traktowany jako podpisany.</span><span class="sxs-lookup"><span data-stu-id="3a253-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="3a253-149">W języku XAML nieobecność znaku plus (`+`) w składni tekstu jest implikowana jako dodatnia wartość ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="3a253-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="3a253-150">Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[sekcje MS-\] XAML 5.2.11 i 5.4.5](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="3a253-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint32"></a><span data-ttu-id="3a253-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="3a253-151">x:Int32</span></span>  
 <span data-ttu-id="3a253-152">W przypadku środowiska CLR `x:Int32` element podstawowy odpowiada. <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="3a253-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="3a253-153">`x:Int32`jest traktowane jako podpisane.</span><span class="sxs-lookup"><span data-stu-id="3a253-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="3a253-154">W języku XAML nieobecność znaku plus (`+`) w składni tekstu jest implikowana jako dodatnia wartość ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="3a253-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="3a253-155">Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[sekcje MS-\] XAML 5.2.12 i 5.4.6](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="3a253-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint64"></a><span data-ttu-id="3a253-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="3a253-156">x:Int64</span></span>  
 <span data-ttu-id="3a253-157">W przypadku środowiska CLR `x:Int64` element podstawowy odpowiada. <xref:System.Int64></span><span class="sxs-lookup"><span data-stu-id="3a253-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="3a253-158">`x:Int64`jest traktowane jako podpisane.</span><span class="sxs-lookup"><span data-stu-id="3a253-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="3a253-159">W języku XAML nieobecność znaku plus (`+`) w składni tekstu jest implikowana jako dodatnia wartość ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="3a253-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="3a253-160">Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[sekcje MS-\] XAML 5.2.13 i 5.4.7](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="3a253-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xtimespan"></a><span data-ttu-id="3a253-161">x:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="3a253-161">x:TimeSpan</span></span>  
 <span data-ttu-id="3a253-162">W przypadku środowiska CLR `x:TimeSpan` element podstawowy odpowiada. <xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="3a253-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="3a253-163">Należy zauważyć, że analiza kodu XAML dla formatu daty i godziny jest zaimplementowana w ramach `en-US` kultury.</span><span class="sxs-lookup"><span data-stu-id="3a253-163">Note that XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>  
  
 <span data-ttu-id="3a253-164">Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[sekcje MS-\] XAML 5.2.16 i 5.4.10](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="3a253-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xuri"></a><span data-ttu-id="3a253-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="3a253-165">x:Uri</span></span>  
 <span data-ttu-id="3a253-166">W przypadku środowiska CLR `x:Uri` element podstawowy odpowiada. <xref:System.Uri></span><span class="sxs-lookup"><span data-stu-id="3a253-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>  
  
 <span data-ttu-id="3a253-167">Sprawdzanie protokołów nie jest częścią definicji XAML dla `x:Uri`.</span><span class="sxs-lookup"><span data-stu-id="3a253-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>  
  
 <span data-ttu-id="3a253-168">Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[sekcje MS-\] XAML 5.2.15 i 5.4.9](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="3a253-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xbyte"></a><span data-ttu-id="3a253-169">x:Byte</span><span class="sxs-lookup"><span data-stu-id="3a253-169">x:Byte</span></span>  
 <span data-ttu-id="3a253-170">W przypadku środowiska CLR `x:Byte` element podstawowy odpowiada. <xref:System.Byte></span><span class="sxs-lookup"><span data-stu-id="3a253-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="3a253-171">A <xref:System.Byte>  /  jest traktowana jakoniepodpisana.`x:Byte`</span><span class="sxs-lookup"><span data-stu-id="3a253-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>  
  
 <span data-ttu-id="3a253-172">Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[sekcje MS-\] XAML 5.2.10 i 5.4.4](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="3a253-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xarray"></a><span data-ttu-id="3a253-173">x:Array</span><span class="sxs-lookup"><span data-stu-id="3a253-173">x:Array</span></span>  
 <span data-ttu-id="3a253-174">W przypadku środowiska CLR `x:Array` element podstawowy odpowiada. <xref:System.Array></span><span class="sxs-lookup"><span data-stu-id="3a253-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>  
  
 <span data-ttu-id="3a253-175">Można zdefiniować tablicę w języku XAML 2006 przy użyciu składni rozszerzenia znaczników; Jednak składnia XAML 2009 jest zdefiniowaną przez język podstawową, która nie wymaga dostępu do rozszerzenia znacznika.</span><span class="sxs-lookup"><span data-stu-id="3a253-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="3a253-176">Aby uzyskać więcej informacji na temat obsługi języka XAML 2006, zobacz [X:Array Markup Extension](x-array-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="3a253-176">For more information about XAML 2006 support, see [x:Array Markup Extension](x-array-markup-extension.md).</span></span>  
  
 <span data-ttu-id="3a253-177">Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[sekcje MS-\] XAML 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="3a253-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a><span data-ttu-id="3a253-178">Obsługa WPF</span><span class="sxs-lookup"><span data-stu-id="3a253-178">WPF Support</span></span>  
 <span data-ttu-id="3a253-179">W programie WPF można używać funkcji języka XAML 2009, ale tylko dla języka XAML, który nie jest kompilowany do znaczników.</span><span class="sxs-lookup"><span data-stu-id="3a253-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="3a253-180">Skompilowane znaczniki XAML dla WPF i forma BAML języka XAML nie obsługują obecnie słów kluczowych i funkcji języka XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="3a253-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="3a253-181">Scenariusz, w którym można używać funkcji języka XAML 2009 razem z WPF, to jeśli utworzysz luźny kod XAML, a następnie załadujesz ten kod XAML do środowiska <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>uruchomieniowego WPF i grafu obiektów przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="3a253-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3a253-182">WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> i jego <xref:System.Windows.Markup.XamlReader.Load%2A> funkcja może przetwarzać słowa kluczowe języka XAML 2009 i funkcje do prawidłowej reprezentacji grafu obiektów.</span><span class="sxs-lookup"><span data-stu-id="3a253-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
