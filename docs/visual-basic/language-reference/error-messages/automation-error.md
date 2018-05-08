---
title: Błąd automatyzacji
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: fdd77510d03cd9e5228be1ba9ec9f746dcc0dfe4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="automation-error"></a>Błąd automatyzacji
Wystąpił błąd podczas wykonywania metody lub pobierania lub ustawiania właściwości zmiennej obiektu. Błąd został zgłoszony przez aplikację, który utworzył obiekt.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź właściwości `Err` obiektem, aby określić źródło i charakteru błędu.  
  
2.  Użyj `On Error Resume Next` instrukcji bezpośrednio przed podczas uzyskiwania dostępu do instrukcji, a następnie Wyszukaj błędy bezpośrednio po instrukcji podczas uzyskiwania dostępu do.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy błędów](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)
