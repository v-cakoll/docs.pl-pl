---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: b2084a1c0ee30478cdc9193cdfcb19476499ee93
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924870"
---
# <a name="-keyfile"></a><span data-ttu-id="97722-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="97722-102">-keyfile</span></span>
<span data-ttu-id="97722-103">Określa plik zawierający parę klucz lub klucz, aby nadać zestawowi silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="97722-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97722-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97722-104">Syntax</span></span>  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="97722-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="97722-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="97722-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="97722-106">Required.</span></span> <span data-ttu-id="97722-107">Plik, który zawiera klucz.</span><span class="sxs-lookup"><span data-stu-id="97722-107">File that contains the key.</span></span> <span data-ttu-id="97722-108">Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="97722-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97722-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97722-109">Remarks</span></span>  
 <span data-ttu-id="97722-110">Kompilator wstawia klucz publiczny do manifestu zestawu, a następnie podpisuje końcowy zestaw kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="97722-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="97722-111">Aby wygenerować plik klucza, wpisz `sn -k file` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="97722-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="97722-112">Aby uzyskać więcej informacji, zobacz [SN. exe (Narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="97722-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="97722-113">Jeśli kompilujesz za `-target:module`pomocą, nazwa pliku klucza jest przechowywana w module i wbudowana w zestaw, który jest tworzony podczas kompilowania zestawu za pomocą [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="97722-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="97722-114">Możesz również przekazać informacje o szyfrowaniu do kompilatora z kontenerem [](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="97722-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="97722-115">Użyj [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) , jeśli chcesz użyć częściowo podpisanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="97722-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="97722-116">Można również określić tę opcję jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyFileAttribute>) w kodzie źródłowym dowolnego modułu języka pośredniego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="97722-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="97722-117">W przypadku określenia `-keyfile` obu typów i [--kontenera](../../../visual-basic/reference/command-line-compiler/keycontainer.md) (za pomocą opcji wiersza polecenia lub przez atrybut niestandardowy) w tej samej kompilacji kompilator próbuje najpierw kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="97722-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="97722-118">Jeśli to się powiedzie, zestaw zostanie podpisany przy użyciu informacji z kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="97722-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="97722-119">Jeśli kompilator nie odnajdzie kontenera kluczy, próbuje plik określony z `-keyfile`.</span><span class="sxs-lookup"><span data-stu-id="97722-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="97722-120">Jeśli to się powiedzie, zestaw zostanie podpisany przy użyciu informacji w pliku klucza, a informacje o kluczu są instalowane w kontenerze kluczy (podobnie jak `sn -i`w przypadku), więc w następnej kompilacji kontener kluczy będzie prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="97722-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="97722-121">Należy pamiętać, że plik klucza może zawierać tylko klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="97722-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="97722-122">Zobacz [Tworzenie i używanie zestawów o silnych nazwach,](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="97722-122">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97722-123">`-keyfile` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="97722-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97722-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="97722-124">Example</span></span>  
 <span data-ttu-id="97722-125">Poniższy kod kompiluje plik `Input.vb` źródłowy i określa plik klucza.</span><span class="sxs-lookup"><span data-stu-id="97722-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="97722-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97722-126">See also</span></span>

- [<span data-ttu-id="97722-127">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="97722-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="97722-128">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="97722-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="97722-129">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97722-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="97722-130">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="97722-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
