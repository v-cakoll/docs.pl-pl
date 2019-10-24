---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 2617c42d7b176806cfac0fc2247760727608261a
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775643"
---
# <a name="-keyfile"></a><span data-ttu-id="3f6cd-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="3f6cd-102">-keyfile</span></span>
<span data-ttu-id="3f6cd-103">Określa plik zawierający parę klucz lub klucz, aby nadać zestawowi silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="3f6cd-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f6cd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f6cd-104">Syntax</span></span>  
  
```console 
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="3f6cd-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3f6cd-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="3f6cd-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="3f6cd-106">Required.</span></span> <span data-ttu-id="3f6cd-107">Plik, który zawiera klucz.</span><span class="sxs-lookup"><span data-stu-id="3f6cd-107">File that contains the key.</span></span> <span data-ttu-id="3f6cd-108">Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="3f6cd-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f6cd-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f6cd-109">Remarks</span></span>  
 <span data-ttu-id="3f6cd-110">Kompilator wstawia klucz publiczny do manifestu zestawu, a następnie podpisuje końcowy zestaw kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="3f6cd-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="3f6cd-111">Aby wygenerować plik klucza, wpisz `sn -k file` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="3f6cd-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="3f6cd-112">Aby uzyskać więcej informacji, zobacz [SN. exe (Narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="3f6cd-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="3f6cd-113">W przypadku kompilowania z `-target:module` nazwa pliku klucza jest przechowywana w module i wbudowana w zestaw, który jest tworzony podczas kompilowania zestawu za pomocą [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="3f6cd-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="3f6cd-114">Możesz również przekazać informacje o szyfrowaniu do kompilatora z [kontenerem](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="3f6cd-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="3f6cd-115">Użyj [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) , jeśli chcesz użyć częściowo podpisanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3f6cd-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="3f6cd-116">Można również określić tę opcję jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyFileAttribute>) w kodzie źródłowym dowolnego modułu języka pośredniego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3f6cd-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="3f6cd-117">W przypadku określenia zarówno `-keyfile`, jak i [-](../../../visual-basic/reference/command-line-compiler/keycontainer.md) klucza (za pomocą opcji wiersza polecenia lub przez atrybut niestandardowy) w tej samej kompilacji, kompilator najpierw próbuje kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="3f6cd-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="3f6cd-118">Jeśli to się powiedzie, zestaw zostanie podpisany przy użyciu informacji z kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="3f6cd-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="3f6cd-119">Jeśli kompilator nie odnajdzie kontenera kluczy, próbuje plik określony z `-keyfile`.</span><span class="sxs-lookup"><span data-stu-id="3f6cd-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="3f6cd-120">Jeśli to się powiedzie, zestaw zostanie podpisany przy użyciu informacji w pliku klucza, a informacje o kluczu są instalowane w kontenerze kluczy (podobnym do `sn -i`), aby w następnej kompilacji kontener kluczy będzie prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="3f6cd-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="3f6cd-121">Należy pamiętać, że plik klucza może zawierać tylko klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="3f6cd-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="3f6cd-122">Zobacz [Tworzenie i używanie zestawów o silnych nazwach,](../../../standard/assembly/create-use-strong-named.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="3f6cd-122">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f6cd-123">Opcja `-keyfile` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="3f6cd-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="3f6cd-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f6cd-124">Example</span></span>

<span data-ttu-id="3f6cd-125">Poniższy kod kompiluje plik źródłowy `Input.vb` i określa plik klucza.</span><span class="sxs-lookup"><span data-stu-id="3f6cd-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a><span data-ttu-id="3f6cd-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f6cd-126">See also</span></span>

- [<span data-ttu-id="3f6cd-127">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="3f6cd-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="3f6cd-128">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3f6cd-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3f6cd-129">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f6cd-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="3f6cd-130">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="3f6cd-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
