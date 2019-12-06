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
ms.openlocfilehash: c6af46fe2ea21d081e693ee83949651bd388a045
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837275"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="b4b89-102">Typy wbudowane dla wspólnych elementów podstawowych języka XAML</span><span class="sxs-lookup"><span data-stu-id="b4b89-102">Built-in Types for Common XAML Language Primitives</span></span>
<span data-ttu-id="b4b89-103">XAML 2009 wprowadza obsługę poziomu języka XAML dla kilku typów danych, które są często używane jako elementy pierwotne w środowisku uruchomieniowym języka wspólnego (CLR) i w innych językach programowania.</span><span class="sxs-lookup"><span data-stu-id="b4b89-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="b4b89-104">Język XAML 2009 dodaje obsługę następujących elementów podstawowych: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`i `x:Array`</span><span class="sxs-lookup"><span data-stu-id="b4b89-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="b4b89-105">Poprzednie techniki dla elementów podstawowych języka w znacznikach języka XAML</span><span class="sxs-lookup"><span data-stu-id="b4b89-105">Previous Techniques for Language Primitives in XAML Markup</span></span>  
 <span data-ttu-id="b4b89-106">W języku XAML dla wcześniejszych wersji środowiska WPF można odwoływać się do elementów podstawowych języka środowiska CLR przez mapowanie zestawu i przestrzeni nazw zawierających klasę definicji elementu podstawowego środowiska CLR dla środowiska .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b4b89-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="b4b89-107">Większość z nich znajduje się w zestawie mscorlib i obszarze nazw <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="b4b89-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="b4b89-108">Na przykład aby użyć typu <xref:System.Int32>, można zadeklarować następujące mapowanie (z przykładem w dalszej części):</span><span class="sxs-lookup"><span data-stu-id="b4b89-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>  
  
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
## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="b4b89-109">Funkcje pierwotne XAML 2009</span><span class="sxs-lookup"><span data-stu-id="b4b89-109">XAML 2009 Language Primitives</span></span>  
 <span data-ttu-id="b4b89-110">Umownie wyświetlane są pierwotne wartości języka XAML i wszystkie inne elementy języka XAML, łącznie z prefiksem `x:`.</span><span class="sxs-lookup"><span data-stu-id="b4b89-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="b4b89-111">W ten sposób elementy języka XAML są zwykle używane w znacznikach rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="b4b89-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="b4b89-112">W dokumentacji koncepcyjnej XAML w programie WPF, a także w specyfikacji języka XAML występuje niniejsza konwencja.</span><span class="sxs-lookup"><span data-stu-id="b4b89-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>  
  
### <a name="xobject"></a><span data-ttu-id="b4b89-113">x:Object</span><span class="sxs-lookup"><span data-stu-id="b4b89-113">x:Object</span></span>  
 <span data-ttu-id="b4b89-114">Dla obsługi środowiska CLR element podstawowy `x:Object` odpowiada obiektowi <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="b4b89-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="b4b89-115">Ten typ pierwotny nie jest zazwyczaj używany w zaznaczaniu aplikacji, ale może być pomocny w niektórych scenariuszach, takich jak sprawdzanie zbywalności w systemie typu XAML.</span><span class="sxs-lookup"><span data-stu-id="b4b89-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>  
  
### <a name="xboolean"></a><span data-ttu-id="b4b89-116">x:Boolean</span><span class="sxs-lookup"><span data-stu-id="b4b89-116">x:Boolean</span></span>  
 <span data-ttu-id="b4b89-117">Dla obsługi środowiska CLR element podstawowy `x:Boolean` odpowiada obiektowi <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="b4b89-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>  
  
 <span data-ttu-id="b4b89-118">XAML analizuje wartości dla `x:Boolean` bez uwzględniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="b4b89-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="b4b89-119">Należy zauważyć, że obiekt `x:Bool` nie jest alternatywą zaakceptowaną.</span><span class="sxs-lookup"><span data-stu-id="b4b89-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="b4b89-120">Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.17 i 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b4b89-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xchar"></a><span data-ttu-id="b4b89-121">x:Char</span><span class="sxs-lookup"><span data-stu-id="b4b89-121">x:Char</span></span>  
 <span data-ttu-id="b4b89-122">Dla obsługi środowiska CLR element podstawowy `x:Char` odpowiada obiektowi <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="b4b89-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>  
  
 <span data-ttu-id="b4b89-123">Typy String lub char wchodzą w interakcję z ogólnym kodowaniem pliku na poziomie XML.</span><span class="sxs-lookup"><span data-stu-id="b4b89-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="b4b89-124">Aby uzyskać definicję specyfikacji języka XAML, zobacz sekcję [\[MS-XAML\] sekcjach 5.2.7 i 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b4b89-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xstring"></a><span data-ttu-id="b4b89-125">x:String</span><span class="sxs-lookup"><span data-stu-id="b4b89-125">x:String</span></span>  
 <span data-ttu-id="b4b89-126">Dla obsługi środowiska CLR element podstawowy `x:String` odpowiada obiektowi <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4b89-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>  
  
 <span data-ttu-id="b4b89-127">Typy String lub char wchodzą w interakcję z ogólnym kodowaniem pliku na poziomie XML.</span><span class="sxs-lookup"><span data-stu-id="b4b89-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="b4b89-128">Aby uzyskać definicję specyfikacji języka XAML, zobacz sekcję [\[MS-XAML\] sekcjach 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b4b89-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xdecimal"></a><span data-ttu-id="b4b89-129">x:Decimal</span><span class="sxs-lookup"><span data-stu-id="b4b89-129">x:Decimal</span></span>  
 <span data-ttu-id="b4b89-130">Dla obsługi środowiska CLR element podstawowy `x:Decimal` odpowiada obiektowi <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="b4b89-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>  
  
 <span data-ttu-id="b4b89-131">Należy zauważyć, że analiza składni języka XAML standardowo odbywa się w kulturze `en-US`.</span><span class="sxs-lookup"><span data-stu-id="b4b89-131">Note that XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="b4b89-132">W kulturze `en-US`, poprawnym separatorem dla elementów ułamków dziesiętny jest zawsze kropka (`.`) niezależnie od ustawień kultury środowiska programowania lub obiektu docelowego ewentualnego klienta gdzie plik XAML jest ładowany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b4b89-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>  
  
 <span data-ttu-id="b4b89-133">Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.14 i 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b4b89-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xsingle"></a><span data-ttu-id="b4b89-134">x:Single</span><span class="sxs-lookup"><span data-stu-id="b4b89-134">x:Single</span></span>  
 <span data-ttu-id="b4b89-135">Dla obsługi środowiska CLR element podstawowy `x:Single` odpowiada obiektowi <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="b4b89-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>  
  
 <span data-ttu-id="b4b89-136">Oprócz wartości liczbowych składnia tekstu `x:Single` również pozwala na tokeny `Infinity`, `-Infinity` i `NaN`.</span><span class="sxs-lookup"><span data-stu-id="b4b89-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="b4b89-137">Te tokeny uwzględniają wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="b4b89-137">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="b4b89-138">`x:Single` może obsługiwać wartości w postaci notacji naukowej, jeśli pierwszy znak w składni tekstu to `e` lub `E`.</span><span class="sxs-lookup"><span data-stu-id="b4b89-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>  
  
 <span data-ttu-id="b4b89-139">Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.8 i 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b4b89-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xdouble"></a><span data-ttu-id="b4b89-140">x:Double</span><span class="sxs-lookup"><span data-stu-id="b4b89-140">x:Double</span></span>  
 <span data-ttu-id="b4b89-141">Dla obsługi środowiska CLR element podstawowy `x:Double` odpowiada obiektowi <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="b4b89-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>  
  
 <span data-ttu-id="b4b89-142">Oprócz wartości liczbowych składnia tekstu `x:Double` pozwala na tokeny `Infinity`, `-Infinity` i `NaN`.</span><span class="sxs-lookup"><span data-stu-id="b4b89-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="b4b89-143">Te tokeny uwzględniają wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="b4b89-143">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="b4b89-144">`x:Double` może obsługiwać wartości w postaci notacji naukowej.</span><span class="sxs-lookup"><span data-stu-id="b4b89-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="b4b89-145">Użyj znaku `e` lub `E` do wprowadzenia wykładnika.</span><span class="sxs-lookup"><span data-stu-id="b4b89-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>  
  
 <span data-ttu-id="b4b89-146">Aby uzyskać definicję specyfikacji języka XAML, zobacz sekcję [\[MS-XAML\] sekcjach 5.2.9 i 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b4b89-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xint16"></a><span data-ttu-id="b4b89-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="b4b89-147">x:Int16</span></span>  
 <span data-ttu-id="b4b89-148">Dla obsługi środowiska CLR element podstawowy `x:Int16` odpowiada obiektowi <xref:System.Int16> i element podstawowy `x:Int16` jest traktowany jako podpisany.</span><span class="sxs-lookup"><span data-stu-id="b4b89-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="b4b89-149">W języku XAML brak znaku plusa (`+`) w składni tekstu jest przez domniemanie interpretowany jako wartość ze znakiem dodatnim.</span><span class="sxs-lookup"><span data-stu-id="b4b89-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="b4b89-150">Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.11 i 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b4b89-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xint32"></a><span data-ttu-id="b4b89-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="b4b89-151">x:Int32</span></span>  
 <span data-ttu-id="b4b89-152">Dla obsługi środowiska CLR element podstawowy `x:Int32` odpowiada obiektowi <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="b4b89-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="b4b89-153">`x:Int32` jest traktowany jako oznaczony.</span><span class="sxs-lookup"><span data-stu-id="b4b89-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="b4b89-154">W języku XAML brak znaku plusa (`+`) w składni tekstu jest przez domniemanie interpretowany jako wartość ze znakiem dodatnim.</span><span class="sxs-lookup"><span data-stu-id="b4b89-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="b4b89-155">Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.12 i 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b4b89-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xint64"></a><span data-ttu-id="b4b89-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="b4b89-156">x:Int64</span></span>  
 <span data-ttu-id="b4b89-157">Dla obsługi środowiska CLR element podstawowy `x:Int64` odpowiada obiektowi <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b4b89-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="b4b89-158">`x:Int64` jest traktowany jako oznaczony.</span><span class="sxs-lookup"><span data-stu-id="b4b89-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="b4b89-159">W języku XAML brak znaku plusa (`+`) w składni tekstu jest przez domniemanie interpretowany jako wartość ze znakiem dodatnim.</span><span class="sxs-lookup"><span data-stu-id="b4b89-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="b4b89-160">Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.13 i 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b4b89-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xtimespan"></a><span data-ttu-id="b4b89-161">x:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="b4b89-161">x:TimeSpan</span></span>  
 <span data-ttu-id="b4b89-162">Dla obsługi środowiska CLR element podstawowy `x:TimeSpan` odpowiada obiektowi <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="b4b89-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="b4b89-163">Należy zauważyć, że analiza składni języka XAML pod kątem formatu daty i godziny standardowo odbywa się w kulturze `en-US`.</span><span class="sxs-lookup"><span data-stu-id="b4b89-163">Note that XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>  
  
 <span data-ttu-id="b4b89-164">Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.16 i 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b4b89-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xuri"></a><span data-ttu-id="b4b89-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="b4b89-165">x:Uri</span></span>  
 <span data-ttu-id="b4b89-166">Dla obsługi środowiska CLR element podstawowy `x:Uri` odpowiada obiektowi <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="b4b89-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>  
  
 <span data-ttu-id="b4b89-167">Szukanie protokołów nie jest częścią definicji XAML dla `x:Uri`.</span><span class="sxs-lookup"><span data-stu-id="b4b89-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>  
  
 <span data-ttu-id="b4b89-168">Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.15 i 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b4b89-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xbyte"></a><span data-ttu-id="b4b89-169">x:Byte</span><span class="sxs-lookup"><span data-stu-id="b4b89-169">x:Byte</span></span>  
 <span data-ttu-id="b4b89-170">Dla obsługi środowiska CLR element podstawowy `x:Byte` odpowiada obiektowi <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="b4b89-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="b4b89-171"><xref:System.Byte> / `x:Byte` jest traktowana jako niepodpisana.</span><span class="sxs-lookup"><span data-stu-id="b4b89-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>  
  
 <span data-ttu-id="b4b89-172">Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.10 i 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b4b89-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xarray"></a><span data-ttu-id="b4b89-173">x:Array</span><span class="sxs-lookup"><span data-stu-id="b4b89-173">x:Array</span></span>  
 <span data-ttu-id="b4b89-174">Dla obsługi środowiska CLR element podstawowy `x:Array` odpowiada obiektowi <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="b4b89-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>  
  
 <span data-ttu-id="b4b89-175">Można zdefiniować tablicę w języku XAML 2006 przy użyciu składni rozszerzenia znaczników; Jednak składnia XAML 2009 jest zdefiniowaną przez język podstawową, która nie wymaga dostępu do rozszerzenia znacznika.</span><span class="sxs-lookup"><span data-stu-id="b4b89-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="b4b89-176">Aby uzyskać więcej informacji na temat obsługi języka XAML 2006, zobacz [X:Array Markup Extension](x-array-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="b4b89-176">For more information about XAML 2006 support, see [x:Array Markup Extension](x-array-markup-extension.md).</span></span>  
  
 <span data-ttu-id="b4b89-177">Aby uzyskać definicję specyfikacji języka XAML, zobacz sekcję [\[MS-XAML\] sekcjach 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b4b89-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a><span data-ttu-id="b4b89-178">Obsługa WPF</span><span class="sxs-lookup"><span data-stu-id="b4b89-178">WPF Support</span></span>  
 <span data-ttu-id="b4b89-179">W programie WPF można używać funkcji języka XAML 2009, ale tylko dla języka XAML, który nie jest kompilowany do znaczników.</span><span class="sxs-lookup"><span data-stu-id="b4b89-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="b4b89-180">Skompilowane znaczniki XAML dla WPF i forma BAML języka XAML nie obsługują obecnie słów kluczowych i funkcji języka XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="b4b89-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="b4b89-181">Scenariusz, w którym można używać funkcji języka XAML 2009 razem z WPF, to jeśli utworzysz luźny kod XAML, a następnie załadujesz ten kod XAML do środowiska uruchomieniowego WPF i grafu obiektów z <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4b89-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b4b89-182"><xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> WPF i jej <xref:System.Windows.Markup.XamlReader.Load%2A> mogą przetwarzać słowa kluczowe języka XAML 2009 i funkcje do prawidłowej reprezentacji grafu obiektów.</span><span class="sxs-lookup"><span data-stu-id="b4b89-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
