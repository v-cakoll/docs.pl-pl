---
title: 'Wystąpił błąd podczas tworzenia manifestu zestawu: &lt;komunikat o błędzie&gt;'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: b3ea5b502abd318c34d957bf7f540602c53c9e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="cff97-102">Wystąpił błąd podczas tworzenia manifestu zestawu: &lt;komunikat o błędzie&gt;</span><span class="sxs-lookup"><span data-stu-id="cff97-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="cff97-103">Kompilator Visual Basic wywołuje konsolidator zestawów (znanej także jako Alink Al.exe), można wygenerować zestawu z manifestu.</span><span class="sxs-lookup"><span data-stu-id="cff97-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="cff97-104">Konsolidator zgłosił błąd w fazie emisji wstępnego tworzenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="cff97-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="cff97-105">Może to występować, jeśli występują problemy z pliku klucza lub kontener klucza określony.</span><span class="sxs-lookup"><span data-stu-id="cff97-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="cff97-106">Pełni podpisać zestawu, należy podać prawidłowy plik klucza, który zawiera informacje o klucze publiczne i prywatne.</span><span class="sxs-lookup"><span data-stu-id="cff97-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="cff97-107">Aby opóźnić Podpisz zestaw, musisz wybrać **opóźnienie tylko znak** pole wyboru i podaj prawidłowy plik klucza, który zawiera informacje o informacje o kluczu publicznym.</span><span class="sxs-lookup"><span data-stu-id="cff97-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="cff97-108">Klucz prywatny nie jest konieczne, gdy zestaw jest podpisywany z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="cff97-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="cff97-109">Aby uzyskać więcej informacji, zobacz [porady: podpisać zestaw o silnej nazwie](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="cff97-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
 <span data-ttu-id="cff97-110">**Identyfikator błędu:** BC30140</span><span class="sxs-lookup"><span data-stu-id="cff97-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cff97-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="cff97-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="cff97-112">Sprawdź ujętego w cudzysłów komunikat i zapoznaj się temacie [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="cff97-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="cff97-113">więcej informacji o AL1019 i porady</span><span class="sxs-lookup"><span data-stu-id="cff97-113">for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="cff97-114">Jeśli błąd będzie się powtarzać, zebrać informacje dotyczące okoliczności i powiadomić pomocy technicznej firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cff97-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff97-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cff97-115">See Also</span></span>  
 [<span data-ttu-id="cff97-116">Instrukcje: podpisywanie zestawu silną nazwą</span><span class="sxs-lookup"><span data-stu-id="cff97-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="cff97-117">Strona podpisywania, Projektant projektu</span><span class="sxs-lookup"><span data-stu-id="cff97-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)  
 <span data-ttu-id="cff97-118">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="cff97-118">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
 [<span data-ttu-id="cff97-119">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="cff97-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
