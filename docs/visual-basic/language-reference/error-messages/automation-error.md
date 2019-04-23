---
title: Błąd automatyzacji
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: 8370f744b916ce4a797c808ed58c5fc9580e6278
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304315"
---
# <a name="automation-error"></a>Błąd automatyzacji
Wystąpił błąd podczas wykonywania metody lub pobieranie lub ustawianie właściwości zmiennej obiektu. Ten błąd został zgłoszony przez aplikację, który utworzył obiekt.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź właściwości `Err` obiektu w celu ustalenia źródła i charakteru błędu.  
  
2. Użyj `On Error Resume Next` instrukcję tuż przed uzyskiwania dostępu do instrukcji i sprawdź, czy błędy bezpośrednio po uzyskiwania dostępu do instrukcji.  
  
## <a name="see-also"></a>Zobacz także

- [Typy błędów](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)
