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
ms.openlocfilehash: 80c9a77494be95365899c6a25435fcfc5d2a7293
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175022"
---
# <a name="operator-procedures-visual-basic"></a>Procedury operatorów (Visual Basic)
Procedury operatora to szereg instrukcji, które definiują zachowanie standardowego operatora (takie jak `*`, `<>`, lub `And`) dla klasy lub struktury, które zostały zdefiniowane. Jest to również nazywane *przeciążenia operatora*.  
  
## <a name="when-to-define-operator-procedures"></a>Kiedy należy zdefiniować procedury operatorów  
 Po zdefiniowaniu klasy lub struktury można zadeklarować zmienne typu tej klasy lub struktury. Czasami takiej zmiennej musi uczestniczyć w operacji jako część wyrażenia. Aby to zrobić, musi być operand operatora.  
  
 Visual Basic definiuje operatory tylko na jego typów podstawowych danych. Można zdefiniować zachowanie operatorowi, gdy jeden lub oba operandy są typu klasy lub struktury.  
  
 Aby uzyskać więcej informacji, zobacz [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="types-of-operator-procedure"></a>Typy procedury operatora  
 Procedury operatora może być jednym z następujących typów:  
  
-   Definicja operatora jednoargumentowego, gdy argument jest typu klasy lub struktury.  
  
-   Definicja operatora binarnego, gdzie jest co najmniej jeden z argumentów typu klasy lub struktury.  
  
-   Definicja operatora konwersji, gdy argument jest typu klasy lub struktury.  
  
-   Definicja operatora konwersji, która zwraca typ klasy lub struktury.  
  
 Operatory konwersji są zawsze jednoargumentowy i zawsze używaj `CType` jako operator jest definiowany.  
  
## <a name="declaration-syntax"></a>Składnia deklaracji  
 Składnia do deklarowania procedury operatora jest następująca:  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol* `(` *operand1*`[,`*operand2* `]) As` *typu danych*   
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 Możesz użyć `Widening` lub `Narrowing` — słowo kluczowe tylko dla operatora konwersji typu. Symbol operatora jest zawsze [funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md) dla operatora konwersji typu.  
  
 Zadeklaruj dwóch argumentów operacji, aby zdefiniować operator binarny i Zadeklaruj jeden argument, aby zdefiniować operator jednoargumentowy, łącznie z operatora konwersji typu. Wszystkie operandy muszą być zadeklarowane `ByVal`.  
  
 Zadeklaruj każdy argument ten sam sposób możesz deklarować parametry [procedury Sub](./sub-procedures.md).  
  
### <a name="data-type"></a>Typ danych  
 Ponieważ operator są definiowane dla klasy lub struktury, zdefiniowane przez Ciebie, co najmniej jeden z argumentów musi być typu danych z tej klasy lub struktury. Dla operatora konwersji typu argument lub zwracany typ musi być typu danych, klasy lub struktury.  
  
 Aby uzyskać więcej informacji, zobacz [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="calling-syntax"></a>Składnia wywoływania  
 Wywoływanie procedury operatora jest niejawnie przy użyciu znaku operator w wyrażeniu. Argumenty operacji Podaj ten sam sposób jak w przypadku operatorów wstępnie zdefiniowane.  
  
 Składnia wywołanie niejawne procedury operatora jest następująca:  
  
 `Dim testStruct As`  *structurename*  
  
 `Dim testNewStruct As`  *structurename*`= testStruct`*operatorsymbol*   `10`  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustracja deklaracji i wywołanie  
 Następującą strukturę przechowuje wartość liczby całkowitej ze znakiem 128-bitowego, jako części składowe wyższego rzędu i niskiego rzędu. Definiuje on `+` operatora, aby dodać dwa `veryLong` wartości i generować co `veryLong` wartość.  
  
 [!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]  
  
 W poniższym przykładzie przedstawiono typowe wywołanie `+` operator wobec `veryLong`.  
  
 [!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]  

## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Operator — Instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Instrukcje: Definiowanie operatora](./how-to-define-an-operator.md)
- [Instrukcje: Definiowanie operatora konwersji](./how-to-define-a-conversion-operator.md)
- [Instrukcje: Wywoływanie procedury operatora](./how-to-call-an-operator-procedure.md)
- [Instrukcje: Używanie klasy definiującej operatory](./how-to-use-a-class-that-defines-operators.md)
