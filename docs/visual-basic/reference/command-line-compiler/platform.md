---
title: -platform
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: a6226b73d5d5d4d48a71afe39e8a546019d4c0bc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352344"
---
# <a name="-platform-visual-basic"></a><span data-ttu-id="ac6ae-102">-platform (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac6ae-102">-platform (Visual Basic)</span></span>
<span data-ttu-id="ac6ae-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac6ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac6ae-104">Syntax</span></span>  
  
```console  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="ac6ae-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ac6ae-105">Arguments</span></span>  
  
|<span data-ttu-id="ac6ae-106">Termin</span><span class="sxs-lookup"><span data-stu-id="ac6ae-106">Term</span></span>|<span data-ttu-id="ac6ae-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="ac6ae-107">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="ac6ae-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="ac6ae-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="ac6ae-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="ac6ae-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="ac6ae-112">Compiles your assembly to run on any platform.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-112">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="ac6ae-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="ac6ae-114">This flag is the default value.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-114">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="ac6ae-115">Compiles your assembly to run on any platform.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-115">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="ac6ae-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="ac6ae-117">This flag is valid only for executables (.EXE) and requires .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-117">This flag is valid only for executables (.EXE) and requires .NET Framework 4.5.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac6ae-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac6ae-118">Remarks</span></span>  
 <span data-ttu-id="ac6ae-119">Use the `-platform` option to specify the type of processor targeted by the output file.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-119">Use the `-platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="ac6ae-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="ac6ae-121">However, there are some cases that behave differently on different platforms.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-121">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="ac6ae-122">These common cases are:</span><span class="sxs-lookup"><span data-stu-id="ac6ae-122">These common cases are:</span></span>  
  
- <span data-ttu-id="ac6ae-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
- <span data-ttu-id="ac6ae-124">Pointer arithmetic that includes constant sizes.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-124">Pointer arithmetic that includes constant sizes.</span></span>  
  
- <span data-ttu-id="ac6ae-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
- <span data-ttu-id="ac6ae-126">Casting <xref:System.IntPtr> to `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-126">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
- <span data-ttu-id="ac6ae-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="ac6ae-128">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-128">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="ac6ae-129">Specifically:</span><span class="sxs-lookup"><span data-stu-id="ac6ae-129">Specifically:</span></span>  
  
- <span data-ttu-id="ac6ae-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
- <span data-ttu-id="ac6ae-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="ac6ae-132">On a 64-bit Windows operating system:</span><span class="sxs-lookup"><span data-stu-id="ac6ae-132">On a 64-bit Windows operating system:</span></span>  
  
- <span data-ttu-id="ac6ae-133">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-133">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
- <span data-ttu-id="ac6ae-134">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-134">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
- <span data-ttu-id="ac6ae-135">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-135">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
- <span data-ttu-id="ac6ae-136">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-136">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="ac6ae-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="ac6ae-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a><span data-ttu-id="ac6ae-138">To set -platform in the Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="ac6ae-138">To set -platform in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="ac6ae-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="ac6ae-140">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-140">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="ac6ae-141">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ac6ae-141">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac6ae-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac6ae-142">Example</span></span>  
 <span data-ttu-id="ac6ae-143">The following example illustrates how to use the `-platform` compiler option.</span><span class="sxs-lookup"><span data-stu-id="ac6ae-143">The following example illustrates how to use the `-platform` compiler option.</span></span>  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac6ae-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac6ae-144">See also</span></span>

- [<span data-ttu-id="ac6ae-145">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac6ae-145">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="ac6ae-146">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="ac6ae-146">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ac6ae-147">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="ac6ae-147">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
