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
ms.openlocfilehash: 006961a0f1d4be6b0d52be5bc273dad9733bfe56
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388702"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>Porady: wywoływanie procedury właściwości (Visual Basic)
Wywoływanie procedury właściwości przez zapisanie wartości we właściwości lub pobranie jej wartości. Dostęp do właściwości jest taki sam jak w przypadku dostępu do zmiennej.  
  
 `Set`Procedura właściwości przechowuje wartość, a jej `Get` procedura Pobiera wartość. Jednak te procedury nie są jawnie wywoływane przez nazwę. Używasz właściwości w instrukcji przypisania lub wyrażeniu, tak jak w przypadku przechowywania lub pobierania wartości zmiennej. Visual Basic wykonuje wywołania procedur właściwości.  
  
### <a name="to-call-a-propertys-get-procedure"></a>Aby wywołać procedurę pobierania właściwości  
  
1. Użyj nazwy właściwości w wyrażeniu tak samo jak w przypadku użycia nazwy zmiennej. Możesz użyć właściwości wszędzie tam, gdzie można użyć zmiennej lub stałej.  
  
     -lub-  
  
     Użyj nazwy właściwości następującego po znaku równości ( `=` ) w instrukcji przypisania.  
  
     Poniższy przykład odczytuje wartość <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> właściwości, niejawnie wywołując swoją `Get` procedurę.  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości z nawiasami, aby umieścić listę argumentów. Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy.  
  
3. Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami. Upewnij się, że argumenty są podawane w tej samej kolejności, w której Właściwość definiuje odpowiednie parametry.  
  
 Wartość właściwości uczestniczy w wyrażeniu tak samo jak zmienna lub stała lub jest przechowywana we właściwości lub właściwość po lewej stronie instrukcji przypisania.  
  
### <a name="to-call-a-propertys-set-procedure"></a>Aby wywołać procedurę ustawiania właściwości  
  
1. Użyj nazwy właściwości po lewej stronie instrukcji przypisania.  
  
     Poniższy przykład ustawia wartość <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> właściwości, niejawnie wywołując `Set` procedurę.  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości z nawiasami, aby umieścić listę argumentów. Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy.  
  
3. Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami. Upewnij się, że argumenty są podawane w tej samej kolejności, w której Właściwość definiuje odpowiednie parametry.  
  
 Wartość wygenerowana po prawej stronie instrukcji przypisania jest przechowywana we właściwości.  
  
## <a name="see-also"></a>Zobacz też

- [Procedury własności](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Property — Instrukcja](../../../language-reference/statements/property-statement.md)
- [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)
- [Instrukcje: tworzenie właściwości](./how-to-create-a-property.md)
- [Porady: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)
- [Instrukcje: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
- [Get — Instrukcja](../../../language-reference/statements/get-statement.md)
- [Set — Instrukcja](../../../language-reference/statements/set-statement.md)
