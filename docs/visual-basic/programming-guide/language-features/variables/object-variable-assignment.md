---
title: Przypisanie zmiennej obiektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: f20a03c4d9a0e33203629ae066686f4c9f25c105
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="object-variable-assignment-visual-basic"></a>Przypisanie zmiennej obiektu (Visual Basic)
Instrukcja przydział normalny umożliwia przydzielanie obiektu do zmiennej obiektu. Można przypisać wyrażenia obiektu lub [nic](../../../../visual-basic/language-reference/nothing.md) — słowo kluczowe, jak w poniższym przykładzie przedstawiono.  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing` oznacza, że nie ma żadnego obiektu aktualnie przypisane do zmiennej.  
  
## <a name="initialization"></a>Inicjalizacja  
 Po kodzie rozpoczyna, zmienne są inicjowane do obiektu `Nothing`. Te, których deklaracje zawierają inicjowania są ponownie inicjowane do wartości, które można określić podczas wykonywania instrukcji deklaracji.  
  
 Inicjowanie można uwzględnić w deklaracji z za pomocą [New](../../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe. Poniższe instrukcje deklaracji Zadeklaruj zmienne obiektu `testUri` i `ver` i przypisz konkretne obiekty do nich. W każdej jedną przeciążone konstruktory odpowiedniej klasy używane do inicjalizacji obiektu.  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a>Ukończona  
 Ustawienie zmiennej obiektu `Nothing` zaprzestaje skojarzenie zmiennej z dowolnego określonego obiektu. Zapobiega to przypadkowym zmianom, zmieniając zmiennej obiektu. Można też sprawdzić, czy zmienna obiektu wskazuje prawidłowy obiekt, jak przedstawiono na poniższym przykładzie.  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 W przypadku obiektu, do którego odnosi się zmienna użytkownika w innej aplikacji, ten test nie może określić, czy tę aplikację ma zakończone lub po prostu unieważnienie obiektu.  
  
 Zmienna obiektu o wartości `Nothing` jest również nazywany *odwołanie o wartości null*.  
  
## <a name="current-instance"></a>Bieżące wystąpienie  
 *Bieżącego wystąpienia* obiektu jest ten, w którym kod jest aktualnie wykonywany. Ponieważ cały kod jest wykonywana wewnątrz procedury, bieżące wystąpienie jest w którym została wywołana procedura.  
  
 `Me` — Słowo kluczowe działa jako zmienna obiektu odwołanie do bieżącego wystąpienia. Jeśli nie jest procedurą [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), może użyć `Me` — słowo kluczowe uzyskać wskaźnik do bieżącego wystąpienia. Procedury udostępnionego nie może być skojarzony z określonym wystąpieniem klasy.  
  
 Przy użyciu `Me` jest szczególnie przydatne podczas przekazywania do procedury w innym module bieżącego wystąpienia. Na przykład załóżmy, że liczba dokumentów XML i chcesz dodać tekst standardowy do wszystkich z nich. W poniższym przykładzie zdefiniowano procedury w tym celu.  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 Każdego obiektu dokumentu XML można następnie wywołania tej procedury i przekaż jej bieżące wystąpienie jako argument. W poniższym przykładzie pokazano to.  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do niego w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [Instrukcje: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)  
 [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
