---
title: 'Porady: kompilacja zestawów wieloplikowych'
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
ms.openlocfilehash: 3072be4e870b64edcea32bb7159db8c64c50d840
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183103"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="83f08-102">Porady: kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="83f08-102">How to: Build a Multifile Assembly</span></span>
<span data-ttu-id="83f08-103">W tym artykule wyjaśniono, jak utworzyć zestaw wieloplikowy i zawiera kod, który ilustruje każdy krok w procedurze.</span><span class="sxs-lookup"><span data-stu-id="83f08-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83f08-104">Visual Studio IDE dla C# i Visual Basic należy używać tylko do tworzenia zespołów pojedynczego pliku.</span><span class="sxs-lookup"><span data-stu-id="83f08-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="83f08-105">Jeśli chcesz utworzyć zestawy wieloplikowe, musisz podać kompilatorów wiersza polecenia lub programu Visual Studio z programem Visual C++.</span><span class="sxs-lookup"><span data-stu-id="83f08-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span>  
  
### <a name="to-create-a-multifile-assembly"></a><span data-ttu-id="83f08-106">Aby utworzyć zestaw wieloplikowy</span><span class="sxs-lookup"><span data-stu-id="83f08-106">To create a multifile assembly</span></span>  
  
1.  <span data-ttu-id="83f08-107">Kompiluj wszystkie pliki zawierające przestrzenie nazw przywoływany przez inne moduły w zestawie do modułów kodu.</span><span class="sxs-lookup"><span data-stu-id="83f08-107">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="83f08-108">Domyślnym rozszerzeniem dla modułów kodu jest .netmodule.</span><span class="sxs-lookup"><span data-stu-id="83f08-108">The default extension for code modules is .netmodule.</span></span>  
  
     <span data-ttu-id="83f08-109">Na przykład, załóżmy, że `Stringer` plik ma przestrzeń nazwy wywołaną `myStringer`, która zawiera klasę o nazwie `Stringer`.</span><span class="sxs-lookup"><span data-stu-id="83f08-109">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="83f08-110">`Stringer` Klasa zawiera metodę o nazwie `StringerMethod` , zapisuje pojedynczy wiersz do konsoli.</span><span class="sxs-lookup"><span data-stu-id="83f08-110">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
     [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
     [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]  
  
     <span data-ttu-id="83f08-111">Użyj następującego polecenia, aby skompilować ten kod:</span><span class="sxs-lookup"><span data-stu-id="83f08-111">Use the following command to compile this code:</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
     [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
     [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]  
  
     <span data-ttu-id="83f08-112">Określanie *modułu* parametrem **t:** opcji kompilatora wskazuje, że pliku powinna być skompilowana jako moduł, a nie jako zespół.</span><span class="sxs-lookup"><span data-stu-id="83f08-112">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="83f08-113">Kompilator generuje moduł o nazwie `Stringer.netmodule`, który może być dodany do zestawu.</span><span class="sxs-lookup"><span data-stu-id="83f08-113">The compiler produces a module called `Stringer.netmodule`, which can be added to an assembly.</span></span>  
  
2.  <span data-ttu-id="83f08-114">Kompiluj wszystkie inne moduły, stosując niezbędne opcje kompilatora w celu wskazania innych modułów, do których istnieją odwołania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="83f08-114">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="83f08-115">Ten krok używa **/addmodule** — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="83f08-115">This step uses the **/addmodule** compiler option.</span></span>  
  
     <span data-ttu-id="83f08-116">W poniższym przykładzie moduł kodu o nazwie `Client` ma punkt wejścia `Main` metodę, która odwołuje się do metody w `Stringer.dll` modułu utworzonego w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="83f08-116">In the following example, a code module called `Client` has an entry point `Main` method that references a method in the `Stringer.dll` module created in step 1.</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
     [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
     [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]  
  
     <span data-ttu-id="83f08-117">Użyj następującego polecenia, aby skompilować ten kod:</span><span class="sxs-lookup"><span data-stu-id="83f08-117">Use the following command to compile this code:</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
     [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
     [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]  
  
     <span data-ttu-id="83f08-118">Określ **/t:module** opcji, ponieważ ten moduł zostanie dodany do zestawu w przyszłym kroku.</span><span class="sxs-lookup"><span data-stu-id="83f08-118">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="83f08-119">Określ **/addmodule** opcji, ponieważ kod w `Client` odwołuje się do przestrzeni nazwy utworzonej przez kod w `Stringer.netmodule`.</span><span class="sxs-lookup"><span data-stu-id="83f08-119">Specify the **/addmodule** option because the code in `Client` references a namespace created by the code in `Stringer.netmodule`.</span></span> <span data-ttu-id="83f08-120">Kompilator generuje moduł o nazwie `Client.netmodule` zawiera odwołanie do innego modułu `Stringer.netmodule`.</span><span class="sxs-lookup"><span data-stu-id="83f08-120">The compiler produces a module called `Client.netmodule` that contains a reference to another module, `Stringer.netmodule`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="83f08-121">C# I Kompilatory języka Visual Basic obsługują bezpośrednio tworzenie zespołów wieloplikowych przy użyciu następujących dwóch różnych składni.</span><span class="sxs-lookup"><span data-stu-id="83f08-121">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>  
    >   
    >  -   <span data-ttu-id="83f08-122">Dwie kompilacje tworzą zestaw dwóch plików:</span><span class="sxs-lookup"><span data-stu-id="83f08-122">Two compilations create a two-file assembly:</span></span>  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
      [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
      [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]  
    > -   <span data-ttu-id="83f08-123">Jeden Kompilacja tworzy zestaw dwóch plików:</span><span class="sxs-lookup"><span data-stu-id="83f08-123">One compilation creates a two-file assembly:</span></span>  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
      [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
      [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]  
  
3.  <span data-ttu-id="83f08-124">Użyj [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) do tworzenia pliku wyjściowego, który zawiera manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="83f08-124">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="83f08-125">Ten plik zawiera informacje dotyczące wszystkich modułów lub zasobów, które są częścią zestawu.</span><span class="sxs-lookup"><span data-stu-id="83f08-125">This file contains reference information for all modules or resources that are part of the assembly.</span></span>  
  
     <span data-ttu-id="83f08-126">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="83f08-126">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="83f08-127">**Al** \< *Nazwa modułu*> \<*Nazwa modułu*>...</span><span class="sxs-lookup"><span data-stu-id="83f08-127">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="83f08-128">**/ main:**\<*nazwę metody*> **/out:**\<*nazwy pliku*>   **/target :**\<*typ pliku zestawu*></span><span class="sxs-lookup"><span data-stu-id="83f08-128">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>  
  
     <span data-ttu-id="83f08-129">W tym poleceniu *Nazwa modułu* argumenty określają nazwę każdego modułu, aby uwzględnić w zestawie.</span><span class="sxs-lookup"><span data-stu-id="83f08-129">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="83f08-130">**/Main:** opcja określa nazwę metody punktu wejścia w zestawie.</span><span class="sxs-lookup"><span data-stu-id="83f08-130">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="83f08-131">**/Out:** opcja określa nazwę pliku wyjściowego, który zawiera metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="83f08-131">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="83f08-132">**/Target:** opcja określa, że zestaw jest plik wykonywalny (.exe) aplikacji konsoli, plikiem wykonywalnym (.exe) Windows lub plikiem biblioteki (.lib).</span><span class="sxs-lookup"><span data-stu-id="83f08-132">The **/target:** option specifies that the assembly is a console application executable (.exe) file, a Windows executable (.win) file, or a library (.lib) file.</span></span>  
  
     <span data-ttu-id="83f08-133">W poniższym przykładzie Al.exe tworzy zestaw, który jest wykonywalną aplikacją konsoli o nazwie `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="83f08-133">In the following example, Al.exe creates an assembly that is a console application executable called `myAssembly.exe`.</span></span> <span data-ttu-id="83f08-134">Aplikacja składa się z dwóch modułów o nazwie `Client.netmodule` i `Stringer.netmodule`, a pliku wykonywalnego o nazwie `myAssembly.exe,` zawierającą tylko metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="83f08-134">The application consists of two modules called `Client.netmodule` and `Stringer.netmodule`, and the executable file called `myAssembly.exe,` which contains only assembly metadata.</span></span> <span data-ttu-id="83f08-135">Punkt wejścia zestawu jest `Main` metody w klasie `MainClientApp`, który znajduje się w `Client.dll`.</span><span class="sxs-lookup"><span data-stu-id="83f08-135">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in `Client.dll`.</span></span>  
  
    ```  
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe   
    ```  
  
     <span data-ttu-id="83f08-136">Możesz użyć [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) Aby sprawdzić zawartość zestawu lub określić, czy plik jest zestawem lub modułem.</span><span class="sxs-lookup"><span data-stu-id="83f08-136">You can use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f08-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83f08-137">See Also</span></span>  
- [<span data-ttu-id="83f08-138">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="83f08-138">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
- [<span data-ttu-id="83f08-139">Instrukcje: wyświetlanie zawartości zestawu</span><span class="sxs-lookup"><span data-stu-id="83f08-139">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
- [<span data-ttu-id="83f08-140">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="83f08-140">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [<span data-ttu-id="83f08-141">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="83f08-141">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
