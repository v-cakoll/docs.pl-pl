---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: be2ad1416e801398fb513593c7f3828e5488bfaf
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005524"
---
# <a name="-keycontainer"></a><span data-ttu-id="9e09e-102">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="9e09e-102">-keycontainer</span></span>
<span data-ttu-id="9e09e-103">Określa nazwę kontenera kluczy, aby nadać zestawowi silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="9e09e-103">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e09e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e09e-104">Syntax</span></span>  
  
```console  
-keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="9e09e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9e09e-105">Arguments</span></span>  
  
|<span data-ttu-id="9e09e-106">Termin</span><span class="sxs-lookup"><span data-stu-id="9e09e-106">Term</span></span>|<span data-ttu-id="9e09e-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="9e09e-107">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="9e09e-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9e09e-108">Required.</span></span> <span data-ttu-id="9e09e-109">Plik kontenera, który zawiera klucz.</span><span class="sxs-lookup"><span data-stu-id="9e09e-109">Container file that contains the key.</span></span> <span data-ttu-id="9e09e-110">Nazwa pliku powinna być ujęta w cudzysłów (""), jeśli nazwa zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="9e09e-110">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e09e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e09e-111">Remarks</span></span>  
 <span data-ttu-id="9e09e-112">Kompilator tworzy składnik udostępniony, wstawiając klucz publiczny do manifestu zestawu i podpisując końcowy zestaw z kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="9e09e-112">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="9e09e-113">Aby wygenerować plik klucza, wpisz `sn -k file` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="9e09e-113">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="9e09e-114">Opcja `-i` instaluje parę kluczy w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="9e09e-114">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="9e09e-115">Aby uzyskać więcej informacji, zobacz [SN. exe (Narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="9e09e-115">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="9e09e-116">W przypadku kompilowania z `-target:module` nazwa pliku klucza jest przechowywana w module i wbudowana w zestaw, który jest tworzony podczas kompilowania zestawu za pomocą [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="9e09e-116">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="9e09e-117">Możesz również określić tę opcję jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyNameAttribute>) w kodzie źródłowym dla dowolnego modułu języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9e09e-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="9e09e-118">Możesz również przekazać informacje o szyfrowaniu do kompilatora za pomocą [-KeyFile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span><span class="sxs-lookup"><span data-stu-id="9e09e-118">You can also pass your encryption information to the compiler with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span></span> <span data-ttu-id="9e09e-119">Użyj [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) , jeśli chcesz użyć częściowo podpisanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="9e09e-119">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="9e09e-120">Zobacz [Tworzenie i używanie zestawów o silnych nazwach,](../../../standard/assembly/create-use-strong-named.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="9e09e-120">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e09e-121">Opcja `-keycontainer` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9e09e-121">The `-keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e09e-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e09e-122">Example</span></span>  
 <span data-ttu-id="9e09e-123">Poniższy kod kompiluje plik źródłowy `Input.vb` i Określa kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="9e09e-123">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```console  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e09e-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e09e-124">See also</span></span>

- [<span data-ttu-id="9e09e-125">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="9e09e-125">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="9e09e-126">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e09e-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="9e09e-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="9e09e-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="9e09e-128">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="9e09e-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
