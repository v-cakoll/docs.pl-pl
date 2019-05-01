---
ms.openlocfilehash: f01d0a24202ecda7e23cbe925bb6dc8962cb7574
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750728"
---
> [!CAUTION]
>  Zabezpieczenia dostępu kodu i częściowo zaufany kod  
>   
>  Platforma .NET Framework zapewnia mechanizm wymuszania różnych poziomów zaufania dla różnego kodu uruchamianego w tej samej aplikacji nazywany zabezpieczeniami dostępu kodu (CAS, Code Access Security).  Zabezpieczeń dostępu kodu na platformie .NET Framework nie należy używać jako mechanizmu wymuszania granic zabezpieczeń na podstawie pochodzenia kodu lub innych aspektów tożsamości. Aktualizujemy nasze wskazówki, aby uwzględnić informacje o tym, że zabezpieczenia dostępu kodu ani kod przezroczysty pod względem zabezpieczeń nie będą obsługiwane jako granice zabezpieczeń z częściowo zaufanym kodem, zwłaszcza kodem nieznanego pochodzenia. Odradzamy ładowanie i wykonywanie kodu z nieznanego źródła bez zapewnienia alternatywnych środków bezpieczeństwa.  
>   
>  Te zasady mają zastosowanie do wszystkich wersji platformy .NET Framework, ale nie mają zastosowania do platformy .NET Framework zawartej w technologii Silverlight.