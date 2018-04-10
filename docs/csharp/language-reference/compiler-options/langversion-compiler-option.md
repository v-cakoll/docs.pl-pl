---
title: -langversion (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
caps.latest.revision: 33
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f1088221a96d0176f08b4c01044e20ab6238fc13
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="-langversion-c-compiler-options"></a><span data-ttu-id="ed5ff-102">-langversion (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="ed5ff-102">-langversion (C# Compiler Options)</span></span>
<span data-ttu-id="ed5ff-103">Powoduje, że kompilator, aby zaakceptować tylko składni, który znajduje się w wybranym specyfikacja języka C#.</span><span class="sxs-lookup"><span data-stu-id="ed5ff-103">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed5ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed5ff-104">Syntax</span></span>  
  
```console  
-langversion:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="ed5ff-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ed5ff-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="ed5ff-106">Prawidłowe są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="ed5ff-106">The following values are valid:</span></span>  
  
|<span data-ttu-id="ed5ff-107">Opcja</span><span class="sxs-lookup"><span data-stu-id="ed5ff-107">Option</span></span>|<span data-ttu-id="ed5ff-108">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="ed5ff-108">Meaning</span></span>|  
|------------|-------------|  
|<span data-ttu-id="ed5ff-109">default</span><span class="sxs-lookup"><span data-stu-id="ed5ff-109">default</span></span>|<span data-ttu-id="ed5ff-110">Kompilator akceptuje wszystkie składni języka prawidłowe z najnowszej wersji głównych, który może obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="ed5ff-110">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span> <span data-ttu-id="ed5ff-111"><sup id="TDefault">[Domyślne](#FDefault)</sup></span><span class="sxs-lookup"><span data-stu-id="ed5ff-111"><sup id="TDefault">[Default](#FDefault)</sup></span></span>| 
|<span data-ttu-id="ed5ff-112">ISO-1</span><span class="sxs-lookup"><span data-stu-id="ed5ff-112">ISO-1</span></span>|<span data-ttu-id="ed5ff-113">Kompilator akceptuje tylko składni, który znajduje się w 23270:2003 ISO/IEC C# (1.0/1.1) <sup id="TISO1"> [ISO1](#FISO1)</sup></span><span class="sxs-lookup"><span data-stu-id="ed5ff-113">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.1) <sup id="TISO1">[ISO1](#FISO1)</sup></span></span>|  
|<span data-ttu-id="ed5ff-114">ISO-2</span><span class="sxs-lookup"><span data-stu-id="ed5ff-114">ISO-2</span></span>|<span data-ttu-id="ed5ff-115">Kompilator akceptuje tylko składni, który znajduje się w 23270:2006 ISO/IEC C# (2.0) <sup id="TISO2"> [ISO2](#FISO2)</sup></span><span class="sxs-lookup"><span data-stu-id="ed5ff-115">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0) <sup id="TISO2">[ISO2](#FISO2)</sup></span></span>|
|<span data-ttu-id="ed5ff-116">3</span><span class="sxs-lookup"><span data-stu-id="ed5ff-116">3</span></span>|<span data-ttu-id="ed5ff-117">Kompilator akceptuje tylko składnię, która jest dostępna w C# 3.0 lub niższy <sup id="TCS3"> [CS3](#FCS3)</sup></span><span class="sxs-lookup"><span data-stu-id="ed5ff-117">The compiler accepts only syntax that is included in C# 3.0 or lower <sup id="TCS3">[CS3](#FCS3)</sup></span></span>|
|<span data-ttu-id="ed5ff-118">4</span><span class="sxs-lookup"><span data-stu-id="ed5ff-118">4</span></span>|<span data-ttu-id="ed5ff-119">Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 4.0 lub niższy <sup id="TCS4"> [CS4](#FCS4)</sup></span><span class="sxs-lookup"><span data-stu-id="ed5ff-119">The compiler accepts only syntax that is included in C# 4.0 or lower <sup id="TCS4">[CS4](#FCS4)</sup></span></span>|
|<span data-ttu-id="ed5ff-120">5</span><span class="sxs-lookup"><span data-stu-id="ed5ff-120">5</span></span>|<span data-ttu-id="ed5ff-121">Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 5.0 lub niższy <sup id="TCS5"> [CS5](#FCS5)</sup></span><span class="sxs-lookup"><span data-stu-id="ed5ff-121">The compiler accepts only syntax that is included in C# 5.0 or lower <sup id="TCS5">[CS5](#FCS5)</sup></span></span>|
|<span data-ttu-id="ed5ff-122">6</span><span class="sxs-lookup"><span data-stu-id="ed5ff-122">6</span></span>|<span data-ttu-id="ed5ff-123">Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 6.0 lub niższy <sup id="TCS6"> [CS6](#FCS6)</sup></span><span class="sxs-lookup"><span data-stu-id="ed5ff-123">The compiler accepts only syntax that is included in C# 6.0 or lower <sup id="TCS6">[CS6](#FCS6)</sup></span></span>|
|<span data-ttu-id="ed5ff-124">7</span><span class="sxs-lookup"><span data-stu-id="ed5ff-124">7</span></span>|<span data-ttu-id="ed5ff-125">Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 7.0 lub niższy <sup id="TCS7"> [CS7](#FCS7)</sup></span><span class="sxs-lookup"><span data-stu-id="ed5ff-125">The compiler accepts only syntax that is included in C# 7.0 or lower <sup id="TCS7">[CS7](#FCS7)</sup></span></span>|
|<span data-ttu-id="ed5ff-126">najnowsze</span><span class="sxs-lookup"><span data-stu-id="ed5ff-126">latest</span></span>|<span data-ttu-id="ed5ff-127">Kompilator akceptuje wszystkie składni odpowiedni język, który może obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="ed5ff-127">The compiler accepts all valid language syntax that it can support.</span></span> <span data-ttu-id="ed5ff-128"><sup id="TLatest">[Latest](#FLatest)</sup></span><span class="sxs-lookup"><span data-stu-id="ed5ff-128"><sup id="TLatest">[Latest](#FLatest)</sup></span></span>|
<!--- Uncomment and move these above
|latest| once they're officially released
|7.1|The compiler accepts only syntax that is included in C# 7.1 or lower <sup id="TCS71">[CS71](#FCS71)</sup>|
|7.2|The compiler accepts only syntax that is included in C# 7.2 or lower <sup id="TCS71">[CS72](#FCS72)</sup>|
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS71">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a><span data-ttu-id="ed5ff-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed5ff-129">Remarks</span></span>  
 <span data-ttu-id="ed5ff-130">Metadane odwołuje się aplikacji C# nie jest warunkiem **- langversion** — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ed5ff-130">Metadata referenced by your C# application is not subject to **-langversion** compiler option.</span></span>  
  
 <span data-ttu-id="ed5ff-131">Ponieważ każdy wersji kompilatora C# zawiera rozszerzenia w specyfikacji języka **- langversion** nie daje równoważne funkcje wcześniejszej wersji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ed5ff-131">Because each version of the C# compiler contains extensions to the language specification, **-langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>  
 
 <span data-ttu-id="ed5ff-132">Ponadto podczas aktualizacji wersji języka C# zazwyczaj pokrywa się z głównych .net Framework w wersji, nowej składni i funkcje nie są zawsze związane z danej wersji określonej platformy.</span><span class="sxs-lookup"><span data-stu-id="ed5ff-132">Additionally, while C# version updates generally coincide with major .Net Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="ed5ff-133">Nowe funkcje ostatecznie wymaga nową aktualizację kompilatora wydaną obok poprawki C#, każdej z funkcji ma własną minimalny interfejs API .net lub typowe wymagania środowiska uruchomieniowego języka, które mogą zezwolić na uruchamianie na platformach niższego poziomu przez w tym pakiety NuGet lub innych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="ed5ff-133">While the new features will definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .Net API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>
  
 <span data-ttu-id="ed5ff-134">Niezależnie od tego, który **- langversion** ustawienie używanie użyjesz bieżącą wersję środowiska CLR do utworzenia .exe lub .dll.</span><span class="sxs-lookup"><span data-stu-id="ed5ff-134">Regardless of which **-langversion** setting you use, you will use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="ed5ff-135">Jedynym wyjątkiem jest przyjaznych zestawów i [- moduleassemblyname (opcja kompilatora C#)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), która pracy w obszarze **- langversion: ISO-1**.</span><span class="sxs-lookup"><span data-stu-id="ed5ff-135">One exception is friend assemblies and [-moduleassemblyname (C# Compiler Option)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), which work under **-langversion:ISO-1**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ed5ff-136">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ed5ff-136">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="ed5ff-137">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="ed5ff-137">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="ed5ff-138">Kliknij przycisk **kompilacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed5ff-138">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="ed5ff-139">Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ed5ff-139">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="ed5ff-140">Modyfikowanie **wersji językowej** właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed5ff-140">Modify the **Language Version** property.</span></span>  
  
 <span data-ttu-id="ed5ff-141">Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="ed5ff-141">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>  
    
## <a name="see-also"></a><span data-ttu-id="ed5ff-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed5ff-142">See Also</span></span>  
 [<span data-ttu-id="ed5ff-143">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="ed5ff-143">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="ed5ff-144">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ed5ff-144">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 
### <a name="c-language-specification"></a><span data-ttu-id="ed5ff-145">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ed5ff-145">C# Language Specification</span></span>
 <span data-ttu-id="ed5ff-146">[Dokumentacja specyfikacja języka C#](../../../csharp/language-reference/language-specification/index.md) : .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="ed5ff-146">[C# Language Specification Reference](../../../csharp/language-reference/language-specification/index.md) : .NET Foundation</span></span>  
 <span data-ttu-id="ed5ff-147">C# 1.0/1.1 [23270:2003 ISO/IEC](https://www.iso.org/standard/36768.html) technologii informatycznych — specyfikacja języka C#: ISO katalogu</span><span class="sxs-lookup"><span data-stu-id="ed5ff-147">C# 1.0/1.1 [ISO/IEC 23270:2003](https://www.iso.org/standard/36768.html) Information technology -- C# Language Specification : ISO Catalogue</span></span>  
 <span data-ttu-id="ed5ff-148">C# 2.0 [23270:2006 ISO/IEC](https://www.iso.org/standard/42926.html) technologii informatycznych — specyfikacja języka C#: ISO katalogu</span><span class="sxs-lookup"><span data-stu-id="ed5ff-148">C# 2.0 [ISO/IEC 23270:2006](https://www.iso.org/standard/42926.html) Information technology -- C# Language Specification : ISO Catalogue</span></span>  
 <span data-ttu-id="ed5ff-149">C# 2.0 [c042926_ISO_IEC_23270_2006 zip (E)](http://standards.iso.org/ittf/PubliclyAvailableStandards/c042926_ISO_IEC_23270_2006(E).zip) 23270:2006 ISO/IEC w formacie PDF: dostępne standardów za darmo ISO</span><span class="sxs-lookup"><span data-stu-id="ed5ff-149">C# 2.0 [c042926_ISO_IEC_23270_2006(E).zip](http://standards.iso.org/ittf/PubliclyAvailableStandards/c042926_ISO_IEC_23270_2006(E).zip) ISO/IEC 23270:2006 in PDF format : ISO Freely Available Standards</span></span>  
 <span data-ttu-id="ed5ff-150">C# 3.0 [Specification.doc języka CSharp](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc) C# wersja specyfikacji języka 3.0: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="ed5ff-150">C# 3.0 [CSharp Language Specification.doc](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc) C# Language Specification Version 3.0 : Microsoft Corporation</span></span>  
 <span data-ttu-id="ed5ff-151">C# 4.0 [Ecma-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf) ECMA 334 4. w wersji Standard</span><span class="sxs-lookup"><span data-stu-id="ed5ff-151">C# 4.0 [Ecma-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf) Standard ECMA-334 4th Edition</span></span>    
 <span data-ttu-id="ed5ff-152">C# w wersji 5.0 [Specification.docx języka CSharp](https://www.microsoft.com/download/details.aspx?id=7029) C# wersja specyfikacji języka 5.0: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="ed5ff-152">C# 5.0 [CSharp Language Specification.docx](https://www.microsoft.com/download/details.aspx?id=7029) C# Language Specification Version 5.0 : Microsoft Corporation</span></span>  
 <span data-ttu-id="ed5ff-153">C# w wersji 6.0 [README.md](https://github.com/dotnet/csharplang/blob/master/spec/README.md) C# wersja specyfikacji języka 6 - nieoficjalny projekt: .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="ed5ff-153">C# 6.0 [README.md](https://github.com/dotnet/csharplang/blob/master/spec/README.md) C# Language Specification Version 6 - Unofficial Draft : .NET Foundation</span></span>  
 <span data-ttu-id="ed5ff-154">C# (nie jest aktualnie dostępna) 7.0</span><span class="sxs-lookup"><span data-stu-id="ed5ff-154">C# 7.0 (not currently available)</span></span>  

<!--- Uncomment and add to the above when they become officially released
 C# 7.1 (spec is not yet finished)  
 C# 7.2 (spec is not yet finished)  
 C# 8.0 (spec is not yet finished)  
-->

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a><span data-ttu-id="ed5ff-155">Wersja minimalna kompilatora potrzebnych do obsługi wszystkich funkcji języka</span><span class="sxs-lookup"><span data-stu-id="ed5ff-155">Minimum compiler version needed to support all language features</span></span>   
<span data-ttu-id="ed5ff-156">[↩](#TDefault)<a name="FDefault">domyślne</a>, <a name="FISO1">ISO1</a>: .net programu Microsoft Visual Studio/Build Tools 2002 lub powiązane .net Framework 1.0 kompilatora</span><span class="sxs-lookup"><span data-stu-id="ed5ff-156">[↩](#TDefault)<a name="FDefault">Default</a>, <a name="FISO1">ISO1</a>: Microsoft Visual Studio/Build Tools .Net 2002 or bundled .Net Framework 1.0 compiler</span></span>     
<span data-ttu-id="ed5ff-157">[↩](#TISO2)<a name="FISO2">ISO2</a>: program Microsoft Visual Studio/kompilacji narzędzia 2005 lub powiązane .net Framework 2.0 kompilatora</span><span class="sxs-lookup"><span data-stu-id="ed5ff-157">[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Build Tools 2005 or bundled .Net Framework 2.0 compiler</span></span>    
<span data-ttu-id="ed5ff-158">[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/kompilacji narzędzia 2008 lub powiązane .net Framework 3.5 kompilatora</span><span class="sxs-lookup"><span data-stu-id="ed5ff-158">[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/Build Tools 2008 or bundled .Net Framework 3.5 compiler</span></span>    
<span data-ttu-id="ed5ff-159">[↩](#TCS4)<a name="FCS4">CS4</a>: programu Microsoft Visual Studio/kompilacji narzędzia 2010 lub powiązane .net Framework 4.0 kompilatora</span><span class="sxs-lookup"><span data-stu-id="ed5ff-159">[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/Build Tools 2010 or bundled .Net Framework 4.0 compiler</span></span>    
<span data-ttu-id="ed5ff-160">[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/kompilacji narzędzia 2012 lub powiązane .net Framework 4.5 kompilatora</span><span class="sxs-lookup"><span data-stu-id="ed5ff-160">[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/Build Tools 2012 or bundled .Net Framework 4.5 compiler</span></span>    
<span data-ttu-id="ed5ff-161">[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015</span><span class="sxs-lookup"><span data-stu-id="ed5ff-161">[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015</span></span>    
<span data-ttu-id="ed5ff-162">[↩](#TCS7)<a name="FCS7">CS7</a>, <a name="FLatest">najnowsze</a>: 2017 narzędzi Microsoft Visual Studio/kompilacji</span><span class="sxs-lookup"><span data-stu-id="ed5ff-162">[↩](#TCS7)<a name="FCS7">CS7</a>, <a name="FLatest">Latest</a>: Microsoft Visual Studio/Build Tools 2017</span></span>   

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS8)<a name="FCS71">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->
