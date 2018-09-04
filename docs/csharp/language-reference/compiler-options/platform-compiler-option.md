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
ms.openlocfilehash: f52192087eb7b73ee930eea073e0c5716ad8c636
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507595"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="c540e-102">-platform (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="c540e-102">-platform (C# Compiler Options)</span></span>
<span data-ttu-id="c540e-103">Określa, która wersja środowiska uruchomieniowego języka w wspólnego (CLR) można uruchomić zestawu.</span><span class="sxs-lookup"><span data-stu-id="c540e-103">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c540e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c540e-104">Syntax</span></span>  
  
```console  
-platform:string  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c540e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c540e-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="c540e-106">(ustawienie domyślne) anycpu, anycpu32bitpreferred, ARM, x 64, x86 lub Itanium.</span><span class="sxs-lookup"><span data-stu-id="c540e-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c540e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c540e-107">Remarks</span></span>  
  
-   <span data-ttu-id="c540e-108">**anycpu** (ustawienie domyślne), kompiluje swoim zestawie, można uruchomić na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="c540e-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="c540e-109">Aplikacja działa jako proces 64-bitowych, jeśli to możliwe i powraca do 32-bitowych, gdy ten tryb jest dostępny tylko.</span><span class="sxs-lookup"><span data-stu-id="c540e-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>  
  
-   <span data-ttu-id="c540e-110">**anycpu32bitpreferred** kompiluje swoim zestawie, można uruchomić na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="c540e-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="c540e-111">Aplikacja działa w trybie 32-bitowych w systemach, które obsługują aplikacje 32-bitowych i 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="c540e-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="c540e-112">Można określić tę opcję, tylko dla projektów, których platformą docelową .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="c540e-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>  
  
-   <span data-ttu-id="c540e-113">**ARM** kompiluje zestaw do uruchomienia na komputerze, który ma procesor Advanced RISC Machine (ARM).</span><span class="sxs-lookup"><span data-stu-id="c540e-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>  
  
-   <span data-ttu-id="c540e-114">**x64** kompiluje zestaw do uruchomienia w 64-bitowym CLR na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T.</span><span class="sxs-lookup"><span data-stu-id="c540e-114">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>  
  
-   <span data-ttu-id="c540e-115">**x86** kompiluje zestawu do uruchomienia przez środowisko CLR 32-bitowy, x86 zgodny.</span><span class="sxs-lookup"><span data-stu-id="c540e-115">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>  
  
-   <span data-ttu-id="c540e-116">**Itanium** kompiluje zestaw do uruchomienia w 64-bitowym CLR na komputerze z procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="c540e-116">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>  
  
 <span data-ttu-id="c540e-117">W 64-bitowym systemie operacyjnym Windows:</span><span class="sxs-lookup"><span data-stu-id="c540e-117">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="c540e-118">Zestawy skompilowane z **-platform: x 86** wykonania na 32-bitowe środowisko CLR, uruchamianie w emulatorze WOW64.</span><span class="sxs-lookup"><span data-stu-id="c540e-118">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="c540e-119">Biblioteki DLL są kompilowane przy użyciu **— platforma: anycpu** wykonuje na tej samej CLR jako proces, do którego jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="c540e-119">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>  
  
-   <span data-ttu-id="c540e-120">Pliki wykonywalne, które są kompilowane przy użyciu **— platforma: anycpu** wykonania na 64-bitowe środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="c540e-120">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="c540e-121">Pliki wykonywalne skompilowany przy użyciu **-platform: anycpu32bitpreferred** wykonania na 32-bitowe środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="c540e-121">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="c540e-122">**Anycpu32bitpreferred** ustawienie jest prawidłowy tylko w przypadku pliku wykonywalnego (. Pliki z rozszerzeniem EXE) która wymaga programu .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="c540e-122">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="c540e-123">Aby uzyskać więcej informacji na temat tworzenia aplikacji, systemem Windows 64-bitowym systemie operacyjnym, zobacz [aplikacji 64-bitowych](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="c540e-123">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c540e-124">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c540e-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="c540e-125">Otwórz **właściwości** strony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="c540e-125">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="c540e-126">Kliknij przycisk **kompilacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="c540e-126">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="c540e-127">Modyfikowanie **platformę docelową** właściwości oraz dla projektów przeznaczonych dla platformy .NET Framework 4.5, zaznacz lub wyczyść **Preferuj 32-bitowe** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="c540e-127">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>  
  
 <span data-ttu-id="c540e-128">**Uwaga — Platforma** nie jest dostępna w środowisku deweloperskim w programie Visual C# Express.</span><span class="sxs-lookup"><span data-stu-id="c540e-128">**Note -platform** is not available in the development environment in Visual C# Express.</span></span>  
  
 <span data-ttu-id="c540e-129">Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span><span class="sxs-lookup"><span data-stu-id="c540e-129">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c540e-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="c540e-130">Example</span></span>  
 <span data-ttu-id="c540e-131">Poniższy przykład pokazuje, jak używać **— Platforma** opcję, aby określić, że aplikacja powinien być wykonywany przez środowisko CLR 64-bitowym na 64-bitowym systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="c540e-131">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>  
  
```console  
csc -platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c540e-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c540e-132">See Also</span></span>  

- [<span data-ttu-id="c540e-133">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="c540e-133">C# Compiler Options</span></span>](index.md)  
- [<span data-ttu-id="c540e-134">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="c540e-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
