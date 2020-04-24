---
title: -target (Opcje kompilatora języka C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: ea5481810e629d911c4d5aba62e60c98d0783f34
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644356"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="2f842-102">-target (Opcje kompilatora języka C#)</span><span class="sxs-lookup"><span data-stu-id="2f842-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="2f842-103">Opcja kompilatora **-target** można określić w jednym z czterech formularzy:</span><span class="sxs-lookup"><span data-stu-id="2f842-103">The **-target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="2f842-104">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="2f842-104">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="2f842-105">Aby utworzyć plik exe dla aplikacji ze Sklepu Windows 8.x.</span><span class="sxs-lookup"><span data-stu-id="2f842-105">To create an .exe file for Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="2f842-106">-target:exe</span><span class="sxs-lookup"><span data-stu-id="2f842-106">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="2f842-107">Aby utworzyć plik exe.</span><span class="sxs-lookup"><span data-stu-id="2f842-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="2f842-108">-target:library</span><span class="sxs-lookup"><span data-stu-id="2f842-108">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="2f842-109">Aby utworzyć bibliotekę kodu.</span><span class="sxs-lookup"><span data-stu-id="2f842-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="2f842-110">-target:module</span><span class="sxs-lookup"><span data-stu-id="2f842-110">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="2f842-111">Aby utworzyć moduł.</span><span class="sxs-lookup"><span data-stu-id="2f842-111">To create a module.</span></span>  
  
 [<span data-ttu-id="2f842-112">-target:winexe</span><span class="sxs-lookup"><span data-stu-id="2f842-112">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="2f842-113">Aby utworzyć program windowsowy.</span><span class="sxs-lookup"><span data-stu-id="2f842-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="2f842-114">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="2f842-114">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="2f842-115">Aby utworzyć pośredni plik .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="2f842-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="2f842-116">O ile nie określisz **-target:module**, **-target** powoduje, że manifest zestawu .NET Framework ma zostać umieszczony w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="2f842-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="2f842-117">Aby uzyskać więcej informacji, zobacz [Zestawy w .NET](../../../standard/assembly/index.md) i [Common Attributes](../attributes/global.md).</span><span class="sxs-lookup"><span data-stu-id="2f842-117">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../attributes/global.md).</span></span>  
  
 <span data-ttu-id="2f842-118">Manifest zestawu jest umieszczany w pierwszym pliku wyjściowym exe w kompilacji lub w pierwszej dll, jeśli nie ma pliku wyjściowego .exe.</span><span class="sxs-lookup"><span data-stu-id="2f842-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="2f842-119">Na przykład w następującym wierszu polecenia manifest `1.exe`zostanie umieszczony w:</span><span class="sxs-lookup"><span data-stu-id="2f842-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="2f842-120">Kompilator tworzy tylko jeden manifest zestawu na kompilację.</span><span class="sxs-lookup"><span data-stu-id="2f842-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="2f842-121">Informacje o wszystkich plikach w kompilacji są umieszczane w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="2f842-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="2f842-122">Wszystkie pliki wyjściowe z wyjątkiem plików utworzonych za pomocą **-target:module** mogą zawierać manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="2f842-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="2f842-123">Podczas tworzenia wielu plików wyjściowych w wierszu polecenia można utworzyć tylko jeden manifest zestawu i musi on przejść do pierwszego pliku wyjściowego określonego w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="2f842-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="2f842-124">Bez względu na to, jaki jest pierwszy plik wyjściowy (**-target:exe**, **-target:winexe**, **-target:library** lub **-target:module**), wszelkie inne pliki wyjściowe wyprodukowane w tej samej kompilacji muszą być modułami (**-target:module**).</span><span class="sxs-lookup"><span data-stu-id="2f842-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="2f842-125">Jeśli utworzysz zestaw, można wskazać, że całość lub część <xref:System.CLSCompliantAttribute> kodu jest cls zgodne z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="2f842-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="2f842-126">Aby uzyskać więcej informacji na temat programowania <xref:VSLangProj80.ProjectProperties3.OutputType%2A>ustawiania tej opcji kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="2f842-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f842-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f842-127">See also</span></span>

- [<span data-ttu-id="2f842-128">Opcje kompilatora języka C#</span><span class="sxs-lookup"><span data-stu-id="2f842-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="2f842-129">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="2f842-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="2f842-130">-subsystemversion (Opcje kompilatora języka C#)</span><span class="sxs-lookup"><span data-stu-id="2f842-130">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
