---
title: Zmienne obiektów w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: cc5be13293a89e73d1790e94a99d7936f1711e12
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352974"
---
# <a name="object-variables-in-visual-basic"></a>Zmienne obiektów w Visual Basic

Oprócz przechowywania wartości bezpośrednio, zmienna może odwoływać się do obiektu. Obiekt można przypisać do zmiennej powodów przypisane żadnej wartości dla zmiennej:

- Nazwa zmiennej jest często krótsze i łatwiejsze do zapamiętania niż pełną ścieżkę metody i właściwości, które są niezbędne do dostępu do samego obiektu.

- Użycie zmiennej, która odwołuje się do obiektu jest bardziej wydajne niż wielokrotnie uzyskiwania dostępu do samego obiektu za pomocą niezbędne metody lub właściwości.

- Możesz zmienić zmienną do odwoływania się do innych obiektów, podczas gdy kod jest uruchomiony.

## <a name="making-code-shorter"></a>Tworzenie kodu krótsze

Skrócenie czasu kod, który trzeba wpisać, można używać zmiennych obiektu. W poniższym przykładzie użyto pełną ścieżkę, metod i właściwości w celu uzyskania dostępu do <xref:System.Windows.Forms.Control> obiektu.

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

Możesz skrócić ten kod i przyspieszyć wykonywanie, jeśli użyjesz zmiennej obiektu dla formantu. Należy zadeklarować zmienną obiektu z określonej klasy, który chcesz przypisać do niej (`Control` w tym przypadku). Po przypisaniu obiektu do zmiennej, można traktować je dokładnie tak samo jak traktować obiektu, do którego odwołuje się. Możesz ustawić lub pobrać właściwości obiektu lub użyć dowolnej z metod. W poniższym przykładzie użyto zmiennej obiektu w celu uproszczenia kodu w poprzednim przykładzie.

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a>Zobacz także

- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Instrukcje: Przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Przypisanie zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
