---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 99f2b9d65f3c2a128e026666c5efb384e22643f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403151"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="b27b7-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="b27b7-102">-moduleassemblyname</span></span>
<span data-ttu-id="b27b7-103">Określa nazwę zestawu, którego częścią ma być ten moduł.</span><span class="sxs-lookup"><span data-stu-id="b27b7-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b27b7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b27b7-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="b27b7-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b27b7-105">Arguments</span></span>  
  
|<span data-ttu-id="b27b7-106">Termin</span><span class="sxs-lookup"><span data-stu-id="b27b7-106">Term</span></span>|<span data-ttu-id="b27b7-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="b27b7-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="b27b7-108">Nazwa zestawu, którego częścią ma być ten moduł.</span><span class="sxs-lookup"><span data-stu-id="b27b7-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b27b7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b27b7-109">Remarks</span></span>  
 <span data-ttu-id="b27b7-110">Kompilator przetwarza `-moduleassemblyname` opcję tylko wtedy, gdy została `-target:module` określona opcja.</span><span class="sxs-lookup"><span data-stu-id="b27b7-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="b27b7-111">Powoduje to, że kompilator tworzy moduł.</span><span class="sxs-lookup"><span data-stu-id="b27b7-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="b27b7-112">Moduł utworzony przez kompilator jest prawidłowy tylko dla zestawu określonego przy użyciu `-moduleassemblyname` opcji.</span><span class="sxs-lookup"><span data-stu-id="b27b7-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="b27b7-113">Jeśli umieścisz moduł w innym zestawie, wystąpią błędy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b27b7-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="b27b7-114">Ta `-moduleassemblyname` opcja jest wymagana tylko wtedy, gdy są spełnione następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="b27b7-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="b27b7-115">Typ danych w module wymaga dostępu do `Friend` typu w przywoływanym zestawie.</span><span class="sxs-lookup"><span data-stu-id="b27b7-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="b27b7-116">Przywoływany zestaw ma udzielony dostęp do zestawu, do którego zostanie skompilowany moduł.</span><span class="sxs-lookup"><span data-stu-id="b27b7-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="b27b7-117">Aby uzyskać więcej informacji na temat tworzenia modułu, zobacz [-Target (Visual Basic)](target.md).</span><span class="sxs-lookup"><span data-stu-id="b27b7-117">For more information about creating a module, see [-target (Visual Basic)](target.md).</span></span> <span data-ttu-id="b27b7-118">Aby uzyskać więcej informacji na temat znajomych zestawów, zobacz [zaprzyjaźnione zestawy](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="b27b7-118">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b27b7-119">`-moduleassemblyname`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="b27b7-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b27b7-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b27b7-120">See also</span></span>

- [<span data-ttu-id="b27b7-121">Instrukcje: kompilowanie zestawu wieloplikowego</span><span class="sxs-lookup"><span data-stu-id="b27b7-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="b27b7-122">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b27b7-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="b27b7-123">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b27b7-123">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="b27b7-124">-main</span><span class="sxs-lookup"><span data-stu-id="b27b7-124">-main</span></span>](main.md)
- [<span data-ttu-id="b27b7-125">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b27b7-125">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="b27b7-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="b27b7-126">-addmodule</span></span>](addmodule.md)
- [<span data-ttu-id="b27b7-127">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="b27b7-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="b27b7-128">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="b27b7-128">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="b27b7-129">Zaprzyjaźnione zestawy</span><span class="sxs-lookup"><span data-stu-id="b27b7-129">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
