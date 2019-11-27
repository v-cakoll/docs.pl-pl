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
# <a name="-platform-visual-basic"></a><span data-ttu-id="ade91-102">-Platforma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ade91-102">-platform (Visual Basic)</span></span>
<span data-ttu-id="ade91-103">Określa, która wersja platformy środowiska uruchomieniowego języka wspólnego (CLR) może uruchomić plik wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="ade91-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ade91-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ade91-104">Syntax</span></span>  
  
```console  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="ade91-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ade91-105">Arguments</span></span>  
  
|<span data-ttu-id="ade91-106">Termin</span><span class="sxs-lookup"><span data-stu-id="ade91-106">Term</span></span>|<span data-ttu-id="ade91-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="ade91-107">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="ade91-108">Kompiluje zestaw do uruchomienia przez 32-bitowe środowisko CLR zgodne z architekturą x86.</span><span class="sxs-lookup"><span data-stu-id="ade91-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="ade91-109">Kompiluje zestaw do uruchomienia przez 64-bitowe środowisko CLR na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T.</span><span class="sxs-lookup"><span data-stu-id="ade91-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="ade91-110">Kompiluje zestaw do uruchomienia przez 64-bitowe środowisko CLR na komputerze z procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="ade91-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="ade91-111">Kompiluje zestaw do uruchomienia na komputerze z procesorem ARM (Advanced RISC Machine).</span><span class="sxs-lookup"><span data-stu-id="ade91-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="ade91-112">Kompiluje zestaw do uruchomienia na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="ade91-112">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="ade91-113">Aplikacja będzie działać jako aplikacja 32-bitowa w 32-bitowych wersjach systemu Windows i jako aplikacja 64-bitowa w systemie 64-bitowe wersje systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ade91-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="ade91-114">Ta flaga jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="ade91-114">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="ade91-115">Kompiluje zestaw do uruchomienia na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="ade91-115">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="ade91-116">Aplikacja będzie działać jako aplikacja 32-bitowa na 32-bitowych i 64-bitowych wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ade91-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="ade91-117">Ta flaga jest prawidłowa tylko dla plików wykonywalnych (. EXE) i wymaga .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="ade91-117">This flag is valid only for executables (.EXE) and requires .NET Framework 4.5.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ade91-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ade91-118">Remarks</span></span>  
 <span data-ttu-id="ade91-119">Użyj opcji `-platform`, aby określić typ procesora docelowego dla pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="ade91-119">Use the `-platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="ade91-120">Ogólnie rzecz biorąc, zestawy .NET Framework, które zapisały w Visual Basic, będą uruchamiane niezależnie od platformy.</span><span class="sxs-lookup"><span data-stu-id="ade91-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="ade91-121">Jednak istnieją sytuacje, które zachowują się inaczej na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="ade91-121">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="ade91-122">Te typowe przypadki są następujące:</span><span class="sxs-lookup"><span data-stu-id="ade91-122">These common cases are:</span></span>  
  
- <span data-ttu-id="ade91-123">Struktury zawierające elementy członkowskie, które zmieniają rozmiar w zależności od platformy, takie jak dowolny typ wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="ade91-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
- <span data-ttu-id="ade91-124">Arytmetyczny wskaźnik obejmujący stałe rozmiary.</span><span class="sxs-lookup"><span data-stu-id="ade91-124">Pointer arithmetic that includes constant sizes.</span></span>  
  
- <span data-ttu-id="ade91-125">Nieprawidłowe wywołanie platformy lub deklaracje COM, które używają `Integer` dla dojść, a nie <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="ade91-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
- <span data-ttu-id="ade91-126">Rzutowanie <xref:System.IntPtr> na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ade91-126">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
- <span data-ttu-id="ade91-127">Użycie wywołania platformy lub międzyoperacyjności modelu COM ze składnikami, które nie istnieją na wszystkich platformach.</span><span class="sxs-lookup"><span data-stu-id="ade91-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="ade91-128">Opcja **-platform** ogranicza niektóre problemy, Jeśli wiesz, że masz założeń dotyczących architektury, w której kod będzie uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="ade91-128">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="ade91-129">Opracowany</span><span class="sxs-lookup"><span data-stu-id="ade91-129">Specifically:</span></span>  
  
- <span data-ttu-id="ade91-130">Jeśli zdecydujesz się na użycie platformy 64-bitowej, a aplikacja jest uruchamiana na komputerze 32-bitowym, komunikat o błędzie jest bardzo wcześniejszy i jest bardziej ukierunkowany na problem niż błąd, który wystąpi bez użycia tego przełącznika.</span><span class="sxs-lookup"><span data-stu-id="ade91-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
- <span data-ttu-id="ade91-131">Jeśli ustawisz flagę `x86` dla opcji, a aplikacja zostanie uruchomiona na komputerze 64-bitowym, aplikacja zostanie uruchomiona w podsystemie WOW zamiast uruchamiać natywnie.</span><span class="sxs-lookup"><span data-stu-id="ade91-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="ade91-132">W 64-bitowym systemie operacyjnym Windows:</span><span class="sxs-lookup"><span data-stu-id="ade91-132">On a 64-bit Windows operating system:</span></span>  
  
- <span data-ttu-id="ade91-133">Zestawy skompilowane z `-platform:x86` będą wykonywane na 32-bitowym CLR uruchomionym w emulatorze WOW64.</span><span class="sxs-lookup"><span data-stu-id="ade91-133">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
- <span data-ttu-id="ade91-134">Pliki wykonywalne skompilowane z `-platform:anycpu` będą wykonywane na 64-bitowym CLR.</span><span class="sxs-lookup"><span data-stu-id="ade91-134">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
- <span data-ttu-id="ade91-135">Biblioteka DLL skompilowana z `-platform:anycpu` będzie wykonywana w tym samym środowisku CLR co proces, w którym został załadowany.</span><span class="sxs-lookup"><span data-stu-id="ade91-135">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
- <span data-ttu-id="ade91-136">Pliki wykonywalne, które są kompilowane przy użyciu `-platform:anycpu32bitpreferred`, zostaną wykonane na 32-bitowym środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="ade91-136">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="ade91-137">Aby uzyskać więcej informacji na temat sposobu tworzenia aplikacji do uruchamiania w 64-bitowej wersji systemu Windows, zobacz [64-bitowe aplikacje](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="ade91-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a><span data-ttu-id="ade91-138">Aby ustawić platformę w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ade91-138">To set -platform in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="ade91-139">W **Eksplorator rozwiązań**wybierz projekt, otwórz menu **projekt** , a następnie kliknij przycisk **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ade91-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="ade91-140">Na karcie **kompilacja** zaznacz lub wyczyść pole wyboru **Preferuj 32-bitowe** , lub na liście **docelowy procesor CPU** wybierz wartość.</span><span class="sxs-lookup"><span data-stu-id="ade91-140">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="ade91-141">Aby uzyskać więcej informacji, zobacz [Strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ade91-141">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ade91-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="ade91-142">Example</span></span>  
 <span data-ttu-id="ade91-143">Poniższy przykład ilustruje sposób użycia opcji kompilatora `-platform`.</span><span class="sxs-lookup"><span data-stu-id="ade91-143">The following example illustrates how to use the `-platform` compiler option.</span></span>  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ade91-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ade91-144">See also</span></span>

- [<span data-ttu-id="ade91-145">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ade91-145">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="ade91-146">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ade91-146">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ade91-147">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="ade91-147">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
