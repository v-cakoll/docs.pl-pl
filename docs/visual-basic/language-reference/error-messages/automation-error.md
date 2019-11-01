---
title: Błąd automatyzacji
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: 25c3b71eb818223c58ab17d9be885033a5d4ded0
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197032"
---
# <a name="automation-error"></a>Błąd automatyzacji
Wystąpił błąd podczas wykonywania metody lub pobierania lub ustawiania właściwości zmiennej obiektu. Błąd został zgłoszony przez aplikację, która utworzyła obiekt.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź właściwości obiektu `Err`, aby określić źródło i charakter błędu.  
  
2. Użyj instrukcji `On Error Resume Next` bezpośrednio przed instrukcją dostępu, a następnie wyewidencjonuj błędy bezpośrednio po instrukcji dostępu.  
  
## <a name="see-also"></a>Zobacz także

- [Typy błędów](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Porozmawiaj z nami](/visualstudio/ide/feedback-options)
