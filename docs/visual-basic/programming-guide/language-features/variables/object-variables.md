---
title: Zmienne obiektów
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 7eb860bc732f923316b8ce1d7b94ecdb368bfec3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351785"
---
# <a name="object-variables-in-visual-basic"></a>Zmienne obiektów w Visual Basic

Oprócz bezpośredniego zapisywania wartości zmienna może odwoływać się do obiektu. Przypisujesz obiekt do zmiennej z tych samych powodów, do których przypisano dowolną wartość do zmiennej:

- Nazwa zmiennej jest często krótsza i łatwiejsza do zapamiętania niż pełna ścieżka metod i właściwości, które są niezbędne do uzyskania dostępu do samego obiektu.

- Użycie zmiennej odwołującej się do obiektu jest bardziej wydajne niż wielokrotne uzyskiwanie dostępu do samego obiektu za pomocą niezbędnych metod lub właściwości.

- Można zmienić zmienną, aby odwoływać się do innych obiektów, gdy kod jest uruchomiony.

## <a name="making-code-shorter"></a>Szybsze wprowadzanie kodu

Możesz użyć zmiennych obiektów, aby skrócić kod, który musisz wpisać. W poniższym przykładzie zastosowano pełną ścieżkę metod i właściwości, aby uzyskać dostęp do obiektu <xref:System.Windows.Forms.Control>.

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

Możesz skrócić ten kod i przyspieszyć wykonywanie, jeśli używasz zmiennej obiektu dla formantu. Należy zadeklarować zmienną obiektu z określoną klasą, która ma zostać przypisana do niej (`Control` w tym przypadku). Po przypisaniu obiektu do zmiennej można go traktować dokładnie tak samo, jak w przypadku obiektu, do którego się odwołuje. Możesz ustawić lub pobrać właściwości obiektu lub użyć dowolnej z jej metod. Poniższy przykład używa zmiennej obiektu do uproszczenia kodu w poprzednim przykładzie.

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a>Zobacz także

- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Instrukcje: przyspieszanie dostępu do obiektu z długą ścieżką kwalifikacji](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Przypisanie zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
