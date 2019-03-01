---
title: 'Instrukcje: Wywoływanie procedury zwracającej wartość (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 10167075e903693df804cba044301e1f1bc6306e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974461"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Instrukcje: Wywoływanie procedury zwracającej wartość (Visual Basic)
A `Function` procedury zwraca wartość do wywołującego kodu. Zostanie ona wywołana przez dołączenie jego nazwa i argumenty albo po prawej stronie instrukcji przypisania lub w wyrażeniu.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>Aby wywołać procedurę funkcji w wyrażeniu  
  
1.  Użyj `Function` procedury nazwij ten sam sposób, należy użyć zmiennej. Możesz użyć `Function` wywoływania gdziekolwiek w wyrażeniu można użyć zmiennej lub stała.  
  
2.  Postępuj zgodnie z nazwą procedury należy umieścić na liście argumentów za pomocą nawiasów. Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów. Jednak przy użyciu nawiasów sprawia, że Twój kod łatwiejsza do odczytania.  
  
3.  Argumenty należy umieścić na liście argumentów w nawiasie rozdzielone przecinkami. Należy podać argumenty w tej samej kolejności, `Function` procedura określa odpowiednich parametrów.  
  
     Możesz też przekazać jeden lub więcej argumentów według nazwy. Aby uzyskać więcej informacji, zobacz [przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md).  
  
4.  Wartość zwracana z procedury uczestniczy w wyrażeniu, podobnie jak wartość zmiennej lub będzie stałą.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Aby wywołać procedurę Function w instrukcji przypisania  
  
1.  Użyj `Function` nazwy procedury po równości (`=`) Zaloguj się w instrukcji przypisania.  
  
2.  Postępuj zgodnie z nazwą procedury należy umieścić na liście argumentów za pomocą nawiasów. Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów. Jednak przy użyciu nawiasów sprawia, że Twój kod łatwiejsza do odczytania.  
  
3.  Argumenty należy umieścić na liście argumentów w nawiasie rozdzielone przecinkami. Należy podać argumenty w tej samej kolejności, `Function` procedura określa odpowiednie parametry, chyba że przekazujesz je według nazwy.  
  
4.  Wartość zwracana z procedury są przechowywane w zmiennej lub właściwość po lewej stronie w instrukcji przypisania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wywołuje Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> można pobrać wartości zmiennej środowiskowej systemu operacyjnego. Pierwszy wiersz wywołania `Environ` w wyrażeniach, a drugi wiersz wywołuje on w instrukcji przypisania. `Environ` pobiera nazwę zmiennej, jako jedyny argument. Zwraca wartość zmiennej do wywołującego kodu.  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Zobacz także
- [Procedury funkcji](./function-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Function, instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrukcje: Utwórz procedurę, która zwraca wartość](./how-to-create-a-procedure-that-returns-a-value.md)
- [Instrukcje: Zwracanie wartości z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Instrukcje: Wywoływanie procedury, która nie zwraca wartości](./how-to-call-a-procedure-that-does-not-return-a-value.md)
