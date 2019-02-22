---
title: -platform (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 6d4918407c68c7164db023b19cb170aef12fd203
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56663902"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="82937-102">-platform (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="82937-102">-platform (C# Compiler Options)</span></span>
<span data-ttu-id="82937-103">Określa, która wersja środowiska uruchomieniowego języka w wspólnego (CLR) można uruchomić zestawu.</span><span class="sxs-lookup"><span data-stu-id="82937-103">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82937-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="82937-104">Syntax</span></span>  
  
```console  
-platform:string  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82937-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="82937-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="82937-106">(ustawienie domyślne) anycpu, anycpu32bitpreferred, ARM, x 64, x86 lub Itanium.</span><span class="sxs-lookup"><span data-stu-id="82937-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82937-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82937-107">Remarks</span></span>  
  
-   <span data-ttu-id="82937-108">**anycpu** (ustawienie domyślne), kompiluje swoim zestawie, można uruchomić na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="82937-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="82937-109">Aplikacja działa jako proces 64-bitowych, jeśli to możliwe i powraca do 32-bitowych, gdy ten tryb jest dostępny tylko.</span><span class="sxs-lookup"><span data-stu-id="82937-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>  
  
-   <span data-ttu-id="82937-110">**anycpu32bitpreferred** kompiluje swoim zestawie, można uruchomić na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="82937-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="82937-111">Aplikacja działa w trybie 32-bitowych w systemach, które obsługują aplikacje 32-bitowych i 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="82937-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="82937-112">Można określić tę opcję, tylko dla projektów, których platformą docelową .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="82937-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>  
  
-   <span data-ttu-id="82937-113">**ARM** kompiluje zestaw do uruchomienia na komputerze, który ma procesor Advanced RISC Machine (ARM).</span><span class="sxs-lookup"><span data-stu-id="82937-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>  
  
-   <span data-ttu-id="82937-114">**ARM64** kompiluje zestaw do uruchomienia w 64-bitowym CLR na komputerze, który ma procesor Advanced RISC Machine (ARM), który obsługuje A64 — zestaw instrukcji.</span><span class="sxs-lookup"><span data-stu-id="82937-114">**ARM64** compiles your assembly to run by the 64-bit CLR on a computer that has an Advanced RISC Machine (ARM) processor that supports the A64 instruction set.</span></span>  

-   <span data-ttu-id="82937-115">**x64** kompiluje zestaw do uruchomienia w 64-bitowym CLR na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T.</span><span class="sxs-lookup"><span data-stu-id="82937-115">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>  
  
-   <span data-ttu-id="82937-116">**x86** kompiluje zestawu do uruchomienia przez środowisko CLR 32-bitowy, x86 zgodny.</span><span class="sxs-lookup"><span data-stu-id="82937-116">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>  
  
-   <span data-ttu-id="82937-117">**Itanium** kompiluje zestaw do uruchomienia w 64-bitowym CLR na komputerze z procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="82937-117">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>  
  
 <span data-ttu-id="82937-118">W 64-bitowym systemie operacyjnym Windows:</span><span class="sxs-lookup"><span data-stu-id="82937-118">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="82937-119">Zestawy skompilowane z **-platform: x 86** wykonania na 32-bitowe środowisko CLR, uruchamianie w emulatorze WOW64.</span><span class="sxs-lookup"><span data-stu-id="82937-119">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="82937-120">Biblioteki DLL są kompilowane przy użyciu **— platforma: anycpu** wykonuje na tej samej CLR jako proces, do którego jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="82937-120">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>  
  
-   <span data-ttu-id="82937-121">Pliki wykonywalne, które są kompilowane przy użyciu **— platforma: anycpu** wykonania na 64-bitowe środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="82937-121">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="82937-122">Pliki wykonywalne skompilowany przy użyciu **-platform: anycpu32bitpreferred** wykonania na 32-bitowe środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="82937-122">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="82937-123">**Anycpu32bitpreferred** ustawienie jest prawidłowy tylko w przypadku pliku wykonywalnego (. Pliki z rozszerzeniem EXE) która wymaga programu .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="82937-123">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="82937-124">Aby uzyskać więcej informacji na temat tworzenia aplikacji, systemem Windows 64-bitowym systemie operacyjnym, zobacz [aplikacji 64-bitowych](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="82937-124">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="82937-125">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="82937-125">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="82937-126">Otwórz **właściwości** strony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="82937-126">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="82937-127">Kliknij przycisk **kompilacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="82937-127">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="82937-128">Modyfikowanie **platformę docelową** właściwości oraz dla projektów przeznaczonych dla platformy .NET Framework 4.5, zaznacz lub wyczyść **Preferuj 32-bitowe** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="82937-128">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>  
  
 <span data-ttu-id="82937-129">**Uwaga — Platforma** nie jest dostępna w środowisku deweloperskim w programie Visual C# Express.</span><span class="sxs-lookup"><span data-stu-id="82937-129">**Note -platform** is not available in the development environment in Visual C# Express.</span></span>  
  
 <span data-ttu-id="82937-130">Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span><span class="sxs-lookup"><span data-stu-id="82937-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82937-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="82937-131">Example</span></span>  
 <span data-ttu-id="82937-132">Poniższy przykład pokazuje, jak używać **— Platforma** opcję, aby określić, że aplikacja powinien być wykonywany przez środowisko CLR 64-bitowym na 64-bitowym systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="82937-132">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>  
  
```console  
csc -platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="82937-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82937-133">See also</span></span>

- [<span data-ttu-id="82937-134">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="82937-134">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="82937-135">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="82937-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
