---
title: -out (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: 51c66d6bc2064d8051415de2ac083da478355a99
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602596"
---
# <a name="-out-c-compiler-options"></a><span data-ttu-id="9acfd-102">-out (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="9acfd-102">-out (C# Compiler Options)</span></span>
<span data-ttu-id="9acfd-103">Opcja **-out** określa nazwę pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="9acfd-103">The **-out** option specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9acfd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9acfd-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="9acfd-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9acfd-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="9acfd-106">Nazwa pliku wyjściowego utworzonego przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="9acfd-106">The name of the output file created by the compiler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9acfd-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9acfd-107">Remarks</span></span>  
 <span data-ttu-id="9acfd-108">W wierszu polecenia można określić wiele plików wyjściowych dla kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9acfd-108">On the command line, it is possible to specify multiple output files for your compilation.</span></span> <span data-ttu-id="9acfd-109">Kompilator oczekuje na znalezienie co najmniej jednego pliku kodu źródłowego po opcji **-out** .</span><span class="sxs-lookup"><span data-stu-id="9acfd-109">The compiler expects to find one or more source code files following the **-out** option.</span></span> <span data-ttu-id="9acfd-110">Następnie wszystkie pliki kodu źródłowego zostaną skompilowane do pliku wyjściowego określonego przez tę opcję.</span><span class="sxs-lookup"><span data-stu-id="9acfd-110">Then, all source code files will be compiled into the output file specified by that **-out** option.</span></span>  
  
 <span data-ttu-id="9acfd-111">Określ pełną nazwę i rozszerzenie pliku, który chcesz utworzyć.</span><span class="sxs-lookup"><span data-stu-id="9acfd-111">Specify the full name and extension of the file you want to create.</span></span>  
  
 <span data-ttu-id="9acfd-112">Jeśli nie określisz nazwy pliku wyjściowego:</span><span class="sxs-lookup"><span data-stu-id="9acfd-112">If you do not specify the name of the output file:</span></span>  
  
- <span data-ttu-id="9acfd-113">Plik. exe zajmie swoją nazwę z pliku kodu źródłowego, który zawiera metodę **Main** .</span><span class="sxs-lookup"><span data-stu-id="9acfd-113">An .exe will take its name from the source code file that contains the **Main** method.</span></span>  
  
- <span data-ttu-id="9acfd-114">Plik. dll lub. webmodule przyjmuje swoją nazwę z pierwszego pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="9acfd-114">A .dll or .netmodule will take its name from the first source code file.</span></span>  
  
 <span data-ttu-id="9acfd-115">Plik kodu źródłowego używany do kompilowania jednego pliku wyjściowego nie może być używany w tej samej kompilacji dla kompilacji innego pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="9acfd-115">A source code file used to compile one output file cannot be used in the same compilation for the compilation of another output file.</span></span>  
  
 <span data-ttu-id="9acfd-116">W przypadku tworzenia wielu plików wyjściowych w kompilacji wiersza polecenia należy pamiętać, że tylko jeden z plików wyjściowych może być zestawem i że tylko pierwszy plik wyjściowy określony (niejawnie lub jawnie w **trybie out**) może być zestawem.</span><span class="sxs-lookup"><span data-stu-id="9acfd-116">When producing multiple output files in a command-line compilation, keep in mind that only one of the output files can be an assembly and that only the first output file specified (implicitly or explicitly with **-out**) can be the assembly.</span></span>  
  
 <span data-ttu-id="9acfd-117">Wszystkie moduły tworzone w ramach kompilacji stają się plikami skojarzonymi z dowolnym zestawem również w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9acfd-117">Any modules produced as part of a compilation become files associated with any assembly also produced in the compilation.</span></span> <span data-ttu-id="9acfd-118">Użyj [Ildasm. exe](../../../framework/tools/ildasm-exe-il-disassembler.md) , aby wyświetlić manifest zestawu, aby wyświetlić skojarzone pliki.</span><span class="sxs-lookup"><span data-stu-id="9acfd-118">Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) to view the assembly manifest to see the associated files.</span></span>  
  
 <span data-ttu-id="9acfd-119">Opcja kompilatora-out jest wymagana, aby plik exe był elementem docelowym zestawu zaprzyjaźnionego.</span><span class="sxs-lookup"><span data-stu-id="9acfd-119">The -out compiler option is required in order for an exe to be the target of a friend assembly.</span></span> <span data-ttu-id="9acfd-120">Aby uzyskać więcej informacji, zobacz [zaprzyjaźnione zestawy](../../../standard/assembly/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="9acfd-120">For more information see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="9acfd-121">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9acfd-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="9acfd-122">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="9acfd-122">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="9acfd-123">Kliknij stronę właściwości **aplikacji** .</span><span class="sxs-lookup"><span data-stu-id="9acfd-123">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="9acfd-124">Zmodyfikuj właściwość **nazwy zestawu** .</span><span class="sxs-lookup"><span data-stu-id="9acfd-124">Modify the **Assembly name** property.</span></span>  
  
     <span data-ttu-id="9acfd-125">Aby programowo ustawić tę opcję kompilatora: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> jest to właściwość tylko do odczytu, która jest określana przez kombinację typu projektu (exe, biblioteka i tak dalej) i nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="9acfd-125">To set this compiler option programmatically: the <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> is a read-only property, which is determined by a combination of the project type (exe, library, and so forth) and the assembly name.</span></span> <span data-ttu-id="9acfd-126">Modyfikacja jednej lub obu tych właściwości będzie konieczna do ustawienia nazwy pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="9acfd-126">Modifying one or both of these properties will be necessary to set the output file name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9acfd-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="9acfd-127">Example</span></span>  
 <span data-ttu-id="9acfd-128">Kompiluj `t.cs` i twórz plik `t.exe`wyjściowy, a także Kompiluj `t2.cs` i twórz plik `mymodule.netmodule`wyjściowy modułu:</span><span class="sxs-lookup"><span data-stu-id="9acfd-128">Compile `t.cs` and create output file `t.exe`, as well as build `t2.cs` and create module output file `mymodule.netmodule`:</span></span>  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="9acfd-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9acfd-129">See also</span></span>

- [<span data-ttu-id="9acfd-130">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="9acfd-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="9acfd-131">Przyjazne zestawy</span><span class="sxs-lookup"><span data-stu-id="9acfd-131">Friend Assemblies</span></span>](../../../standard/assembly/friend-assemblies.md)
- [<span data-ttu-id="9acfd-132">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="9acfd-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
