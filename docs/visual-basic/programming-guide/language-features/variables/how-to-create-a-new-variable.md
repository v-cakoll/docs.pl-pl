---
title: 'Instrukcje: Tworzenie nowej zmiennej (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: ee1e93b4e9819992f17738eb024004a4d66210d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938245"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Instrukcje: Tworzenie nowej zmiennej (Visual Basic)
Utwórz zmienną za pomocą [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
### <a name="to-create-a-new-variable"></a>Aby utworzyć nową zmienną  
  
1. Zadeklaruj zmienną w `Dim` instrukcji.  
  
    ```  
    Dim newCustomer  
    ```  
  
2. Uwzględnić wymagania dotyczące cech zmiennej, takie jak [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md), [statyczne](../../../../visual-basic/language-reference/modifiers/static.md), [cieni](../../../../visual-basic/language-reference/modifiers/shadows.md), lub [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md). Aby uzyskać więcej informacji, zobacz [zadeklarowana Charakterystyka elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
     Nie ma potrzeby `Dim` — słowo kluczowe, jeśli używasz innych słów kluczowych w deklaracji.  
  
3. Postępuj zgodnie z specyfikacją o nazwie zmiennej, która musi być zgodna reguły Visual Basic i konwencje. Aby uzyskać więcej informacji, zobacz [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) (Deklarowane nazwy elementów).  
  
    ```  
    Public Static newCustomer  
    ```  
  
4. Postępuj zgodnie z nazwą [jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzuli, aby określić typ danych zmiennej.  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     Jeśli nie określisz typ danych, wykorzystuje wartość domyślna: `Object`.  
  
5. Postępuj zgodnie z `As` klauzuli znakiem równości (`=`) i postępuj zgodnie z równości z wartością początkową zmiennej.  
  
     Visual Basic przypisuje określoną wartość do zmiennej za każdym razem, gdy działa `Dim` instrukcji. Jeśli nie określisz wartości początkowej, Visual Basic po raz pierwszy najedzie kodu, który zawiera, przypisuje początkowa wartość domyślna dla typu danych zmiennej `Dim` instrukcji.  
  
     Jeśli zmienna jest typem referencyjnym, można utworzyć wystąpienia klasy, umieszczając [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe w `As` klauzuli. Jeśli nie używasz `New`, jest wartością początkową zmiennej [nic](../../../../visual-basic/language-reference/nothing.md).  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Nazwy zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Charakterystyka zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Instrukcje](../../../../visual-basic/language-reference/statements/index.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer, instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
