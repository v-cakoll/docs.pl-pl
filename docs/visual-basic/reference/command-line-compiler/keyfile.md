---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: cffc3c5f0ff3dd48ca2c74bde346a967b209dc5f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266745"
---
# <a name="-keyfile"></a><span data-ttu-id="8c314-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="8c314-102">-keyfile</span></span>
<span data-ttu-id="8c314-103">Określa plik zawierający klucz lub parę kluczy, aby nadać zestawowi silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="8c314-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c314-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c314-104">Syntax</span></span>  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="8c314-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8c314-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="8c314-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8c314-106">Required.</span></span> <span data-ttu-id="8c314-107">Plik zawierający klucz.</span><span class="sxs-lookup"><span data-stu-id="8c314-107">File that contains the key.</span></span> <span data-ttu-id="8c314-108">Jeśli nazwa pliku zawiera spację, należy ją ująć w cudzysłów (" ").</span><span class="sxs-lookup"><span data-stu-id="8c314-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c314-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c314-109">Remarks</span></span>  
 <span data-ttu-id="8c314-110">Kompilator wstawia klucz publiczny do manifestu zestawu, a następnie podpisuje końcowy zestaw za pomocą klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="8c314-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="8c314-111">Aby wygenerować `sn -k file` plik klucza, wpisz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="8c314-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="8c314-112">Aby uzyskać więcej informacji, zobacz [Sn.exe (Narzędzie Silnej nazwy).](../../../framework/tools/sn-exe-strong-name-tool.md)</span><span class="sxs-lookup"><span data-stu-id="8c314-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="8c314-113">Jeśli kompilujesz `-target:module`z , nazwa pliku klucza jest utrzymywana w module i włączona do zestawu, który jest tworzony podczas kompilowania zestawu z [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="8c314-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="8c314-114">Informacje o szyfrowaniu można również przekazać do kompilatora za pomocą [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="8c314-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="8c314-115">Użyj [-delaysign,](../../../visual-basic/reference/command-line-compiler/delaysign.md) jeśli chcesz częściowo podpisanyzesśmy.</span><span class="sxs-lookup"><span data-stu-id="8c314-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="8c314-116">Można również określić tę opcję jako<xref:System.Reflection.AssemblyKeyFileAttribute>atrybut niestandardowy ( ) w kodzie źródłowym dla dowolnego modułu języka pośredniego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8c314-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="8c314-117">W przypadku, gdy zarówno `-keyfile` i [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) są określone (przez opcję wiersza polecenia lub atrybutu niestandardowego) w tej samej kompilacji, kompilator najpierw próbuje kontenera klucza.</span><span class="sxs-lookup"><span data-stu-id="8c314-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="8c314-118">Jeśli to się powiedzie, zestaw jest podpisany z informacjami w kontenerze kluczy.</span><span class="sxs-lookup"><span data-stu-id="8c314-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="8c314-119">Jeśli kompilator nie znajdzie kontenera kluczy, `-keyfile`próbuje plik określony za pomocą pliku .</span><span class="sxs-lookup"><span data-stu-id="8c314-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="8c314-120">Jeśli to się powiedzie, zestaw jest podpisany z informacjami w pliku klucza, a `sn -i`informacje o kluczu są instalowane w kontenerze kluczy (podobnie jak), tak aby w następnej kompilacji kontener kluczy był prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8c314-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="8c314-121">Należy zauważyć, że plik klucza może zawierać tylko klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="8c314-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="8c314-122">Zobacz [Tworzenie i używanie zestawów o silnych nazwach, aby](../../../standard/assembly/create-use-strong-named.md) uzyskać więcej informacji na temat podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="8c314-122">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c314-123">Opcja `-keyfile` nie jest dostępna z poziomu środowiska programistycznego programu Visual Studio; jest on dostępny tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="8c314-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="8c314-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c314-124">Example</span></span>

<span data-ttu-id="8c314-125">Poniższy kod kompiluje plik `Input.vb` źródłowy i określa plik klucza.</span><span class="sxs-lookup"><span data-stu-id="8c314-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a><span data-ttu-id="8c314-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c314-126">See also</span></span>

- [<span data-ttu-id="8c314-127">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="8c314-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="8c314-128">Visual Basic Kompilator wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="8c314-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="8c314-129">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c314-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="8c314-130">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="8c314-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
