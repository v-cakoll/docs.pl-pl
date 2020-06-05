---
title: 'Porady: tworzenie nowej zmiennej'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: 501c8f3aff4c5b204d231bdc26213e13d125a7cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410532"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Porady: tworzenie nowej zmiennej (Visual Basic)

Tworzysz zmienną za pomocą [instrukcji Dim](../../../language-reference/statements/dim-statement.md).

### <a name="to-create-a-new-variable"></a>Aby utworzyć nową zmienną

1. Zadeklaruj zmienną w `Dim` instrukcji.

    ```vb
    Dim newCustomer
    ```

2. Zawierają specyfikacje dla charakterystyki zmiennej, takie jak [Private](../../../language-reference/modifiers/private.md), [static](../../../language-reference/modifiers/static.md), [Shadows](../../../language-reference/modifiers/shadows.md)lub [WithEvents](../../../language-reference/modifiers/withevents.md). Aby uzyskać więcej informacji, zobacz [deklarowane cechy elementu](../declared-elements/declared-element-characteristics.md).

    ```vb
    Public Static newCustomer
    ```

    Słowo kluczowe nie jest potrzebne, `Dim` Jeśli używasz innych słów kluczowych w deklaracji.

3. Postępuj zgodnie ze specyfikacją, podając nazwę zmiennej, która musi być zgodna z regułami i konwencjami Visual Basic. Aby uzyskać więcej informacji, zobacz [zadeklarowane nazwy elementów](../declared-elements/declared-element-names.md).

    ```vb
    Public Static newCustomer
    ```

4. Użyj nazwy z klauzulą [as](../../../language-reference/statements/as-clause.md) , aby określić typ danych zmiennej.

    ```vb
    Public Static newCustomer As Customer
    ```

    Jeśli nie określisz typu danych, zostanie użyta wartość domyślna: `Object` .

5. Postępuj zgodnie z `As` klauzulą znaku równości ( `=` ) i obserwuj znak równości ze początkową wartością zmiennej.

    Visual Basic przypisuje określoną wartość do zmiennej przy każdym uruchomieniu `Dim` instrukcji. Jeśli nie określisz wartości początkowej, Visual Basic przypisze domyślną wartość początkową dla typu danych zmiennej, gdy po raz pierwszy wprowadzi kod, który zawiera `Dim` instrukcję.

    Jeśli zmienna jest typem referencyjnym, można utworzyć wystąpienie klasy, dołączając słowo kluczowe [new operatora](../../../language-reference/operators/new-operator.md) w `As` klauzuli. Jeśli nie używasz `New` , początkowa wartość zmiennej to [Nothing](../../../language-reference/nothing.md).

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a>Zobacz też

- [Zmienne](index.md)
- [Deklaracja zmiennej](variable-declaration.md)
- [Nazwy zadeklarowanych elementów](../declared-elements/declared-element-names.md)
- [Charakterystyka zadeklarowanych elementów](../declared-elements/declared-element-characteristics.md)
- [Typy wartości i odwołań](../data-types/value-types-and-reference-types.md)
- [Instrukcje](../../../language-reference/statements/index.md)
- [Wnioskowanie o typie lokalnym](local-type-inference.md)
- [Option Infer — Instrukcja](../../../language-reference/statements/option-infer-statement.md)
