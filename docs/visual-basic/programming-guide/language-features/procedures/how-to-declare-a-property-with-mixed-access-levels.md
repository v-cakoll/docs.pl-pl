---
title: 'Porady: deklarowanie właściwości z mieszanymi poziomami dostępu'
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
ms.openlocfilehash: d74e23f33fbf7d9d29ab84b9b1bd4fc08863ac48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349693"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Porady: deklarowanie właściwości z mieszanymi poziomami dostępu (Visual Basic)
Jeśli chcesz, aby procedury `Get` i `Set` na właściwości miały różne poziomy dostępu, możesz użyć poziomu bardziej ograniczającego w instrukcji `Property` i bardziej restrykcyjnego poziomu w instrukcji `Get` lub `Set`. Możesz użyć mieszanych poziomów dostępu dla właściwości, jeśli chcesz, aby niektóre części kodu mogły uzyskać wartość właściwości, a niektóre inne części kodu, aby można było zmienić wartość.  
  
 Aby uzyskać więcej informacji na temat poziomów dostępu, zobacz [poziomy dostępu w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Aby zadeklarować właściwość z mieszanymi poziomami dostępu  
  
1. Zadeklaruj właściwość w normalny sposób i określ mniej restrykcyjny poziom dostępu (taki jak `Public`) w instrukcji `Property`.  
  
2. Zadeklaruj `Get` lub procedurę `Set` określającą bardziej restrykcyjny poziom dostępu (na przykład `Friend`).  
  
3. Nie określaj poziomu dostępu dla innej procedury właściwości. Przyjęto założenie poziomu dostępu zadeklarowanego w instrukcji `Property`. Można ograniczyć dostęp tylko do jednej z procedur dotyczących właściwości.  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     W poprzednim przykładzie procedura `Get` ma taki sam `Protected` dostęp jak sama właściwość, podczas gdy procedura `Set` ma `Private` dostępu. Klasa pochodna `employee` może odczytać wartość `salary`, ale można ją ustawić tylko przez klasę `employee`.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Procedury właściwości](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Property, instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Różnice między właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)
- [Instrukcje: tworzenie właściwości](./how-to-create-a-property.md)
- [Instrukcje: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)
- [Instrukcje: deklarowanie i wywoływanie właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)
- [Instrukcje: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
