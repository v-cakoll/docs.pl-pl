---
title: -moduleassemblyname
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
author: rpetrusha
ms.author: ronpett
ms.openlocfilehash: 0a097ea8a7e30f25a0abb877dc496fb81d1c139f
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="51701-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="51701-102">-moduleassemblyname</span></span>
<span data-ttu-id="51701-103">Określa nazwę zestawu, którego częścią ma być ten moduł.</span><span class="sxs-lookup"><span data-stu-id="51701-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51701-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="51701-104">Syntax</span></span>  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="51701-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="51701-105">Arguments</span></span>  
  
|<span data-ttu-id="51701-106">Termin</span><span class="sxs-lookup"><span data-stu-id="51701-106">Term</span></span>|<span data-ttu-id="51701-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="51701-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="51701-108">Nazwa zestawu, którego częścią ma być ten moduł.</span><span class="sxs-lookup"><span data-stu-id="51701-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51701-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51701-109">Remarks</span></span>  
 <span data-ttu-id="51701-110">Procesy kompilatora `-moduleassemblyname` tylko wtedy, gdy opcja `-target:module` określono opcję.</span><span class="sxs-lookup"><span data-stu-id="51701-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="51701-111">Powoduje to, że kompilator Utwórz moduł.</span><span class="sxs-lookup"><span data-stu-id="51701-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="51701-112">Moduł, który został utworzony przez kompilator jest prawidłowa tylko dla zestawu określony za pomocą `-moduleassemblyname` opcji.</span><span class="sxs-lookup"><span data-stu-id="51701-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="51701-113">Jeśli moduł zostanie umieszczony w innym zestawie, zostanie przeprowadzona błędów czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="51701-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="51701-114">`-moduleassemblyname` Opcja jest potrzebna tylko wtedy, gdy spełnione są poniższe warunki:</span><span class="sxs-lookup"><span data-stu-id="51701-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
-   <span data-ttu-id="51701-115">Typ danych w module musi mieć dostęp do `Friend` typu w zestawie.</span><span class="sxs-lookup"><span data-stu-id="51701-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
-   <span data-ttu-id="51701-116">Przywoływany zestaw ma przyznane dostęp do przyjaznego zestawu do zestawu, do którego zostanie utworzony moduł.</span><span class="sxs-lookup"><span data-stu-id="51701-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="51701-117">Aby uzyskać więcej informacji na temat tworzenia modułu, zobacz [/TARGET (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="51701-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="51701-118">Aby uzyskać więcej informacji na temat przyjaznych zestawów, zobacz [przyjazne zestawy](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span><span class="sxs-lookup"><span data-stu-id="51701-118">For more information about friend assemblies, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51701-119">`-moduleassemblyname` Opcja nie jest dostępne w środowisku programowania Visual Studio; będzie dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="51701-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51701-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51701-120">See Also</span></span>  
 [<span data-ttu-id="51701-121">Instrukcje: kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="51701-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="51701-122">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="51701-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="51701-123">-docelowego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51701-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="51701-124">-main</span><span class="sxs-lookup"><span data-stu-id="51701-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)  
 [<span data-ttu-id="51701-125">-odwołania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51701-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="51701-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="51701-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [<span data-ttu-id="51701-127">Zestawy i globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="51701-127">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="51701-128">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="51701-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="51701-129">Przyjazne zestawy</span><span class="sxs-lookup"><span data-stu-id="51701-129">Friend Assemblies</span></span>](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)
