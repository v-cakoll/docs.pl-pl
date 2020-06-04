---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 3f476f6b6db1a788002a938eb5ae4bbbed7a5dae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408578"
---
# <a name="-keyfile"></a><span data-ttu-id="5e71e-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="5e71e-102">-keyfile</span></span>
<span data-ttu-id="5e71e-103">Określa plik zawierający parę klucz lub klucz, aby nadać zestawowi silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="5e71e-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e71e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e71e-104">Syntax</span></span>  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="5e71e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5e71e-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="5e71e-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="5e71e-106">Required.</span></span> <span data-ttu-id="5e71e-107">Plik, który zawiera klucz.</span><span class="sxs-lookup"><span data-stu-id="5e71e-107">File that contains the key.</span></span> <span data-ttu-id="5e71e-108">Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="5e71e-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e71e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e71e-109">Remarks</span></span>  
 <span data-ttu-id="5e71e-110">Kompilator wstawia klucz publiczny do manifestu zestawu, a następnie podpisuje końcowy zestaw kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="5e71e-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="5e71e-111">Aby wygenerować plik klucza, wpisz `sn -k file` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="5e71e-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="5e71e-112">Aby uzyskać więcej informacji, zobacz [SN. exe (Narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="5e71e-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="5e71e-113">W przypadku kompilowania za pomocą `-target:module` programu nazwa pliku klucza jest przechowywana w module i włączana do zestawu, który jest tworzony podczas kompilowania zestawu za pomocą [-addmodule](addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="5e71e-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](addmodule.md).</span></span>  
  
 <span data-ttu-id="5e71e-114">Możesz również przekazać informacje o szyfrowaniu do kompilatora z [kontenerem](keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="5e71e-114">You can also pass your encryption information to the compiler with [-keycontainer](keycontainer.md).</span></span> <span data-ttu-id="5e71e-115">Użyj [-delaysign](delaysign.md) , jeśli chcesz użyć częściowo podpisanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5e71e-115">Use [-delaysign](delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="5e71e-116">Można również określić tę opcję jako atrybut niestandardowy ( <xref:System.Reflection.AssemblyKeyFileAttribute> ) w kodzie źródłowym dowolnego modułu języka pośredniego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5e71e-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="5e71e-117">W przypadku określenia obu typów `-keyfile` i [--kontenera](keycontainer.md) (za pomocą opcji wiersza polecenia lub przez atrybut niestandardowy) w tej samej kompilacji kompilator próbuje najpierw kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="5e71e-117">In case both `-keyfile` and [-keycontainer](keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="5e71e-118">Jeśli to się powiedzie, zestaw zostanie podpisany przy użyciu informacji z kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="5e71e-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="5e71e-119">Jeśli kompilator nie odnajdzie kontenera kluczy, próbuje plik określony z `-keyfile` .</span><span class="sxs-lookup"><span data-stu-id="5e71e-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="5e71e-120">Jeśli to się powiedzie, zestaw zostanie podpisany przy użyciu informacji w pliku klucza, a informacje o kluczu są instalowane w kontenerze kluczy (podobnie jak w przypadku `sn -i` ), więc w następnej kompilacji kontener kluczy będzie prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="5e71e-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="5e71e-121">Należy pamiętać, że plik klucza może zawierać tylko klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="5e71e-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="5e71e-122">Zobacz [Tworzenie i używanie zestawów o silnych nazwach,](../../../standard/assembly/create-use-strong-named.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="5e71e-122">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e71e-123">`-keyfile`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5e71e-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="5e71e-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e71e-124">Example</span></span>

<span data-ttu-id="5e71e-125">Poniższy kod kompiluje plik źródłowy `Input.vb` i określa plik klucza.</span><span class="sxs-lookup"><span data-stu-id="5e71e-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a><span data-ttu-id="5e71e-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e71e-126">See also</span></span>

- [<span data-ttu-id="5e71e-127">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="5e71e-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="5e71e-128">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e71e-128">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="5e71e-129">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e71e-129">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="5e71e-130">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="5e71e-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
