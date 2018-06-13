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
ms.openlocfilehash: 916db7ec9bee0c85db1f2fcf4db7a9f8a61f9be3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744086"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="03d9a-102">Porady: kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="03d9a-102">How to: Build a Multifile Assembly</span></span>
<span data-ttu-id="03d9a-103">W tym artykule opisano sposób tworzenia zestawów wieloplikowych i zawiera kod, który przedstawia każdego kroku w procedurze.</span><span class="sxs-lookup"><span data-stu-id="03d9a-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03d9a-104">Aby utworzyć zestawy jednoplikowe można tylko programu Visual Studio IDE języka C# i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="03d9a-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="03d9a-105">Jeśli chcesz utworzyć zestawy wieloplikowe muszą używać kompilatory w wierszu polecenia lub programu Visual Studio z programem Visual C++.</span><span class="sxs-lookup"><span data-stu-id="03d9a-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span>  
  
### <a name="to-create-a-multifile-assembly"></a><span data-ttu-id="03d9a-106">Aby utworzyć zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="03d9a-106">To create a multifile assembly</span></span>  
  
1.  <span data-ttu-id="03d9a-107">Kompiluj wszystkie pliki, które zawierają odwołuje się innych modułów w zestawie do modułów kodu przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="03d9a-107">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="03d9a-108">Domyślne rozszerzenie dla modułów kodu jest modułu .netmodule.</span><span class="sxs-lookup"><span data-stu-id="03d9a-108">The default extension for code modules is .netmodule.</span></span>  
  
     <span data-ttu-id="03d9a-109">Na przykład, załóżmy, że `Stringer` plik ma przestrzeń nazw o nazwie `myStringer`, która obejmuje klasy o nazwie `Stringer`.</span><span class="sxs-lookup"><span data-stu-id="03d9a-109">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="03d9a-110">`Stringer` Klasa zawiera metodę o nazwie `StringerMethod` który zapisuje pojedynczy wiersz do konsoli.</span><span class="sxs-lookup"><span data-stu-id="03d9a-110">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
     [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
     [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]  
  
     <span data-ttu-id="03d9a-111">Użyj następującego polecenia, aby skompilować ten kod:</span><span class="sxs-lookup"><span data-stu-id="03d9a-111">Use the following command to compile this code:</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
     [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
     [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]  
  
     <span data-ttu-id="03d9a-112">Określanie *modułu* parametr o **/t:** — opcja kompilatora wskazuje, że plik ma być kompilowana jako moduł, a nie jako do zestawu.</span><span class="sxs-lookup"><span data-stu-id="03d9a-112">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="03d9a-113">Kompilator generuje modułu o nazwie `Stringer.netmodule`, które mogą być dodane do zestawu.</span><span class="sxs-lookup"><span data-stu-id="03d9a-113">The compiler produces a module called `Stringer.netmodule`, which can be added to an assembly.</span></span>  
  
2.  <span data-ttu-id="03d9a-114">Kompiluj wszystkie inne moduły, przy użyciu opcji kompilatora niezbędne wskazująca modułów, które są używane w kodzie.</span><span class="sxs-lookup"><span data-stu-id="03d9a-114">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="03d9a-115">Ten krok używa **/addmodule** — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="03d9a-115">This step uses the **/addmodule** compiler option.</span></span>  
  
     <span data-ttu-id="03d9a-116">W poniższym przykładzie modułu kodu o nazwie `Client` ma punkt wejścia `Main` metodę, która odwołuje się do metody w `Stringer.dll` modułu utworzonego w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="03d9a-116">In the following example, a code module called `Client` has an entry point `Main` method that references a method in the `Stringer.dll` module created in step 1.</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
     [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
     [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]  
  
     <span data-ttu-id="03d9a-117">Użyj następującego polecenia, aby skompilować ten kod:</span><span class="sxs-lookup"><span data-stu-id="03d9a-117">Use the following command to compile this code:</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
     [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
     [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]  
  
     <span data-ttu-id="03d9a-118">Określ **/t:module** opcja, ponieważ ten moduł zostaną dodane do zestawu w przyszłości kroku.</span><span class="sxs-lookup"><span data-stu-id="03d9a-118">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="03d9a-119">Określ **/addmodule** opcja, ponieważ kod w `Client` odwołuje się do przestrzeni nazw tworzona przez kod w `Stringer.netmodule`.</span><span class="sxs-lookup"><span data-stu-id="03d9a-119">Specify the **/addmodule** option because the code in `Client` references a namespace created by the code in `Stringer.netmodule`.</span></span> <span data-ttu-id="03d9a-120">Kompilator generuje modułu o nazwie `Client.netmodule` zawiera odwołanie do innego modułu `Stringer.netmodule`.</span><span class="sxs-lookup"><span data-stu-id="03d9a-120">The compiler produces a module called `Client.netmodule` that contains a reference to another module, `Stringer.netmodule`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="03d9a-121">C# i Visual Basic kompilatory obsługuje tworzenie bezpośrednio za pomocą następujących dwóch składnie zestawy wieloplikowe.</span><span class="sxs-lookup"><span data-stu-id="03d9a-121">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>  
    >   
    >  -   <span data-ttu-id="03d9a-122">Dwie kompilacje utworzyć dwa pliku zestawu:</span><span class="sxs-lookup"><span data-stu-id="03d9a-122">Two compilations create a two-file assembly:</span></span>  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
      [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
      [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]  
    > -   <span data-ttu-id="03d9a-123">Kompilacja co tworzy zestaw dwóch plików:</span><span class="sxs-lookup"><span data-stu-id="03d9a-123">One compilation creates a two-file assembly:</span></span>  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
      [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
      [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]  
  
3.  <span data-ttu-id="03d9a-124">Użyj [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) można utworzyć pliku wyjściowego, który zawiera manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="03d9a-124">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="03d9a-125">Ten plik zawiera informacje dotyczące wszystkich modułów lub zasobów, które są częścią zestawu.</span><span class="sxs-lookup"><span data-stu-id="03d9a-125">This file contains reference information for all modules or resources that are part of the assembly.</span></span>  
  
     <span data-ttu-id="03d9a-126">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="03d9a-126">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="03d9a-127">**Al** \< *nazwy modułu*> \<*nazwy modułu*>...</span><span class="sxs-lookup"><span data-stu-id="03d9a-127">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="03d9a-128">**/ main:**\<*nazwę metody*> **/out:**\<*nazwę pliku*>   **/target :**\<*typ pliku zestawu*></span><span class="sxs-lookup"><span data-stu-id="03d9a-128">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>  
  
     <span data-ttu-id="03d9a-129">W tym poleceniu *nazwy modułu* argumenty określają nazwę każdego modułu do uwzględnienia w zestawie.</span><span class="sxs-lookup"><span data-stu-id="03d9a-129">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="03d9a-130">**/Main:** opcji określa nazwę metody, która jest punkt wejścia w zestawie.</span><span class="sxs-lookup"><span data-stu-id="03d9a-130">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="03d9a-131">**/Out:** opcji określa nazwę pliku wyjściowego, który zawiera metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="03d9a-131">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="03d9a-132">**/Target:** opcja określa, że zestaw jest plik wykonywalny (.exe) aplikacji konsoli, plik wykonywalny (.win) systemu Windows lub pliku biblioteki (lib).</span><span class="sxs-lookup"><span data-stu-id="03d9a-132">The **/target:** option specifies that the assembly is a console application executable (.exe) file, a Windows executable (.win) file, or a library (.lib) file.</span></span>  
  
     <span data-ttu-id="03d9a-133">W poniższym przykładzie Al.exe tworzy zestawu, który jest plik wykonywalny aplikacji konsoli o nazwie `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="03d9a-133">In the following example, Al.exe creates an assembly that is a console application executable called `myAssembly.exe`.</span></span> <span data-ttu-id="03d9a-134">Aplikacja składa się z dwóch modułów o nazwie `Client.netmodule` i `Stringer.netmodule`, i wywołać plik wykonywalny `myAssembly.exe,` zawierającą tylko metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="03d9a-134">The application consists of two modules called `Client.netmodule` and `Stringer.netmodule`, and the executable file called `myAssembly.exe,` which contains only assembly metadata .</span></span> <span data-ttu-id="03d9a-135">Punkt wejścia zestawu jest `Main` metody w klasie `MainClientApp`, który znajduje się w `Client.dll`.</span><span class="sxs-lookup"><span data-stu-id="03d9a-135">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in `Client.dll`.</span></span>  
  
    ```  
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe   
    ```  
  
     <span data-ttu-id="03d9a-136">Można użyć [dezasembler MSIL (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) Sprawdź zawartość zestawu lub określanie, czy plik jest zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="03d9a-136">You can use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03d9a-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03d9a-137">See Also</span></span>  
 [<span data-ttu-id="03d9a-138">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="03d9a-138">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="03d9a-139">Instrukcje: wyświetlanie zawartości zestawu</span><span class="sxs-lookup"><span data-stu-id="03d9a-139">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 [<span data-ttu-id="03d9a-140">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="03d9a-140">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="03d9a-141">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="03d9a-141">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
