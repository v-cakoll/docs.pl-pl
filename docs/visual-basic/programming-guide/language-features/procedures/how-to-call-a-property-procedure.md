---
title: 'Instrukcje: Wywoływanie procedury właściwości (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 1f8871c2cc5126110fa849d42eed3d8edb3a03f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602575"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>Instrukcje: Wywoływanie procedury właściwości (Visual Basic)
Przechowywanie wartości we właściwości lub pobieranie jej wartość jest wywoływanie procedury właściwości. Możesz uzyskać dostęp do właściwości taki sam sposób, dostęp do zmiennej.  
  
 Właściwości `Set` procedury przechowuje wartość, a jego `Get` procedury pobiera wartość. Jednakże nie zostanie jawnie wywołana tych procedur według nazwy. Używasz właściwości w instrukcji przypisania lub wyrażenie, tak jak będzie zapisanie lub pobranie wartości zmiennej. Visual Basic sprawia, że wywołania procedur właściwość.  
  
### <a name="to-call-a-propertys-get-procedure"></a>Aby wywołać procedura Get właściwości  
  
1.  Użyj nazwy właściwości w wyrażeniu taki sam sposób użyje nazwy zmiennej. Można użyć właściwości wszędzie można użyć zmienną lub stałą.  
  
     —lub—  
  
     Użyj nazwy właściwości po równości (`=`) Zaloguj się w instrukcji przypisania.  
  
     Poniższy przykład odczytuje wartość <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> właściwości i niejawne wywoływanie jej `Get` procedury.  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości, za pomocą nawiasów, aby ująć listy argumentów. Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.  
  
3.  Argumenty należy umieścić na liście argumentów w nawiasie rozdzielone przecinkami. Upewnij się, że podajesz argumentów w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.  
  
 Wartość właściwości uczestniczy w wyrażeniu tylko jako zmienna będzie — stała lub jest on przechowywany w zmiennej lub właściwość po lewej stronie w instrukcji przypisania.  
  
### <a name="to-call-a-propertys-set-procedure"></a>Aby wywołać właściwości ustawione przez procedurę  
  
1.  Po lewej stronie instrukcji przypisania, należy użyć nazwy właściwości.  
  
     W poniższym przykładzie ustawiono wartość <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> właściwości i niejawne wywoływanie `Set` procedury.  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości, za pomocą nawiasów, aby ująć listy argumentów. Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.  
  
3.  Argumenty należy umieścić na liście argumentów w nawiasie rozdzielone przecinkami. Upewnij się, że podajesz argumentów w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.  
  
 Wartość generowane po prawej stronie instrukcji przypisania są przechowywane we właściwości.  
  
## <a name="see-also"></a>Zobacz także
- [Procedury właściwości](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcja Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Różnice między właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)
- [Instrukcje: Tworzenie właściwości](./how-to-create-a-property.md)
- [Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: Umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)
- [Instrukcje: Pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
- [Get, instrukcja](../../../../visual-basic/language-reference/statements/get-statement.md)
- [Set, instrukcja](../../../../visual-basic/language-reference/statements/set-statement.md)
