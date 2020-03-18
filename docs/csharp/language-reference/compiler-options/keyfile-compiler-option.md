---
title: -keyfile (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: bf271cc6b6887e930911071d4603b51daed55e61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970257"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="c694c-102">-keyfile (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="c694c-102">-keyfile (C# Compiler Options)</span></span>
<span data-ttu-id="c694c-103">Określa nazwę pliku zawierającą klucz kryptograficzny.</span><span class="sxs-lookup"><span data-stu-id="c694c-103">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c694c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c694c-104">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="c694c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c694c-105">Arguments</span></span>  
  
|<span data-ttu-id="c694c-106">Termin</span><span class="sxs-lookup"><span data-stu-id="c694c-106">Term</span></span>|<span data-ttu-id="c694c-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="c694c-107">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="c694c-108">Nazwa pliku zawierającego klucz silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="c694c-108">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c694c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c694c-109">Remarks</span></span>  
 <span data-ttu-id="c694c-110">Gdy ta opcja jest używana, kompilator wstawia klucz publiczny z określonego pliku do manifestu zestawu, a następnie podpisuje końcowy zestaw kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="c694c-110">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="c694c-111">Aby wygenerować plik klucza, `file` wpisz sn -k w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="c694c-111">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="c694c-112">Jeśli skompilować z **-target:module**, nazwa pliku klucza jest utrzymywana w module i włączone do zestawu, który jest tworzony podczas kompilowania zestawu z [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="c694c-112">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="c694c-113">Można również przekazać informacje szyfrowania do kompilatora z [-keycontainer](./keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="c694c-113">You can also pass your encryption information to the compiler with [-keycontainer](./keycontainer-compiler-option.md).</span></span> <span data-ttu-id="c694c-114">Użyj [-delaysign,](./delaysign-compiler-option.md) jeśli chcesz, aby zestaw częściowo podpisany.</span><span class="sxs-lookup"><span data-stu-id="c694c-114">Use [-delaysign](./delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="c694c-115">W przypadku, gdy zarówno -keyfile i -keycontainer są określone (przez opcję wiersza polecenia lub przez atrybut niestandardowy) w tej samej kompilacji, kompilator najpierw spróbuje kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="c694c-115">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="c694c-116">Jeśli to się powiedzie, zestaw jest podpisany z informacjami w kontenerze kluczy.</span><span class="sxs-lookup"><span data-stu-id="c694c-116">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="c694c-117">Jeśli kompilator nie znajdzie kontenera kluczy, spróbuje plik określony z -keyfile.</span><span class="sxs-lookup"><span data-stu-id="c694c-117">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="c694c-118">Jeśli to się powiedzie, zestaw jest podpisany z informacjami w pliku klucza, a informacje o kluczu zostaną zainstalowane w kontenerze kluczy (podobnie jak sn -i), tak aby podczas następnej kompilacji kontener kluczy był prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="c694c-118">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="c694c-119">Należy zauważyć, że plik klucza może zawierać tylko klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="c694c-119">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="c694c-120">Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnych nazwach](../../../standard/assembly/create-use-strong-named.md) i [Opóźnianie podpisywania zestawu](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="c694c-120">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c694c-121">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c694c-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="c694c-122">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="c694c-122">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="c694c-123">Kliknij stronę **Właściwości Podpisywania.**</span><span class="sxs-lookup"><span data-stu-id="c694c-123">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="c694c-124">Zmodyfikuj właściwość **Wybierz właściwość pliku klucza silnej nazwy.**</span><span class="sxs-lookup"><span data-stu-id="c694c-124">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="c694c-125">Można programowo uzyskać dostęp do <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>tej opcji kompilatora z .</span><span class="sxs-lookup"><span data-stu-id="c694c-125">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c694c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c694c-126">See also</span></span>

- [<span data-ttu-id="c694c-127">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="c694c-127">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="c694c-128">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="c694c-128">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
