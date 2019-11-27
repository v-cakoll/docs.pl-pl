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
ms.openlocfilehash: b62a730e8ade211821826afbb55fa8858ea311a3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341088"
---
# <a name="function-procedures-visual-basic"></a>Procedury funkcji (Visual Basic)
Procedura `Function` jest serią Visual Basic instrukcji ujętych w instrukcji `Function` i `End Function`. Procedura `Function` wykonuje zadanie, a następnie zwraca sterowanie do kodu wywołującego. Gdy zwraca formant, zwraca również wartość do kodu wywołującego.  
  
 Za każdym razem, gdy procedura jest wywoływana, jej instrukcje są uruchamiane, rozpoczynając od pierwszej instrukcji wykonywalnej po instrukcji `Function` i kończąc na pierwszej instrukcji `End Function`, `Exit Function`lub `Return`.  
  
 Można zdefiniować `Function` procedury w module, klasie lub strukturze. Domyślnie jest `Public`, co oznacza, że można wywołać ją z dowolnego miejsca w aplikacji, która ma dostęp do modułu, klasy lub struktury, w której został zdefiniowany.  
  
 Procedura `Function` może przyjmować argumenty, takie jak stałe, zmienne lub wyrażenia, które są przekazane do niego przez wywołujący kod.  
  
## <a name="declaration-syntax"></a>Składnia deklaracji  
 Składnia do deklarowania procedury `Function` jest następująca:  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 *Modyfikatory* mogą określać poziom dostępu i informacje dotyczące przeciążania, przesłaniania, udostępniania i przesłaniania. Aby uzyskać więcej informacji, zobacz [Instrukcja function](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Każdy parametr należy zadeklarować w taki sam sposób jak [procedury Sub](./sub-procedures.md).  
  
### <a name="data-type"></a>Typ danych  
 Każda procedura `Function` ma typ danych, tak jak każda zmienna. Ten typ danych jest określany przez klauzulę `As` w instrukcji `Function` i określa typ danych wartości zwracanej przez funkcję do kodu wywołującego. Przedstawiono następujące przykładowe deklaracje.  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 Aby uzyskać więcej informacji, zobacz sekcję "części" w [instrukcji funkcji](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="returning-values"></a>Zwracanie wartości  
 Wartość `Function` procedura jest wysyłana z powrotem do wywołującego kodu jest nazywana jego wartością zwracaną. Ta procedura zwraca tę wartość na jeden z dwóch sposobów:  
  
- Używa instrukcji `Return`, aby określić wartość zwracaną, i natychmiast zwraca kontrolę do wywołującego programu. Ilustruje to poniższy przykład.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
- Przypisuje wartość do własnej nazwy funkcji w jednej lub kilku instrukcjach procedury. Formant nie wraca do wywołującego programu do momentu wykonania instrukcji `Exit Function` lub `End Function`. Ilustruje to poniższy przykład.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 Zaletą przypisania wartości zwracanej do nazwy funkcji jest to, że formant nie zwraca z procedury do momentu napotkania instrukcji `Exit Function` lub `End Function`. Pozwala to na przypisanie wartości wstępnej i dostosowanie jej później w razie potrzeby.  
  
 Aby uzyskać więcej informacji na temat zwracanych wartości, zobacz [Instrukcja function](../../../../visual-basic/language-reference/statements/function-statement.md). Aby uzyskać informacje na temat zwracania tablic, zobacz [tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="calling-syntax"></a>Składnia wywołania  
 Procedurę `Function` można wywołać, dołączając jej nazwę i argumenty po prawej stronie instrukcji przypisania lub w wyrażeniu. Musisz podać wartości dla wszystkich argumentów, które nie są opcjonalne, i należy ująć listę argumentów w nawiasach. Jeśli nie podano argumentów, można opcjonalnie pominąć nawiasy.  
  
 Składnia wywołania procedury `Function` jest następująca:  
  
 *lvalue*`=`*FunctionName* `[(` *listaargumentów* `)]`  
  
 `If ((` *functionname* `[(` *listaargumentów* `)] / 3) <=`*Expression* `) Then`  
  
 Po wywołaniu procedury `Function` nie trzeba używać jej wartości zwracanej. W przeciwnym razie wszystkie akcje funkcji są wykonywane, ale zwracana wartość jest ignorowana. <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> jest często wywoływana w ten sposób.  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustracja deklaracji i wywołania  
 Poniższa procedura `Function` oblicza najdłuższy bok lub przeciwprostokątnej w prawym trójkątze, uwzględniając wartości pozostałych dwóch stron.  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
 Poniższy przykład przedstawia typowe wywołanie do `hypotenuse`.  
  
 [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Function, instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrukcje: tworzenie procedury, która zwraca wartość](./how-to-create-a-procedure-that-returns-a-value.md)
- [Instrukcje: zwracanie wartości z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Instrukcje: wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)
