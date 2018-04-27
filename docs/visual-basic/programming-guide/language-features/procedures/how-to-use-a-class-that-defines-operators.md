---
title: 'Porady: używanie klasy definiującej operatory (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e0bcfaeca638dfabb841a9e935b872f76fdf957
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Porady: używanie klasy definiującej operatory (Visual Basic)
Jeśli używasz klasy lub struktury, która definiuje własną operatory są dostępne te operatory języka Visual Basic.  
  
 Definiowanie operatora w klasie lub strukturze jest również nazywany *przeładowanie* operatora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład uzyskuje dostęp do struktury SQL <xref:System.Data.SqlTypes.SqlString>, który definiuje operatory konwersji ([CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md)) w obu kierunkach między ciągu SQL i ciąg języka Visual Basic. Użyj `CType(` *wyrażenia ciągu SQL*, `String)` do przekonwertowania ciągu SQL na ciąg języka Visual Basic i `CType(` *wyrażenia ciągu w języku Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` przekonwertować w innym kierunku.  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <xref:System.Data.SqlTypes.SqlString> Struktury definiuje operator konwersji ([CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md)) z `String` do <xref:System.Data.SqlTypes.SqlString> oraz z <xref:System.Data.SqlTypes.SqlString> do `String`. Instrukcja, która przypisuje `title` do `jobTitle` sprawia, że użycie operatora pierwszy i <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> drugi używa wywołania funkcji.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Upewnij się, że klasy lub struktury, którego używasz definiuje operator, który ma być używany. Zakłada się, że klasy lub struktury ma zdefiniowany co dostępne do przeciążania operatora. Aby uzyskać listę dostępnych operatorów, zobacz [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Dołączyć odpowiednie `Imports` instrukcji SQL ciągu na początku pliku źródłowego (w tym przypadku <xref:System.Data.SqlTypes>).  
  
 Projekt musi mieć odwołania do system.dane i zestawów System.XML.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury operatorów](./operator-procedures.md)  
 [Instrukcje: definiowanie operatora](./how-to-define-an-operator.md)  
 [Instrukcje: definiowanie operatora konwersji](./how-to-define-a-conversion-operator.md)  
 [Instrukcje: wywoływanie procedury operatora](./how-to-call-an-operator-procedure.md)  
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Instrukcje: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
