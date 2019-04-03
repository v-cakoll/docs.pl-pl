---
title: Wartości typu „type1” nie można przekonwertować na „type2”.
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: c8480c6fab2bff931950ebc21d0a8affe3c41c66
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827149"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a>Wartości typu „type1” nie można przekonwertować na „type2”.
Nie można przekonwertować wartości typu 'type1' na 'Typ2'. Właściwość "Value" umożliwia uzyskać wartość ciągu pierwszego elementu obiektu "\<parentElement >".  
  
 Podjęta próba niejawnie rzutowany literał dla określonego typu XML. Literał XML nie może być niejawnie rzutowany na określonego typu.  
  
 **Identyfikator błędu:** BC31194  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Użyj `Value` właściwość literał XML, aby odwoływać się do jej wartość jako `String`. Użyj `CType` funkcji, inny typ funkcji konwersji lub <xref:System.Convert> klasy, aby rzutować wartość jako określonego typu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Convert>
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
