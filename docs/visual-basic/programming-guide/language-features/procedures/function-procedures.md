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
ms.openlocfilehash: 4fd24369380e5f8ccf8de939c36ba72a12dc872e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649612"
---
# <a name="function-procedures-visual-basic"></a>Procedury funkcji (Visual Basic)
A `Function` procedura jest szereg instrukcji ujęta w `Function` i `End Function` instrukcji. `Function` Procedura wykonuje zadanie, a następnie przekazuje sterowanie do kodu wywołującego. Przekazuje sterowanie, również zwraca wartość do wywołującego kodu.  
  
 Każdorazowo, procedura jest wywoływana, jego instrukcje uruchamiania, począwszy od pierwszej instrukcji wykonywalnej po `Function` instrukcji i kończącą pierwszy `End Function`, `Exit Function`, lub `Return` instrukcji napotkany.  
  
 Można zdefiniować `Function` procedury w module, klasy lub struktury. Jest `Public` domyślnie, co oznacza, że można ją wywołać z dowolnego miejsca w aplikacji, które ma dostęp do modułu, klasy lub struktury on zdefiniowany.  
  
 A `Function` procedurę można wykonać argumentów, takich jak stałe, zmienne lub wyrażeń, które są przekazywane do niej przez kod wywołujący.  
  
## <a name="declaration-syntax"></a>Składnia deklaracji  
 Składnia do deklarowania `Function` procedura jest następująca:  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 *Modyfikatory* można określić poziom dostępu i informacji dotyczących przeciążenia, zastępowanie, udostępnianie i cieniowania. Aby uzyskać więcej informacji, zobacz [Function — instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Zadeklaruj taki sam sposób jak w przypadku każdego parametru [procedury Sub](./sub-procedures.md).  
  
### <a name="data-type"></a>Typ danych  
 Każdy `Function` procedura ma typ danych, jest po prostu każdej zmiennej. Ten typ danych jest określony przez `As` w klauzuli `Function` instrukcji która określa typ danych wartości, funkcja zwraca do wywołującego kodu. Następujące deklaracje przykładowe przedstawiają to.  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 Aby uzyskać więcej informacji, zobacz "Części" w [Function — instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="returning-values"></a>Zwracanie wartości  
 Wartość `Function` procedury wysyła Wstecz, aby kod wywołujący nosi nazwę wartość zwracaną. Procedura zwraca tę wartość w jeden z dwóch sposobów:  
  
- Używa ona `Return` instrukcję, aby określić wartości zwracanej i zwraca kontrolę natychmiast program wywołujący. Ilustruje to poniższy przykład.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
- Przypisuje wartość do jego własnej nazwy funkcji w jedną lub więcej instrukcji procedury. Formant powraca do program wywołujący, aż do `Exit Function` lub `End Function` instrukcja jest wykonywana. Ilustruje to poniższy przykład.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 Zaletą przypisywanie wartości zwracanej do nazwy funkcji jest, że kontrolka nie zwraca z procedury aż do napotkania `Exit Function` lub `End Function` instrukcji. Dzięki temu można przypisać wartości wstępny i dostosować go później, jeśli to konieczne.  
  
 Aby uzyskać więcej informacji na temat zwracanie wartości zobacz [Function — instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md). Aby uzyskać informacje dotyczące zwracania tablic, zobacz [tablic](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="calling-syntax"></a>Składnia wywoływania  
 Wywołuje się `Function` procedury, takie jak jego nazwa i argumentów, albo po prawej stronie instrukcji przypisania lub w wyrażeniu. Należy podać wartości w argumentach, które nie są opcjonalne, a na liście argumentów należy ująć w nawiasy. Jeśli zostały dostarczone żadne argumenty, opcjonalnie można pominąć nawiasów.  
  
 Składnia służąca do wywołania `Function` procedura jest następująca:  
  
 *l-wartości*`=`*functionname* `[(` *listaargumentów* `)]`  
  
 `If ((` *FunctionName* `[(` *listaargumentów* `)] / 3) <=` *wyrażenia* `) Then`  
  
 Gdy wywołujesz `Function` procedury, trzeba użyć jego zwracanej wartości. Jeśli tego nie zrobisz, wykonywane są wszystkie akcje funkcji, ale zwracana wartość jest ignorowana. <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> jest często nazywana w ten sposób.  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustracja deklaracji i wywołanie  
 Następujące `Function` procedury oblicza najdłuższy bok lub przeciwprostokątnej trójkąta prostokątnego, biorąc pod uwagę wartości dla obu stron.  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
 W poniższym przykładzie przedstawiono typowe wywołanie `hypotenuse`.  
  
 [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Function, instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrukcje: Utwórz procedurę, która zwraca wartość](./how-to-create-a-procedure-that-returns-a-value.md)
- [Instrukcje: Zwracanie wartości z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Instrukcje: Wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)
