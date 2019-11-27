---
title: 'Porady: przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 83670ae6af0904156b08398024658cf504b7663f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346817"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Porady: przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji (Visual Basic)

Jeśli często uzyskujesz dostęp do obiektu, który wymaga ścieżki kwalifikacji kilku metod i właściwości, możesz przyspieszyć kod, nie powtarzając się ścieżki kwalifikacji.

Istnieją dwa sposoby, aby uniknąć powtarzania ścieżki kwalifikacji. Obiekt można przypisać do zmiennej lub użyć go w bloku `With`...`End With`.

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

1. Umieść ścieżkę kwalifikacji w instrukcji `With`.

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. Uzyskaj dostęp do elementów członkowskich obiektu wewnątrz bloku `With` przed instrukcją `End With`.

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a>Zobacz także

- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [With...End With, instrukcja](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
