---
title: Określanie typu obiektu
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: a77cc0603a0b61f58a4aa703c4b1e6ef4c26729c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345196"
---
# <a name="determining-object-type-visual-basic"></a>Określanie typu obiektu (Visual Basic)
Zmienne obiektów ogólnych (czyli zmienne zadeklarowane jako `Object`) mogą zawierać obiekty z dowolnej klasy. W przypadku używania zmiennych typu `Object`może być konieczne wykonanie różnych akcji na podstawie klasy obiektu; na przykład niektóre obiekty mogą nie obsługiwać określonej właściwości lub metody. Visual Basic zapewnia dwa sposoby określania, który typ obiektu jest przechowywany w zmiennej obiektu: funkcja `TypeName` i operator `TypeOf...Is`.  
  
## <a name="typename-and-typeofis"></a>TypeName i TypeOf... Była  
 Funkcja `TypeName` zwraca ciąg i jest najlepszym wyborem, gdy trzeba przechowywać lub wyświetlać nazwę klasy obiektu, jak pokazano w poniższym fragmencie kodu:  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 Operator `TypeOf...Is` jest najlepszym wyborem do testowania typu obiektu, ponieważ jest znacznie szybszy niż równoważne porównanie ciągów przy użyciu `TypeName`. Poniższy fragment kodu używa `TypeOf...Is` w instrukcji `If...Then...Else`:  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 W tym miejscu należy wyrazić uwagę na ostrzeżenie. Operator `TypeOf...Is` zwraca `True`, jeśli obiekt jest określonego typu lub pochodzi od określonego typu. Prawie wszystko, co należy zrobić, Visual Basic obejmuje obiekty, które obejmują pewne elementy, które nie są zwykle traktowane jako obiekty, takie jak ciągi i liczby całkowite. Te obiekty pochodzą z i dziedziczą metody z <xref:System.Object>. Po przekazaniu `Integer` i ocenie przy użyciu `Object`, operator `TypeOf...Is` zwraca `True`. Poniższy przykład zgłasza, że parametr `InParam` jest zarówno `Object`, jak i `Integer`:  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 Poniższy przykład używa zarówno `TypeOf...Is`, jak i `TypeName` do określenia typu obiektu, do którego jest przenoszona w argumencie `Ctrl`. Procedura `TestObject` wywołuje `ShowType` z trzema różnymi rodzajami kontrolek.  
  
#### <a name="to-run-the-example"></a>Aby uruchomić przykład  
  
1. Tworzenie nowego projektu aplikacji systemu Windows i Dodawanie kontrolki <xref:System.Windows.Forms.Button>, kontrolki <xref:System.Windows.Forms.CheckBox> i kontrolki <xref:System.Windows.Forms.RadioButton> do formularza.  
  
2. Na przycisku w formularzu Wywołaj procedurę `TestObject`.  
  
3. Dodaj następujący kod do formularza:  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [Wywoływanie właściwości lub metody za pomocą nazwy ciągu](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [If...Then...Else, instrukcja](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [String, typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Integer, typ danych](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
