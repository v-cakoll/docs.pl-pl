---
title: /platform (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4177b9da15bb89f37a7b3cbb27937e09d1c12635
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="platform-visual-basic"></a><span data-ttu-id="59b94-102">/platform (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59b94-102">/platform (Visual Basic)</span></span>
<span data-ttu-id="59b94-103">Określa, która wersja platformy środowisko uruchomieniowe języka wspólnego (CLR) można uruchomić pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="59b94-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59b94-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="59b94-104">Syntax</span></span>  
  
```  
/platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="59b94-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="59b94-105">Arguments</span></span>  
  
|<span data-ttu-id="59b94-106">Termin</span><span class="sxs-lookup"><span data-stu-id="59b94-106">Term</span></span>|<span data-ttu-id="59b94-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="59b94-107">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="59b94-108">Kompiluje z zestawu do uruchomienia przez środowisko CLR 32-bitowy, x86 zgodna.</span><span class="sxs-lookup"><span data-stu-id="59b94-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="59b94-109">Kompiluje z zestawu do uruchomienia na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T przez 64-bitowym CLR.</span><span class="sxs-lookup"><span data-stu-id="59b94-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="59b94-110">Kompiluje z zestawu do uruchomienia w 64-bitowym CLR na komputerze z procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="59b94-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="59b94-111">Kompiluje z zestawu do uruchomienia na komputerze z procesorem ARM (Advanced RISC Machine).</span><span class="sxs-lookup"><span data-stu-id="59b94-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="59b94-112">Kompiluje używanemu zestawowi można uruchomić na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="59b94-112">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="59b94-113">Aplikacja będzie działać jako aplikacja 32-bitowego w 32-bitowych wersjach systemu Windows i jako 64-bitowej aplikacji w 64-bitowych wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="59b94-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="59b94-114">Ta flaga jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="59b94-114">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="59b94-115">Kompiluje używanemu zestawowi można uruchomić na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="59b94-115">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="59b94-116">Aplikacja będzie działać jako aplikacja 32-bitowych na zarówno 32-bitowe i 64-bitowych wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="59b94-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="59b94-117">Ta flaga jest prawidłowa tylko dla plików wykonywalnych (. Wywołanie pliku EXE) i wymaga [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="59b94-117">This flag is valid only for executables (.EXE) and requires [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59b94-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59b94-118">Remarks</span></span>  
 <span data-ttu-id="59b94-119">Użyj `/platform` opcję, aby określić typ procesora objęci pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="59b94-119">Use the `/platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="59b94-120">Ogólnie rzecz biorąc zestawy .NET Framework napisane w języku Visual Basic uruchomi się takie same, niezależnie od platformy.</span><span class="sxs-lookup"><span data-stu-id="59b94-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="59b94-121">Istnieją jednak przypadki, które zachowują się inaczej na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="59b94-121">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="59b94-122">Następujące typowe przypadki są:</span><span class="sxs-lookup"><span data-stu-id="59b94-122">These common cases are:</span></span>  
  
-   <span data-ttu-id="59b94-123">Struktury zawierające elementy członkowskie, które zmiany rozmiaru w zależności od platformy, takich jak dowolnego typu wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="59b94-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
-   <span data-ttu-id="59b94-124">Arytmetyki wskaźnika, który obejmuje stałą rozmiary.</span><span class="sxs-lookup"><span data-stu-id="59b94-124">Pointer arithmetic that includes constant sizes.</span></span>  
  
-   <span data-ttu-id="59b94-125">Nieprawidłowa platforma wywołania lub deklaracje COM, które używają `Integer` dla dojść zamiast <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="59b94-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
-   <span data-ttu-id="59b94-126">Rzutowanie <xref:System.IntPtr> do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="59b94-126">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
-   <span data-ttu-id="59b94-127">Przy użyciu platformy wywołania lub COM. ze składnikami, które nie istnieją na wszystkich platformach.</span><span class="sxs-lookup"><span data-stu-id="59b94-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="59b94-128">**/Platform** opcji będzie ograniczyć problemy, jeśli wiadomo, że zostały wykonane założenia o architekturze kodu zostanie uruchomiony na.</span><span class="sxs-lookup"><span data-stu-id="59b94-128">The **/platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="59b94-129">W szczególności:</span><span class="sxs-lookup"><span data-stu-id="59b94-129">Specifically:</span></span>  
  
-   <span data-ttu-id="59b94-130">Jeśli zdecydujesz się skorzystać z platformy 64-bitowe i uruchomieniu aplikacji na komputerze 32-bitowy, komunikat o błędzie jest znacznie wcześniej i bardziej celem problem niż błąd występujący bez użycia tego przełącznika.</span><span class="sxs-lookup"><span data-stu-id="59b94-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
-   <span data-ttu-id="59b94-131">Jeśli ustawisz `x86` flagi opcji i następnie uruchomieniu aplikacji na komputerze 64-bitowym, aplikacja będzie działać w podsystemu WOW zamiast działać w sposób macierzysty.</span><span class="sxs-lookup"><span data-stu-id="59b94-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="59b94-132">W 64-bitowym systemie operacyjnym Windows:</span><span class="sxs-lookup"><span data-stu-id="59b94-132">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="59b94-133">Zestawy są kompilowane przy użyciu `/platform:x86` będą wykonywane na 32-bitowego środowiska CLR uruchomione w emulatorze WOW64.</span><span class="sxs-lookup"><span data-stu-id="59b94-133">Assemblies compiled with `/platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="59b94-134">Pliki wykonywalne skompilowane z `/platform:anycpu` będą wykonywane na 64-bitowym CLR.</span><span class="sxs-lookup"><span data-stu-id="59b94-134">Executables compiled with the `/platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="59b94-135">Biblioteki DLL są kompilowane przy użyciu `/platform:anycpu` będzie wykonywana na tej samej CLR jako proces, do którego ładowany.</span><span class="sxs-lookup"><span data-stu-id="59b94-135">A DLL compiled with the `/platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
-   <span data-ttu-id="59b94-136">Pliki wykonywalne, które są kompilowane przy użyciu `/platform:anycpu32bitpreferred` będą wykonywane na 32-bitowym CLR.</span><span class="sxs-lookup"><span data-stu-id="59b94-136">Executables that are compiled with `/platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="59b94-137">Aby uzyskać więcej informacji dotyczących sposobu tworzenia aplikacji do uruchomienia w 64-bitowej wersji systemu Windows, zobacz [aplikacji 64-bitowych](../../../../docs/framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="59b94-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../../docs/framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set-platform-in-the-visual-studio-ide"></a><span data-ttu-id="59b94-138">Aby ustawić/platform w programie Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="59b94-138">To set /platform in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="59b94-139">W **Eksploratora rozwiązań**, wybierz projekt, otwórz **projektu** menu, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="59b94-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="59b94-140">Aby uzyskać więcej informacji, zobacz [NIB: Zarządzanie właściwości projektu przy użyciu projektanta projektów](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="59b94-140">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="59b94-141">Na **skompilować** karcie, zaznacz lub wyczyść **preferowane jest 32-bitowych** pole wyboru lub w **Procesora docelowej** listy, wybierz wartość.</span><span class="sxs-lookup"><span data-stu-id="59b94-141">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="59b94-142">Aby uzyskać więcej informacji, zobacz [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="59b94-142">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="59b94-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="59b94-143">Example</span></span>  
 <span data-ttu-id="59b94-144">Poniższy przykład przedstawia sposób użycia `/platform` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="59b94-144">The following example illustrates how to use the `/platform` compiler option.</span></span>  
  
```  
vbc /platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="59b94-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59b94-145">See Also</span></span>  
 [<span data-ttu-id="59b94-146">/ TARGET (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59b94-146">/target (Visual Basic)</span></span>](target.md)  
 [<span data-ttu-id="59b94-147">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="59b94-147">Visual Basic Command-Line Compiler</span></span>](index.md)  
 [<span data-ttu-id="59b94-148">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="59b94-148">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
