---
title: Procedury operatorów (Visual Basic)
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
ms.openlocfilehash: 5b4641ce8509e3111a11ed803d36194d5a301bce
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805714"
---
# <a name="operator-procedures-visual-basic"></a>Procedury operatorów (Visual Basic)
Procedury operatora jest szereg instrukcji, które definiują zachowanie standardowe — operator (takich jak `*`, `<>`, lub `And`) dla klasy lub struktury zdefiniowane. Jest to również *przeładowania operatora*.  
  
## <a name="when-to-define-operator-procedures"></a>Kiedy należy zdefiniować procedury operatorów  
 Po zdefiniowaniu klasy lub struktury, należy zadeklarować zmienne, które mają być typu tej klasy lub struktury. Czasami taki zmiennej musi uczestniczyć w operacji jako część wyrażenia. Aby to zrobić, musi ona być argumentu operacji operatora.  
  
 Visual Basic definiuje operatory tylko na jego typów podstawowych danych. Można określić zachowanie operatora, jeśli jeden lub oba argumenty operacji są typu klasy lub struktury.  
  
 Aby uzyskać więcej informacji, zobacz [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="types-of-operator-procedure"></a>Typy procedury operatora  
 Procedury operatora może być jedną z następujących typów:  
  
-   Definicja operatora jednoargumentowego, gdy argument jest typu klasy lub struktury.  
  
-   Definicja operatora binarnego, gdzie jest co najmniej jeden z argumentów typu klasy lub struktury.  
  
-   Definicja operatora konwersji, gdy argument jest typu klasy lub struktury.  
  
-   Definicja operatora konwersji, który zwraca typ klasy lub struktury.  
  
 Operatory konwersji są zawsze jednoargumentowy i zawsze używaj `CType` jako operator definiujesz.  
  
## <a name="declaration-syntax"></a>Składnia deklaracji  
 Składnia deklaracji procedury operatora wygląda następująco:  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol* `(` *operand1*`[,`*operand2* `]) As` *typu danych*  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 Możesz użyć `Widening` lub `Narrowing` — słowo kluczowe tylko na operatora konwersji typu. Symbol operatora jest zawsze [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md) dla operatora konwersji typu.  
  
 Deklarowanie dwóch argumentów operacji, aby zdefiniować operator binarny i zadeklarować jeden operand, aby zdefiniować operator Jednoargumentowy operator konwersji typu w tym. Należy zadeklarować wszystkie operandy `ByVal`.  
  
 Zadeklaruj każdy argument deklarować parametrów tak samo [procedury Sub](./sub-procedures.md).  
  
### <a name="data-type"></a>Typ danych  
 Ponieważ operator są definiowane w klasie lub strukturze zdefiniowanych, co najmniej jeden z argumentów musi być typu danych z tej klasy lub struktury. Dla operatora konwersji typu argument lub typ zwracany musi być typu danych klasy lub struktury.  
  
 Aby uzyskać więcej informacji, zobacz [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="calling-syntax"></a>Składnia wywoływania  
 Wywołanie procedury operatora jest niejawnie za pomocą symbol operatora w wyrażeniu. Argumenty operacji Podaj ten sam sposób jak w przypadku operatorów wstępnie zdefiniowane.  
  
 Niejawne wywołanie procedury operatora ma następującą składnię:  
  
 `Dim testStruct As`  *structurename*  
  
 `Dim testNewStruct As`  *structurename*`= testStruct`*operatorsymbol*  `10`  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustracja deklaracji i wywołanie  
 Następującą strukturę przechowuje wartość całkowita 128-bitowego jako elementy składowe znaczących i znaczącymi bitami. Definiuje `+` operatora, aby dodać dwa `veryLong` wartości oraz generowanie wynikowa `veryLong` wartość.  
  
 [!code-vb[VbVbcnProcedures#23](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 W poniższym przykładzie przedstawiono typowe wywołania `+` operator zdefiniowany na `veryLong`.  
  
 [!code-vb[VbVbcnProcedures#24](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [przeciążanie operatora w Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Sub, procedury](./sub-procedures.md)  
 [Procedury funkcji](./function-procedures.md)  
 [Procedury właściwości](./property-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Operator, instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Instrukcje: definiowanie operatora](./how-to-define-an-operator.md)  
 [Instrukcje: definiowanie operatora konwersji](./how-to-define-a-conversion-operator.md)  
 [Instrukcje: wywoływanie procedury operatora](./how-to-call-an-operator-procedure.md)  
 [Instrukcje: używanie klasy definiującej operatory](./how-to-use-a-class-that-defines-operators.md)
