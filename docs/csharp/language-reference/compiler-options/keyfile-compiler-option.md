---
title: -keyfile (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: 45ab88609c26dd26a1f8bb3d68d1f579af9d3f77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="1ee33-102">-keyfile (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="1ee33-102">-keyfile (C# Compiler Options)</span></span>
<span data-ttu-id="1ee33-103">Określa nazwę pliku zawierającego klucz kryptograficzny.</span><span class="sxs-lookup"><span data-stu-id="1ee33-103">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ee33-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ee33-104">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="1ee33-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1ee33-105">Arguments</span></span>  
  
|<span data-ttu-id="1ee33-106">Termin</span><span class="sxs-lookup"><span data-stu-id="1ee33-106">Term</span></span>|<span data-ttu-id="1ee33-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="1ee33-107">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="1ee33-108">Nazwa pliku zawierającego klucz silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="1ee33-108">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ee33-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ee33-109">Remarks</span></span>  
 <span data-ttu-id="1ee33-110">Gdy ta opcja jest używana, kompilator wstawia klucza publicznego z określonego pliku do manifestu zestawu i podpisuje następnie zestawie końcowym z kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="1ee33-110">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="1ee33-111">Aby wygenerować plik klucza, wpisz sn -k `file` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="1ee33-111">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="1ee33-112">Jeśli kompilacji z **-docelowych: moduł**, nazwa pliku klucza jest przechowywany w module i włączyć do zestawu, który jest tworzony podczas kompilowania zestawu z [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="1ee33-112">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="1ee33-113">Można również przekazać do kompilatora z informacjami szyfrowania [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="1ee33-113">You can also pass your encryption information to the compiler with [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span></span> <span data-ttu-id="1ee33-114">Użyj [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) Jeśli chcesz częściowo podpisanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="1ee33-114">Use [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="1ee33-115">W przypadku - keyfile i keycontainer — podano (przez opcję wiersza polecenia lub przez atrybut niestandardowy) w tej samej kompilacji, kompilator próbują używać najpierw kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="1ee33-115">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="1ee33-116">Jeśli który zakończy się powodzeniem, zestaw jest podpisany z informacjami w kontenerze kluczy.</span><span class="sxs-lookup"><span data-stu-id="1ee33-116">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="1ee33-117">Kompilator nie może znaleźć kontener kluczy, spróbuje plik określony za pomocą - keyfile.</span><span class="sxs-lookup"><span data-stu-id="1ee33-117">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="1ee33-118">Jeśli który zakończy się powodzeniem, zestaw jest podpisany za pomocą informacji w pliku klucza i informacje o kluczu zostaną zainstalowane w kontenerze kluczy (podobnie jak sn -i), aby w następnej kompilacji, kontener kluczy będzie nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="1ee33-118">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="1ee33-119">Należy pamiętać, że plik klucza może zawierać tylko klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="1ee33-119">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="1ee33-120">Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) i [opóźnione podpisywanie zestawu](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="1ee33-120">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1ee33-121">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1ee33-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="1ee33-122">Otwórz **właściwości** strony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="1ee33-122">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="1ee33-123">Kliknij przycisk **podpisywanie** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="1ee33-123">Click the **Signing** property page.</span></span>  
  
3.  <span data-ttu-id="1ee33-124">Modyfikowanie **wybierz plik klucza o silnej nazwie** właściwości.</span><span class="sxs-lookup"><span data-stu-id="1ee33-124">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="1ee33-125">Programowo dostęp do tej opcji kompilatora z <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="1ee33-125">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee33-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ee33-126">See Also</span></span>  
 [<span data-ttu-id="1ee33-127">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="1ee33-127">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="1ee33-128">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="1ee33-128">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
