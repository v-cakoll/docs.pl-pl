---
title: 'Instrukcje: Używanie klasy definiującej operatory (Visual Basic)'
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
ms.openlocfilehash: bd512adf2f06ed0fbd3d36ed3175a0928bf1c57c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58829411"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Instrukcje: Używanie klasy definiującej operatory (Visual Basic)
Jeśli używasz klasy lub struktury, która definiuje swój własny operatory są dostępne te operatory języka Visual Basic.  
  
 Definiowanie operatora dla klasy lub struktury jest również nazywany *przeciążenie* operatora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład uzyskuje dostęp do struktury SQL <xref:System.Data.SqlTypes.SqlString>, która definiuje operatory konwersji ([funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) w obu kierunkach między ciąg SQL i ciąg języka Visual Basic. Użyj `CType(` *wyrażenia ciągu SQL*, `String)` do przekonwertowania ciągu SQL na ciąg języka Visual Basic i `CType(` *wyrażenia ciągu w języku Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` do przekonwertowania w drugą stronę.  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <xref:System.Data.SqlTypes.SqlString> Struktury definiuje operator konwersji ([funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) z `String` do <xref:System.Data.SqlTypes.SqlString> , a drugi z <xref:System.Data.SqlTypes.SqlString> do `String`. Instrukcja, która przypisuje `title` do `jobTitle` sprawia, że użycie pierwszy operator i <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> wywołanie funkcji używa drugiego.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Upewnij się, że klasy lub struktury, którego używasz, określa operator, który chcesz użyć. Nie należy zakładać, że klasa lub struktura został zdefiniowany co dostępne dla przeciążania operatora. Aby uzyskać listę dostępnych operatorów, zobacz [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Dołączyć odpowiednie `Imports` poufności informacji dla ciągu SQL na początku pliku źródłowego (w tym przypadku <xref:System.Data.SqlTypes>).  
  
 Projekt musi mieć odwołania do dane systemowe i System.XML.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: Definiowanie operatora](./how-to-define-an-operator.md)
- [Instrukcje: Definiowanie operatora konwersji](./how-to-define-a-conversion-operator.md)
- [Instrukcje: Wywoływanie procedury operatora](./how-to-call-an-operator-procedure.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrukcje: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
