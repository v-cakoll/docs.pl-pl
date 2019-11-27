---
title: 'Porady: tworzenie nowej zmiennej'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: 2a2b5b8bef3b66f9727f0e65b61882186c007e94
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353632"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Porady: tworzenie nowej zmiennej (Visual Basic)

Tworzysz zmienną za pomocą [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).

### <a name="to-create-a-new-variable"></a>Aby utworzyć nową zmienną

1. Zadeklaruj zmienną w instrukcji `Dim`.

    ```vb
    Dim newCustomer
    ```

2. Zawierają specyfikacje dla charakterystyki zmiennej, takie jak [Private](../../../../visual-basic/language-reference/modifiers/private.md), [static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)lub [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md). Aby uzyskać więcej informacji, zobacz [deklarowane cechy elementu](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).

    ```vb
    Public Static newCustomer
    ```

    Nie jest potrzebne słowo kluczowe `Dim`, jeśli używasz innych słów kluczowych w deklaracji.

3. Postępuj zgodnie ze specyfikacją, podając nazwę zmiennej, która musi być zgodna z regułami i konwencjami Visual Basic. Aby uzyskać więcej informacji, zobacz [zadeklarowane nazwy elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

    ```vb
    Public Static newCustomer
    ```

4. Użyj nazwy z klauzulą [as](../../../../visual-basic/language-reference/statements/as-clause.md) , aby określić typ danych zmiennej.

    ```vb
    Public Static newCustomer As Customer
    ```

    Jeśli nie określisz typu danych, zostanie użyta wartość domyślna: `Object`.

5. Postępuj zgodnie z klauzulą `As` z znakiem równości (`=`) i obserwuj znak równości ze początkową wartością zmiennej.

    Visual Basic przypisuje określoną wartość do zmiennej przy każdym uruchomieniu instrukcji `Dim`. Jeśli nie określisz wartości początkowej, Visual Basic przypisze domyślną wartość początkową dla typu danych zmiennej, gdy po raz pierwszy przejdzie kod, który zawiera instrukcję `Dim`.

    Jeśli zmienna jest typem referencyjnym, można utworzyć wystąpienie klasy, dołączając słowo kluczowe [new operatora](../../../../visual-basic/language-reference/operators/new-operator.md) w klauzuli `As`. Jeśli nie używasz `New`, początkowa wartość zmiennej to [Nothing](../../../../visual-basic/language-reference/nothing.md).

    ```vb
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
