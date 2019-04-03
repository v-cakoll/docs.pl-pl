---
title: 'Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu (Visual Basic)'
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
ms.openlocfilehash: aa0c71621b72d01067db0749a0678b706d13fbfa
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832128"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu (Visual Basic)
Jeśli chcesz `Get` i `Set` procedury dotyczące właściwości, aby mieć różne poziomy dostępu, możesz użyć mniej ograniczająca poziom w `Property` instrukcji i bardziej restrykcyjny poziom albo `Get` lub `Set` Instrukcja. Za pomocą mieszanymi poziomami dostępu we właściwości niektórych części kodu, aby można było pobrać wartości właściwości, a niektóre części kodu, aby można było zmienić wartość.  
  
 Aby uzyskać więcej informacji na temat poziomów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Deklarowanie właściwości z mieszanymi poziomami dostępu  
  
1.  Zadeklaruj właściwość w normalny sposób i określić poziom dostępu mniej restrykcyjny (takie jak `Public`) w `Property` instrukcji.  
  
2.  Zadeklaruj jedną `Get` lub `Set` procedurę, określając bardziej restrykcyjny poziom dostępu (takich jak `Friend`).  
  
3.  Na innej procedury właściwość nie zostanie określony poziom dostępu. Przyjęto założenie, poziom dostępu, zadeklarowany w `Property` instrukcji. Możesz ograniczyć dostęp tylko dla jednej z procedur właściwość.  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     W poprzednim przykładzie `Get` procedura ma taką samą `Protected` dostępu jako właściwość, podczas gdy `Set` procedura ma `Private` dostępu. Klasa pochodząca z `employee` może odczytywać `salary` wartość, ale tylko `employee` klasy można ustawić go.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Procedury właściwości](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcja Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Różnice między właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)
- [Instrukcje: Tworzenie właściwości](./how-to-create-a-property.md)
- [Instrukcje: Wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)
- [Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: Umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)
- [Instrukcje: Pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
