---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: a612a68cffd927f3e360406cca6d9daae4f66c86
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775633"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="e5fcc-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="e5fcc-102">-moduleassemblyname</span></span>
<span data-ttu-id="e5fcc-103">Określa nazwę zestawu, którego częścią ma być ten moduł.</span><span class="sxs-lookup"><span data-stu-id="e5fcc-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5fcc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5fcc-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="e5fcc-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e5fcc-105">Arguments</span></span>  
  
|<span data-ttu-id="e5fcc-106">Termin</span><span class="sxs-lookup"><span data-stu-id="e5fcc-106">Term</span></span>|<span data-ttu-id="e5fcc-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="e5fcc-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="e5fcc-108">Nazwa zestawu, którego częścią ma być ten moduł.</span><span class="sxs-lookup"><span data-stu-id="e5fcc-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5fcc-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5fcc-109">Remarks</span></span>  
 <span data-ttu-id="e5fcc-110">Kompilator przetwarza opcję `-moduleassemblyname` tylko wtedy, gdy została określona opcja `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="e5fcc-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="e5fcc-111">Powoduje to, że kompilator tworzy moduł.</span><span class="sxs-lookup"><span data-stu-id="e5fcc-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="e5fcc-112">Moduł utworzony przez kompilator jest prawidłowy tylko dla zestawu określonego przy użyciu opcji `-moduleassemblyname`.</span><span class="sxs-lookup"><span data-stu-id="e5fcc-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="e5fcc-113">Jeśli umieścisz moduł w innym zestawie, wystąpią błędy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e5fcc-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="e5fcc-114">Opcja `-moduleassemblyname` jest wymagana tylko wtedy, gdy są spełnione następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="e5fcc-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="e5fcc-115">Typ danych w module wymaga dostępu do typu `Friend` w przywoływanym zestawie.</span><span class="sxs-lookup"><span data-stu-id="e5fcc-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="e5fcc-116">Przywoływany zestaw ma udzielony dostęp do zestawu, do którego zostanie skompilowany moduł.</span><span class="sxs-lookup"><span data-stu-id="e5fcc-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="e5fcc-117">Aby uzyskać więcej informacji na temat tworzenia modułu, zobacz [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="e5fcc-117">For more information about creating a module, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="e5fcc-118">Aby uzyskać więcej informacji na temat znajomych zestawów, zobacz [zaprzyjaźnione zestawy](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="e5fcc-118">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5fcc-119">Opcja `-moduleassemblyname` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e5fcc-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5fcc-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5fcc-120">See also</span></span>

- [<span data-ttu-id="e5fcc-121">Instrukcje: kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="e5fcc-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="e5fcc-122">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e5fcc-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e5fcc-123">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5fcc-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="e5fcc-124">-main</span><span class="sxs-lookup"><span data-stu-id="e5fcc-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="e5fcc-125">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5fcc-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="e5fcc-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="e5fcc-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [<span data-ttu-id="e5fcc-127">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="e5fcc-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="e5fcc-128">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="e5fcc-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="e5fcc-129">Przyjazne zestawy</span><span class="sxs-lookup"><span data-stu-id="e5fcc-129">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
