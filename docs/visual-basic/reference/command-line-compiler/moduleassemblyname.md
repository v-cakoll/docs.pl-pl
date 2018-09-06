---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 479f9f639548eb81351d1df3f8f08b29b393cba1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890886"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="50f92-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="50f92-102">-moduleassemblyname</span></span>
<span data-ttu-id="50f92-103">Określa nazwę zestawu, który będzie należeć tego modułu.</span><span class="sxs-lookup"><span data-stu-id="50f92-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50f92-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50f92-104">Syntax</span></span>  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="50f92-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="50f92-105">Arguments</span></span>  
  
|<span data-ttu-id="50f92-106">Termin</span><span class="sxs-lookup"><span data-stu-id="50f92-106">Term</span></span>|<span data-ttu-id="50f92-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="50f92-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="50f92-108">Nazwa zestawu, który będzie należeć tego modułu.</span><span class="sxs-lookup"><span data-stu-id="50f92-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50f92-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50f92-109">Remarks</span></span>  
 <span data-ttu-id="50f92-110">Procesy kompilatora `-moduleassemblyname` tylko wtedy, gdy opcja `-target:module` określono opcję.</span><span class="sxs-lookup"><span data-stu-id="50f92-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="50f92-111">Powoduje to, że kompilator Utwórz moduł.</span><span class="sxs-lookup"><span data-stu-id="50f92-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="50f92-112">Moduł, który został utworzony przez kompilator jest prawidłowy tylko w przypadku zestawu określony za pomocą `-moduleassemblyname` opcji.</span><span class="sxs-lookup"><span data-stu-id="50f92-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="50f92-113">Jeśli umieścisz modułu w innym zestawie będzie pojawiają się błędy czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="50f92-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="50f92-114">`-moduleassemblyname` Opcja jest potrzebna tylko wtedy, gdy spełnione są poniższe warunki:</span><span class="sxs-lookup"><span data-stu-id="50f92-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
-   <span data-ttu-id="50f92-115">Typ danych w module musi mieć dostęp do `Friend` typu w zestawie odwołania.</span><span class="sxs-lookup"><span data-stu-id="50f92-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
-   <span data-ttu-id="50f92-116">Przywoływany zestaw przyznał prawa dostępu do zestawu friend do zestawu, do którego zostanie skompilowany moduł.</span><span class="sxs-lookup"><span data-stu-id="50f92-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="50f92-117">Aby uzyskać więcej informacji na temat tworzenia modułu, zobacz [/TARGET (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="50f92-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="50f92-118">Aby uzyskać więcej informacji na temat przyjaznych zestawów, zobacz [przyjaznych zestawów](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="50f92-118">For more information about friend assemblies, see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50f92-119">`-moduleassemblyname` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilacji z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="50f92-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f92-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50f92-120">See Also</span></span>  
 [<span data-ttu-id="50f92-121">Instrukcje: kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="50f92-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="50f92-122">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="50f92-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="50f92-123">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50f92-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="50f92-124">-main</span><span class="sxs-lookup"><span data-stu-id="50f92-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)  
 [<span data-ttu-id="50f92-125">— Odwołanie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50f92-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="50f92-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="50f92-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [<span data-ttu-id="50f92-127">Zestawy i globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="50f92-127">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="50f92-128">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="50f92-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="50f92-129">Przyjazne zestawy</span><span class="sxs-lookup"><span data-stu-id="50f92-129">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)
