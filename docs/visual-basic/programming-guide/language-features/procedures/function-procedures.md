---
title: Procedury funkcji
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: b0ba96a875fd8785e45eee565beefe4b961ffc9d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388754"
---
# <a name="function-procedures-visual-basic"></a>Procedury funkcji (Visual Basic)

`Function`Procedura jest serią Visual Basic instrukcji ujętych w `Function` `End Function` instrukcji i. `Function`Procedura wykonuje zadanie, a następnie zwraca sterowanie do kodu wywołującego. Gdy zwraca formant, zwraca również wartość do kodu wywołującego.

Za każdym razem, gdy procedura jest wywoływana, jej instrukcje są uruchamiane, rozpoczynając od pierwszej instrukcji wykonywalnej po `Function` instrukcji i kończąc na pierwszej `End Function` , `Exit Function` , lub `Return` napotkanej instrukcji.

Można zdefiniować `Function` procedurę w module, klasie lub strukturze. Jest to `Public` domyślne ustawienie, które oznacza, że można wywołać go z dowolnego miejsca w aplikacji, która ma dostęp do modułu, klasy lub struktury, w której został zdefiniowany.

`Function`Procedura może przyjmować argumenty, takie jak stałe, zmienne lub wyrażenia, które są do niego przekazane przez wywołujący kod.

## <a name="declaration-syntax"></a>Składnia deklaracji

Składnia do deklarowania `Function` procedury jest następująca:

```vb
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType
    [Statements]
End Function
```

*Modyfikatory* mogą określać poziom dostępu i informacje dotyczące przeciążania, przesłaniania, udostępniania i przesłaniania. Aby uzyskać więcej informacji, zobacz [Instrukcja function](../../../language-reference/statements/function-statement.md).

Każdy parametr należy zadeklarować w taki sam sposób jak [procedury Sub](./sub-procedures.md).

### <a name="data-type"></a>Typ danych

Każda `Function` procedura ma typ danych, tak jak każda zmienna. Ten typ danych jest określany przez `As` klauzulę w `Function` instrukcji i określa typ danych wartości zwracanej przez funkcję do kodu wywołującego. Przedstawiono następujące przykładowe deklaracje.

```vb
Function Yesterday() As Date
End Function

Function FindSqrt(radicand As Single) As Single
End Function
```

Aby uzyskać więcej informacji, zobacz sekcję "części" w [instrukcji funkcji](../../../language-reference/statements/function-statement.md).

### <a name="returning-values"></a>Zwracanie wartości

Wartość, `Function` którą procedura odsyła z powrotem do wywołującego kodu jest nazywana jego wartością zwracaną. Ta procedura zwraca tę wartość na jeden z dwóch sposobów:

- Używa `Return` instrukcji, aby określić wartość zwracaną, i natychmiast zwraca kontrolę do wywołującego programu. Ilustruje to poniższy przykład.

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement immediately transfers control back
      ' to the calling code and returns the value of Expression.
      Return Expression
  End Function
  ```

- Przypisuje wartość do własnej nazwy funkcji w jednej lub kilku instrukcjach procedury. Formant nie wraca do wywołującego programu do momentu `Exit Function` `End Function` wykonania instrukcji lub. Ilustruje to poniższy przykład.

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement does not transfer control back to the calling code.
      FunctionName = Expression
      ' When control returns to the calling code, Expression is the return value.
  End Function
  ```

Zaletą przypisania wartości zwracanej do nazwy funkcji jest to, że formant nie zwraca z procedury do momentu napotkania `Exit Function` `End Function` instrukcji or. Pozwala to na przypisanie wartości wstępnej i dostosowanie jej później w razie potrzeby.

Aby uzyskać więcej informacji na temat zwracanych wartości, zobacz [Instrukcja function](../../../language-reference/statements/function-statement.md). Aby uzyskać informacje na temat zwracania tablic, zobacz [tablice](../arrays/index.md).

## <a name="calling-syntax"></a>Składnia wywołania

Procedurę można wywołać `Function` przez dołączenie jej nazwy i argumentów po prawej stronie instrukcji przypisania lub w wyrażeniu. Musisz podać wartości dla wszystkich argumentów, które nie są opcjonalne, i należy ująć listę argumentów w nawiasach. Jeśli nie podano argumentów, można opcjonalnie pominąć nawiasy.

Składnia wywołania `Function` procedury jest następująca.

*lvalue* `=` *funkcjaname* `[(` *listaargumentów*    `)]`

`If ((`*funkcjaname* `[(` *listaargumentów* `)] / 3) <=` *wyrażenie*  `) Then`

Po wywołaniu `Function` procedury nie trzeba używać jej wartości zwracanej. W przeciwnym razie wszystkie akcje funkcji są wykonywane, ale zwracana wartość jest ignorowana. <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>jest często wywoływany w ten sposób.

### <a name="illustration-of-declaration-and-call"></a>Ilustracja deklaracji i wywołania

Poniższa `Function` procedura oblicza najdłuższy Trójkąt lub przeciwprostokątnej, z prawej strony, z uwzględnieniem wartości pozostałych dwóch stron.

[!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

Poniższy przykład przedstawia typowe wywołanie `hypotenuse` .

[!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]

## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury własności](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Function, instrukcja](../../../language-reference/statements/function-statement.md)
- [Instrukcje: tworzenie procedury, która zwraca wartość](./how-to-create-a-procedure-that-returns-a-value.md)
- [Porady: zwracanie wartości z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Instrukcje: wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)
