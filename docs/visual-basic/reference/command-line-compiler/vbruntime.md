---
title: /vbruntime
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbruntime
- /vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dda8ea7285a748bac53e30af8bd7a60099fe7411
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="vbruntime"></a><span data-ttu-id="daba2-102">/vbruntime</span><span class="sxs-lookup"><span data-stu-id="daba2-102">/vbruntime</span></span>
<span data-ttu-id="daba2-103">Określa, że kompilator powinien kompilować bez odwołanie w Visual Basic Runtime Library lub odwołanie do biblioteki środowiska uruchomieniowego określonych.</span><span class="sxs-lookup"><span data-stu-id="daba2-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daba2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="daba2-104">Syntax</span></span>  
  
```  
/vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="daba2-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="daba2-105">Arguments</span></span>  
 \-  
 <span data-ttu-id="daba2-106">Kompiluj bez odwołania do Visual Basic Runtime Library.</span><span class="sxs-lookup"><span data-stu-id="daba2-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="daba2-107">Kompiluj z odwołaniem do domyślnego Visual Basic Runtime Library.</span><span class="sxs-lookup"><span data-stu-id="daba2-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="daba2-108">Kompiluj bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic, a następnie osadź podstawowych funkcji z Visual Basic Runtime Library w zestawie.</span><span class="sxs-lookup"><span data-stu-id="daba2-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="daba2-109">Kompiluj z odwołaniem do określonej biblioteki (DLL).</span><span class="sxs-lookup"><span data-stu-id="daba2-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="daba2-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="daba2-110">Remarks</span></span>  
 <span data-ttu-id="daba2-111">`/vbruntime` — Opcja kompilatora umożliwia określenie, czy kompilator powinien kompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="daba2-111">The `/vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="daba2-112">Jeśli kompilacja bez odwołania do Visual Basic Runtime Library błędy lub ostrzeżenia są rejestrowane na kod lub język konstrukcje generujących wywołanie pomocnika środowiska uruchomieniowego języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="daba2-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="daba2-113">(A *pomocnika środowisko uruchomieniowe Visual Basic* jest funkcją zdefiniowaną w pliku Microsoft.VisualBasic.dll, która jest wywoływana w czasie wykonywania, wykonanie określonego języka semantycznego.)</span><span class="sxs-lookup"><span data-stu-id="daba2-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="daba2-114">`/vbruntime+` Opcja zapewnia takie samo zachowanie, który występuje, jeśli nie `/vbruntime` został określony przełącznik.</span><span class="sxs-lookup"><span data-stu-id="daba2-114">The `/vbruntime+` option produces the same behavior that occurs if no `/vbruntime` switch is specified.</span></span> <span data-ttu-id="daba2-115">Można użyć `/vbruntime+` możliwość zastąpienia poprzedniego `/vbruntime` przełączników.</span><span class="sxs-lookup"><span data-stu-id="daba2-115">You can use the `/vbruntime+` option to override previous `/vbruntime` switches.</span></span>  
  
 <span data-ttu-id="daba2-116">Większość obiektów z `My` typu są niedostępne, gdy używasz `/vbruntime-` lub `vbruntime:``path` opcje.</span><span class="sxs-lookup"><span data-stu-id="daba2-116">Most objects of the `My` type are unavailable when you use the `/vbruntime-` or `vbruntime:``path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="daba2-117">Osadzanie funkcje podstawowe środowisko uruchomieniowe Visual Basic</span><span class="sxs-lookup"><span data-stu-id="daba2-117">Embedding Visual Basic Runtime core functionality</span></span>  
 <span data-ttu-id="daba2-118">`/vbruntime*` Opcja umożliwia kompilowanie bez odwołania do biblioteki środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="daba2-118">The `/vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="daba2-119">Zamiast tego podstawowych funkcji z Visual Basic Runtime Library jest osadzony w zestawie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="daba2-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="daba2-120">Tej opcji można użyć, gdy aplikacja działa na platformach, które nie zawierają środowisko uruchomieniowe Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="daba2-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="daba2-121">Osadzone są następujące elementy członkowskie środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="daba2-121">The following runtime members are embedded:</span></span>  
  
-   <span data-ttu-id="daba2-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions>klasy</span><span class="sxs-lookup"><span data-stu-id="daba2-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
-   <span data-ttu-id="daba2-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>— Metoda</span><span class="sxs-lookup"><span data-stu-id="daba2-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
-   <span data-ttu-id="daba2-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>— Metoda</span><span class="sxs-lookup"><span data-stu-id="daba2-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
-   <span data-ttu-id="daba2-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>— Metoda</span><span class="sxs-lookup"><span data-stu-id="daba2-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
-   <span data-ttu-id="daba2-126"><xref:Microsoft.VisualBasic.Constants.vbBack>Stała</span><span class="sxs-lookup"><span data-stu-id="daba2-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
-   <span data-ttu-id="daba2-127"><xref:Microsoft.VisualBasic.Constants.vbCr>Stała</span><span class="sxs-lookup"><span data-stu-id="daba2-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
-   <span data-ttu-id="daba2-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf>Stała</span><span class="sxs-lookup"><span data-stu-id="daba2-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
-   <span data-ttu-id="daba2-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed>Stała</span><span class="sxs-lookup"><span data-stu-id="daba2-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
-   <span data-ttu-id="daba2-130"><xref:Microsoft.VisualBasic.Constants.vbLf>Stała</span><span class="sxs-lookup"><span data-stu-id="daba2-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
-   <span data-ttu-id="daba2-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine>Stała</span><span class="sxs-lookup"><span data-stu-id="daba2-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
-   <span data-ttu-id="daba2-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar>Stała</span><span class="sxs-lookup"><span data-stu-id="daba2-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
-   <span data-ttu-id="daba2-133"><xref:Microsoft.VisualBasic.Constants.vbNullString>Stała</span><span class="sxs-lookup"><span data-stu-id="daba2-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
-   <span data-ttu-id="daba2-134"><xref:Microsoft.VisualBasic.Constants.vbTab>Stała</span><span class="sxs-lookup"><span data-stu-id="daba2-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
-   <span data-ttu-id="daba2-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab>Stała</span><span class="sxs-lookup"><span data-stu-id="daba2-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
-   <span data-ttu-id="daba2-136">Niektóre obiekty `My` typu</span><span class="sxs-lookup"><span data-stu-id="daba2-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="daba2-137">Jeśli kompilacja przy użyciu `/vbruntime*` opcji i kod odwołuje się do elementu członkowskiego z Visual Basic Runtime Library nie jest zagnieżdżony z podstawowych funkcji, kompilator zwraca błąd, który wskazuje, że element członkowski nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="daba2-137">If you compile using the `/vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="daba2-138">Odwołanie do określonej biblioteki</span><span class="sxs-lookup"><span data-stu-id="daba2-138">Referencing a specified library</span></span>  
 <span data-ttu-id="daba2-139">Można użyć `path` argument skompilować z odwołaniem do biblioteki środowiska uruchomieniowego niestandardowych zamiast domyślnej Visual Basic Runtime Library.</span><span class="sxs-lookup"><span data-stu-id="daba2-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="daba2-140">Jeśli wartość `path` argument jest w pełni kwalifikowana ścieżka do biblioteki DLL, kompilator użyje tego pliku jako biblioteka środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="daba2-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="daba2-141">Jeśli wartość `path` argument nie jest w pełni kwalifikowana ścieżka do biblioteki DLL, kompilator Visual Basic umożliwia wyszukiwanie określonych biblioteki DLL w bieżącym folderze najpierw.</span><span class="sxs-lookup"><span data-stu-id="daba2-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="daba2-142">Następnie umożliwia wyszukiwanie w ścieżce określony za pomocą [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="daba2-142">It will then search in the path that you have specified by using the [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) compiler option.</span></span> <span data-ttu-id="daba2-143">Jeśli `/sdkpath` — opcja kompilatora nie jest używany, kompilator będzie szukał zidentyfikowanych biblioteki DLL w folderze .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span><span class="sxs-lookup"><span data-stu-id="daba2-143">If the `/sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="daba2-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="daba2-144">Example</span></span>  
 <span data-ttu-id="daba2-145">Poniższy przykład przedstawia użycie `/vbruntime` opcję, aby skompilować z odwołaniem do niestandardowa biblioteka.</span><span class="sxs-lookup"><span data-stu-id="daba2-145">The following example shows how to use the `/vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```  
vbc /vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="daba2-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="daba2-146">See Also</span></span>  
 [<span data-ttu-id="daba2-147">Podstawowe języka Visual Basic — nowy tryb kompilacji w programie Visual Studio 2010 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="daba2-147">Visual Basic Core – New compilation mode in Visual Studio 2010 SP1</span></span>](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)  
 [<span data-ttu-id="daba2-148">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="daba2-148">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="daba2-149">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="daba2-149">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="daba2-150">/ sdkpath</span><span class="sxs-lookup"><span data-stu-id="daba2-150">/sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
