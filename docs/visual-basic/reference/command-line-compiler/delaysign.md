---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c979ada9984ef345ffbb6b5e29c2f30595c3074d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-delaysign"></a><span data-ttu-id="ee3ed-102">-delaysign</span><span class="sxs-lookup"><span data-stu-id="ee3ed-102">-delaysign</span></span>
<span data-ttu-id="ee3ed-103">Określa, czy zestaw zostanie podpisany całkowicie czy częściowo.</span><span class="sxs-lookup"><span data-stu-id="ee3ed-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee3ed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee3ed-104">Syntax</span></span>  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ee3ed-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ee3ed-105">Arguments</span></span>  
 <span data-ttu-id="ee3ed-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ee3ed-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="ee3ed-107">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ee3ed-107">Optional.</span></span> <span data-ttu-id="ee3ed-108">Użyj `-delaysign-` Jeśli chcesz całkowicie podpisane zestawu.</span><span class="sxs-lookup"><span data-stu-id="ee3ed-108">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="ee3ed-109">Użyj `-delaysign+` Jeśli chcesz umieścić klucz publiczny w zestawu i Rezerwacja miejsca na podpisem wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="ee3ed-109">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="ee3ed-110">Wartość domyślna to `-delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="ee3ed-110">The default is `-delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee3ed-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee3ed-111">Remarks</span></span>  
 <span data-ttu-id="ee3ed-112">`-delaysign` Opcja nie ma znaczenia, chyba że używana z [- keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) lub [- keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="ee3ed-112">The `-delaysign` option has no effect unless used with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="ee3ed-113">Gdy użytkownik żąda zestawem całkowicie podpisane, kompilator tworzy skrót pliku, który zawiera manifest (metadanych zestawu) i podpisuje ten skrót z kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="ee3ed-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="ee3ed-114">Wynikowy podpis cyfrowy jest przechowywany w pliku, który zawiera manifest.</span><span class="sxs-lookup"><span data-stu-id="ee3ed-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="ee3ed-115">Jeśli zestaw jest podpisywany z opóźnieniem, kompilator nie obliczania i przechowywania podpisu, ale rezerw miejsca w pliku, aby później można dodać podpisu.</span><span class="sxs-lookup"><span data-stu-id="ee3ed-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="ee3ed-116">Na przykład za pomocą `-delaysign+`, deweloperów w organizacji można rozpowszechniać testu bez znaku testerów można zarejestrować przy użyciu pamięci podręcznej GAC i korzystać z zestawu.</span><span class="sxs-lookup"><span data-stu-id="ee3ed-116">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="ee3ed-117">Po zakończeniu pracy w zestawie osoba odpowiedzialna za klucz prywatny organizacji można pełni podpisać zestawu.</span><span class="sxs-lookup"><span data-stu-id="ee3ed-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="ee3ed-118">Ta segmentacji poszczególnych chroni klucz prywatny organizacji przed ujawnieniem, umożliwiając wszystkich deweloperów do pracy z zestawów.</span><span class="sxs-lookup"><span data-stu-id="ee3ed-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="ee3ed-119">Zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="ee3ed-119">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="ee3ed-120">Aby ustawić - delaysign w Visual Studio zintegrowane środowisko programistyczne</span><span class="sxs-lookup"><span data-stu-id="ee3ed-120">To set -delaysign in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="ee3ed-121">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="ee3ed-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ee3ed-122">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ee3ed-122">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="ee3ed-123">Kliknij przycisk **podpisywanie** kartę.</span><span class="sxs-lookup"><span data-stu-id="ee3ed-123">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="ee3ed-124">Ustaw wartość **opóźnienie tylko znak** pole.</span><span class="sxs-lookup"><span data-stu-id="ee3ed-124">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee3ed-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee3ed-125">See Also</span></span>  
 [<span data-ttu-id="ee3ed-126">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee3ed-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ee3ed-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="ee3ed-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="ee3ed-128">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="ee3ed-128">-keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [<span data-ttu-id="ee3ed-129">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="ee3ed-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
