---
title: Zmienne obiektów
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: a5e61f9308d3484dc228a7d09cc2fd30a2f41b35
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410338"
---
# <a name="object-variables-in-visual-basic"></a>Zmienne obiektów w Visual Basic

Oprócz bezpośredniego zapisywania wartości zmienna może odwoływać się do obiektu. Przypisujesz obiekt do zmiennej z tych samych powodów, do których przypisano dowolną wartość do zmiennej:

- Nazwa zmiennej jest często krótsza i łatwiejsza do zapamiętania niż pełna ścieżka metod i właściwości, które są niezbędne do uzyskania dostępu do samego obiektu.

- Użycie zmiennej odwołującej się do obiektu jest bardziej wydajne niż wielokrotne uzyskiwanie dostępu do samego obiektu za pomocą niezbędnych metod lub właściwości.

- Można zmienić zmienną, aby odwoływać się do innych obiektów, gdy kod jest uruchomiony.

## <a name="making-code-shorter"></a>Szybsze wprowadzanie kodu

Możesz użyć zmiennych obiektów, aby skrócić kod, który musisz wpisać. W poniższym przykładzie zastosowano pełną ścieżkę metod i właściwości, aby uzyskać dostęp do <xref:System.Windows.Forms.Control> obiektu.

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

Możesz skrócić ten kod i przyspieszyć wykonywanie, jeśli używasz zmiennej obiektu dla formantu. Należy zadeklarować zmienną obiektu z określoną klasą, która ma zostać przypisana do niej ( `Control` w tym przypadku). Po przypisaniu obiektu do zmiennej można go traktować dokładnie tak samo, jak w przypadku obiektu, do którego się odwołuje. Możesz ustawić lub pobrać właściwości obiektu lub użyć dowolnej z jej metod. Poniższy przykład używa zmiennej obiektu do uproszczenia kodu w poprzednim przykładzie.

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a>Zobacz też

- [Deklaracja zmiennej](variable-declaration.md)
- [Instrukcje: przyspieszanie dostępu do obiektu z długą ścieżką kwalifikacji](how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [Deklaracja zmiennej obiektu](object-variable-declaration.md)
- [Przypisanie zmiennej obiektu](object-variable-assignment.md)
- [Wartości zmiennej obiektu](object-variable-values.md)
