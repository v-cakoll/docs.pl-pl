---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d682533f96b5fb56430a0826d37a9794dc8c5d8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-keycontainer"></a><span data-ttu-id="59d88-102">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="59d88-102">-keycontainer</span></span>
<span data-ttu-id="59d88-103">Określa nazwę kontenera kluczy parę kluczy zapewnić silnej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="59d88-103">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59d88-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="59d88-104">Syntax</span></span>  
  
```  
-keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="59d88-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="59d88-105">Arguments</span></span>  
  
|<span data-ttu-id="59d88-106">Termin</span><span class="sxs-lookup"><span data-stu-id="59d88-106">Term</span></span>|<span data-ttu-id="59d88-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="59d88-107">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="59d88-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="59d88-108">Required.</span></span> <span data-ttu-id="59d88-109">Plik kontenera, który zawiera klucz.</span><span class="sxs-lookup"><span data-stu-id="59d88-109">Container file that contains the key.</span></span> <span data-ttu-id="59d88-110">Nazwę pliku należy ująć w cudzysłów (""), jeśli nazwa zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="59d88-110">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59d88-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59d88-111">Remarks</span></span>  
 <span data-ttu-id="59d88-112">Kompilator tworzy składnik zabezpieczać przez wstawianie klucza publicznego do manifestu zestawu i podpisywania z kluczem prywatnym zestawie końcowym.</span><span class="sxs-lookup"><span data-stu-id="59d88-112">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="59d88-113">Aby wygenerować plik klucza, wpisz `sn -k``file` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="59d88-113">To generate a key file, type `sn -k``file` at the command line.</span></span> <span data-ttu-id="59d88-114">`-i` Opcja powoduje zainstalowanie pary kluczy do kontenera.</span><span class="sxs-lookup"><span data-stu-id="59d88-114">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="59d88-115">Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnej nazwy)][Sn.exe (narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="59d88-115">For more information, see [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="59d88-116">Jeśli kompilacji z `-target:module`, nazwa pliku klucza jest przechowywany w module i włączyć do zestawu, który jest tworzony podczas kompilowania zestawu z [- addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="59d88-116">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="59d88-117">Tę opcję można również określić jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyNameAttribute>) w kodzie źródłowym dla każdy moduł język pośredni (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="59d88-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="59d88-118">Można również przekazać do kompilatora z informacjami szyfrowania [- keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span><span class="sxs-lookup"><span data-stu-id="59d88-118">You can also pass your encryption information to the compiler with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span></span> <span data-ttu-id="59d88-119">Użyj [- delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) Jeśli chcesz częściowo podpisanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="59d88-119">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="59d88-120">Zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="59d88-120">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59d88-121">`-keycontainer` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="59d88-121">The `-keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59d88-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="59d88-122">Example</span></span>  
 <span data-ttu-id="59d88-123">Poniższy kod tworzy plik źródłowy `Input.vb` i Określa kontener klucza.</span><span class="sxs-lookup"><span data-stu-id="59d88-123">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="59d88-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59d88-124">See Also</span></span>  
 [<span data-ttu-id="59d88-125">Zestawy i globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="59d88-125">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="59d88-126">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="59d88-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="59d88-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="59d88-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="59d88-128">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="59d88-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
