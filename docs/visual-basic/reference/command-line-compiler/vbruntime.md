---
title: -vbruntime —
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
ms.openlocfilehash: a1988fcd19c6629d85ae0e739681fd39fe033c0d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843867"
---
# <a name="-vbruntime"></a><span data-ttu-id="3a45b-102">-vbruntime —</span><span class="sxs-lookup"><span data-stu-id="3a45b-102">-vbruntime</span></span>
<span data-ttu-id="3a45b-103">Określa, czy kompilator powinien kompilować się bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic lub odwołanie do biblioteki środowiska uruchomieniowego określonych.</span><span class="sxs-lookup"><span data-stu-id="3a45b-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a45b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a45b-104">Syntax</span></span>  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="3a45b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3a45b-105">Arguments</span></span>  
 \-  
 <span data-ttu-id="3a45b-106">Kompiluj bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3a45b-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="3a45b-107">Skompiluj z odwołaniem do domyślnej biblioteki środowiska uruchomieniowego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3a45b-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="3a45b-108">Skompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic, a następnie osadź podstawowe funkcje z biblioteki środowiska uruchomieniowego Visual Basic w zestawie.</span><span class="sxs-lookup"><span data-stu-id="3a45b-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="3a45b-109">Skompiluj z odwołaniem do określonej biblioteki (DLL).</span><span class="sxs-lookup"><span data-stu-id="3a45b-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a45b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a45b-110">Remarks</span></span>  
 <span data-ttu-id="3a45b-111">`-vbruntime` — Opcja kompilatora umożliwia określenie, czy kompilator powinien kompilować się bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3a45b-111">The `-vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="3a45b-112">W przypadku kompilacji bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic, błędy lub ostrzeżenia są rejestrowane w konstrukcji kodu lub języka, które generuje wywołanie pomocnika środowiska uruchomieniowego języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3a45b-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="3a45b-113">(A *pomocnika środowiska uruchomieniowego Visual Basic* jest funkcją zdefiniowaną w pliku Microsoft.VisualBasic.dll, która jest wywoływana w czasie wykonywania do wykonania określonego języka semantycznego.)</span><span class="sxs-lookup"><span data-stu-id="3a45b-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="3a45b-114">`-vbruntime+` Opcja zapewnia takie samo zachowanie, który występuje, jeśli nie `-vbruntime` określono przełącznik.</span><span class="sxs-lookup"><span data-stu-id="3a45b-114">The `-vbruntime+` option produces the same behavior that occurs if no `-vbruntime` switch is specified.</span></span> <span data-ttu-id="3a45b-115">Możesz użyć `-vbruntime+` możliwości zastąpienia poprzedniego `-vbruntime` przełączników.</span><span class="sxs-lookup"><span data-stu-id="3a45b-115">You can use the `-vbruntime+` option to override previous `-vbruntime` switches.</span></span>  
  
 <span data-ttu-id="3a45b-116">Większość obiektów `My` typu są niedostępne, gdy używasz `-vbruntime-` lub `-vbruntime:path` opcje.</span><span class="sxs-lookup"><span data-stu-id="3a45b-116">Most objects of the `My` type are unavailable when you use the `-vbruntime-` or `-vbruntime:path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="3a45b-117">Osadzanie środowiska uruchomieniowego Visual Basic podstawowe funkcje</span><span class="sxs-lookup"><span data-stu-id="3a45b-117">Embedding Visual Basic Runtime core functionality</span></span>  
 <span data-ttu-id="3a45b-118">`-vbruntime*` Opcja umożliwia kompilowanie bez odwołania do biblioteki środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3a45b-118">The `-vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="3a45b-119">Zamiast tego podstawowe funkcje z biblioteki środowiska uruchomieniowego Visual Basic jest osadzony w zestawie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3a45b-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="3a45b-120">Można użyć tej opcji, jeśli aplikacja działa na platformach, które nie zawierają środowisko uruchomieniowe języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3a45b-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="3a45b-121">Następujące składniki środowiska uruchomieniowego są osadzone:</span><span class="sxs-lookup"><span data-stu-id="3a45b-121">The following runtime members are embedded:</span></span>  
  
-   <span data-ttu-id="3a45b-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> Klasa</span><span class="sxs-lookup"><span data-stu-id="3a45b-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
-   <span data-ttu-id="3a45b-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a45b-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
-   <span data-ttu-id="3a45b-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a45b-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
-   <span data-ttu-id="3a45b-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a45b-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
-   <span data-ttu-id="3a45b-126"><xref:Microsoft.VisualBasic.Constants.vbBack> Stałe</span><span class="sxs-lookup"><span data-stu-id="3a45b-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
-   <span data-ttu-id="3a45b-127"><xref:Microsoft.VisualBasic.Constants.vbCr> Stałe</span><span class="sxs-lookup"><span data-stu-id="3a45b-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
-   <span data-ttu-id="3a45b-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> Stałe</span><span class="sxs-lookup"><span data-stu-id="3a45b-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
-   <span data-ttu-id="3a45b-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> Stałe</span><span class="sxs-lookup"><span data-stu-id="3a45b-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
-   <span data-ttu-id="3a45b-130"><xref:Microsoft.VisualBasic.Constants.vbLf> Stałe</span><span class="sxs-lookup"><span data-stu-id="3a45b-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
-   <span data-ttu-id="3a45b-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> Stałe</span><span class="sxs-lookup"><span data-stu-id="3a45b-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
-   <span data-ttu-id="3a45b-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> Stałe</span><span class="sxs-lookup"><span data-stu-id="3a45b-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
-   <span data-ttu-id="3a45b-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> Stałe</span><span class="sxs-lookup"><span data-stu-id="3a45b-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
-   <span data-ttu-id="3a45b-134"><xref:Microsoft.VisualBasic.Constants.vbTab> Stałe</span><span class="sxs-lookup"><span data-stu-id="3a45b-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
-   <span data-ttu-id="3a45b-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> Stałe</span><span class="sxs-lookup"><span data-stu-id="3a45b-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
-   <span data-ttu-id="3a45b-136">Niektóre obiekty `My` typu</span><span class="sxs-lookup"><span data-stu-id="3a45b-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="3a45b-137">Jeśli kompilujesz przy użyciu `-vbruntime*` opcji, a kod odwołuje się do elementu członkowskiego z biblioteki środowiska uruchomieniowego Visual Basic, który nie jest osadzony z podstawowych funkcji, kompilator zwraca komunikat o błędzie wskazujący, że element członkowski nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="3a45b-137">If you compile using the `-vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="3a45b-138">Odwoływanie się do określonej biblioteki</span><span class="sxs-lookup"><span data-stu-id="3a45b-138">Referencing a specified library</span></span>  
 <span data-ttu-id="3a45b-139">Możesz użyć `path` argument do kompilowania za pomocą odwołania do biblioteki niestandardowego środowiska uruchomieniowego zamiast domyślnego języka Visual Basic Runtime Library.</span><span class="sxs-lookup"><span data-stu-id="3a45b-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="3a45b-140">Jeśli wartość `path` argument jest w pełni kwalifikowaną ścieżkę do biblioteki DLL, kompilator użyje tego pliku jako biblioteka środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3a45b-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="3a45b-141">Jeśli wartość `path` argument nie jest w pełni kwalifikowana ścieżka do biblioteki DLL, kompilator Visual Basic umożliwia wyszukiwanie określonych bibliotek DLL w bieżącym folderze najpierw.</span><span class="sxs-lookup"><span data-stu-id="3a45b-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="3a45b-142">Następnie zostanie wyszukany w ścieżce zostali zdefiniowani za pomocą [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="3a45b-142">It will then search in the path that you have specified by using the [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) compiler option.</span></span> <span data-ttu-id="3a45b-143">Jeśli `-sdkpath` — opcja kompilatora nie jest używany, kompilator będzie wyszukiwał określonych bibliotek DLL w folderze .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span><span class="sxs-lookup"><span data-stu-id="3a45b-143">If the `-sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a45b-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a45b-144">Example</span></span>  
 <span data-ttu-id="3a45b-145">Poniższy przykład pokazuje, jak używać `-vbruntime` opcji, aby skompilować z odwołaniem do niestandardową biblioteką.</span><span class="sxs-lookup"><span data-stu-id="3a45b-145">The following example shows how to use the `-vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a45b-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a45b-146">See also</span></span>

- [<span data-ttu-id="3a45b-147">Podstawowe języka Visual Basic — nowy tryb kompilacji w Visual Studio 2010 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="3a45b-147">Visual Basic Core – New compilation mode in Visual Studio 2010 SP1</span></span>](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [<span data-ttu-id="3a45b-148">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3a45b-148">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3a45b-149">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="3a45b-149">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="3a45b-150">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="3a45b-150">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
