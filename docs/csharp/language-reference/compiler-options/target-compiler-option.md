---
title: -target (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: 7736b8850a7b09f7212e83e05acf0e1994bce0fe
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2018
ms.locfileid: "43000007"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="56d6a-102">-target (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="56d6a-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="56d6a-103">**-Target** — opcja kompilatora można określić w jednej z czterech form:</span><span class="sxs-lookup"><span data-stu-id="56d6a-103">The **-target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="56d6a-104">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="56d6a-104">-target:appcontainerexe</span></span>](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="56d6a-105">Aby utworzyć plik .exe [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="56d6a-105">To create an .exe file for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [<span data-ttu-id="56d6a-106">-target:exe</span><span class="sxs-lookup"><span data-stu-id="56d6a-106">-target:exe</span></span>](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 <span data-ttu-id="56d6a-107">Aby utworzyć plik .exe.</span><span class="sxs-lookup"><span data-stu-id="56d6a-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="56d6a-108">-target:library</span><span class="sxs-lookup"><span data-stu-id="56d6a-108">-target:library</span></span>](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 <span data-ttu-id="56d6a-109">Aby utworzyć bibliotekę kodu.</span><span class="sxs-lookup"><span data-stu-id="56d6a-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="56d6a-110">-target:module</span><span class="sxs-lookup"><span data-stu-id="56d6a-110">-target:module</span></span>](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 <span data-ttu-id="56d6a-111">Aby utworzyć moduł.</span><span class="sxs-lookup"><span data-stu-id="56d6a-111">To create a module.</span></span>  
  
 [<span data-ttu-id="56d6a-112">-target:winexe</span><span class="sxs-lookup"><span data-stu-id="56d6a-112">-target:winexe</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 <span data-ttu-id="56d6a-113">Aby utworzyć Windows program.</span><span class="sxs-lookup"><span data-stu-id="56d6a-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="56d6a-114">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="56d6a-114">-target:winmdobj</span></span>](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 <span data-ttu-id="56d6a-115">Aby utworzyć plik pośredni .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="56d6a-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="56d6a-116">Chyba że określisz **-target: module**, **-target** powoduje, że manifest zestawu .NET Framework, należy umieścić w pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="56d6a-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="56d6a-117">Aby uzyskać więcej informacji, zobacz [zestawów w środowisko uruchomieniowe języka wspólnego](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) i [wspólne atrybuty](../../programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="56d6a-117">For more information, see [Assemblies in the Common Language Runtime](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
 <span data-ttu-id="56d6a-118">Manifest zestawu jest umieszczany w pierwszym pliku wyjściowego .exe w kompilacji lub w pierwszym pliku DLL, jeśli nie ma żadnego pliku wyjściowego .exe.</span><span class="sxs-lookup"><span data-stu-id="56d6a-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="56d6a-119">Na przykład, w wierszu polecenia następujące manifestu zostaną umieszczone w `1.exe`:</span><span class="sxs-lookup"><span data-stu-id="56d6a-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="56d6a-120">Kompilator tworzy tylko jeden manifest zestawu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="56d6a-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="56d6a-121">Informacje o wszystkich plikach w zestawieniu jest umieszczany w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="56d6a-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="56d6a-122">Wszystkie pliki, z wyjątkiem tych utworzonych za pomocą wyjściowe **-target: module** może zawierać manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="56d6a-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="56d6a-123">Podczas produkowania wiele plików wyjściowych w wierszu polecenia, można utworzyć tylko jedną manifestu dla aplikacji i musi przejść do pierwszego pliku wyjściowego, określone w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="56d6a-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="56d6a-124">Niezależnie od tego, jakie pierwszy plik wyjściowy jest (**-target: exe**, **-target: winexe**, **-target: library** lub **-target: module**) wszystkie inne pliki wyjściowe utworzone w tej samej kompilacji musi być modułów (**-target: module**).</span><span class="sxs-lookup"><span data-stu-id="56d6a-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="56d6a-125">Jeśli utworzysz zestaw, można wskazać, że całość lub część kodu jest zgodne ze specyfikacją CLS <xref:System.CLSCompliantAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="56d6a-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="56d6a-126">Aby uzyskać więcej informacji na temat programowego ustawiania tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="56d6a-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d6a-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56d6a-127">See Also</span></span>  
 [<span data-ttu-id="56d6a-128">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="56d6a-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="56d6a-129">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="56d6a-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="56d6a-130">-subsystemversion (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="56d6a-130">-subsystemversion (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)
