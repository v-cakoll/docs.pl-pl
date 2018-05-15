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
ms.openlocfilehash: 15c359a9a7f9797fc03ce20c453905af01f925d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="2fdbf-102">Typy wbudowane dla wspólnych elementów podstawowych języka XAML</span><span class="sxs-lookup"><span data-stu-id="2fdbf-102">Built-in Types for Common XAML Language Primitives</span></span>
<span data-ttu-id="2fdbf-103">XAML 2009 wprowadzono obsługę poziom języka XAML dla kilku typów danych, które są często używanych elementów podstawowych, środowisko uruchomieniowe języka wspólnego (CLR) i w innych językach programowania.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="2fdbf-104">XAML 2009 dodaje obsługę tych podstawowych: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, i `x:Array`</span><span class="sxs-lookup"><span data-stu-id="2fdbf-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="2fdbf-105">Poprzednie techniki elementów podstawowych języka w kodzie XAML</span><span class="sxs-lookup"><span data-stu-id="2fdbf-105">Previous Techniques for Language Primitives in XAML Markup</span></span>  
 <span data-ttu-id="2fdbf-106">W języku XAML w poprzednich wersjach WPF mapowanie zestawu i przestrzeni nazw, która zawiera klasę pierwotnych definicji CLR dla programu .NET Framework może odwoływać się do elementów podstawowych języka CLR.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="2fdbf-107">Większość tych znajdują się w zestawie mscorlib i <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="2fdbf-108">Na przykład, aby użyć <xref:System.Int32>, można deklaruje następującego mapowania (z użycia przykładzie pokazano później):</span><span class="sxs-lookup"><span data-stu-id="2fdbf-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>  
  
```  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="2fdbf-109">Elementy podstawowe języka XAML 2009 języka</span><span class="sxs-lookup"><span data-stu-id="2fdbf-109">XAML 2009 Language Primitives</span></span>  
 <span data-ttu-id="2fdbf-110">Konwencja, są wyświetlane elementów podstawowych języka XAML i wszystkie inne elementy języka XAML, łącznie z `x:` prefiks.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="2fdbf-111">Jest to, jak elementy języka XAML są zazwyczaj używane w znaczniku rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="2fdbf-112">Konwencja jest zachowana w dokumentacja koncepcyjna dla XAML w WPF, a także w specyfikacji języka XAML.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>  
  
### <a name="xobject"></a><span data-ttu-id="2fdbf-113">x: obiekt</span><span class="sxs-lookup"><span data-stu-id="2fdbf-113">x:Object</span></span>  
 <span data-ttu-id="2fdbf-114">Dla zapasowy CLR `x:Object` pierwotnych odpowiada <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="2fdbf-115">Ten element podstawowy nie jest zazwyczaj używana w znaczniku aplikacji, ale może być przydatne w przypadku niektórych scenariuszy, takich jak sprawdzanie assignability w systemie typów języka XAML.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>  
  
### <a name="xboolean"></a><span data-ttu-id="2fdbf-116">x: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="2fdbf-116">x:Boolean</span></span>  
 <span data-ttu-id="2fdbf-117">Dla zapasowy CLR `x:Boolean` pierwotnych odpowiada <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>  
  
 <span data-ttu-id="2fdbf-118">XAML analizuje wartości `x:Boolean` jako bez uwzględniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="2fdbf-119">Należy pamiętać, że `x:Bool` nie jest akceptowane zamiast.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="2fdbf-120">Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje 5.2.17 i 5.4.11](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="2fdbf-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xchar"></a><span data-ttu-id="2fdbf-121">x: Char</span><span class="sxs-lookup"><span data-stu-id="2fdbf-121">x:Char</span></span>  
 <span data-ttu-id="2fdbf-122">Dla zapasowy CLR `x:Char` pierwotnych odpowiada <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>  
  
 <span data-ttu-id="2fdbf-123">Typy String lub char mieć interakcji z ogólną kodowanie plików na tym poziomie XML.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="2fdbf-124">Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje ppkt 5.2.7 i 5.4.1](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="2fdbf-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xstring"></a><span data-ttu-id="2fdbf-125">x: String</span><span class="sxs-lookup"><span data-stu-id="2fdbf-125">x:String</span></span>  
 <span data-ttu-id="2fdbf-126">Dla zapasowy CLR `x:String` pierwotnych odpowiada <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>  
  
 <span data-ttu-id="2fdbf-127">Typy String lub char mieć interakcji z ogólną kodowanie plików na tym poziomie XML.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="2fdbf-128">Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje 5.2.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="2fdbf-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdecimal"></a><span data-ttu-id="2fdbf-129">x: dziesiętne</span><span class="sxs-lookup"><span data-stu-id="2fdbf-129">x:Decimal</span></span>  
 <span data-ttu-id="2fdbf-130">Dla zapasowy CLR `x:Decimal` pierwotnych odpowiada <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>  
  
 <span data-ttu-id="2fdbf-131">Należy pamiętać, że analiza kodu XAML z założenia odbywa się w obszarze `en-US` kultury.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-131">Note that XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="2fdbf-132">W obszarze `en-US` kultury, poprawnego separatora dla składników wartości dziesiętnej jest zawsze kropka (`.`) niezależnie od kultury ustawień środowiska deweloperskiego lub docelowego ostatecznego klienta załadunku XAML w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>  
  
 <span data-ttu-id="2fdbf-133">Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje 5.2.14 i 5.4.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="2fdbf-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xsingle"></a><span data-ttu-id="2fdbf-134">x: Single</span><span class="sxs-lookup"><span data-stu-id="2fdbf-134">x:Single</span></span>  
 <span data-ttu-id="2fdbf-135">Dla zapasowy CLR `x:Single` pierwotnych odpowiada <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>  
  
 <span data-ttu-id="2fdbf-136">Oprócz wartości liczbowych składnię tekst `x:Single` umożliwia również tokeny `Infinity`, `-Infinity`, i `NaN`.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="2fdbf-137">Tokeny te są traktowane jako wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-137">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="2fdbf-138">`x:Single` Możliwe wartości w formie wykładniczej jest pierwszy znak w składni tekstu `e` lub `E`.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>  
  
 <span data-ttu-id="2fdbf-139">Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje 5.2.8 i 5.4.2](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="2fdbf-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdouble"></a><span data-ttu-id="2fdbf-140">x: Double</span><span class="sxs-lookup"><span data-stu-id="2fdbf-140">x:Double</span></span>  
 <span data-ttu-id="2fdbf-141">Dla zapasowy CLR `x:Double` pierwotnych odpowiada <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>  
  
 <span data-ttu-id="2fdbf-142">Oprócz wartości liczbowych składnię tekst `x:Double` pozwala na tokeny `Infinity`, `-Infinity`, i `NaN`.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="2fdbf-143">Tokeny te są traktowane jako wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-143">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="2fdbf-144">`x:Double` Możliwe wartości w formie wykładniczej.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="2fdbf-145">Użyć znaku `e` lub `E` wprowadzenie wykładnika części.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>  
  
 <span data-ttu-id="2fdbf-146">Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje 5.2.9 i 5.4.3](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="2fdbf-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint16"></a><span data-ttu-id="2fdbf-147">x: Int16.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-147">x:Int16</span></span>  
 <span data-ttu-id="2fdbf-148">Dla zapasowy CLR `x:Int16` pierwotnych odpowiada <xref:System.Int16> i `x:Int16` jest traktowany jako podpisany.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="2fdbf-149">W języku XAML, Brak znaku plus (`+`) logowania w składni tekst jest domniemane jako dodatnią podpisem.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="2fdbf-150">Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje 5.2.11 i 5.4.5](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="2fdbf-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint32"></a><span data-ttu-id="2fdbf-151">x: Int32</span><span class="sxs-lookup"><span data-stu-id="2fdbf-151">x:Int32</span></span>  
 <span data-ttu-id="2fdbf-152">Dla zapasowy CLR `x:Int32` pierwotnych odpowiada <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="2fdbf-153">`x:Int32` jest traktowany jako podpisany.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="2fdbf-154">W języku XAML, Brak znaku plus (`+`) logowania w składni tekst jest domniemane jako dodatnią podpisem.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="2fdbf-155">Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje ppkt 5.2.12 i 5.4.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="2fdbf-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint64"></a><span data-ttu-id="2fdbf-156">x: Int64.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-156">x:Int64</span></span>  
 <span data-ttu-id="2fdbf-157">Dla zapasowy CLR `x:Int64` pierwotnych odpowiada <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="2fdbf-158">`x:Int64` jest traktowany jako podpisany.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="2fdbf-159">W języku XAML, Brak znaku plus (`+`) logowania w składni tekst jest domniemane jako dodatnią podpisem.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="2fdbf-160">Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje ppkt 5.2.13 i 5.4.7](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="2fdbf-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xtimespan"></a><span data-ttu-id="2fdbf-161">x: TimeSpan</span><span class="sxs-lookup"><span data-stu-id="2fdbf-161">x:TimeSpan</span></span>  
 <span data-ttu-id="2fdbf-162">Dla zapasowy CLR `x:TimeSpan` pierwotnych odpowiada <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="2fdbf-163">Pamiętaj, że analiza kodu XAML na format godziny i daty z założenia odbywa się w obszarze `en-US` kultury.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-163">Note that XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>  
  
 <span data-ttu-id="2fdbf-164">Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje ppkt 5.2.16 i 5.4.10](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="2fdbf-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xuri"></a><span data-ttu-id="2fdbf-165">x: Uri</span><span class="sxs-lookup"><span data-stu-id="2fdbf-165">x:Uri</span></span>  
 <span data-ttu-id="2fdbf-166">Dla zapasowy CLR `x:Uri` pierwotnych odpowiada <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>  
  
 <span data-ttu-id="2fdbf-167">Sprawdzanie protokołów nie jest częścią definicji XAML `x:Uri`.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>  
  
 <span data-ttu-id="2fdbf-168">Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje ppkt 5.2.15 i 5.4.9](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="2fdbf-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xbyte"></a><span data-ttu-id="2fdbf-169">x: Byte</span><span class="sxs-lookup"><span data-stu-id="2fdbf-169">x:Byte</span></span>  
 <span data-ttu-id="2fdbf-170">Dla zapasowy CLR `x:Byte` pierwotnych odpowiada <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="2fdbf-171">A <xref:System.Byte>  /  `x:Byte` jest traktowany jako bez znaku.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>  
  
 <span data-ttu-id="2fdbf-172">Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje 5.2.10 i 5.4.4](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="2fdbf-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xarray"></a><span data-ttu-id="2fdbf-173">x: Array</span><span class="sxs-lookup"><span data-stu-id="2fdbf-173">x:Array</span></span>  
 <span data-ttu-id="2fdbf-174">Dla zapasowy CLR `x:Array` pierwotnych odpowiada <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>  
  
 <span data-ttu-id="2fdbf-175">Można zdefiniować tablicy w języku XAML 2006 przy użyciu składni rozszerzenia znaczników; jednak składni języka XAML 2009 jest zdefiniowany w języku podstawowy, który nie wymaga dostępu do rozszerzenia znacznika.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="2fdbf-176">Aby uzyskać więcej informacji na temat obsługi XAML 2006, zobacz [x: Array — rozszerzenie znaczników](../../../docs/framework/xaml-services/x-array-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="2fdbf-176">For more information about XAML 2006 support, see [x:Array Markup Extension](../../../docs/framework/xaml-services/x-array-markup-extension.md).</span></span>  
  
 <span data-ttu-id="2fdbf-177">Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje 5.2.18](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="2fdbf-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a><span data-ttu-id="2fdbf-178">Obsługa WPF</span><span class="sxs-lookup"><span data-stu-id="2fdbf-178">WPF Support</span></span>  
 <span data-ttu-id="2fdbf-179">W WPF można użyć XAML 2009 — funkcje, ale tylko dla języka XAML, który nie jest kompilowany do znaczników.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="2fdbf-180">Skompilowany kod znaczników XAML w WPF i BAML formę XAML aktualnie nie obsługują słowa kluczowe języka XAML 2009 i funkcje.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="2fdbf-181">Scenariusz, w których można użyć XAML 2009 — funkcje wraz z WPF jest Jeśli autora utracić XAML, a następnie załadować tego XAML w WPF wykres środowiska uruchomieniowego i obiektu o <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2fdbf-182">WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> i jego <xref:System.Windows.Markup.XamlReader.Load%2A> może przetwarzać słów kluczowych języka XAML 2009 i funkcje w reprezentację Graf prawidłowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="2fdbf-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
