---
title: -docelowego (opcje kompilatora C#)
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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215501"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="9dd64-102">-docelowego (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="9dd64-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="9dd64-103">**-Docelowy** — opcja kompilatora można określić w jednym z czterech formularzy:</span><span class="sxs-lookup"><span data-stu-id="9dd64-103">The **-target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="9dd64-104">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="9dd64-104">-target:appcontainerexe</span></span>](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="9dd64-105">Aby utworzyć plik .exe [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9dd64-105">To create an .exe file for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [<span data-ttu-id="9dd64-106">-target:exe</span><span class="sxs-lookup"><span data-stu-id="9dd64-106">-target:exe</span></span>](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 <span data-ttu-id="9dd64-107">Aby utworzyć plik .exe.</span><span class="sxs-lookup"><span data-stu-id="9dd64-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="9dd64-108">-target:library</span><span class="sxs-lookup"><span data-stu-id="9dd64-108">-target:library</span></span>](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 <span data-ttu-id="9dd64-109">Aby utworzyć biblioteki kodu.</span><span class="sxs-lookup"><span data-stu-id="9dd64-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="9dd64-110">-target:module</span><span class="sxs-lookup"><span data-stu-id="9dd64-110">-target:module</span></span>](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 <span data-ttu-id="9dd64-111">Aby utworzyć moduł.</span><span class="sxs-lookup"><span data-stu-id="9dd64-111">To create a module.</span></span>  
  
 [<span data-ttu-id="9dd64-112">-target:winexe</span><span class="sxs-lookup"><span data-stu-id="9dd64-112">-target:winexe</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 <span data-ttu-id="9dd64-113">Aby utworzyć program systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9dd64-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="9dd64-114">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="9dd64-114">-target:winmdobj</span></span>](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 <span data-ttu-id="9dd64-115">Aby utworzyć plik pośredni .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="9dd64-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="9dd64-116">Chyba że zostanie **-docelowych: moduł**, **-docelowy** powoduje, że manifestu zestawu .NET Framework do umieszczenia w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="9dd64-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="9dd64-117">Aby uzyskać więcej informacji, zobacz [zestawy w środowisku uruchomieniowym języka](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) i [takie same atrybuty wspólne](../../programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="9dd64-117">For more information, see [Assemblies in the Common Language Runtime](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
 <span data-ttu-id="9dd64-118">Manifest zestawu jest umieszczany w pierwszym pliku wyjściowego .exe w kompilacji lub w pierwszej biblioteki DLL, jeśli plik wyjściowy .exe nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="9dd64-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="9dd64-119">Na przykład, w wierszu polecenia następujący plik manifestu zostaną umieszczone w `1.exe`:</span><span class="sxs-lookup"><span data-stu-id="9dd64-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="9dd64-120">Kompilator tworzy tylko jeden manifest zestawu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9dd64-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="9dd64-121">Informacje o wszystkich plików w kompilacji jest umieszczany w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="9dd64-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="9dd64-122">Wszystkie pliki z wyjątkiem tych, utworzone za pomocą wyjściowe **-docelowych: moduł** może zawierać manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="9dd64-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="9dd64-123">Podczas produkowania wielu plików wyjściowych w wierszu polecenia, można utworzyć tylko jeden zestaw manifestu i należy przejść do pierwszego pliku wyjściowego, określona w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="9dd64-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="9dd64-124">Niezależnie od tego, jakie pierwszy plik wyjściowy jest (**-docelowych: exe**, **-docelowych: winexe**, **— docelowa: Biblioteka** lub **-docelowych: moduł**) wszystkie inne pliki wyjściowe wygenerowane w tej samej kompilacji musi być modułów (**-docelowych: moduł**).</span><span class="sxs-lookup"><span data-stu-id="9dd64-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="9dd64-125">W przypadku utworzenia zestawu, może oznaczać, że całość lub część kodu jest zgodny ze specyfikacją CLS <xref:System.CLSCompliantAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9dd64-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="9dd64-126">Aby uzyskać więcej informacji na temat ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="9dd64-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd64-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9dd64-127">See Also</span></span>  
 [<span data-ttu-id="9dd64-128">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="9dd64-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="9dd64-129">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="9dd64-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="9dd64-130">-subsystemversion (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="9dd64-130">-subsystemversion (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)
