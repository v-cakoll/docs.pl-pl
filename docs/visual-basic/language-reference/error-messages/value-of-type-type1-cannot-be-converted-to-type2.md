---
title: Wartości typu &#39;type1&#39; nie można przekonwertować na &#39;Typ2&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 657e0feb675e15b9ece00d40c3d1ebe932a29099
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568296"
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a>Wartości typu &#39;type1&#39; nie można przekonwertować na &#39;Typ2&#39;
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
