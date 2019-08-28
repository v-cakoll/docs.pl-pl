---
title: 'Instrukcje: Kompilacja zestawów wieloplikowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a964e73cc41cebad33a3edc34b89ef240fbc62c8
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040855"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="88a7b-102">Instrukcje: Kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="88a7b-102">How to: Build a Multifile Assembly</span></span>

<span data-ttu-id="88a7b-103">W tym artykule opisano sposób tworzenia zestawu wieloplikowego i zawiera kod, który ilustruje każdy krok w procedurze.</span><span class="sxs-lookup"><span data-stu-id="88a7b-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="88a7b-104">Środowisko IDE programu Visual Studio C# dla i Visual Basic może być używane tylko do tworzenia zestawów jednoplikowych.</span><span class="sxs-lookup"><span data-stu-id="88a7b-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="88a7b-105">Jeśli chcesz utworzyć zestawy wieloplikowe, musisz użyć kompilatorów wiersza polecenia lub programu Visual Studio z wizualizacją C++.</span><span class="sxs-lookup"><span data-stu-id="88a7b-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span>

### <a name="to-create-a-multifile-assembly"></a><span data-ttu-id="88a7b-106">Aby utworzyć zestaw wieloplikowy</span><span class="sxs-lookup"><span data-stu-id="88a7b-106">To create a multifile assembly</span></span>

01. <span data-ttu-id="88a7b-107">Kompiluj wszystkie pliki, które zawierają przestrzenie nazw, do których odwołują się inne moduły w zestawie, do modułów kodu.</span><span class="sxs-lookup"><span data-stu-id="88a7b-107">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="88a7b-108">Domyślnym rozszerzeniem modułów kodu jest. module.</span><span class="sxs-lookup"><span data-stu-id="88a7b-108">The default extension for code modules is .netmodule.</span></span>

    <span data-ttu-id="88a7b-109">Załóżmy na przykład, że `Stringer` plik ma przestrzeń nazw o nazwie `myStringer`, która zawiera klasę o nazwie `Stringer`.</span><span class="sxs-lookup"><span data-stu-id="88a7b-109">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="88a7b-110">Klasa zawiera metodę o nazwie `StringerMethod` , która zapisuje jeden wiersz w konsoli. `Stringer`</span><span class="sxs-lookup"><span data-stu-id="88a7b-110">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>

    [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
    [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
    [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]

    <span data-ttu-id="88a7b-111">Użyj następującego polecenia, aby skompilować ten kod:</span><span class="sxs-lookup"><span data-stu-id="88a7b-111">Use the following command to compile this code:</span></span>

    [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
    [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
    [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]

    <span data-ttu-id="88a7b-112">Określenie parametru *modułu* z opcją **/t:** kompilator wskazuje, że plik powinien zostać skompilowany jako moduł, a nie jako zestaw.</span><span class="sxs-lookup"><span data-stu-id="88a7b-112">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="88a7b-113">Kompilator tworzy moduł o nazwie `Stringer.netmodule`, który można dodać do zestawu.</span><span class="sxs-lookup"><span data-stu-id="88a7b-113">The compiler produces a module called `Stringer.netmodule`, which can be added to an assembly.</span></span>

02. <span data-ttu-id="88a7b-114">Kompiluj wszystkie inne moduły przy użyciu niezbędnych opcji kompilatora, aby wskazać inne moduły, do których istnieją odwołania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="88a7b-114">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="88a7b-115">W tym kroku jest stosowana opcja kompilatora **/addmodule** .</span><span class="sxs-lookup"><span data-stu-id="88a7b-115">This step uses the **/addmodule** compiler option.</span></span>

    <span data-ttu-id="88a7b-116">W poniższym przykładzie moduł kodu o nazwie `Client` ma metodę punktu `Main` wejścia, która `Stringer.dll` odwołuje się do metody w module utworzonym w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="88a7b-116">In the following example, a code module called `Client` has an entry point `Main` method that references a method in the `Stringer.dll` module created in step 1.</span></span>

    [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
    [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
    [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]

    <span data-ttu-id="88a7b-117">Użyj następującego polecenia, aby skompilować ten kod:</span><span class="sxs-lookup"><span data-stu-id="88a7b-117">Use the following command to compile this code:</span></span>

    [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
    [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
    [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]

    <span data-ttu-id="88a7b-118">Określ opcję **/t: module** , ponieważ ten moduł zostanie dodany do zestawu w przyszłym kroku.</span><span class="sxs-lookup"><span data-stu-id="88a7b-118">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="88a7b-119">Określ opcję **/addmodule** , ponieważ kod w `Client` odwołuje się do przestrzeni nazw utworzonej przez kod w. `Stringer.netmodule`</span><span class="sxs-lookup"><span data-stu-id="88a7b-119">Specify the **/addmodule** option because the code in `Client` references a namespace created by the code in `Stringer.netmodule`.</span></span> <span data-ttu-id="88a7b-120">Kompilator tworzy moduł o nazwie `Client.netmodule` , który zawiera odwołanie do innego `Stringer.netmodule`modułu.</span><span class="sxs-lookup"><span data-stu-id="88a7b-120">The compiler produces a module called `Client.netmodule` that contains a reference to another module, `Stringer.netmodule`.</span></span>

    >[!NOTE]
    ><span data-ttu-id="88a7b-121">Kompilatory C# i Visual Basic obsługują bezpośrednie tworzenie zestawów wieloplikowych przy użyciu następujących dwóch różnych składni.</span><span class="sxs-lookup"><span data-stu-id="88a7b-121">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>
    >
    >- <span data-ttu-id="88a7b-122">Dwie kompilacje tworzą zestaw dwóch plików:[!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]</span><span class="sxs-lookup"><span data-stu-id="88a7b-122">Two compilations create a two-file assembly: [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]</span></span>
    >  [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
    >  [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]
    >
    >- <span data-ttu-id="88a7b-123">Jedna kompilacja tworzy zestaw dwóch plików:[!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]</span><span class="sxs-lookup"><span data-stu-id="88a7b-123">One compilation creates a two-file assembly: [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]</span></span>
    >  [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
    >  [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]

03. <span data-ttu-id="88a7b-124">Użyj [konsolidatora zestawu (Al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) , aby utworzyć plik wyjściowy, który zawiera manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="88a7b-124">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="88a7b-125">Ten plik zawiera informacje referencyjne dotyczące wszystkich modułów lub zasobów, które są częścią zestawu.</span><span class="sxs-lookup"><span data-stu-id="88a7b-125">This file contains reference information for all modules or resources that are part of the assembly.</span></span>

    <span data-ttu-id="88a7b-126">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="88a7b-126">At the command prompt, type the following command:</span></span>

    <span data-ttu-id="88a7b-127">\**Al\*\*\*Nazwa*modułunazw> modułów>... \<\<</span><span class="sxs-lookup"><span data-stu-id="88a7b-127">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="88a7b-128">**/Main:** \<*Nazwa\*\*\*metody/out:*\* nazwa pliku/Target:\<*Typ pliku* zestawu\<> > ></span><span class="sxs-lookup"><span data-stu-id="88a7b-128">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>

    <span data-ttu-id="88a7b-129">W tym poleceniu argumenty *nazwy modułu* określają nazwę każdego modułu, który ma zostać uwzględniony w zestawie.</span><span class="sxs-lookup"><span data-stu-id="88a7b-129">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="88a7b-130">**/Main:** opcja określa nazwę metody, która jest punktem wejścia zestawu.</span><span class="sxs-lookup"><span data-stu-id="88a7b-130">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="88a7b-131">**/Out:** opcja określa nazwę pliku wyjściowego, który zawiera metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="88a7b-131">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="88a7b-132">**/Target:** opcja określa, że zestaw to plik wykonywalny aplikacji konsoli (exe), plik wykonywalny systemu Windows (. win) lub plik biblioteki (. lib).</span><span class="sxs-lookup"><span data-stu-id="88a7b-132">The **/target:** option specifies that the assembly is a console application executable (.exe) file, a Windows executable (.win) file, or a library (.lib) file.</span></span>

    <span data-ttu-id="88a7b-133">W poniższym przykładzie Al. exe tworzy zestaw, który jest plikiem wykonywalnym aplikacji konsoli o nazwie `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="88a7b-133">In the following example, Al.exe creates an assembly that is a console application executable called `myAssembly.exe`.</span></span> <span data-ttu-id="88a7b-134">Aplikacja składa się z dwóch modułów `Client.netmodule` o `Stringer.netmodule`nazwie i, a plik wykonywalny o nazwie `myAssembly.exe,` , który zawiera tylko metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="88a7b-134">The application consists of two modules called `Client.netmodule` and `Stringer.netmodule`, and the executable file called `myAssembly.exe,` which contains only assembly metadata.</span></span> <span data-ttu-id="88a7b-135">Punkt wejścia zestawu jest `Main` metodą w klasie `MainClientApp`, która znajduje się w `Client.dll`.</span><span class="sxs-lookup"><span data-stu-id="88a7b-135">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in `Client.dll`.</span></span>

    ```
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    <span data-ttu-id="88a7b-136">Aby sprawdzić zawartość zestawu lub określić, czy plik jest zestawem lub modułem, można użyć [Dezasembler MSIL (Ildasm. exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) .</span><span class="sxs-lookup"><span data-stu-id="88a7b-136">You can use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>

## <a name="see-also"></a><span data-ttu-id="88a7b-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88a7b-137">See also</span></span>

- [<span data-ttu-id="88a7b-138">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="88a7b-138">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="88a7b-139">Instrukcje: Wyświetl zawartość zestawu</span><span class="sxs-lookup"><span data-stu-id="88a7b-139">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)
- [<span data-ttu-id="88a7b-140">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="88a7b-140">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="88a7b-141">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="88a7b-141">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
