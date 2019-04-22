---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: c13f34c23cad9c909c2c5bd3447f1a8fa53f9b4d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833330"
---
# <a name="-keyfile"></a><span data-ttu-id="6d03b-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="6d03b-102">-keyfile</span></span>
<span data-ttu-id="6d03b-103">Określa plik zawierający klucz lub parę kluczy, aby zapewnić zestawu z silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="6d03b-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d03b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d03b-104">Syntax</span></span>  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="6d03b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6d03b-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="6d03b-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="6d03b-106">Required.</span></span> <span data-ttu-id="6d03b-107">Plik, który zawiera klucz.</span><span class="sxs-lookup"><span data-stu-id="6d03b-107">File that contains the key.</span></span> <span data-ttu-id="6d03b-108">Jeśli nazwa pliku zawiera spację, nazwę należy ująć w znaki cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="6d03b-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d03b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d03b-109">Remarks</span></span>  
 <span data-ttu-id="6d03b-110">Kompilator wstawia klucz publiczny w manifeście zestawu, a następnie podpisuje ostateczny zestaw przy użyciu klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="6d03b-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="6d03b-111">Aby wygenerować plik klucza, wpisz `sn -k file` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="6d03b-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="6d03b-112">Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="6d03b-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="6d03b-113">Jeśli kompilujesz z opcją `-target:module`, nazwę pliku klucza jest przechowywany w module i włączyć do zestawu, który jest tworzony podczas kompilowania zestawu za pomocą [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="6d03b-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="6d03b-114">Można również przekazać szyfrowania informacji do kompilatora przy użyciu [- keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="6d03b-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="6d03b-115">Użyj [- delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) Jeśli chcesz, aby częściowo podpisany zestawu.</span><span class="sxs-lookup"><span data-stu-id="6d03b-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="6d03b-116">Można również określić tę opcję jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyFileAttribute>) w kodzie źródłowym dla każdego modułu języka pośredniego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6d03b-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="6d03b-117">W przypadku obu `-keyfile` i [- keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) podano (przez opcję wiersza polecenia lub przez atrybut niestandardowy) w tej samej kompilacji kompilator po raz pierwszy próbuje kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="6d03b-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="6d03b-118">Jeśli się to powiedzie, zestaw zostanie podpisany przy użyciu informacji z kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="6d03b-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="6d03b-119">Jeśli kompilator nie znajdzie kontenera kluczy, spróbuje pliku określonego przez `-keyfile`.</span><span class="sxs-lookup"><span data-stu-id="6d03b-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="6d03b-120">Jeśli operacja się powiedzie, zestaw zostanie podpisany przy użyciu informacji z pliku klucza i informacje o kluczu jest zainstalowany w kontenerze kluczy (podobnie jak `sn -i`) tak, aby przy następnej kompilacji będzie obowiązywać kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="6d03b-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="6d03b-121">Należy pamiętać, że plik klucza może zawierać tylko klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="6d03b-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="6d03b-122">Zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) więcej informacji na temat podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="6d03b-122">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d03b-123">`-keyfile` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="6d03b-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d03b-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d03b-124">Example</span></span>  
 <span data-ttu-id="6d03b-125">Poniższy kod kompiluje plik źródłowy `Input.vb` i określa plik klucza.</span><span class="sxs-lookup"><span data-stu-id="6d03b-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d03b-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d03b-126">See also</span></span>

- [<span data-ttu-id="6d03b-127">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="6d03b-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="6d03b-128">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6d03b-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="6d03b-129">— Odwołanie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d03b-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="6d03b-130">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="6d03b-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
