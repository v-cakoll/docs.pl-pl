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
ms.openlocfilehash: f0f7aba25888544dfcc093906850ae7ada621182
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388248"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Porady: deklarowanie właściwości z mieszanymi poziomami dostępu (Visual Basic)
Jeśli chcesz, `Get` `Set` aby procedury i dla właściwości miały różne poziomy dostępu, możesz użyć poziomu bardziej ograniczającego w `Property` instrukcji i bardziej restrykcyjnego poziomu w `Get` `Set` instrukcji or. Możesz użyć mieszanych poziomów dostępu dla właściwości, jeśli chcesz, aby niektóre części kodu mogły uzyskać wartość właściwości, a niektóre inne części kodu, aby można było zmienić wartość.  
  
 Aby uzyskać więcej informacji na temat poziomów dostępu, zobacz [poziomy dostępu w Visual Basic](../declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Aby zadeklarować właściwość z mieszanymi poziomami dostępu  
  
1. Zadeklaruj właściwość w normalny sposób i określ mniej restrykcyjny poziom dostępu (na przykład `Public` ) w `Property` instrukcji.  
  
2. Zadeklaruj albo `Get` `Set` procedurę określającą bardziej restrykcyjny poziom dostępu (na przykład `Friend` ).  
  
3. Nie określaj poziomu dostępu dla innej procedury właściwości. Przyjęto założenie poziomu dostępu zadeklarowanego w `Property` instrukcji. Można ograniczyć dostęp tylko do jednej z procedur dotyczących właściwości.  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     W poprzednim przykładzie `Get` procedura ma taki sam `Protected` dostęp jak sama właściwość, podczas gdy `Set` procedura ma `Private` dostęp. Klasa pochodna `employee` może odczytać `salary` wartość, ale `employee` można ją ustawić tylko przez klasę.  
  
## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Procedury własności](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Property — Instrukcja](../../../language-reference/statements/property-statement.md)
- [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)
- [Instrukcje: tworzenie właściwości](./how-to-create-a-property.md)
- [Porady: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)
- [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)
- [Instrukcje: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
