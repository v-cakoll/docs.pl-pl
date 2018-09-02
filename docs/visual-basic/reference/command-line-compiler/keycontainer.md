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
ms.openlocfilehash: dc6453dc188e7621444b6f44b805aab9354d81f0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402064"
---
# <a name="-keycontainer"></a><span data-ttu-id="522eb-102">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="522eb-102">-keycontainer</span></span>
<span data-ttu-id="522eb-103">Określa nazwę kontenera kluczy parę kluczy zapewnić zestawu z silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="522eb-103">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="522eb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="522eb-104">Syntax</span></span>  
  
```  
-keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="522eb-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="522eb-105">Arguments</span></span>  
  
|<span data-ttu-id="522eb-106">Termin</span><span class="sxs-lookup"><span data-stu-id="522eb-106">Term</span></span>|<span data-ttu-id="522eb-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="522eb-107">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="522eb-108">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="522eb-108">Required.</span></span> <span data-ttu-id="522eb-109">Plik kontenera, który zawiera klucz.</span><span class="sxs-lookup"><span data-stu-id="522eb-109">Container file that contains the key.</span></span> <span data-ttu-id="522eb-110">Nazwę pliku należy ująć w znaki cudzysłowu (""), jeśli nazwa zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="522eb-110">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="522eb-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="522eb-111">Remarks</span></span>  
 <span data-ttu-id="522eb-112">Kompilator tworzy składnik, które można udostępnić przez wstawienie klucza publicznego do manifestu zestawu i rejestrując ostateczny zestaw przy użyciu klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="522eb-112">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="522eb-113">Aby wygenerować plik klucza, wpisz `sn -k file` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="522eb-113">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="522eb-114">`-i` Opcja instaluje parę kluczy w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="522eb-114">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="522eb-115">Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnych nazw)][Sn.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="522eb-115">For more information, see [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="522eb-116">Jeśli kompilujesz z opcją `-target:module`, nazwę pliku klucza jest przechowywany w module i włączyć do zestawu, który jest tworzony podczas kompilowania zestawu za pomocą [- addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="522eb-116">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="522eb-117">Można również określić tę opcję jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyNameAttribute>) w kodzie źródłowym dla każdego modułu języka intermediate language (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="522eb-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="522eb-118">Można również przekazać szyfrowania informacji do kompilatora przy użyciu [- keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span><span class="sxs-lookup"><span data-stu-id="522eb-118">You can also pass your encryption information to the compiler with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span></span> <span data-ttu-id="522eb-119">Użyj [- delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) Jeśli chcesz, aby częściowo podpisany zestawu.</span><span class="sxs-lookup"><span data-stu-id="522eb-119">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="522eb-120">Zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) więcej informacji na temat podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="522eb-120">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="522eb-121">`-keycontainer` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="522eb-121">The `-keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="522eb-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="522eb-122">Example</span></span>  
 <span data-ttu-id="522eb-123">Poniższy kod kompiluje plik źródłowy `Input.vb` i Określa kontener klucza.</span><span class="sxs-lookup"><span data-stu-id="522eb-123">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="522eb-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="522eb-124">See Also</span></span>  
 [<span data-ttu-id="522eb-125">Zestawy i globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="522eb-125">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="522eb-126">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="522eb-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="522eb-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="522eb-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="522eb-128">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="522eb-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
