---
title: 'Instrukcje: tworzenie zestawów wieloplikowych'
description: Dowiedz się, jak skompilować (utworzyć) zestaw wieloplikowy w programie .NET przy użyciu przykładowego kodu, aby zilustrować każdy krok w procedurze.
ms.date: 08/20/2019
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
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
ms.openlocfilehash: a4c298284950ba2989bb73e6d3383b3c4024e6e7
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104944"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="6064b-103">Instrukcje: tworzenie zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="6064b-103">How to: Build a multifile assembly</span></span>

<span data-ttu-id="6064b-104">W tym artykule opisano sposób tworzenia zestawu wieloplikowego i zawiera kod, który ilustruje każdy krok w procedurze.</span><span class="sxs-lookup"><span data-stu-id="6064b-104">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="6064b-105">Środowisko IDE programu Visual Studio dla języka C# i Visual Basic może być używane tylko do tworzenia zestawów jednoplikowych.</span><span class="sxs-lookup"><span data-stu-id="6064b-105">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="6064b-106">Jeśli chcesz utworzyć zestawy wieloplikowe, musisz użyć kompilatorów wiersza polecenia lub programu Visual Studio z Visual C++.</span><span class="sxs-lookup"><span data-stu-id="6064b-106">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="6064b-107">Zestawy wieloplikowe są obsługiwane tylko przez .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6064b-107">Multifile assemblies are supported by .NET Framework only.</span></span>

## <a name="create-a-multifile-assembly"></a><span data-ttu-id="6064b-108">Tworzenie zestawu wieloplikowego</span><span class="sxs-lookup"><span data-stu-id="6064b-108">Create a multifile assembly</span></span>

1. <span data-ttu-id="6064b-109">Kompiluj wszystkie pliki, które zawierają przestrzenie nazw, do których odwołują się inne moduły w zestawie, do modułów kodu.</span><span class="sxs-lookup"><span data-stu-id="6064b-109">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="6064b-110">Domyślnym rozszerzeniem modułów kodu jest *. module*.</span><span class="sxs-lookup"><span data-stu-id="6064b-110">The default extension for code modules is *.netmodule*.</span></span>

   <span data-ttu-id="6064b-111">Załóżmy na przykład, że `Stringer` plik ma przestrzeń nazw o nazwie `myStringer` , która zawiera klasę o nazwie `Stringer` .</span><span class="sxs-lookup"><span data-stu-id="6064b-111">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="6064b-112">`Stringer`Klasa zawiera metodę o nazwie `StringerMethod` , która zapisuje jeden wiersz w konsoli.</span><span class="sxs-lookup"><span data-stu-id="6064b-112">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>

   ```cpp
   // Assembly building example in the .NET Framework.
   using namespace System;

   namespace myStringer
   {
       public ref class Stringer
       {
       public:
           void StringerMethod()
           {
               System::Console::WriteLine("This is a line from StringerMethod.");
           }
       };
   }
   ```

   ```csharp
   // Assembly building example in the .NET Framework.
   using System;

   namespace myStringer
   {
       public class Stringer
       {
           public void StringerMethod()
           {
               System.Console.WriteLine("This is a line from StringerMethod.");
           }
       }
   }
   ```

   ```vb
   ' Assembly building example in the .NET Framework.
   Namespace myStringer
       Public Class Stringer
           Public Sub StringerMethod()
               System.Console.WriteLine("This is a line from StringerMethod.")
           End Sub
       End Class
   End Namespace
   ```

2. <span data-ttu-id="6064b-113">Użyj następującego polecenia, aby skompilować ten kod:</span><span class="sxs-lookup"><span data-stu-id="6064b-113">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /LN Stringer.cpp
   ```

   ```csharp
   csc /t:module Stringer.cs
   ```

   ```vb
   vbc /t:module Stringer.vb
   ```

   <span data-ttu-id="6064b-114">Określenie parametru *modułu* z opcją **/t:** kompilator wskazuje, że plik powinien zostać skompilowany jako moduł, a nie jako zestaw.</span><span class="sxs-lookup"><span data-stu-id="6064b-114">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="6064b-115">Kompilator tworzy moduł o nazwie *Stringer. webmodule*, który można dodać do zestawu.</span><span class="sxs-lookup"><span data-stu-id="6064b-115">The compiler produces a module called *Stringer.netmodule*, which can be added to an assembly.</span></span>

3. <span data-ttu-id="6064b-116">Kompiluj wszystkie inne moduły przy użyciu niezbędnych opcji kompilatora, aby wskazać inne moduły, do których istnieją odwołania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6064b-116">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="6064b-117">W tym kroku jest stosowana opcja kompilatora **/addmodule** .</span><span class="sxs-lookup"><span data-stu-id="6064b-117">This step uses the **/addmodule** compiler option.</span></span>

   <span data-ttu-id="6064b-118">W poniższym przykładzie moduł kodu o nazwie *Client* ma metodę punktu wejścia `Main` , która odwołuje się do metody w module *Stringer.dll* utworzonym w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="6064b-118">In the following example, a code module called *Client* has an entry point `Main` method that references a method in the *Stringer.dll* module created in step 1.</span></span>

   ```cpp
   #using "Stringer.netmodule"

   using namespace System;
   using namespace myStringer; //The namespace created in Stringer.netmodule.

   ref class MainClientApp
   {
       // Static method Main is the entry point method.
   public:
       static void Main()
       {
           Stringer^ myStringInstance = gcnew Stringer();
           Console::WriteLine("Client code executes");
           myStringInstance->StringerMethod();
       }
   };

   int main()
   {
       MainClientApp::Main();
   }
   ```

   ```csharp
   using System;
   using myStringer;

   class MainClientApp
   {
       // Static method Main is the entry point method.
       public static void Main()
       {
           Stringer myStringInstance = new Stringer();
           Console.WriteLine("Client code executes");
           myStringInstance.StringerMethod();
       }
   }
   ```

   ```vb
   Imports myStringer

   Class MainClientApp
       ' Static method Main is the entry point method.
       Public Shared Sub Main()
           Dim myStringInstance As New Stringer()
           Console.WriteLine("Client code executes")
           myStringInstance.StringerMethod()
       End Sub
   End Class
   ```

4. <span data-ttu-id="6064b-119">Użyj następującego polecenia, aby skompilować ten kod:</span><span class="sxs-lookup"><span data-stu-id="6064b-119">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /FUStringer.netmodule /LN Client.cpp
   ```

   ```csharp
   csc /addmodule:Stringer.netmodule /t:module Client.cs
   ```

   ```vb
   vbc /addmodule:Stringer.netmodule /t:module Client.vb
   ```

   <span data-ttu-id="6064b-120">Określ opcję **/t: module** , ponieważ ten moduł zostanie dodany do zestawu w przyszłym kroku.</span><span class="sxs-lookup"><span data-stu-id="6064b-120">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="6064b-121">Określ opcję **/addmodule** , ponieważ kod w *kliencie* odwołuje się do przestrzeni nazw utworzonej przez kod w *Stringer. module*.</span><span class="sxs-lookup"><span data-stu-id="6064b-121">Specify the **/addmodule** option because the code in *Client* references a namespace created by the code in *Stringer.netmodule*.</span></span> <span data-ttu-id="6064b-122">Kompilator generuje moduł o nazwie *Client. webmodule* , który zawiera odwołanie do innego modułu, *Stringer. webmodule*.</span><span class="sxs-lookup"><span data-stu-id="6064b-122">The compiler produces a module called *Client.netmodule* that contains a reference to another module, *Stringer.netmodule*.</span></span>

   > [!NOTE]
   > <span data-ttu-id="6064b-123">Kompilatory C# i Visual Basic obsługują bezpośrednie tworzenie zestawów wieloplikowych przy użyciu następujących dwóch różnych składni.</span><span class="sxs-lookup"><span data-stu-id="6064b-123">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>
   >
   > <span data-ttu-id="6064b-124">Dwie kompilacje tworzą zestaw dwóch plików:</span><span class="sxs-lookup"><span data-stu-id="6064b-124">Two compilations create a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /t:module Stringer.cs
   >   csc Client.cs /addmodule:Stringer.netmodule
   >   ```
   >
   >   ```vb
   >   vbc /t:module Stringer.vb
   >   vbc Client.vb /addmodule:Stringer.netmodule
   >   ```
   >
   > <span data-ttu-id="6064b-125">Jedna kompilacja tworzy zestaw dwóch plików:</span><span class="sxs-lookup"><span data-stu-id="6064b-125">One compilation creates a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /out:Client.exe Client.cs /out:Stringer.netmodule Stringer.cs
   >   ```
   >
   >   ```vb
   >   vbc /out:Client.exe Client.vb /out:Stringer.netmodule Stringer.vb
   >   ```

5. <span data-ttu-id="6064b-126">Użyj [konsolidatora zestawu (Al.exe)](../tools/al-exe-assembly-linker.md) , aby utworzyć plik wyjściowy, który zawiera manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="6064b-126">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="6064b-127">Ten plik zawiera informacje referencyjne dotyczące wszystkich modułów lub zasobów, które są częścią zestawu.</span><span class="sxs-lookup"><span data-stu-id="6064b-127">This file contains reference information for all modules or resources that are part of the assembly.</span></span>

    <span data-ttu-id="6064b-128">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="6064b-128">At the command prompt, type the following command:</span></span>

    <span data-ttu-id="6064b-129">**Al** \<*module name*> \<*module name*>...</span><span class="sxs-lookup"><span data-stu-id="6064b-129">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="6064b-130">**/Main:** \<*method name*> **/out:** \<*file name*> **/target:**\<*assembly file type*></span><span class="sxs-lookup"><span data-stu-id="6064b-130">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>

    <span data-ttu-id="6064b-131">W tym poleceniu argumenty *nazwy modułu* określają nazwę każdego modułu, który ma zostać uwzględniony w zestawie.</span><span class="sxs-lookup"><span data-stu-id="6064b-131">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="6064b-132">**/Main:** opcja określa nazwę metody, która jest punktem wejścia zestawu.</span><span class="sxs-lookup"><span data-stu-id="6064b-132">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="6064b-133">**/Out:** opcja określa nazwę pliku wyjściowego, który zawiera metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="6064b-133">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="6064b-134">**/Target:** opcja określa, że zestaw to plik wykonywalny aplikacji konsoli (*exe*), plik wykonywalny systemu Windows (*. win*) lub plik biblioteki (*. lib*).</span><span class="sxs-lookup"><span data-stu-id="6064b-134">The **/target:** option specifies that the assembly is a console application executable (*.exe*) file, a Windows executable (*.win*) file, or a library (*.lib*) file.</span></span>

    <span data-ttu-id="6064b-135">W poniższym przykładzie *Al.exe* tworzy zestaw, który jest plikiem wykonywalnym aplikacji konsoli o nazwie *myAssembly.exe*.</span><span class="sxs-lookup"><span data-stu-id="6064b-135">In the following example, *Al.exe* creates an assembly that is a console application executable called *myAssembly.exe*.</span></span> <span data-ttu-id="6064b-136">Aplikacja składa się z dwóch modułów o nazwie *Client. webmodule* i *Stringer. webmodule*, a plik wykonywalny o nazwie *myAssembly.exe*, który zawiera tylko metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="6064b-136">The application consists of two modules called *Client.netmodule* and *Stringer.netmodule*, and the executable file called *myAssembly.exe*, which contains only assembly metadata.</span></span> <span data-ttu-id="6064b-137">Punkt wejścia zestawu jest `Main` metodą w klasie `MainClientApp` , która znajduje się w *Client.dll*.</span><span class="sxs-lookup"><span data-stu-id="6064b-137">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in *Client.dll*.</span></span>

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    <span data-ttu-id="6064b-138">Aby sprawdzić zawartość zestawu lub określić, czy plik jest zestawem lub modułem, można użyć [Dezasembler MSIL (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) .</span><span class="sxs-lookup"><span data-stu-id="6064b-138">You can use the [MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>

## <a name="see-also"></a><span data-ttu-id="6064b-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6064b-139">See also</span></span>

- [<span data-ttu-id="6064b-140">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="6064b-140">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="6064b-141">Instrukcje: wyświetlanie zawartości zestawu</span><span class="sxs-lookup"><span data-stu-id="6064b-141">How to: View assembly contents</span></span>](../../standard/assembly/view-contents.md)
- [<span data-ttu-id="6064b-142">Jak środowisko uruchomieniowe lokalizuje zestawy</span><span class="sxs-lookup"><span data-stu-id="6064b-142">How the runtime locates assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="6064b-143">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="6064b-143">Multifile assemblies</span></span>](multifile-assemblies.md)
