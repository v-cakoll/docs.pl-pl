---
title: -platformy (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: 5c01136564d64d5b2f1f56d311a6b7eadf1742f0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64633082"
---
# <a name="-platform-visual-basic"></a><span data-ttu-id="5d0bb-102">-platformy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d0bb-102">-platform (Visual Basic)</span></span>
<span data-ttu-id="5d0bb-103">Określa, którą platformy wersję środowiska uruchomieniowego języka wspólnego (CLR) można uruchomić pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d0bb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d0bb-104">Syntax</span></span>  
  
```  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="5d0bb-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5d0bb-105">Arguments</span></span>  
  
|<span data-ttu-id="5d0bb-106">Termin</span><span class="sxs-lookup"><span data-stu-id="5d0bb-106">Term</span></span>|<span data-ttu-id="5d0bb-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="5d0bb-107">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="5d0bb-108">Kompiluje zestawu do uruchomienia przez środowisko CLR 32-bitowy, x86 zgodny.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="5d0bb-109">Kompiluje zestaw do uruchomienia w 64-bitowym CLR na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="5d0bb-110">Kompiluje zestaw do uruchomienia w 64-bitowym CLR na komputerze z procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="5d0bb-111">Kompiluje zestaw do uruchomienia na komputerze z procesorem ARM (Advanced RISC Machine).</span><span class="sxs-lookup"><span data-stu-id="5d0bb-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="5d0bb-112">Kompiluje zestaw można uruchomić na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-112">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="5d0bb-113">Aplikacja jest uruchamiana jako aplikacja 32-bitowego na 32-bitowe wersje systemu Windows i jako aplikacji 64-bitowych w 64-bitowych wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="5d0bb-114">Ta flaga jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-114">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="5d0bb-115">Kompiluje zestaw można uruchomić na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-115">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="5d0bb-116">Aplikacja jest uruchamiana jako aplikacja 32-bitowa w 32-bitowych i 64-bitowych wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="5d0bb-117">Ta flaga jest prawidłowy tylko dla plików wykonywalnych (. Z rozszerzeniem EXE) i wymaga [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5d0bb-117">This flag is valid only for executables (.EXE) and requires [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d0bb-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d0bb-118">Remarks</span></span>  
 <span data-ttu-id="5d0bb-119">Użyj `-platform` opcję, aby określić typ procesora przeznaczone dla pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-119">Use the `-platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="5d0bb-120">Ogólnie rzecz biorąc zestawów .NET Framework, napisany w języku Visual Basic uruchomi się takie same, niezależnie od platformy.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="5d0bb-121">Jednakże istnieją przypadki, które zachowują się inaczej, na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-121">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="5d0bb-122">Następujące typowe przypadki są:</span><span class="sxs-lookup"><span data-stu-id="5d0bb-122">These common cases are:</span></span>  
  
- <span data-ttu-id="5d0bb-123">Struktury, które zawierają składowe, które zmiany rozmiaru, w zależności od platformy, takie jak dowolny typ wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
- <span data-ttu-id="5d0bb-124">Arytmetyczny wskaźnik, obejmującą stałych rozmiarach.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-124">Pointer arithmetic that includes constant sizes.</span></span>  
  
- <span data-ttu-id="5d0bb-125">Nieprawidłowa platforma wywołania lub deklaracji COM, które używają `Integer` dla dojścia, zamiast <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
- <span data-ttu-id="5d0bb-126">Rzutowanie <xref:System.IntPtr> do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-126">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
- <span data-ttu-id="5d0bb-127">Za pomocą platformy wywołania lub Usługa międzyoperacyjna modelu COM ze składnikami, które nie istnieją na wszystkich platformach.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="5d0bb-128">**— Platforma** opcji ograniczą niektóre problemy, jeśli wiesz, że wprowadzono założenia dotyczące architektury, kod będzie działał na.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-128">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="5d0bb-129">W szczególności:</span><span class="sxs-lookup"><span data-stu-id="5d0bb-129">Specifically:</span></span>  
  
- <span data-ttu-id="5d0bb-130">Jeśli zdecydujesz się na docelowe platformy 64-bitowej, a aplikacja jest uruchamiana na komputerze 32-bitowym, komunikat o błędzie jest znacznie wcześniej i bardziej celem problem niż błąd występujący bez korzystania z tego przełącznika.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
- <span data-ttu-id="5d0bb-131">Jeśli ustawisz `x86` flagi opcję i później uruchomieniu aplikacji na komputerze 64-bitowym, aplikacja zostanie uruchomiona w ramach podsystemu WOW zamiast działające natywnie.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="5d0bb-132">W 64-bitowym systemie operacyjnym Windows:</span><span class="sxs-lookup"><span data-stu-id="5d0bb-132">On a 64-bit Windows operating system:</span></span>  
  
- <span data-ttu-id="5d0bb-133">Zestawy skompilowane z `-platform:x86` zostanie wykonana w 32-bitowe środowisko CLR, uruchamianie w emulatorze WOW64.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-133">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
- <span data-ttu-id="5d0bb-134">Pliki wykonywalne skompilowany przy użyciu `-platform:anycpu` zostanie wykonana w 64-bitowe środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-134">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
- <span data-ttu-id="5d0bb-135">Biblioteki DLL są kompilowane przy użyciu `-platform:anycpu` zostaną wykonane zgodnie z tym samym CLR jako proces, do którego on ładowany.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-135">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
- <span data-ttu-id="5d0bb-136">Pliki wykonywalne, które są kompilowane przy użyciu `-platform:anycpu32bitpreferred` zostanie wykonana w 32-bitowe środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-136">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="5d0bb-137">Aby uzyskać więcej informacji o sposobie tworzenia aplikacji do uruchamiania w 64-bitowej wersji systemu Windows, zobacz [aplikacji 64-bitowych](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="5d0bb-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a><span data-ttu-id="5d0bb-138">Aby ustawić - platform w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5d0bb-138">To set -platform in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="5d0bb-139">W **Eksploratora rozwiązań**, wybierz projekt, otwórz **projektu** menu, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="5d0bb-140">Na **skompilować** kartę, zaznacz lub wyczyść **Preferuj 32-bitowe** pole wyboru lub w **Procesora docelowego** listy, wybierz wartość.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-140">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="5d0bb-141">Aby uzyskać więcej informacji, zobacz [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5d0bb-141">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d0bb-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d0bb-142">Example</span></span>  
 <span data-ttu-id="5d0bb-143">Poniższy przykład ilustruje sposób używania `-platform` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="5d0bb-143">The following example illustrates how to use the `-platform` compiler option.</span></span>  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d0bb-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d0bb-144">See also</span></span>

- [<span data-ttu-id="5d0bb-145">/ TARGET (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d0bb-145">/target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="5d0bb-146">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d0bb-146">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="5d0bb-147">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="5d0bb-147">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
