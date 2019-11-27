---
title: Przypisanie zmiennej obiektu
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
ms.openlocfilehash: 93de17490935d6d5cad01000e9ee3e2fe55bd16c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351829"
---
# <a name="object-variable-assignment-visual-basic"></a>Przypisanie zmiennej obiektu (Visual Basic)

Możesz użyć normalnej instrukcji przypisania, aby przypisać obiekt do zmiennej obiektu. Można przypisać wyrażenie obiektu lub słowo kluczowe [Nothing](../../../../visual-basic/language-reference/nothing.md) , jak pokazano w poniższym przykładzie.

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

`Nothing` oznacza, że żaden obiekt nie jest obecnie przypisany do zmiennej.

## <a name="initialization"></a>Inicjowanie

Gdy kod zacznie działać, zmienne obiektu są inicjowane w celu `Nothing`. Te, których deklaracje obejmują inicjalizację, są ponownie inicjowane do wartości określonych podczas wykonywania instrukcji deklaracji.

Można uwzględnić inicjalizację w deklaracji za pomocą słowa kluczowego [New](../../../../visual-basic/language-reference/operators/new-operator.md) . Następujące instrukcje deklaracji deklarują zmienne obiektów `testUri` i `ver` i przypisują do nich określone obiekty. Każdy z nich używa jednego z przeciążonych konstruktorów odpowiedniej klasy w celu zainicjowania obiektu.

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a>Usunięcia powiązania zastrzeżonego

Ustawienie zmiennej obiektu na `Nothing` przerywa skojarzenie zmiennej z dowolnym określonym obiektem. Zapobiega to przypadkowemu zmianie obiektu przez zmianę zmiennej. Pozwala również sprawdzić, czy zmienna obiektu wskazuje prawidłowy obiekt, jak pokazano w poniższym przykładzie.

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

Jeśli obiekt, do którego odwołuje się zmienna, znajduje się w innej aplikacji, ten test nie może określić, czy aplikacja została zakończona, czy po prostu unieważnia obiekt.

Zmienna obiektu o wartości `Nothing` jest również nazywana *odwołaniem o wartości null*.

## <a name="current-instance"></a>Bieżące wystąpienie

*Bieżące wystąpienie* obiektu to ten, w którym kod jest aktualnie wykonywany. Ponieważ cały kod jest wykonywany wewnątrz procedury, bieżące wystąpienie jest tym, w którym procedura została wywołana.

Słowo kluczowe `Me` działa jako zmienna obiektu odwołująca się do bieżącego wystąpienia. Jeśli procedura nie jest [udostępniona](../../../../visual-basic/language-reference/modifiers/shared.md), może użyć słowa kluczowego `Me`, aby uzyskać wskaźnik do bieżącego wystąpienia. Współużytkowane procedury nie mogą być skojarzone z określonym wystąpieniem klasy.

Używanie `Me` jest szczególnie przydatne do przekazywania bieżącego wystąpienia do procedury w innym module. Załóżmy na przykład, że masz pewną liczbę dokumentów XML i chcesz dodać do nich część tekstu standardowego. Poniższy przykład definiuje procedurę, aby to zrobić.

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

Każdy obiekt dokumentu XML może następnie wywołać procedurę i przekazać jej bieżące wystąpienie jako argument. Poniższy przykład ilustruje to.

```vb
addStandardText(Me)
```

## <a name="see-also"></a>Zobacz także

- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Instrukcje: deklarowanie zmiennej obiektu i przypisywanie do niej obiektu w Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Instrukcje: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
