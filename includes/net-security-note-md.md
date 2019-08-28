---
ms.openlocfilehash: f70452cbadc8927521f0fcfda693586c277e4d0f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041168"
---
> [!CAUTION]
> <span data-ttu-id="6977d-101">Zabezpieczenia dostępu kodu i częściowo zaufany kod</span><span class="sxs-lookup"><span data-stu-id="6977d-101">Code Access Security and Partially Trusted Code</span></span>
>
> <span data-ttu-id="6977d-102">Platforma .NET Framework zapewnia mechanizm wymuszania różnych poziomów zaufania dla różnego kodu uruchamianego w tej samej aplikacji nazywany zabezpieczeniami dostępu kodu (CAS, Code Access Security).</span><span class="sxs-lookup"><span data-stu-id="6977d-102">The .NET Framework provides a mechanism for the enforcement of varying levels of trust on different code running in the same application called Code Access Security (CAS).</span></span>  <span data-ttu-id="6977d-103">Zabezpieczeń dostępu kodu na platformie .NET Framework nie należy używać jako mechanizmu wymuszania granic zabezpieczeń na podstawie pochodzenia kodu lub innych aspektów tożsamości.</span><span class="sxs-lookup"><span data-stu-id="6977d-103">Code Access Security in .NET Framework should not  be used as a mechanism for enforcing security boundaries based on code origination or other identity aspects.</span></span> <span data-ttu-id="6977d-104">Aktualizujemy nasze wskazówki, aby uwzględnić informacje o tym, że zabezpieczenia dostępu kodu ani kod przezroczysty pod względem zabezpieczeń nie będą obsługiwane jako granice zabezpieczeń z częściowo zaufanym kodem, zwłaszcza kodem nieznanego pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="6977d-104">We are updating our guidance to reflect that Code Access Security and Security-Transparent Code will not be supported as a security boundary with partially trusted code, especially code of unknown origin.</span></span> <span data-ttu-id="6977d-105">Odradzamy ładowanie i wykonywanie kodu z nieznanego źródła bez zapewnienia alternatywnych środków bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="6977d-105">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span>
>
> <span data-ttu-id="6977d-106">Te zasady mają zastosowanie do wszystkich wersji platformy .NET Framework, ale nie mają zastosowania do platformy .NET Framework zawartej w technologii Silverlight.</span><span class="sxs-lookup"><span data-stu-id="6977d-106">This policy applies to all versions of .NET Framework, but does not apply to the .NET Framework included in Silverlight.</span></span>
