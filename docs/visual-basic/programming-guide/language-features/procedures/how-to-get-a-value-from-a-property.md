---
title: 'Instrukcje: Pobieranie wartości z właściwości (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 5e2676a0880092a78405fe5dafa0469161b85610
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302936"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>Instrukcje: Pobieranie wartości z właściwości (Visual Basic)
Możesz pobrać wartości właściwości, łącznie z nazwą właściwości w wyrażeniu.  
  
 Właściwości `Get` procedury pobiera wartość, ale nie zostanie jawnie wywołana je według nazwy. Użyj właściwości, tak samo, jak należy użyć zmiennej. Visual Basic sprawia, że wywołania procedur właściwość.  
  
### <a name="to-retrieve-a-value-from-a-property"></a>Do pobierania wartości z właściwości  
  
1. Użyj nazwy właściwości w wyrażeniu taki sam sposób użyje nazwy zmiennej. Można użyć właściwości wszędzie można użyć zmienną lub stałą.  
  
     —lub—  
  
     Użyj nazwy właściwości po równości (`=`) Zaloguj się w instrukcji przypisania.  
  
     Poniższy przykład odczytuje wartość języka Visual Basic `Now` właściwości i niejawne wywoływanie jej `Get` procedury.  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości, za pomocą nawiasów, aby ująć listy argumentów. Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.  
  
3. Argumenty należy umieścić na liście argumentów w nawiasie rozdzielone przecinkami. Upewnij się, że podajesz argumentów w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.  
  
 Wartość właściwości uczestniczy w wyrażeniu tylko jako zmienna będzie — stała lub jest on przechowywany w zmiennej lub właściwość po lewej stronie w instrukcji przypisania.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Procedury właściwości](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Property — Instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)
- [Instrukcje: Tworzenie właściwości](./how-to-create-a-property.md)
- [Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Instrukcje: Wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)
- [Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: Umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)
