---
title: Procedury funkcji (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: 887c930cb757b012542c97d64a57a62882a2eed3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="function-procedures-visual-basic"></a>Procedury funkcji (Visual Basic)
A `Function` procedura jest serię instrukcji języka Visual Basic otoczony `Function` i `End Function` instrukcje. `Function` Procedury wykonuje zadanie, a następnie zwraca sterowania do wywołującego kodu. Zwraca kontroli, również zwraca wartość do wywołującego kodu.  
  
 Zawsze procedura jest wywoływana, jego instrukcje uruchamiania, zaczynając od pierwszej instrukcji wykonywalnej po `Function` instrukcji i kończąc pierwszy `End Function`, `Exit Function`, lub `Return` Napotkano instrukcję.  
  
 Można zdefiniować `Function` procedury w module, klasy lub struktury. Jest `Public` domyślnie oznacza wywołać ją z dowolnego miejsca w aplikacji, który ma dostęp do modułu, klasy lub struktury ona zdefiniowana.  
  
 A `Function` może potrwać argumenty, takie jak stałe, zmiennych lub wyrażeń, które są przekazywane do niej przez kod wywołujący.  
  
## <a name="declaration-syntax"></a>Składnia deklaracji  
 Składnia deklaracji `Function` procedura wygląda następująco:  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 *Modyfikatory* można określić poziom dostępu i informacji dotyczących przeładowanie, zastępowanie udostępniania i przesłanianie. Aby uzyskać więcej informacji, zobacz [instrukcji Function](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Deklarowanie tak samo jak w przypadku każdego parametru [procedury Sub](./sub-procedures.md).  
  
### <a name="data-type"></a>Typ danych  
 Każdy `Function` procedura ma typ danych, jest tylko każdej zmiennej. Ten typ danych jest określony przez `As` w klauzuli `Function` instrukcji która określa typ danych wartości, funkcja zwraca wartość do wywołującego kodu. Następujące przykładowe deklaracje ilustrację.  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 Aby uzyskać więcej informacji, zobacz "Części" w [instrukcji Function](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="returning-values"></a>Zwracanie wartości  
 Wartość `Function` procedury wysyła Wstecz, aby kod wywołujący nosi nazwę swojej zwracanej wartości. Procedura zwraca tę wartość w jeden z dwóch sposobów:  
  
-   Używa `Return` instrukcji, aby określić zwracanej wartości i zwraca kontrolować natychmiast do wywoływania programu. Ilustruje to poniższy przykład.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   Przypisuje wartość do jego własnej nazwy funkcji w jedną lub więcej instrukcji procedury. Formant nie powróci do wywoływania programu do `Exit Function` lub `End Function` instrukcja jest wykonywana. Ilustruje to poniższy przykład.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 Zaletą przypisywanie wartości zwracanej nazwa funkcji jest, że formant nie zwraca z procedury aż do napotkania `Exit Function` lub `End Function` instrukcji. Dzięki temu można przypisać wartości wstępny i dostosowanie go później, jeśli to konieczne.  
  
 Aby uzyskać więcej informacji na temat zwracanie wartości, zobacz [instrukcji Function](../../../../visual-basic/language-reference/statements/function-statement.md). Informacje dotyczące zwracania tablic, zobacz [tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="calling-syntax"></a>Składnia wywoływania  
 Wywołuje się `Function` procedury w tym jego nazwa i argumenty albo po prawej stronie instrukcji przypisania lub w wyrażeniu. Należy podać wartości dla wszystkich argumentów, które nie są opcjonalne i listy argumentów należy ująć w nawias. Jeśli nie jest dostarczony bez argumentów, opcjonalnie można pominąć nawiasów.  
  
 Składnia wywołania `Function` procedura wygląda następująco:  
  
 *l-wartością*`=`*functionname* `[(` *listaargumentów*  `)]`  
  
 `If ((` *FunctionName* `[(` *listaargumentów* `)] / 3) <=` *wyrażenia*  `) Then`  
  
 Podczas wywoływania `Function` procedury, nie trzeba używać jej zwracanych wartości. Jeśli nie chcesz, wykonywane są wszystkie akcje funkcji, ale wartość zwracana jest ignorowana. <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> jest często nazywana w ten sposób.  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustracja deklaracji i wywołanie  
 Następujące `Function` procedury oblicza najdłuższego boku lub przeciwprostokątnej trójkąta prawo podanych wartości dla obu stron.  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 W poniższym przykładzie przedstawiono typowe wywołania `hypotenuse`.  
  
 [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Sub, procedury](./sub-procedures.md)  
 [Procedury właściwości](./property-procedures.md)  
 [Procedury operatorów](./operator-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Function, instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Instrukcje: tworzenie procedury, która zwraca wartość](./how-to-create-a-procedure-that-returns-a-value.md)  
 [Instrukcje: zwracanie wartości z procedury](./how-to-return-a-value-from-a-procedure.md)  
 [Instrukcje: wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)
