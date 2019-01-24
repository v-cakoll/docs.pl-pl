---
title: Błąd automatyzacji
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: 8a00efe988eb39be75818b5c2c401b58e5f7f2ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490885"
---
# <a name="automation-error"></a>Błąd automatyzacji
Wystąpił błąd podczas wykonywania metody lub pobieranie lub ustawianie właściwości zmiennej obiektu. Ten błąd został zgłoszony przez aplikację, który utworzył obiekt.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź właściwości `Err` obiektu w celu ustalenia źródła i charakteru błędu.  
  
2.  Użyj `On Error Resume Next` instrukcję tuż przed uzyskiwania dostępu do instrukcji i sprawdź, czy błędy bezpośrednio po uzyskiwania dostępu do instrukcji.  
  
## <a name="see-also"></a>Zobacz także
- [Typy błędów](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)
