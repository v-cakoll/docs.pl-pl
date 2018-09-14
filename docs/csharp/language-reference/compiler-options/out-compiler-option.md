---
title: -out (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: ea371dc968c8d8bf1569d17531cf7f6faff1d315
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45558002"
---
# <a name="-out-c-compiler-options"></a><span data-ttu-id="53f5d-102">-out (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="53f5d-102">-out (C# Compiler Options)</span></span>
<span data-ttu-id="53f5d-103">**-Out** opcja określa nazwę pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="53f5d-103">The **-out** option specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53f5d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53f5d-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="53f5d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="53f5d-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="53f5d-106">Nazwa pliku wyjściowego, utworzony przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="53f5d-106">The name of the output file created by the compiler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53f5d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53f5d-107">Remarks</span></span>  
 <span data-ttu-id="53f5d-108">W wierszu polecenia jest możliwość określenia wielu plików wyjściowych dla kompilacji.</span><span class="sxs-lookup"><span data-stu-id="53f5d-108">On the command line, it is possible to specify multiple output files for your compilation.</span></span> <span data-ttu-id="53f5d-109">Kompilator spodziewa się znaleźć pliki kodu co najmniej jeden źródłowy zgodnie z **-out** opcji.</span><span class="sxs-lookup"><span data-stu-id="53f5d-109">The compiler expects to find one or more source code files following the **-out** option.</span></span> <span data-ttu-id="53f5d-110">Następnie wszystkich plikach kodu źródłowego zostanie skompilowany w określony przez to plik wyjściowy **-out** opcji.</span><span class="sxs-lookup"><span data-stu-id="53f5d-110">Then, all source code files will be compiled into the output file specified by that **-out** option.</span></span>  
  
 <span data-ttu-id="53f5d-111">Podaj pełną nazwę i rozszerzenie pliku, który chcesz utworzyć.</span><span class="sxs-lookup"><span data-stu-id="53f5d-111">Specify the full name and extension of the file you want to create.</span></span>  
  
 <span data-ttu-id="53f5d-112">Jeśli nie określisz nazwy pliku wyjściowego:</span><span class="sxs-lookup"><span data-stu-id="53f5d-112">If you do not specify the name of the output file:</span></span>  
  
-   <span data-ttu-id="53f5d-113">.Exe zajmie się jego nazwy w pliku kodu źródłowego, który zawiera **Main** metody.</span><span class="sxs-lookup"><span data-stu-id="53f5d-113">An .exe will take its name from the source code file that contains the **Main** method.</span></span>  
  
-   <span data-ttu-id="53f5d-114">Plik .dll lub moduł .netmodule potrwa nazwy z pierwszego pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="53f5d-114">A .dll or .netmodule will take its name from the first source code file.</span></span>  
  
 <span data-ttu-id="53f5d-115">Plik kodu źródłowego, używana do kompilowania jednego pliku danych wyjściowych nie można użyć w tej samej kompilacji dla kompilacji inny plik danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="53f5d-115">A source code file used to compile one output file cannot be used in the same compilation for the compilation of another output file.</span></span>  
  
 <span data-ttu-id="53f5d-116">Podczas produkowania wiele plików wyjściowych w kompilacji wiersza polecenia, pamiętać, że tylko jeden z plików wyjściowych może być zestaw, a określony tylko pierwszy plik wyjściowy (jawnie lub niejawnie za pomocą **-out**) może być zestaw .</span><span class="sxs-lookup"><span data-stu-id="53f5d-116">When producing multiple output files in a command-line compilation, keep in mind that only one of the output files can be an assembly and that only the first output file specified (implicitly or explicitly with **-out**) can be the assembly.</span></span>  
  
 <span data-ttu-id="53f5d-117">Wszystkie moduły, utworzony jako część kompilacji stają się pliki skojarzone z dowolnego złożenia, również jest generowany w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="53f5d-117">Any modules produced as part of a compilation become files associated with any assembly also produced in the compilation.</span></span> <span data-ttu-id="53f5d-118">Użyj [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) Aby wyświetlić manifest zestawu, aby wyświetlić skojarzone pliki.</span><span class="sxs-lookup"><span data-stu-id="53f5d-118">Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) to view the assembly manifest to see the associated files.</span></span>  
  
 <span data-ttu-id="53f5d-119">Out — opcja kompilatora jest wymagana dla pliku exe jako obiekt docelowy zestaw przyjazny.</span><span class="sxs-lookup"><span data-stu-id="53f5d-119">The -out compiler option is required in order for an exe to be the target of a friend assembly.</span></span> <span data-ttu-id="53f5d-120">Aby uzyskać więcej informacji, zobacz [przyjaznych zestawów](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="53f5d-120">For more information see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="53f5d-121">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="53f5d-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="53f5d-122">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="53f5d-122">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="53f5d-123">Kliknij przycisk **aplikacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="53f5d-123">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="53f5d-124">Modyfikowanie **nazwy zestawu** właściwości.</span><span class="sxs-lookup"><span data-stu-id="53f5d-124">Modify the **Assembly name** property.</span></span>  
  
     <span data-ttu-id="53f5d-125">Aby programowo ustawić tę opcję kompilatora: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> jest tylko do odczytu właściwość, która jest określana przez połączenie typu projektu (exe, biblioteki i tak dalej) i nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="53f5d-125">To set this compiler option programmatically: the <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> is a read-only property, which is determined by a combination of the project type (exe, library, and so forth) and the assembly name.</span></span> <span data-ttu-id="53f5d-126">Modyfikowanie jedną lub obie te właściwości będą należy ustawić nazwę pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="53f5d-126">Modifying one or both of these properties will be necessary to set the output file name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53f5d-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="53f5d-127">Example</span></span>  
 <span data-ttu-id="53f5d-128">Skompilować `t.cs` i utworzyć plik wyjściowy `t.exe`, a także kompilacji `t2.cs` i utworzyć plik wyjściowy modułu `mymodule.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="53f5d-128">Compile `t.cs` and create output file `t.exe`, as well as build `t2.cs` and create module output file `mymodule.netmodule`:</span></span>  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="53f5d-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53f5d-129">See Also</span></span>  

- [<span data-ttu-id="53f5d-130">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="53f5d-130">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="53f5d-131">Przyjazne zestawy</span><span class="sxs-lookup"><span data-stu-id="53f5d-131">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
- [<span data-ttu-id="53f5d-132">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="53f5d-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
