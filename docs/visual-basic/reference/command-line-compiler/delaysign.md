---
title: /delaysign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b4d29f99d0c375eebee0f477720cb9a22172dddb
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="delaysign"></a><span data-ttu-id="f6a4e-102">/delaysign</span><span class="sxs-lookup"><span data-stu-id="f6a4e-102">/delaysign</span></span>
<span data-ttu-id="f6a4e-103">Określa, czy zestaw zostanie podpisany całkowicie czy częściowo.</span><span class="sxs-lookup"><span data-stu-id="f6a4e-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6a4e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6a4e-104">Syntax</span></span>  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f6a4e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f6a4e-105">Arguments</span></span>  
 <span data-ttu-id="f6a4e-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="f6a4e-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="f6a4e-107">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f6a4e-107">Optional.</span></span> <span data-ttu-id="f6a4e-108">Użyj `/delaysign-` Jeśli chcesz całkowicie podpisane zestawu.</span><span class="sxs-lookup"><span data-stu-id="f6a4e-108">Use `/delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="f6a4e-109">Użyj `/delaysign+` Jeśli chcesz umieścić klucz publiczny w zestawu i Rezerwacja miejsca na podpisem wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="f6a4e-109">Use `/delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="f6a4e-110">Wartość domyślna to `/delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="f6a4e-110">The default is `/delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6a4e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6a4e-111">Remarks</span></span>  
 <span data-ttu-id="f6a4e-112">`/delaysign` Opcja nie ma znaczenia, chyba że używana z [/KeyFile](../../../visual-basic/reference/command-line-compiler/keyfile.md) lub [/KeyContainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="f6a4e-112">The `/delaysign` option has no effect unless used with [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="f6a4e-113">Gdy użytkownik żąda zestawem całkowicie podpisane, kompilator tworzy skrót pliku, który zawiera manifest (metadanych zestawu) i podpisuje ten skrót z kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="f6a4e-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="f6a4e-114">Wynikowy podpis cyfrowy jest przechowywany w pliku, który zawiera manifest.</span><span class="sxs-lookup"><span data-stu-id="f6a4e-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="f6a4e-115">Jeśli zestaw jest podpisywany z opóźnieniem, kompilator nie obliczania i przechowywania podpisu, ale rezerw miejsca w pliku, aby później można dodać podpisu.</span><span class="sxs-lookup"><span data-stu-id="f6a4e-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="f6a4e-116">Na przykład za pomocą `/delaysign+`, deweloperów w organizacji można rozpowszechniać testu bez znaku testerów można zarejestrować przy użyciu pamięci podręcznej GAC i korzystać z zestawu.</span><span class="sxs-lookup"><span data-stu-id="f6a4e-116">For example, by using `/delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="f6a4e-117">Po zakończeniu pracy w zestawie osoba odpowiedzialna za klucz prywatny organizacji można pełni podpisać zestawu.</span><span class="sxs-lookup"><span data-stu-id="f6a4e-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="f6a4e-118">Ta segmentacji poszczególnych chroni klucz prywatny organizacji przed ujawnieniem, umożliwiając wszystkich deweloperów do pracy z zestawów.</span><span class="sxs-lookup"><span data-stu-id="f6a4e-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="f6a4e-119">Zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="f6a4e-119">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="f6a4e-120">Aby ustawić/DelaySign w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="f6a4e-120">To set /delaysign in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="f6a4e-121">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="f6a4e-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f6a4e-122">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="f6a4e-122">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="f6a4e-123">Kliknij przycisk **podpisywanie** kartę.</span><span class="sxs-lookup"><span data-stu-id="f6a4e-123">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="f6a4e-124">Ustaw wartość **opóźnienie tylko znak** pole.</span><span class="sxs-lookup"><span data-stu-id="f6a4e-124">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6a4e-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6a4e-125">See Also</span></span>  
 [<span data-ttu-id="f6a4e-126">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6a4e-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="f6a4e-127">/keyfile</span><span class="sxs-lookup"><span data-stu-id="f6a4e-127">/keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="f6a4e-128">/keycontainer</span><span class="sxs-lookup"><span data-stu-id="f6a4e-128">/keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [<span data-ttu-id="f6a4e-129">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="f6a4e-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
