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
ms.openlocfilehash: 3b1c4ad0ab4fd8d2897aff6ad9097cdc81272455
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410647"
---
# <a name="determining-object-type-visual-basic"></a>Określanie typu obiektu (Visual Basic)
Zmienne obiektów ogólnych (czyli zmienne zadeklarowane jako `Object` ) mogą zawierać obiekty z dowolnej klasy. W przypadku używania zmiennych typu `Object` , może być konieczne wykonanie różnych akcji na podstawie klasy obiektu; na przykład niektóre obiekty mogą nie obsługiwać określonej właściwości lub metody. Visual Basic zapewnia dwa sposoby określania, który typ obiektu jest przechowywany w zmiennej obiektu: `TypeName` funkcji i `TypeOf...Is` operatora.  
  
## <a name="typename-and-typeofis"></a>TypeName i TypeOf... Była  
 `TypeName`Funkcja zwraca ciąg i jest najlepszym wyborem, gdy trzeba przechowywać lub wyświetlać nazwę klasy obiektu, jak pokazano w poniższym fragmencie kodu:  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 `TypeOf...Is`Operator jest najlepszym wyborem do testowania typu obiektu, ponieważ jest znacznie szybszy niż równoważne porównanie ciągów przy użyciu `TypeName` . Poniższy fragment kodu używa `TypeOf...Is` w `If...Then...Else` instrukcji:  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 W tym miejscu należy wyrazić uwagę na ostrzeżenie. `TypeOf...Is`Operator zwraca `True` , jeśli obiekt jest określonego typu lub pochodzi od określonego typu. Prawie wszystko, co należy zrobić, Visual Basic obejmuje obiekty, które obejmują pewne elementy, które nie są zwykle traktowane jako obiekty, takie jak ciągi i liczby całkowite. Te obiekty pochodzą z i dziedziczą metody z <xref:System.Object> . Po przekazaniu `Integer` i obliczeniu z `Object` , `TypeOf...Is` operator zwraca `True` . Poniższy przykład zgłasza, że parametr `InParam` jest zarówno `Object` , jak i `Integer` :  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 W poniższym przykładzie zastosowano `TypeOf...Is` i, `TypeName` Aby określić typ obiektu, który przeszedł do niego w `Ctrl` argumencie. `TestObject`Procedura wywołuje `ShowType` trzy różne rodzaje kontrolek.  
  
#### <a name="to-run-the-example"></a>Aby uruchomić przykład  
  
1. Tworzenie nowego projektu aplikacji systemu Windows i Dodawanie <xref:System.Windows.Forms.Button> kontrolki, <xref:System.Windows.Forms.CheckBox> kontrolki i <xref:System.Windows.Forms.RadioButton> kontrolki do formularza.  
  
2. Na przycisku w formularzu Wywołaj `TestObject` procedurę.  
  
3. Dodaj następujący kod do formularza:  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [Wywoływanie właściwości lub metody za pomocą nazwy ciągu](calling-a-property-or-method-using-a-string-name.md)
- [Object — typ danych](../../../language-reference/data-types/object-data-type.md)
- [If...Then...Else, instrukcja](../../../language-reference/statements/if-then-else-statement.md)
- [Typ danych ciągu](../../../language-reference/data-types/string-data-type.md)
- [Integer, typ danych](../../../language-reference/data-types/integer-data-type.md)
