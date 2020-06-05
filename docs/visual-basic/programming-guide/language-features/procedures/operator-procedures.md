---
title: Procedury operatorów
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: a1dd183570c8aa50efff85bdaebef90bd3b0120f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364321"
---
# <a name="operator-procedures-visual-basic"></a>Procedury operatorów (Visual Basic)

Procedura operatora to seria Visual Basic instrukcji, które definiują zachowanie operatora standardowego (takiego jak `*` , `<>` lub `And` ) dla zdefiniowanej klasy lub struktury. Jest to również nazywane *przeciążeniem operatora*.

## <a name="when-to-define-operator-procedures"></a>Kiedy należy definiować procedury operatorów

Po zdefiniowaniu klasy lub struktury można zadeklarować zmienne jako typu tej klasy lub struktury. Czasami taka zmienna musi brać udział w operacji jako część wyrażenia. Aby to zrobić, musi to być operand operatora.

Visual Basic definiuje operatory tylko dla podstawowych typów danych. Można zdefiniować zachowanie operatora, gdy jeden lub oba operandy są typu klasy lub struktury.

Aby uzyskać więcej informacji, zobacz [instrukcja operatora](../../../language-reference/statements/operator-statement.md).

## <a name="types-of-operator-procedure"></a>Typy procedur operatora

Procedura operatora może być jednym z następujących typów:

- Definicja operatora jednoargumentowego, gdzie argument jest typu klasy lub struktury.

- Definicja operatora binarnego, w którym co najmniej jeden z argumentów jest typem klasy lub struktury.

- Definicja operatora konwersji, gdzie argument jest typu klasy lub struktury.

- Definicja operatora konwersji, która zwraca typ klasy lub struktury.

 Operatory konwersji są zawsze jednoargumentowe i zawsze `CType` są używane jako definiowane operatory.

## <a name="declaration-syntax"></a>Składnia deklaracji

Składnia do deklarowania procedury operatora jest następująca:

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

Użyj `Widening` `Narrowing` słowa kluczowego or tylko w operatorze konwersji typu. Symbol operatora jest zawsze [CType Funkcja](../../../language-reference/functions/ctype-function.md) dla operatora konwersji typu.

Należy zadeklarować dwa operandy do definiowania operatora binarnego i zadeklarować jeden operand do definiowania operatora jednoargumentowego, łącznie z operatorem konwersji typu. Wszystkie operandy muszą być zadeklarowane `ByVal` .

Każdy operand należy zadeklarować w taki sam sposób, w jaki deklaruje parametry [procedur podrzędnych](./sub-procedures.md).

### <a name="data-type"></a>Typ danych

Ponieważ definiujesz operator dla zdefiniowanej klasy lub struktury, co najmniej jeden z operandów musi być typem danych tej klasy lub struktury. Dla operatora konwersji typu argument operacji lub typ zwracany musi być typem danych klasy lub struktury.

Aby uzyskać więcej informacji, zobacz [instrukcja operatora](../../../language-reference/statements/operator-statement.md).

## <a name="calling-syntax"></a>Składnia wywołania

Procedurę operatora można wywołać niejawnie przy użyciu symbolu operatora w wyrażeniu. Należy podać operandy tak samo jak w przypadku wstępnie zdefiniowanych operatorów.

Składnia niejawnego wywołania procedury operatora jest następująca:

`Dim testStruct As`  *structurename*

`Dim testNewStruct As`  *strukturaname* `= testStruct` *operatorsymbol*      `10`

### <a name="illustration-of-declaration-and-call"></a>Ilustracja deklaracji i wywołania

Poniższa struktura przechowuje podpisaną 128-bitową wartość całkowitą jako składnik wysokiej kolejności i niskiego rzędu. Definiuje operator, `+` Aby dodawać dwie `veryLong` wartości i generować wartość będącą wynikiem `veryLong` .

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

Poniższy przykład przedstawia typowe wywołanie `+` operatora zdefiniowanego w `veryLong` .

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury własności](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Operator — Instrukcja](../../../language-reference/statements/operator-statement.md)
- [Instrukcje: definiowanie operatora](./how-to-define-an-operator.md)
- [Instrukcje: definiowanie operatora konwersji](./how-to-define-a-conversion-operator.md)
- [Instrukcje: wywoływanie procedury operatora](./how-to-call-an-operator-procedure.md)
- [Instrukcje: używanie klasy definiującej operatory](./how-to-use-a-class-that-defines-operators.md)
