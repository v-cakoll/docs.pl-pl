---
title: 'Instrukcje: Tworzenie programów obsługi zdarzeń w czasie wykonywania dla formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handlers [Windows Forms], creating
- run time [Windows Forms], creating event handlers at
- examples [Windows Forms], event handling
- Button control [Windows Forms], event handlers
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
ms.openlocfilehash: 4d2290622e648030f150d9bb06ce1f3000145759
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211472"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a>Instrukcje: Tworzenie programów obsługi zdarzeń w czasie wykonywania dla formularzy Windows Forms

Oprócz tworzenia zdarzeń za pomocą programu Windows Forms Designer w programie Visual Studio, możesz również utworzyć program obsługi zdarzeń w czasie wykonywania. Ta akcja umożliwia łączenie programów obsługi zdarzeń na podstawie warunków w kodzie w czasie wykonywania, a nie po ich połączone po początkowym uruchomieniu programu.

## <a name="create-an-event-handler-at-run-time"></a>Utwórz procedurę obsługi zdarzeń w czasie wykonywania

1. Otwórz formularz, który chcesz dodać program obsługi zdarzeń do.

2. Dodaj metodę do formularza przy użyciu podpisu metody dla zdarzenia, które mają być obsługiwane.

     Na przykład, jeśli zostały obsługi <xref:System.Windows.Forms.Control.Click> zdarzenia <xref:System.Windows.Forms.Button> kontrolki, należy utworzyć metodę podobny do następującego:

    ```vb
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)
       ' Add event handler code here.
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
    // Add event handler code here.
    }
    ```

    ```cpp
    private:
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          // Add event handler code here.
       }
    ```

3. Dodaj kod do narzędzia obsługi zdarzeń, odpowiednio do swojej aplikacji.

4. Ustal, które formularza lub kontrolki, w której chcesz utworzyć program obsługi zdarzeń dla.

5. W przypadku metody w klasie formularza Dodaj kod, który określa program obsługi zdarzeń, aby obsłużyć zdarzenie. Na przykład, poniższy kod określa program obsługi zdarzeń `button1_Click` uchwyty <xref:System.Windows.Forms.Control.Click> zdarzenia <xref:System.Windows.Forms.Button> sterowania:

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> Metoda pokazano w powyższym kodzie języka Visual Basic ustanawia obsługi zdarzeń kliknięcia dla przycisku.

## <a name="see-also"></a>Zobacz także

- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Przegląd procedur obsługi zdarzeń](event-handlers-overview-windows-forms.md)
- [Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
