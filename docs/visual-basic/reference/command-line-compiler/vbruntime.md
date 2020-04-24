---
title: -vbruntime
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
ms.openlocfilehash: 8c7789c6af7b82ecb40ecd73d09f64aa1da3fd4b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005055"
---
# <a name="-vbruntime"></a><span data-ttu-id="66207-102">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="66207-102">-vbruntime</span></span>
<span data-ttu-id="66207-103">Określa, że kompilator ma kompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic lub z odwołaniem do określonej biblioteki środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="66207-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66207-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66207-104">Syntax</span></span>  
  
```console  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="66207-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="66207-105">Arguments</span></span>  
 \-  
 <span data-ttu-id="66207-106">Kompiluj bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="66207-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="66207-107">Kompiluj z odwołaniem do domyślnej biblioteki środowiska uruchomieniowego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="66207-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="66207-108">Kompiluj bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic i Osadź podstawowe funkcje z biblioteki środowiska uruchomieniowego Visual Basic do zestawu.</span><span class="sxs-lookup"><span data-stu-id="66207-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="66207-109">Kompiluj z odwołaniem do określonej biblioteki (DLL).</span><span class="sxs-lookup"><span data-stu-id="66207-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66207-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66207-110">Remarks</span></span>  
 <span data-ttu-id="66207-111">Opcja `-vbruntime` kompilatora pozwala określić, że kompilator ma kompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="66207-111">The `-vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="66207-112">Jeśli kompilujesz bez odniesienia do biblioteki środowiska uruchomieniowego Visual Basic, błędy lub ostrzeżenia są rejestrowane dla kodu lub konstrukcje języka, które generują wywołanie do pomocnika Visual Basic środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="66207-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="66207-113">( *Pomocnik środowiska uruchomieniowego Visual Basic* jest funkcją zdefiniowaną w pliku Microsoft. VisualBasic. dll, która jest wywoływana w czasie wykonywania, aby wykonać określoną semantykę języka).</span><span class="sxs-lookup"><span data-stu-id="66207-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="66207-114">Ta `-vbruntime+` opcja daje takie samo zachowanie, które występuje, `-vbruntime` Jeśli nie określono przełącznika.</span><span class="sxs-lookup"><span data-stu-id="66207-114">The `-vbruntime+` option produces the same behavior that occurs if no `-vbruntime` switch is specified.</span></span> <span data-ttu-id="66207-115">Możesz użyć opcji, `-vbruntime+` aby zastąpić poprzednie `-vbruntime` przełączniki.</span><span class="sxs-lookup"><span data-stu-id="66207-115">You can use the `-vbruntime+` option to override previous `-vbruntime` switches.</span></span>  
  
 <span data-ttu-id="66207-116">Większość obiektów `My` typu jest niedostępna w przypadku korzystania z `-vbruntime-` opcji `-vbruntime:path` lub.</span><span class="sxs-lookup"><span data-stu-id="66207-116">Most objects of the `My` type are unavailable when you use the `-vbruntime-` or `-vbruntime:path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="66207-117">Osadzanie podstawowych funkcji środowiska uruchomieniowego Visual Basic</span><span class="sxs-lookup"><span data-stu-id="66207-117">Embedding Visual Basic Runtime core functionality</span></span>  
 <span data-ttu-id="66207-118">`-vbruntime*` Opcja umożliwia skompilowanie bez odwołania do biblioteki środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="66207-118">The `-vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="66207-119">Zamiast tego, podstawowe funkcje z biblioteki środowiska uruchomieniowego Visual Basic są osadzane w zestawie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="66207-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="66207-120">Tej opcji można użyć, jeśli aplikacja działa na platformach, które nie zawierają środowiska uruchomieniowego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="66207-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="66207-121">Następujące elementy członkowskie środowiska uruchomieniowego są osadzone:</span><span class="sxs-lookup"><span data-stu-id="66207-121">The following runtime members are embedded:</span></span>  
  
- <span data-ttu-id="66207-122">Klasa <xref:Microsoft.VisualBasic.CompilerServices.Conversions></span><span class="sxs-lookup"><span data-stu-id="66207-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
- <span data-ttu-id="66207-123">Metoda <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29></span><span class="sxs-lookup"><span data-stu-id="66207-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
- <span data-ttu-id="66207-124">Metoda <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29></span><span class="sxs-lookup"><span data-stu-id="66207-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
- <span data-ttu-id="66207-125">Metoda <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29></span><span class="sxs-lookup"><span data-stu-id="66207-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
- <span data-ttu-id="66207-126"><xref:Microsoft.VisualBasic.Constants.vbBack>stałego</span><span class="sxs-lookup"><span data-stu-id="66207-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
- <span data-ttu-id="66207-127"><xref:Microsoft.VisualBasic.Constants.vbCr>stałego</span><span class="sxs-lookup"><span data-stu-id="66207-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
- <span data-ttu-id="66207-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf>stałego</span><span class="sxs-lookup"><span data-stu-id="66207-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
- <span data-ttu-id="66207-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed>stałego</span><span class="sxs-lookup"><span data-stu-id="66207-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
- <span data-ttu-id="66207-130"><xref:Microsoft.VisualBasic.Constants.vbLf>stałego</span><span class="sxs-lookup"><span data-stu-id="66207-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
- <span data-ttu-id="66207-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine>stałego</span><span class="sxs-lookup"><span data-stu-id="66207-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
- <span data-ttu-id="66207-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar>stałego</span><span class="sxs-lookup"><span data-stu-id="66207-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
- <span data-ttu-id="66207-133"><xref:Microsoft.VisualBasic.Constants.vbNullString>stałego</span><span class="sxs-lookup"><span data-stu-id="66207-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
- <span data-ttu-id="66207-134"><xref:Microsoft.VisualBasic.Constants.vbTab>stałego</span><span class="sxs-lookup"><span data-stu-id="66207-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
- <span data-ttu-id="66207-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab>stałego</span><span class="sxs-lookup"><span data-stu-id="66207-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
- <span data-ttu-id="66207-136">Niektóre obiekty `My` typu</span><span class="sxs-lookup"><span data-stu-id="66207-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="66207-137">Jeśli kompilujesz przy użyciu `-vbruntime*` opcji, a kod odwołuje się do elementu członkowskiego z biblioteki środowiska uruchomieniowego Visual Basic, która nie jest osadzona w podstawowej funkcji, kompilator zwróci błąd wskazujący, że element członkowski nie jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="66207-137">If you compile using the `-vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="66207-138">Odwoływanie się do określonej biblioteki</span><span class="sxs-lookup"><span data-stu-id="66207-138">Referencing a specified library</span></span>  
 <span data-ttu-id="66207-139">Można użyć argumentu, `path` aby skompilować z odwołaniem do niestandardowej biblioteki środowiska uruchomieniowego zamiast domyślnej biblioteki środowiska uruchomieniowego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="66207-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="66207-140">Jeśli wartość `path` argumentu jest w pełni kwalifikowana ścieżka do biblioteki DLL, kompilator użyje tego pliku jako biblioteki środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="66207-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="66207-141">Jeśli wartość `path` argumentu nie jest w pełni kwalifikowaną ścieżką do biblioteki DLL, kompilator Visual Basic będzie najpierw wyszukać ZIDENTYFIKOWANĄ bibliotekę DLL w bieżącym folderze.</span><span class="sxs-lookup"><span data-stu-id="66207-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="66207-142">Następnie wyszukuje ścieżkę określoną przy użyciu opcji kompilatora [-SdkPath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) .</span><span class="sxs-lookup"><span data-stu-id="66207-142">It will then search in the path that you have specified by using the [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) compiler option.</span></span> <span data-ttu-id="66207-143">Jeśli opcja `-sdkpath` kompilatora nie jest używana, kompilator wyszuka ZIDENTYFIKOWANĄ bibliotekę DLL w folderze .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span><span class="sxs-lookup"><span data-stu-id="66207-143">If the `-sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="66207-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="66207-144">Example</span></span>  
 <span data-ttu-id="66207-145">Poniższy przykład pokazuje, `-vbruntime` jak używać opcji do kompilowania z odwołaniem do biblioteki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="66207-145">The following example shows how to use the `-vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="66207-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66207-146">See also</span></span>

- [<span data-ttu-id="66207-147">Visual Basic Core — nowy tryb kompilacji w programie Visual Studio 2010 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="66207-147">Visual Basic Core – New compilation mode in Visual Studio 2010 SP1</span></span>](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [<span data-ttu-id="66207-148">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="66207-148">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="66207-149">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="66207-149">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="66207-150">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="66207-150">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
