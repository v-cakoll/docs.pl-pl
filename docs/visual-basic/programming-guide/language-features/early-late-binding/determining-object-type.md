---
title: Określanie typu obiektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: 5980549dd063b2c7d5c60ebd4e9762284c072009
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586621"
---
# <a name="determining-object-type-visual-basic"></a>Określanie typu obiektu (Visual Basic)
Obiekt generyczny zmienne (czyli zmienne został zadeklarowany jako `Object`) może zawierać obiekty z dowolnej klasy. W przypadku używania zmiennych typu `Object`, konieczne może być różne akcje na podstawie klasy obiektu; na przykład niektóre obiekty mogą nie obsługiwać określoną właściwość lub metoda. Visual Basic zapewnia dwa sposoby kontrolowania, jakiego typu obiektu jest przechowywany w zmiennej obiektu: `TypeName` funkcji i `TypeOf...Is` operatora.  
  
## <a name="typename-and-typeofis"></a>TypeName, jak i TypeOf... Jest  
 `TypeName` Funkcja zwraca wartość typu ciąg i sprawdza się najlepiej, gdy należy zapisać lub wyświetlić nazwę klasy obiektu, jak pokazano na następujący fragment kodu:  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 `TypeOf...Is` Operator jest najlepszym wyborem do testowania typu obiektu, ponieważ jest znacznie szybsze niż porównania ciągu równoważnego przy użyciu `TypeName`. Poniższy fragment kodu używa `TypeOf...Is` w ramach `If...Then...Else` instrukcji:  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 W tym miejscu jest zaległe word ostrożności. `TypeOf...Is` Operator zwraca `True` Jeśli obiekt jest określonego typu lub pochodzi z określonego typu. Prawie wszystko, co zrobić za pomocą Visual Basic obejmuje obiekty, które zawierają jakieś elementy, które nie są zazwyczaj uważane za obiekty, takie jak ciągi i liczby całkowite. Te obiekty są uzyskiwane z i odziedziczenie metody z <xref:System.Object>. Przy przekazywaniu `Integer` ocenione z `Object`, `TypeOf...Is` operator zwraca `True`. Poniższy przykład informuje, że parametr `InParam` jest zarówno `Object` i `Integer`:  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 W poniższym przykładzie użyto obu `TypeOf...Is` i `TypeName` można ustalić typu obiektu, przekazana do niej w `Ctrl` argumentu. `TestObject` Wywołania procedur `ShowType` z trzech różnych rodzajów formantów.  
  
#### <a name="to-run-the-example"></a>Aby uruchomić przykład  
  
1.  Utwórz nowy projekt aplikacji Windows i Dodaj <xref:System.Windows.Forms.Button> kontroli <xref:System.Windows.Forms.CheckBox> kontroli i <xref:System.Windows.Forms.RadioButton> formantu do formularza.  
  
2.  Przy użyciu przycisku w formularzu, należy wywołać `TestObject` procedury.  
  
3.  Dodaj następujący kod do formularza:  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [Wywoływanie właściwości lub metody za pomocą nazwy ciągu](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Dyrektywa #If...Then...#Else](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [String, typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Integer, typ danych](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
