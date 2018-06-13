---
title: 'Porady: deklarowanie właściwości z mieszanymi poziomami dostępu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: 8d25086fe6f8b5f5300006466ef49782cb065edf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651414"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Porady: deklarowanie właściwości z mieszanymi poziomami dostępu (Visual Basic)
Jeśli chcesz `Get` i `Set` procedur we właściwości w celu mają różne poziomy dostępu, można użyć poziomu mniej ograniczająca w `Property` instrukcji i bardziej restrykcyjne poziomu w jednym `Get` lub `Set` instrukcji. Mieszanymi poziomami dostępu można używać we właściwości, gdy chce niektórych części kodu, aby można było pobrać wartości właściwości i części kodu, aby można było zmienić wartość.  
  
 Aby uzyskać więcej informacji na temat poziomów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Deklarowanie właściwości z mieszanymi poziomami dostępu  
  
1.  Deklarowanie właściwości w zwykły sposób, a następnie określ poziom dostępu mniej restrykcyjny (takich jak `Public`) w `Property` instrukcji.  
  
2.  Deklarowanie albo `Get` lub `Set` procedurę określając bardziej restrykcyjne poziom dostępu (takie jak `Friend`).  
  
3.  Nie określaj poziom dostępu w procedurze właściwości. Zakłada się poziom dostępu zadeklarowany w `Property` instrukcji. Można ograniczyć dostęp tylko dla jednej z właściwości procedur.  
  
     [!code-vb[VbVbcnProcedures#10](./codesnippet/VisualBasic/how-to-declare-a-property-with-mixed-access-levels_1.vb)]  
  
     W poprzednim przykładzie `Get` procedura ma taką samą `Protected` dostępu jako właściwość, gdy `Set` procedura ma `Private` dostępu. Klasa pochodna od `employee` może odczytywać `salary` wartość, ale tylko `employee` klasy może go ustawić.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Procedury właściwości](./property-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Property, instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)  
 [Instrukcje: tworzenie właściwości](./how-to-create-a-property.md)  
 [Instrukcje: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)  
 [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Instrukcje: umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)  
 [Instrukcje: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
