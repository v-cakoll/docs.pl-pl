---
title: 'Porady: wywoływanie procedury właściwości'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 52e6c62ffb81c480ccc1abf06f04eb780218dbf1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340554"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>Porady: wywoływanie procedury właściwości (Visual Basic)
Wywoływanie procedury właściwości przez zapisanie wartości we właściwości lub pobranie jej wartości. Dostęp do właściwości jest taki sam jak w przypadku dostępu do zmiennej.  
  
 Procedura `Set` właściwości przechowuje wartość, a jej `Get` procedura Pobiera wartość. Jednak te procedury nie są jawnie wywoływane przez nazwę. Używasz właściwości w instrukcji przypisania lub wyrażeniu, tak jak w przypadku przechowywania lub pobierania wartości zmiennej. Visual Basic wykonuje wywołania procedur właściwości.  
  
### <a name="to-call-a-propertys-get-procedure"></a>Aby wywołać procedurę pobierania właściwości  
  
1. Użyj nazwy właściwości w wyrażeniu tak samo jak w przypadku użycia nazwy zmiennej. Możesz użyć właściwości wszędzie tam, gdzie można użyć zmiennej lub stałej.  
  
     —lub—  
  
     Użyj nazwy właściwości następującego po znaku równości (`=`) w instrukcji przypisania.  
  
     Poniższy przykład odczytuje wartość właściwości <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>, niejawnie wywołując `Get` procedurę.  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości z nawiasami, aby umieścić listę argumentów. Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy.  
  
3. Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami. Upewnij się, że argumenty są podawane w tej samej kolejności, w której Właściwość definiuje odpowiednie parametry.  
  
 Wartość właściwości uczestniczy w wyrażeniu tak samo jak zmienna lub stała lub jest przechowywana we właściwości lub właściwość po lewej stronie instrukcji przypisania.  
  
### <a name="to-call-a-propertys-set-procedure"></a>Aby wywołać procedurę ustawiania właściwości  
  
1. Użyj nazwy właściwości po lewej stronie instrukcji przypisania.  
  
     Poniższy przykład ustawia wartość właściwości <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>, niejawnie wywołując procedurę `Set`.  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości z nawiasami, aby umieścić listę argumentów. Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy.  
  
3. Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami. Upewnij się, że argumenty są podawane w tej samej kolejności, w której Właściwość definiuje odpowiednie parametry.  
  
 Wartość wygenerowana po prawej stronie instrukcji przypisania jest przechowywana we właściwości.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury właściwości](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Property, instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Różnice między właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)
- [Instrukcje: tworzenie właściwości](./how-to-create-a-property.md)
- [Instrukcje: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Instrukcje: deklarowanie i wywoływanie właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)
- [Instrukcje: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
- [Get, instrukcja](../../../../visual-basic/language-reference/statements/get-statement.md)
- [Set, instrukcja](../../../../visual-basic/language-reference/statements/set-statement.md)
