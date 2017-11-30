---
title: "Określanie typu obiektu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9a63b5cf5941deb4dcc7518880b4dc7d0545803c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="determining-object-type-visual-basic"></a>Określanie typu obiektu (Visual Basic)
Obiekt generyczny zmienne (czyli zmienne można zadeklarować jako `Object`) może przechowywać obiektów z dowolnej klasy. Używając zmiennych typu `Object`, należy wykonać różne operacje, oparty na klasie obiektu; na przykład niektórych obiektów może nie obsługuje określonej właściwości lub metody. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]udostępnia dwa sposoby kontrolowania, jakiego typu obiektu są przechowywane w zmiennej obiektu: `TypeName` funkcji i `TypeOf...Is` operatora.  
  
## <a name="typename-and-typeofis"></a>Właściwość TypeName i TypeOf... Jest  
 `TypeName` Funkcja zwróci ciąg i jest najlepszym rozwiązaniem, gdy potrzebne do przechowywania lub wyświetlana nazwa klasy obiektu, jak pokazano w poniższy fragment kodu:  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 `TypeOf...Is` Operator jest najlepszym wyborem do testowania typu obiektu, ponieważ jest znacznie szybsza niż porównanie ciągu równoważne przy użyciu `TypeName`. Poniższy fragment kodu używa `TypeOf...Is` w `If...Then...Else` instrukcji:  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 Wyraz ostrożność jest termin tutaj. `TypeOf...Is` Operator zwraca `True` Jeśli obiekt jest określonego typu lub pochodzi z konkretnego typu. Prawie wszystko, co się dzieje [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] obejmuje obiekty, do których należą niektóre elementy nie mogą traktować jako obiekty, takie jak parametry i liczb całkowitych. Te obiekty pochodne i dziedziczy metody <xref:System.Object>. Po upływie `Integer` ocenione z `Object`, `TypeOf...Is` operator zwraca `True`. Poniższy przykład zgłasza, że parametr `InParam` jest zarówno `Object` i `Integer`:  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 W poniższym przykładzie użyto zarówno `TypeOf...Is` i `TypeName` można określić typu obiektu przekazana do niej w `Ctrl` argumentu. `TestObject` Wywołań procedur `ShowType` z trzech różnych rodzajów formantów.  
  
#### <a name="to-run-the-example"></a>Aby uruchomić przykład  
  
1.  Utwórz nowy projekt aplikacji systemu Windows i Dodaj <xref:System.Windows.Forms.Button> kontroli, <xref:System.Windows.Forms.CheckBox> kontroli, a <xref:System.Windows.Forms.RadioButton> sterowania do formularza.  
  
2.  Po kliknięciu przycisku w formularzu wywołać `TestObject` procedury.  
  
3.  Dodaj następujący kod do formularza:  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A>  
 [Wywoływanie właściwości lub metody za pomocą nazwy ciągu](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)  
 [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [IF... Następnie... Else — instrukcja](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [String — typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [Integer — typ danych](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
