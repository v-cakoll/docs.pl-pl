---
title: 'Błąd podczas tworzenia manifestu zestawu: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: 7ccfb970a0e471b4a7e6808f041dfea2f386e7e9
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197124"
---
# <a name="error-creating-assembly-manifest-error-message"></a><span data-ttu-id="8947e-102">Wystąpił błąd podczas tworzenia manifestu zestawu: \<komunikat o błędzie ></span><span class="sxs-lookup"><span data-stu-id="8947e-102">Error creating assembly manifest: \<error message></span></span>
<span data-ttu-id="8947e-103">Kompilator Visual Basic wywołuje konsolidator zestawu (Al. exe, znany również jako ALink) w celu wygenerowania zestawu z manifestem.</span><span class="sxs-lookup"><span data-stu-id="8947e-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="8947e-104">Konsolidator zgłosił błąd w fazie wstępnej emisji tworzenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="8947e-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="8947e-105">Taka sytuacja może wystąpić w przypadku problemów z plikiem klucza lub określonego kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="8947e-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="8947e-106">Aby w pełni podpisać zestaw, należy podać prawidłowy plik klucza zawierający informacje o kluczach publiczny i prywatny.</span><span class="sxs-lookup"><span data-stu-id="8947e-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="8947e-107">Aby opóźnić podpisywanie zestawu, musisz zaznaczyć pole wyboru **Opóźnij tylko znak** i podać prawidłowy plik klucza, który zawiera informacje o kluczu publicznym.</span><span class="sxs-lookup"><span data-stu-id="8947e-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="8947e-108">Klucz prywatny nie jest konieczny, gdy zestaw jest podpisany z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="8947e-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="8947e-109">Aby uzyskać więcej informacji, zobacz [jak: podpisywanie zestawu za pomocą silnej nazwy](../../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="8947e-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>  
  
 <span data-ttu-id="8947e-110">**Identyfikator błędu:** BC30140</span><span class="sxs-lookup"><span data-stu-id="8947e-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8947e-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="8947e-111">To correct this error</span></span>  
  
1. <span data-ttu-id="8947e-112">Sprawdź cytowany komunikat o błędzie i zapoznaj się z tematem [Al. exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="8947e-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="8947e-113">Aby uzyskać informacje o błędzie, AL1019 dalsze wyjaśnienie i porady</span><span class="sxs-lookup"><span data-stu-id="8947e-113">for error AL1019 further explanation and advice</span></span>  
  
2. <span data-ttu-id="8947e-114">Jeśli błąd będzie się powtarzać, Zbierz informacje o okolicznościach i powiadom usługi pomocy technicznej firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8947e-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8947e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8947e-115">See also</span></span>

- [<span data-ttu-id="8947e-116">Instrukcje: podpisywanie zestawu silną nazwą</span><span class="sxs-lookup"><span data-stu-id="8947e-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="8947e-117">Strona podpisywania, Projektant projektu</span><span class="sxs-lookup"><span data-stu-id="8947e-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
- [<span data-ttu-id="8947e-118">Al. exe</span><span class="sxs-lookup"><span data-stu-id="8947e-118">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="8947e-119">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="8947e-119">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
