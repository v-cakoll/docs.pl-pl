---
title: Wartości typu „type1” nie można przekonwertować na „type2”.
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 4a0f3eb2b1603899e9acc1273c023ec5d0ed3132
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913343"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a>Wartości typu „type1” nie można przekonwertować na „type2”.
Nie można przekonwertować wartości typu 'type1' na 'Typ2'. Właściwość "Value" umożliwia uzyskać wartość ciągu pierwszego elementu obiektu "\<parentElement >".  
  
 Podjęta próba niejawnie rzutowany literał dla określonego typu XML. Literał XML nie może być niejawnie rzutowany na określonego typu.  
  
 **Identyfikator błędu:** BC31194  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Użyj `Value` właściwość literał XML, aby odwoływać się do jej wartość jako `String`. Użyj `CType` funkcji, inny typ funkcji konwersji lub <xref:System.Convert> klasy, aby rzutować wartość jako określonego typu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Convert>
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
