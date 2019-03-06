---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: a16dd616c8a38dea4bd1779e4feea779b3a18e2d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375301"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="c0165-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="c0165-102">-moduleassemblyname</span></span>
<span data-ttu-id="c0165-103">Określa nazwę zestawu, który będzie należeć tego modułu.</span><span class="sxs-lookup"><span data-stu-id="c0165-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0165-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0165-104">Syntax</span></span>  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="c0165-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c0165-105">Arguments</span></span>  
  
|<span data-ttu-id="c0165-106">Termin</span><span class="sxs-lookup"><span data-stu-id="c0165-106">Term</span></span>|<span data-ttu-id="c0165-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="c0165-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="c0165-108">Nazwa zestawu, który będzie należeć tego modułu.</span><span class="sxs-lookup"><span data-stu-id="c0165-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0165-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0165-109">Remarks</span></span>  
 <span data-ttu-id="c0165-110">Procesy kompilatora `-moduleassemblyname` tylko wtedy, gdy opcja `-target:module` określono opcję.</span><span class="sxs-lookup"><span data-stu-id="c0165-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="c0165-111">Powoduje to, że kompilator Utwórz moduł.</span><span class="sxs-lookup"><span data-stu-id="c0165-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="c0165-112">Moduł, który został utworzony przez kompilator jest prawidłowy tylko w przypadku zestawu określony za pomocą `-moduleassemblyname` opcji.</span><span class="sxs-lookup"><span data-stu-id="c0165-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="c0165-113">Jeśli umieścisz modułu w innym zestawie będzie pojawiają się błędy czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c0165-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="c0165-114">`-moduleassemblyname` Opcja jest potrzebna tylko wtedy, gdy spełnione są poniższe warunki:</span><span class="sxs-lookup"><span data-stu-id="c0165-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
-   <span data-ttu-id="c0165-115">Typ danych w module musi mieć dostęp do `Friend` typu w zestawie odwołania.</span><span class="sxs-lookup"><span data-stu-id="c0165-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
-   <span data-ttu-id="c0165-116">Przywoływany zestaw przyznał prawa dostępu do zestawu friend do zestawu, do którego zostanie skompilowany moduł.</span><span class="sxs-lookup"><span data-stu-id="c0165-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="c0165-117">Aby uzyskać więcej informacji na temat tworzenia modułu, zobacz [/TARGET (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="c0165-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="c0165-118">Aby uzyskać więcej informacji na temat przyjaznych zestawów, zobacz [przyjaznych zestawów](../../../standard/assembly/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="c0165-118">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0165-119">`-moduleassemblyname` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilacji z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c0165-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0165-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0165-120">See also</span></span>
- [<span data-ttu-id="c0165-121">Instrukcje: Kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="c0165-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="c0165-122">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0165-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c0165-123">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0165-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="c0165-124">-main</span><span class="sxs-lookup"><span data-stu-id="c0165-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="c0165-125">— Odwołanie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0165-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="c0165-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="c0165-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [<span data-ttu-id="c0165-127">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="c0165-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="c0165-128">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="c0165-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="c0165-129">Przyjazne zestawy</span><span class="sxs-lookup"><span data-stu-id="c0165-129">Friend Assemblies</span></span>](../../../standard/assembly/friend-assemblies.md)
