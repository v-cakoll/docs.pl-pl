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
ms.openlocfilehash: c0fb3e137010390097a68aea161efcff93839d94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414340"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Porady: umieszczanie wartości we właściwości (Visual Basic)
Wartość właściwości jest przechowywana przez umieszczenie nazwy właściwości po lewej stronie instrukcji przypisania.  
  
 `Set`Procedura właściwości przechowuje wartość, ale nie jest jawnie wywoływana przez nazwę. Właściwość jest używana tak samo jak w przypadku użycia zmiennej. Visual Basic wykonuje wywołania procedur właściwości.  
  
### <a name="to-store-a-value-in-a-property"></a>Aby zapisać wartość w właściwości  
  
1. Użyj nazwy właściwości po lewej stronie instrukcji przypisania.  
  
     Poniższy przykład ustawia wartość `TimeOfDay` właściwości Visual Basic na południe, niejawnie wywołując `Set` procedurę.  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości z nawiasami, aby umieścić listę argumentów. Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy.  
  
3. Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami. Upewnij się, że argumenty są podawane w tej samej kolejności, w której Właściwość definiuje odpowiednie parametry.  
  
4. Wartość wygenerowana po prawej stronie instrukcji przypisania jest przechowywana we właściwości.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [Procedury własności](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Property — Instrukcja](../../../language-reference/statements/property-statement.md)
- [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)
- [Instrukcje: tworzenie właściwości](./how-to-create-a-property.md)
- [Porady: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Porady: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)
- [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
