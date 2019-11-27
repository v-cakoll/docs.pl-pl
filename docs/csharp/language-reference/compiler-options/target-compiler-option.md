---
title: -Target (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: af7bd917f57c8752a2026fbb98aa8b22adc98db7
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204515"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="cbeca-102">-Target (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="cbeca-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="cbeca-103">Opcja kompilatora **-Target** może być określona w jednej z czterech postaci:</span><span class="sxs-lookup"><span data-stu-id="cbeca-103">The **-target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="cbeca-104">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="cbeca-104">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="cbeca-105">Aby utworzyć plik exe dla aplikacji ze sklepu Windows 8. x.</span><span class="sxs-lookup"><span data-stu-id="cbeca-105">To create an .exe file for Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="cbeca-106">-target:exe</span><span class="sxs-lookup"><span data-stu-id="cbeca-106">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="cbeca-107">Do utworzenia pliku. exe.</span><span class="sxs-lookup"><span data-stu-id="cbeca-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="cbeca-108">-target:library</span><span class="sxs-lookup"><span data-stu-id="cbeca-108">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="cbeca-109">Aby utworzyć bibliotekę kodu.</span><span class="sxs-lookup"><span data-stu-id="cbeca-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="cbeca-110">-target:module</span><span class="sxs-lookup"><span data-stu-id="cbeca-110">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="cbeca-111">Do utworzenia modułu.</span><span class="sxs-lookup"><span data-stu-id="cbeca-111">To create a module.</span></span>  
  
 [<span data-ttu-id="cbeca-112">-target:winexe</span><span class="sxs-lookup"><span data-stu-id="cbeca-112">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="cbeca-113">Do utworzenia programu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="cbeca-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="cbeca-114">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="cbeca-114">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="cbeca-115">Aby utworzyć pośredni plik. winmdobj.</span><span class="sxs-lookup"><span data-stu-id="cbeca-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="cbeca-116">O ile nie określono **elementu-target: module**, **-Target** powoduje, że manifest zestawu .NET Framework zostanie umieszczony w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="cbeca-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="cbeca-117">Aby uzyskać więcej informacji, zobacz [zestawy w programie .NET](../../../standard/assembly/index.md) i [wspólne atrybuty](../../programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="cbeca-117">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
 <span data-ttu-id="cbeca-118">Manifest zestawu jest umieszczany w pierwszym pliku wyjściowym exe w kompilacji lub w pierwszej bibliotece DLL, jeśli nie ma pliku wyjściowego. exe.</span><span class="sxs-lookup"><span data-stu-id="cbeca-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="cbeca-119">Na przykład w poniższym wierszu polecenia manifest zostanie umieszczony w `1.exe`:</span><span class="sxs-lookup"><span data-stu-id="cbeca-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="cbeca-120">Kompilator tworzy tylko jeden manifest zestawu na kompilację.</span><span class="sxs-lookup"><span data-stu-id="cbeca-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="cbeca-121">Informacje o wszystkich plikach w kompilacji są umieszczane w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="cbeca-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="cbeca-122">Wszystkie pliki wyjściowe z wyjątkiem plików utworzonych za pomocą **elementu-target: module** mogą zawierać manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="cbeca-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="cbeca-123">W przypadku tworzenia wielu plików wyjściowych w wierszu polecenia można utworzyć tylko jeden manifest zestawu i musi on przejść do pierwszego pliku wyjściowego określonego w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="cbeca-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="cbeca-124">Niezależnie od tego, jaki pierwszy plik wyjściowy jest ( **-target: exe**, **-target: winexe**, **-target: Library** lub **-target: module**), wszystkie inne pliki wyjściowe utworzone w tej samej kompilacji muszą być modułami ( **-target: module**).</span><span class="sxs-lookup"><span data-stu-id="cbeca-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="cbeca-125">W przypadku utworzenia zestawu można wskazać, że całość lub część kodu jest zgodna ze specyfikacją CLS z atrybutem <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cbeca-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="cbeca-126">Aby uzyskać więcej informacji o tym, jak można programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="cbeca-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbeca-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbeca-127">See also</span></span>

- [<span data-ttu-id="cbeca-128">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="cbeca-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="cbeca-129">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="cbeca-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="cbeca-130">-subsystemversion (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="cbeca-130">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
