---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 770dcad385c522a548a0c6fd3b6ef02dfbac82f5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649715"
---
# <a name="-delaysign"></a><span data-ttu-id="2e85c-102">-delaysign</span><span class="sxs-lookup"><span data-stu-id="2e85c-102">-delaysign</span></span>
<span data-ttu-id="2e85c-103">Określa, czy zestaw zostanie podpisany całkowicie czy częściowo.</span><span class="sxs-lookup"><span data-stu-id="2e85c-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e85c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e85c-104">Syntax</span></span>  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2e85c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2e85c-105">Arguments</span></span>  
 <span data-ttu-id="2e85c-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="2e85c-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="2e85c-107">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="2e85c-107">Optional.</span></span> <span data-ttu-id="2e85c-108">Użyj `-delaysign-` Jeśli chcesz, aby podpisać zestaw całkowicie.</span><span class="sxs-lookup"><span data-stu-id="2e85c-108">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="2e85c-109">Użyj `-delaysign+` Jeśli chcesz umieścić klucz publiczny w zestaw i rezerwa ilości miejsca na skrót podpisanego.</span><span class="sxs-lookup"><span data-stu-id="2e85c-109">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="2e85c-110">Wartość domyślna to `-delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="2e85c-110">The default is `-delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e85c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e85c-111">Remarks</span></span>  
 <span data-ttu-id="2e85c-112">`-delaysign` Opcja nie ma wpływu, chyba że używana z [- keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) lub [- keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="2e85c-112">The `-delaysign` option has no effect unless used with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="2e85c-113">W przypadku żądania całkowicie podpisanego zestawu, kompilator tworzy skrót pliku który zawiera manifest (metadane zestawu) i podpisuje skrót przy użyciu klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="2e85c-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="2e85c-114">Wynikowy podpis cyfrowy jest przechowywany w pliku, który zawiera manifest.</span><span class="sxs-lookup"><span data-stu-id="2e85c-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="2e85c-115">Gdy zestaw jest podpisany z opóźnieniem, kompilator nie obliczanie oraz przechowywanie miejsce na podpis, ale rezerwy w pliku, aby podpis mógł zostać dodany później.</span><span class="sxs-lookup"><span data-stu-id="2e85c-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="2e85c-116">Na przykład za pomocą `-delaysign+`, Deweloper w organizacji mogą dystrybuować testu niepodpisane wersje zestawu, który testerów może rejestrować z globalnej pamięci podręcznej i używać.</span><span class="sxs-lookup"><span data-stu-id="2e85c-116">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="2e85c-117">Po zakończeniu pracy w zestawie osoba odpowiedzialna za klucz prywatny organizacji można całkowicie podpisać zestaw.</span><span class="sxs-lookup"><span data-stu-id="2e85c-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="2e85c-118">Ta segmentacji poszczególnych chroni klucz prywatny organizacji przed ujawnieniem, pozwalając wszystkich deweloperów pracowało nad zestawów.</span><span class="sxs-lookup"><span data-stu-id="2e85c-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="2e85c-119">Zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) więcej informacji na temat podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="2e85c-119">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="2e85c-120">Aby ustawić delaysign — w programie Visual Studio zintegrowane środowisko projektowe</span><span class="sxs-lookup"><span data-stu-id="2e85c-120">To set -delaysign in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="2e85c-121">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="2e85c-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="2e85c-122">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="2e85c-122">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="2e85c-123">Kliknij przycisk **podpisywanie** kartę.</span><span class="sxs-lookup"><span data-stu-id="2e85c-123">Click the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="2e85c-124">Ustaw wartość w **opóźnienie logowania tylko** pole.</span><span class="sxs-lookup"><span data-stu-id="2e85c-124">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e85c-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e85c-125">See also</span></span>

- [<span data-ttu-id="2e85c-126">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e85c-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="2e85c-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="2e85c-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="2e85c-128">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="2e85c-128">-keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [<span data-ttu-id="2e85c-129">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="2e85c-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
