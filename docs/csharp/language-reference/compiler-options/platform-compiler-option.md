---
title: -platform (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 5150e871d75c3c34dab10f10cdac3d8322d7a834
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70849869"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="0fe7b-102">-platform (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="0fe7b-102">-platform (C# Compiler Options)</span></span>

<span data-ttu-id="0fe7b-103">Określa, która wersja common language runtime (CLR) może uruchomić zestaw.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-103">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>

## <a name="syntax"></a><span data-ttu-id="0fe7b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fe7b-104">Syntax</span></span>

```console
-platform:string
```

## <a name="parameters"></a><span data-ttu-id="0fe7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0fe7b-105">Parameters</span></span>

`string` \
<span data-ttu-id="0fe7b-106">anycpu (domyślnie), anycpu32bitpreferred, ARM, x64, x86 lub Itanium.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>

## <a name="remarks"></a><span data-ttu-id="0fe7b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0fe7b-107">Remarks</span></span>

- <span data-ttu-id="0fe7b-108">**anycpu** (domyślnie) kompiluje zestawu do uruchomienia na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="0fe7b-109">Aplikacja jest uruchamiana jako proces 64-bitowy, gdy jest to możliwe i powraca do 32-bitowych, gdy tylko ten tryb jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>

- <span data-ttu-id="0fe7b-110">**anycpu32bitpreferred** kompiluje swój zestaw do uruchamiania na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="0fe7b-111">Aplikacja działa w trybie 32-bitowym w systemach obsługujących zarówno aplikacje 64-bitowe, jak i 32-bitowe.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="0fe7b-112">Tę opcję można określić tylko dla projektów, które są przeznaczone dla .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>

- <span data-ttu-id="0fe7b-113">**ARM** kompiluje zestaw do uruchamiania na komputerze z procesorem ARM (Advanced RISC Machine).</span><span class="sxs-lookup"><span data-stu-id="0fe7b-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>

- <span data-ttu-id="0fe7b-114">**ARM64** kompiluje zestaw do uruchamiania przez 64-bitowy clr na komputerze z procesorem Advanced RISC Machine (ARM), który obsługuje zestaw instrukcji A64.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-114">**ARM64** compiles your assembly to run by the 64-bit CLR on a computer that has an Advanced RISC Machine (ARM) processor that supports the A64 instruction set.</span></span>

- <span data-ttu-id="0fe7b-115">**x64** kompiluje swój zestaw do uruchomienia przez 64-bitowy clr na komputerze obsługującym zestaw instrukcji AMD64 lub EM64T.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-115">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>

- <span data-ttu-id="0fe7b-116">**x86** kompiluje swój zestaw do uruchomienia przez 32-bitowy, zgodny z x86 CLR.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-116">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>

- <span data-ttu-id="0fe7b-117">**Itanium** kompiluje swój zestaw do uruchomienia przez 64-bitowy CLR na komputerze z procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-117">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>

<span data-ttu-id="0fe7b-118">W 64-bitowym systemie operacyjnym Windows:</span><span class="sxs-lookup"><span data-stu-id="0fe7b-118">On a 64-bit Windows operating system:</span></span>

- <span data-ttu-id="0fe7b-119">Zestawy skompilowane z **-platform:x86** wykonać na 32-bitowej clr działa w ramach WOW64.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-119">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>

- <span data-ttu-id="0fe7b-120">DLL skompilowany z **-platform:anycpu** wykonuje na tym samym CLR jako proces, do którego jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-120">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>

- <span data-ttu-id="0fe7b-121">Pliki wykonywalne, które są kompilowane z **-platform:anycpu** wykonać na 64-bitowy CLR.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-121">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>

- <span data-ttu-id="0fe7b-122">Pliki wykonywalne skompilowane z **-platform:anycpu32bitpreferred** wykonać na 32-bitowym CLR.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-122">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>

<span data-ttu-id="0fe7b-123">Ustawienie **anycpu32bitpreferred** jest ważne tylko dla pliku wykonywalnego (. EXE) i wymaga .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-123">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>

<span data-ttu-id="0fe7b-124">Aby uzyskać więcej informacji na temat tworzenia aplikacji do uruchamiania w systemie operacyjnym Windows 64-bitowy, zobacz [Aplikacje 64-bitowe](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="0fe7b-124">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="0fe7b-125">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0fe7b-125">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="0fe7b-126">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-126">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="0fe7b-127">Kliknij stronę **Właściwości kompilacji.**</span><span class="sxs-lookup"><span data-stu-id="0fe7b-127">Click the **Build** property page.</span></span>

3. <span data-ttu-id="0fe7b-128">Zmodyfikuj **właściwość docelową platformy** i w przypadku projektów docelowych programu .NET Framework 4.5 zaznacz lub wyczyść pole wyboru **Preferuj 32-bitowe.**</span><span class="sxs-lookup"><span data-stu-id="0fe7b-128">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>

> [!NOTE]
> <span data-ttu-id="0fe7b-129">`-platform`nie jest dostępna w środowisku programistycznym w programie Visual C# Express.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-129">`-platform` is not available in the development environment in Visual C# Express.</span></span>

<span data-ttu-id="0fe7b-130">Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="0fe7b-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>

## <a name="example"></a><span data-ttu-id="0fe7b-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="0fe7b-131">Example</span></span>

<span data-ttu-id="0fe7b-132">W poniższym przykładzie pokazano, jak użyć opcji **-platform,** aby określić, że aplikacja powinna być uruchamiana przez 64-bitowy clr w 64-bitowym systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="0fe7b-132">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>

```console
csc -platform:anycpu filename.cs
```

## <a name="see-also"></a><span data-ttu-id="0fe7b-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fe7b-133">See also</span></span>

- [<span data-ttu-id="0fe7b-134">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="0fe7b-134">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="0fe7b-135">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="0fe7b-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
