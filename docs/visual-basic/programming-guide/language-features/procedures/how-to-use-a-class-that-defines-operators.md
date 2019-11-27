---
title: 'Porady: używanie klasy definiującej operatory'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: 9ec4b4c07910100dd02cc86e882b44aa7dbd2ced
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346034"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Porady: używanie klasy definiującej operatory (Visual Basic)
Jeśli używasz klasy lub struktury, która definiuje własne operatory, możesz uzyskać dostęp do tych operatorów z Visual Basic.  
  
 Definiowanie operatora w klasie lub strukturze jest również nazywane *przeciążeniem* operatora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład uzyskuje dostęp do struktury SQL <xref:System.Data.SqlTypes.SqlString>, która definiuje operatory konwersji ([Funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) w obu kierunkach między ciągiem SQL i ciągiem Visual Basic. Użyj `CType(`*wyrażenia ciągu SQL*, `String)` do przekonwertowania ciągu SQL na ciąg Visual Basic i `CType(`*Visual Basic wyrażenie ciągu*, <xref:System.Data.SqlTypes.SqlString>`)` do konwersji w innym kierunku.  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 Struktura <xref:System.Data.SqlTypes.SqlString> definiuje operator konwersji ([Funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) z `String` do <xref:System.Data.SqlTypes.SqlString> i innej od <xref:System.Data.SqlTypes.SqlString> do `String`. Instrukcja, która przypisuje `title` do `jobTitle` używa pierwszego operatora, a wywołanie funkcji <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> używa drugiego.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Upewnij się, że używana Klasa lub struktura definiuje operatora, którego chcesz użyć. Nie należy zakładać, że Klasa lub struktura zdefiniowano każdy operator dostępny do przeciążenia. Aby uzyskać listę dostępnych operatorów, zobacz [instrukcja operatora](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Uwzględnij odpowiednią instrukcję `Imports` dla ciągu SQL na początku pliku źródłowego (w tym przypadku <xref:System.Data.SqlTypes>).  
  
 Projekt musi mieć odwołania do System. Data i system. XML.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: definiowanie operatora](./how-to-define-an-operator.md)
- [Instrukcje: definiowanie operatora konwersji](./how-to-define-a-conversion-operator.md)
- [Instrukcje: wywoływanie procedury operatora](./how-to-call-an-operator-procedure.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrukcje: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
