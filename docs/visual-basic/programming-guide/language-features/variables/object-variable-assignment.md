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
ms.openlocfilehash: dff1b9bb9e87f827663786cac3f33531db41b2c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840279"
---
# <a name="object-variable-assignment-visual-basic"></a>Przypisanie zmiennej obiektu (Visual Basic)
Instrukcja przypisania normalne umożliwia przydzielanie obiektu do zmiennej obiektu. Możesz przypisać wyrażenie obiektu lub [nic](../../../../visual-basic/language-reference/nothing.md) — słowo kluczowe, w poniższym przykładzie pokazano.  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing` oznacza, że nie ma obiektu aktualnie przypisana do zmiennej.  
  
## <a name="initialization"></a>Inicjalizacja  
 Po kodzie rozpoczyna się uruchomiony, zmienne są inicjowane na obiekt `Nothing`. Te, których deklaracje zawierają inicjowania są ponownie inicjowane na wartości, które określisz, gdy wykonywane są instrukcje deklaracji.  
  
 Inicjowanie można uwzględnić w swojej deklaracji, za pomocą [New](../../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe. Poniższe instrukcje deklaracji deklarują zmienne obiektów `testUri` i `ver` i przypisywać im konkretnych obiektów. Każdy używa jednego z przeciążenia konstruktorów z odpowiedniej klasy do inicjalizacji obiektu.  
  
```  
Dim testUri As New System.Uri("https://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a>Usuwanie skojarzeń  
 Ustawienie zmiennej obiektu `Nothing` zaprzestaje skojarzenia zmiennej z dowolnego określonego obiektu. Zapobiega to przypadkowym zmianom obiektu przez zmianę zmiennej. Umożliwia on również sprawdzić, czy zmienna obiektu wskazuje prawidłowego obiektu, co ilustruje poniższy przykład.  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 Jeśli obiekt, który Twoja zmienna odwołuje się do innej aplikacji, ten test nie może określić, czy tę aplikację ma zakończone lub po prostu unieważnione obiektu.  
  
 Zmienna obiektu z wartością `Nothing` jest również nazywany *null odwołanie*.  
  
## <a name="current-instance"></a>Bieżące wystąpienie  
 *Bieżącego wystąpienia* obiektu jest ten, w którym aktualnie wykonuje kod. Ponieważ cały kod jest wykonywany wewnątrz procedury, bieżące wystąpienie jest w której wywołano procedury.  
  
 `Me` — Słowo kluczowe działa jako zmienną obiektu odwołanie do bieżącego wystąpienia. Jeśli nie jest procedurą [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), można użyć `Me` — słowo kluczowe, aby uzyskać wskaźnik do bieżącego wystąpienia. Udostępnione procedury można skojarzyć z określonego wystąpienia klasy.  
  
 Za pomocą `Me` jest szczególnie przydatne w przypadku przekazywania bieżącego wystąpienia do procedury w innym module. Na przykład załóżmy, że masz wiele dokumentów XML i chcesz dodać standardowy tekst do wszystkich z nich. W poniższym przykładzie zdefiniowano procedury, aby to zrobić.  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 Każdy obiekt dokumentu XML może następnie wywołania tej procedury i przekaż jej bieżące wystąpienie jako argument. Poniższy przykład przedstawia to.  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Instrukcje: Deklarowanie zmiennej obiektu i przydzielanie obiektu do niego w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Instrukcje: Sprawianie Aby zmienna obiektu nie odwoływała się do dowolnego wystąpienia](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
