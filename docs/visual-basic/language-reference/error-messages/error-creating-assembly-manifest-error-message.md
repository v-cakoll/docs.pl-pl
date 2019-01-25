---
title: 'Wystąpił błąd podczas tworzenia manifestu zestawu: &lt;komunikat o błędzie&gt;'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: 7efdfa09ad7bf58fc3ddc8f702377a4d41b2fed6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655390"
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="f6c09-102">Wystąpił błąd podczas tworzenia manifestu zestawu: &lt;komunikat o błędzie&gt;</span><span class="sxs-lookup"><span data-stu-id="f6c09-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="f6c09-103">Kompilator Visual Basic wywołuje Assembly Linker (Al.exe, znany także jako Alink) do generowania manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="f6c09-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="f6c09-104">Konsolidator zgłosił błąd podczas etapu emisji wstępnego tworzenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="f6c09-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="f6c09-105">Może to wystąpić, jeśli występują problemy z pliku klucza lub określony kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="f6c09-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="f6c09-106">Aby w pełni Podpisz zestaw, należy podać prawidłowy plik klucza, który zawiera informacje o kluczach publicznych i prywatnych.</span><span class="sxs-lookup"><span data-stu-id="f6c09-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="f6c09-107">Aby opóźnić Podpisz zestaw, należy wybrać **opóźnienie logowania tylko** pole wyboru, a następnie podaj prawidłowy plik klucza, który zawiera informacje o informacje o kluczu publicznym.</span><span class="sxs-lookup"><span data-stu-id="f6c09-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="f6c09-108">Klucz prywatny nie jest konieczne w przypadku, gdy zestaw jest podpisany z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="f6c09-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="f6c09-109">Aby uzyskać więcej informacji, zobacz [jak: Podpisywanie zestawu silną nazwą](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="f6c09-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
 <span data-ttu-id="f6c09-110">**Identyfikator błędu:** BC30140</span><span class="sxs-lookup"><span data-stu-id="f6c09-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f6c09-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f6c09-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="f6c09-112">Sprawdź komunikat o błędzie w cudzysłowach i zapoznaj się z tematem [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="f6c09-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="f6c09-113">Aby uzyskać dalsze wyjaśnienie błędu AL1019 i porady</span><span class="sxs-lookup"><span data-stu-id="f6c09-113">for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="f6c09-114">Jeśli błąd będzie się powtarzać, należy zebrać informacje dotyczące okoliczności i powiadom pomoc techniczna firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f6c09-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6c09-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6c09-115">See also</span></span>
- [<span data-ttu-id="f6c09-116">Instrukcje: Podpisywanie zestawu silną nazwą</span><span class="sxs-lookup"><span data-stu-id="f6c09-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- <span data-ttu-id="f6c09-117">[Strona podpisywania, Projektant projektu](/visualstudio/ide/reference/signing-page-project-designer)
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="f6c09-117">[Signing Page, Project Designer](/visualstudio/ide/reference/signing-page-project-designer)
[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
- [<span data-ttu-id="f6c09-118">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="f6c09-118">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
