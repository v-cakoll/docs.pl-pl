---
title: "Wystąpił błąd podczas tworzenia manifestu zestawu: &lt;komunikat o błędzie&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords: BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5e88d28ef787eb57b71d94f4ee51c09e9751dbff
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="a1fca-102">Wystąpił błąd podczas tworzenia manifestu zestawu: &lt;komunikat o błędzie&gt;</span><span class="sxs-lookup"><span data-stu-id="a1fca-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="a1fca-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora wywołuje konsolidator zestawów (znanej także jako Alink Al.exe), można wygenerować zestawu z manifestu.</span><span class="sxs-lookup"><span data-stu-id="a1fca-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="a1fca-104">Konsolidator zgłosił błąd w fazie emisji wstępnego tworzenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="a1fca-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="a1fca-105">Może to występować, jeśli występują problemy z pliku klucza lub kontener klucza określony.</span><span class="sxs-lookup"><span data-stu-id="a1fca-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="a1fca-106">Pełni podpisać zestawu, należy podać prawidłowy plik klucza, który zawiera informacje o klucze publiczne i prywatne.</span><span class="sxs-lookup"><span data-stu-id="a1fca-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="a1fca-107">Aby opóźnić Podpisz zestaw, musisz wybrać **opóźnienie tylko znak** pole wyboru i podaj prawidłowy plik klucza, który zawiera informacje o informacje o kluczu publicznym.</span><span class="sxs-lookup"><span data-stu-id="a1fca-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="a1fca-108">Klucz prywatny nie jest konieczne, gdy zestaw jest podpisywany z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="a1fca-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="a1fca-109">Aby uzyskać więcej informacji, zobacz [porady: podpisać zestaw o silnej nazwie](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="a1fca-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
 <span data-ttu-id="a1fca-110">**Identyfikator błędu:** BC30140</span><span class="sxs-lookup"><span data-stu-id="a1fca-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a1fca-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a1fca-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="a1fca-112">Sprawdź ujętego w cudzysłów komunikat i zapoznaj się temacie [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="a1fca-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="a1fca-113">więcej informacji o AL1019 i porady</span><span class="sxs-lookup"><span data-stu-id="a1fca-113">for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="a1fca-114">Jeśli błąd będzie się powtarzać, zebrać informacje dotyczące okoliczności i powiadomić pomocy technicznej firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a1fca-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1fca-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1fca-115">See Also</span></span>  
 [<span data-ttu-id="a1fca-116">Instrukcje: podpisywanie zestawu silną nazwą</span><span class="sxs-lookup"><span data-stu-id="a1fca-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="a1fca-117">Strona podpisywania, Projektant projektu</span><span class="sxs-lookup"><span data-stu-id="a1fca-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)  
 <span data-ttu-id="a1fca-118">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="a1fca-118">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
 [<span data-ttu-id="a1fca-119">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="a1fca-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
