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
ms.openlocfilehash: 9ae1a307e8c886166d516140b7f100a411cedcfa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410377"
---
# <a name="object-variable-assignment-visual-basic"></a>Przypisanie zmiennej obiektu (Visual Basic)

Możesz użyć normalnej instrukcji przypisania, aby przypisać obiekt do zmiennej obiektu. Można przypisać wyrażenie obiektu lub słowo kluczowe [Nothing](../../../language-reference/nothing.md) , jak pokazano w poniższym przykładzie.

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

`Nothing`oznacza, że żaden obiekt nie jest aktualnie przypisany do zmiennej.

## <a name="initialization"></a>Inicjalizacja

Gdy kod zacznie działać, zmienne obiektu są inicjowane do `Nothing` . Te, których deklaracje obejmują inicjalizację, są ponownie inicjowane do wartości określonych podczas wykonywania instrukcji deklaracji.

Można uwzględnić inicjalizację w deklaracji za pomocą słowa kluczowego [New](../../../language-reference/operators/new-operator.md) . Następujące instrukcje deklaracji deklarują zmienne obiektów `testUri` i `ver` przypisują do nich określone obiekty. Każdy z nich używa jednego z przeciążonych konstruktorów odpowiedniej klasy w celu zainicjowania obiektu.

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a>Usunięcia powiązania zastrzeżonego

Ustawienie zmiennej obiektu, aby nie `Nothing` przerywa skojarzenia zmiennej z żadnym konkretnym obiektem. Zapobiega to przypadkowemu zmianie obiektu przez zmianę zmiennej. Pozwala również sprawdzić, czy zmienna obiektu wskazuje prawidłowy obiekt, jak pokazano w poniższym przykładzie.

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

Jeśli obiekt, do którego odwołuje się zmienna, znajduje się w innej aplikacji, ten test nie może określić, czy aplikacja została zakończona, czy po prostu unieważnia obiekt.

Zmienna obiektu o wartości `Nothing` jest również nazywana *odwołaniem o wartości null*.

## <a name="current-instance"></a>Bieżące wystąpienie

*Bieżące wystąpienie* obiektu to ten, w którym kod jest aktualnie wykonywany. Ponieważ cały kod jest wykonywany wewnątrz procedury, bieżące wystąpienie jest tym, w którym procedura została wywołana.

`Me`Słowo kluczowe działa jako zmienna obiektu odwołująca się do bieżącego wystąpienia. Jeśli procedura nie jest [udostępniona](../../../language-reference/modifiers/shared.md), może użyć `Me` słowa kluczowego, aby uzyskać wskaźnik do bieżącego wystąpienia. Współużytkowane procedury nie mogą być skojarzone z określonym wystąpieniem klasy.

Użycie `Me` jest szczególnie przydatne w przypadku przekazywania bieżącego wystąpienia do procedury w innym module. Załóżmy na przykład, że masz pewną liczbę dokumentów XML i chcesz dodać do nich część tekstu standardowego. Poniższy przykład definiuje procedurę, aby to zrobić.

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

Każdy obiekt dokumentu XML może następnie wywołać procedurę i przekazać jej bieżące wystąpienie jako argument. Poniższy przykład ilustruje to.

```vb
addStandardText(Me)
```

## <a name="see-also"></a>Zobacz też

- [Zmienne obiektów](object-variables.md)
- [Deklaracja zmiennej obiektu](object-variable-declaration.md)
- [Wartości zmiennej obiektu](object-variable-values.md)
- [Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do It w Visual Basic](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Porady: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia](how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [Me, My, MyBase i MyClass](../../program-structure/me-my-mybase-and-myclass.md)
