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
ms.openlocfilehash: 6c42e351808281d90eafdb6e61a3f1736ef15c9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="delaysign"></a><span data-ttu-id="81f9f-102">/delaysign</span><span class="sxs-lookup"><span data-stu-id="81f9f-102">/delaysign</span></span>
<span data-ttu-id="81f9f-103">Określa, czy zestaw zostanie podpisany całkowicie czy częściowo.</span><span class="sxs-lookup"><span data-stu-id="81f9f-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81f9f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81f9f-104">Syntax</span></span>  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="81f9f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="81f9f-105">Arguments</span></span>  
 <span data-ttu-id="81f9f-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="81f9f-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="81f9f-107">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="81f9f-107">Optional.</span></span> <span data-ttu-id="81f9f-108">Użyj `/delaysign-` Jeśli chcesz całkowicie podpisane zestawu.</span><span class="sxs-lookup"><span data-stu-id="81f9f-108">Use `/delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="81f9f-109">Użyj `/delaysign+` Jeśli chcesz umieścić klucz publiczny w zestawu i Rezerwacja miejsca na podpisem wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="81f9f-109">Use `/delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="81f9f-110">Wartość domyślna to `/delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="81f9f-110">The default is `/delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81f9f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="81f9f-111">Remarks</span></span>  
 <span data-ttu-id="81f9f-112">`/delaysign` Opcja nie ma znaczenia, chyba że używana z [/KeyFile](../../../visual-basic/reference/command-line-compiler/keyfile.md) lub [/KeyContainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="81f9f-112">The `/delaysign` option has no effect unless used with [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="81f9f-113">Gdy użytkownik żąda zestawem całkowicie podpisane, kompilator tworzy skrót pliku, który zawiera manifest (metadanych zestawu) i podpisuje ten skrót z kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="81f9f-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="81f9f-114">Wynikowy podpis cyfrowy jest przechowywany w pliku, który zawiera manifest.</span><span class="sxs-lookup"><span data-stu-id="81f9f-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="81f9f-115">Jeśli zestaw jest podpisywany z opóźnieniem, kompilator nie obliczania i przechowywania podpisu, ale rezerw miejsca w pliku, aby później można dodać podpisu.</span><span class="sxs-lookup"><span data-stu-id="81f9f-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="81f9f-116">Na przykład za pomocą `/delaysign+`, deweloperów w organizacji można rozpowszechniać testu bez znaku testerów można zarejestrować przy użyciu pamięci podręcznej GAC i korzystać z zestawu.</span><span class="sxs-lookup"><span data-stu-id="81f9f-116">For example, by using `/delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="81f9f-117">Po zakończeniu pracy w zestawie osoba odpowiedzialna za klucz prywatny organizacji można pełni podpisać zestawu.</span><span class="sxs-lookup"><span data-stu-id="81f9f-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="81f9f-118">Ta segmentacji poszczególnych chroni klucz prywatny organizacji przed ujawnieniem, umożliwiając wszystkich deweloperów do pracy z zestawów.</span><span class="sxs-lookup"><span data-stu-id="81f9f-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="81f9f-119">Zobacz [tworzenie i zestawy Using Strong-Named](https://msdn.microsoft.com/library/xwb8f617) Aby uzyskać więcej informacji na temat podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="81f9f-119">See [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) for more information on signing an assembly.</span></span>  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="81f9f-120">Aby ustawić/DelaySign w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="81f9f-120">To set /delaysign in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="81f9f-121">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="81f9f-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="81f9f-122">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="81f9f-122">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="81f9f-123">Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="81f9f-123">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="81f9f-124">Kliknij przycisk **podpisywanie** kartę.</span><span class="sxs-lookup"><span data-stu-id="81f9f-124">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="81f9f-125">Ustaw wartość **opóźnienie tylko znak** pole.</span><span class="sxs-lookup"><span data-stu-id="81f9f-125">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81f9f-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81f9f-126">See Also</span></span>  
 [<span data-ttu-id="81f9f-127">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81f9f-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="81f9f-128">/ KeyFile</span><span class="sxs-lookup"><span data-stu-id="81f9f-128">/keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="81f9f-129">/ KeyContainer</span><span class="sxs-lookup"><span data-stu-id="81f9f-129">/keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [<span data-ttu-id="81f9f-130">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="81f9f-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
