---
title: -platform (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
caps.latest.revision: "46"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5d35a91805f6189f60803056c541ce8344c024f0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="platform-c-compiler-options"></a><span data-ttu-id="dc15e-102">/platform (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="dc15e-102">/platform (C# Compiler Options)</span></span>
<span data-ttu-id="dc15e-103">Określa, która wersja z środowiska uruchomieniowego języka wspólnego (CLR) można uruchomić zestawu.</span><span class="sxs-lookup"><span data-stu-id="dc15e-103">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc15e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc15e-104">Syntax</span></span>  
  
```console  
/platform:string  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc15e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc15e-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="dc15e-106">anycpu (domyślna), anycpu32bitpreferred, ARM, x 64, x86 lub Itanium.</span><span class="sxs-lookup"><span data-stu-id="dc15e-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc15e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc15e-107">Remarks</span></span>  
  
-   <span data-ttu-id="dc15e-108">**anycpu** (ustawienie domyślne) kompiluje używanemu zestawowi można uruchomić na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="dc15e-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="dc15e-109">Aplikacja działa jako procesu 64-bitowego, jeśli to możliwe i powraca do 32-bitowego, gdy tylko ten tryb jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="dc15e-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>  
  
-   <span data-ttu-id="dc15e-110">**anycpu32bitpreferred** kompiluje używanemu zestawowi można uruchomić na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="dc15e-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="dc15e-111">Aplikacja działa w trybie 32-bitowych systemach, które obsługują zarówno 64-bitowe i 32-bitowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc15e-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="dc15e-112">Można określić tę opcję tylko w przypadku projektów przeznaczonych .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="dc15e-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>  
  
-   <span data-ttu-id="dc15e-113">**ARM** kompiluje z zestawu do uruchomienia na komputerze, na które ma procesor Advanced RISC Machine (ARM).</span><span class="sxs-lookup"><span data-stu-id="dc15e-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>  
  
-   <span data-ttu-id="dc15e-114">**x64** kompiluje z zestawu do uruchomienia na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T przez 64-bitowym CLR.</span><span class="sxs-lookup"><span data-stu-id="dc15e-114">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>  
  
-   <span data-ttu-id="dc15e-115">**x86** kompiluje z zestawu do uruchomienia przez środowisko CLR 32-bitowy, x86 zgodna.</span><span class="sxs-lookup"><span data-stu-id="dc15e-115">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>  
  
-   <span data-ttu-id="dc15e-116">**Itanium** kompiluje z zestawu do uruchomienia w 64-bitowym CLR na komputerze z procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="dc15e-116">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>  
  
 <span data-ttu-id="dc15e-117">W 64-bitowym systemie operacyjnym Windows:</span><span class="sxs-lookup"><span data-stu-id="dc15e-117">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="dc15e-118">Zestawy są kompilowane przy użyciu **x 86** wykonania na 32-bitowego środowiska CLR uruchomione w emulatorze WOW64.</span><span class="sxs-lookup"><span data-stu-id="dc15e-118">Assemblies compiled with **/platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="dc15e-119">Biblioteki DLL są kompilowane przy użyciu **/platform:anycpu** wykonuje w tej samej CLR jako proces, do którego został załadowany.</span><span class="sxs-lookup"><span data-stu-id="dc15e-119">A DLL compiled with the **/platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>  
  
-   <span data-ttu-id="dc15e-120">Pliki wykonywalne, które są kompilowane przy użyciu **/platform:anycpu** wykonania na 64-bitowym CLR.</span><span class="sxs-lookup"><span data-stu-id="dc15e-120">Executables that are compiled with the **/platform:anycpu** execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="dc15e-121">Pliki wykonywalne skompilowane z **/platform: anycpu32bitpreferred** wykonania na 32-bitowym CLR.</span><span class="sxs-lookup"><span data-stu-id="dc15e-121">Executables compiled with **/platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="dc15e-122">**Anycpu32bitpreferred** ustawienie jest prawidłowe tylko dla pliku wykonywalnego (. Pliki z rozszerzeniem EXE) który wymaga platformy .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="dc15e-122">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="dc15e-123">Aby uzyskać więcej informacji dotyczących tworzenia aplikacji do uruchamiania w systemie Windows 64-bitowym systemie operacyjnym, zobacz [aplikacji 64-bitowych](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="dc15e-123">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="dc15e-124">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dc15e-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="dc15e-125">Otwórz **właściwości** strony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="dc15e-125">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="dc15e-126">Kliknij przycisk **kompilacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="dc15e-126">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="dc15e-127">Modyfikowanie **platformy docelowej** właściwości oraz dla projektów przeznaczonych dla platformy .NET Framework 4.5, zaznacz lub wyczyść **preferowane jest 32-bitowych** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="dc15e-127">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>  
  
 <span data-ttu-id="dc15e-128">**Należy pamiętać, / platform** nie jest dostępna w środowisku projektowania w programie Visual C# Express.</span><span class="sxs-lookup"><span data-stu-id="dc15e-128">**Note /platform** is not available in the development environment in Visual C# Express.</span></span>  
  
 <span data-ttu-id="dc15e-129">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span><span class="sxs-lookup"><span data-stu-id="dc15e-129">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc15e-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc15e-130">Example</span></span>  
 <span data-ttu-id="dc15e-131">Poniższy przykład przedstawia użycie **/platform** opcję, aby określić, że aplikacja powinien być wykonywany przez środowisko CLR 64-bitowym na 64-bitowym systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="dc15e-131">The following example shows how to use the **/platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>  
  
```console  
csc /platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc15e-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc15e-132">See Also</span></span>  
 [<span data-ttu-id="dc15e-133">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="dc15e-133">C# Compiler Options</span></span>](index.md)  
 [<span data-ttu-id="dc15e-134">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="dc15e-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
