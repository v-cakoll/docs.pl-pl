---
title: 'Instrukcje: Przyspiesz dostęp do obiektu z długą ścieżką kwalifikacyjną (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: a8e50a2ed04037b48091321dc0c9ac2ea1db35f4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631099"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Instrukcje: Przyspiesz dostęp do obiektu z długą ścieżką kwalifikacyjną (Visual Basic)

Jeśli często uzyskujesz dostęp do obiektu, który wymaga ścieżki kwalifikacji kilku metod i właściwości, możesz przyspieszyć kod, nie powtarzając się ścieżki kwalifikacji.

Istnieją dwa sposoby, aby uniknąć powtarzania ścieżki kwalifikacji. Obiekt można przypisać do zmiennej lub użyć go w `With`... `End With` blok.

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>Aby przyspieszyć dostęp do wysoce kwalifikowanego obiektu przez przypisanie go do zmiennej

1. Zadeklaruj zmienną typu obiektu, do którego jest często uzyskiwany dostęp. Określ ścieżkę kwalifikacji w części inicjującej deklaracji.

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. Użyj zmiennej, aby uzyskać dostęp do elementów członkowskich obiektu.

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>Aby przyspieszyć dostęp do wysoce kwalifikowanego obiektu za pomocą... Koniec z blokiem

1. Umieszczenie ścieżki kwalifikacji w `With` instrukcji.

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. Dostęp do elementów członkowskich obiektu wewnątrz `With` bloku `End With` przed instrukcją.

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a>Zobacz także

- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [With...End With, instrukcja](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
