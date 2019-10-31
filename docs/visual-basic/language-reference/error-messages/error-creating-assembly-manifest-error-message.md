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
# <a name="error-creating-assembly-manifest-error-message"></a>Wystąpił błąd podczas tworzenia manifestu zestawu: \<komunikat o błędzie >
Kompilator Visual Basic wywołuje konsolidator zestawu (Al. exe, znany również jako ALink) w celu wygenerowania zestawu z manifestem. Konsolidator zgłosił błąd w fazie wstępnej emisji tworzenia zestawu.  
  
 Taka sytuacja może wystąpić w przypadku problemów z plikiem klucza lub określonego kontenera kluczy. Aby w pełni podpisać zestaw, należy podać prawidłowy plik klucza zawierający informacje o kluczach publiczny i prywatny. Aby opóźnić podpisywanie zestawu, musisz zaznaczyć pole wyboru **Opóźnij tylko znak** i podać prawidłowy plik klucza, który zawiera informacje o kluczu publicznym. Klucz prywatny nie jest konieczny, gdy zestaw jest podpisany z opóźnieniem. Aby uzyskać więcej informacji, zobacz [jak: podpisywanie zestawu za pomocą silnej nazwy](../../../standard/assembly/sign-strong-name.md).  
  
 **Identyfikator błędu:** BC30140  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź cytowany komunikat o błędzie i zapoznaj się z tematem [Al. exe](../../../framework/tools/al-exe-assembly-linker.md). Aby uzyskać informacje o błędzie, AL1019 dalsze wyjaśnienie i porady  
  
2. Jeśli błąd będzie się powtarzać, Zbierz informacje o okolicznościach i powiadom usługi pomocy technicznej firmy Microsoft.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: podpisywanie zestawu silną nazwą](../../../standard/assembly/sign-strong-name.md)
- [Strona podpisywania, Projektant projektu](/visualstudio/ide/reference/signing-page-project-designer)
- [Al. exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Porozmawiaj z nami](/visualstudio/ide/feedback-options)
