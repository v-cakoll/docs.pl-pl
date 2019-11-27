---
title: 'Porady: umieszczanie wartości we właściwości'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: ad0d0e81f94dd3dead50f21c3bd6ff580c004dd6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346053"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Porady: umieszczanie wartości we właściwości (Visual Basic)
Wartość właściwości jest przechowywana przez umieszczenie nazwy właściwości po lewej stronie instrukcji przypisania.  
  
 Procedura `Set` właściwości przechowuje wartość, ale nie można jawnie wywołać jej według nazwy. Właściwość jest używana tak samo jak w przypadku użycia zmiennej. Visual Basic wykonuje wywołania procedur właściwości.  
  
### <a name="to-store-a-value-in-a-property"></a>Aby zapisać wartość w właściwości  
  
1. Użyj nazwy właściwości po lewej stronie instrukcji przypisania.  
  
     Poniższy przykład ustawia wartość właściwości Visual Basic `TimeOfDay` na południe, niejawnie wywołując procedurę `Set`.  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości z nawiasami, aby umieścić listę argumentów. Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy.  
  
3. Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami. Upewnij się, że argumenty są podawane w tej samej kolejności, w której Właściwość definiuje odpowiednie parametry.  
  
4. Wartość wygenerowana po prawej stronie instrukcji przypisania jest przechowywana we właściwości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [Procedury właściwości](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Property, instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Różnice między właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)
- [Instrukcje: tworzenie właściwości](./how-to-create-a-property.md)
- [Instrukcje: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Instrukcje: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)
- [Instrukcje: deklarowanie i wywoływanie właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
