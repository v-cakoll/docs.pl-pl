---
title: Błąd automatyzacji
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: d62ba57db8bffefb2cfebed705251d87fe285602
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409897"
---
# <a name="automation-error"></a>Błąd automatyzacji

Wystąpił błąd podczas wykonywania metody lub pobierania lub ustawiania właściwości zmiennej obiektu. Błąd został zgłoszony przez aplikację, która utworzyła obiekt.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź właściwości `Err` obiektu, aby określić źródło i charakter błędu.  
  
2. Użyj `On Error Resume Next` instrukcji bezpośrednio przed instrukcją dostępu, a następnie wyewidencjonuj błędy natychmiast po instrukcji uzyskiwania dostępu.  
  
## <a name="see-also"></a>Zobacz też

- [Typy błędów](../../programming-guide/language-features/error-types.md)
- [Porozmawiaj z nami](/visualstudio/ide/feedback-options)
