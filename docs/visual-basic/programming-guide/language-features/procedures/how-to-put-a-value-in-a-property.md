---
title: 'Instrukcje: Umieszczanie wartości we właściwości (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: e6aee5ea36c0315d5b01ae2734d17c9e7dab8e93
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341858"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Instrukcje: Umieszczanie wartości we właściwości (Visual Basic)
Wartość jest przechowywana we właściwości, umieszczając nazwę właściwości po lewej stronie instrukcji przypisania.  
  
 Właściwości `Set` procedury przechowuje wartość, ale nie zostanie jawnie wywołana je według nazwy. Użyj właściwości, tak samo, jak należy użyć zmiennej. Visual Basic sprawia, że wywołania procedur właściwość.  
  
### <a name="to-store-a-value-in-a-property"></a>Do przechowywania wartości we właściwości  
  
1. Po lewej stronie instrukcji przypisania, należy użyć nazwy właściwości.  
  
     W poniższym przykładzie ustawiono wartość języka Visual Basic `TimeOfDay` właściwość południe, niejawnie wywoływania jego `Set` procedury.  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości, za pomocą nawiasów, aby ująć listy argumentów. Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.  
  
3. Argumenty należy umieścić na liście argumentów w nawiasie rozdzielone przecinkami. Upewnij się, że podajesz argumentów w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.  
  
4. Wartość generowane po prawej stronie instrukcji przypisania są przechowywane we właściwości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [Procedury właściwości](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Property — Instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)
- [Instrukcje: Tworzenie właściwości](./how-to-create-a-property.md)
- [Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Instrukcje: Wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)
- [Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: Pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
