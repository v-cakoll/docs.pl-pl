---
title: Wartości typu &#39;type1&#39; nie można przekonwertować na &#39;type2&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 9e59d3bc5e2bfca3628248d08ffc475334d4da79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602765"
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a>Wartości typu &#39;type1&#39; nie można przekonwertować na &#39;type2&#39;
Nie można przekonwertować wartości typu "type1" na "type2". Można użyć właściwości 'Value' można uzyskać wartość ciągu pierwszego elementu obiektu "\<parentElement >".  
  
 Nastąpiła próba niejawnie rzutować literału dla określonego typu XML. Literał XML nie można rzutować niejawnie do określonego typu.  
  
 **Identyfikator błędu:** BC31194  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Użyj `Value` właściwość literału XML odwoływać się do jego wartości jako `String`. Użyj `CType` funkcji, funkcji konwersji innego typu, lub <xref:System.Convert> klasy można rzutować wartości jako określonego typu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Convert>  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
