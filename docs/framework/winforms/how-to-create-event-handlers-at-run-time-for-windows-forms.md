---
title: 'Instrukcje: tworzenie programów obsługi zdarzeń w czasie wykonywania'
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
ms.openlocfilehash: 0b496a3da77c5bcf7a08c435edba468a7c5809cb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739495"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a>Porady: tworzenie programów do obsługi zdarzeń w czasie wykonywania dla formularzy systemu Windows

Oprócz tworzenia zdarzeń przy użyciu Projektant formularzy systemu Windows w programie Visual Studio, można również utworzyć procedurę obsługi zdarzeń w czasie wykonywania. Ta akcja umożliwia nawiązanie połączenia programów obsługi zdarzeń na podstawie warunków w kodzie w czasie wykonywania, które nie są połączone podczas początkowego uruchamiania programu.

## <a name="create-an-event-handler-at-run-time"></a>Utwórz procedurę obsługi zdarzeń w czasie wykonywania

1. Otwórz formularz, do którego chcesz dodać procedurę obsługi zdarzeń.

2. Dodaj metodę do formularza z podpisem metody dla zdarzenia, które chcesz obsłużyć.

     Na przykład jeśli obsłużysz zdarzenie <xref:System.Windows.Forms.Control.Click> formantu <xref:System.Windows.Forms.Button>, utworzysz metodę taką jak:

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

3. Dodaj kod do programu obsługi zdarzeń odpowiednio do aplikacji.

4. Określ formularz lub kontrolkę, dla której chcesz utworzyć procedurę obsługi zdarzeń.

5. W metodzie w klasie formularza Dodaj kod, który określa procedurę obsługi zdarzeń, aby obsłużyć zdarzenie. Na przykład poniższy kod określa procedurę obsługi zdarzeń `button1_Click` obsługuje zdarzenie <xref:System.Windows.Forms.Control.Click> kontrolki <xref:System.Windows.Forms.Button>:

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     Metoda <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> przedstawiona w powyższym kodzie Visual Basic określa procedurę obsługi zdarzeń kliknięcia dla przycisku.

## <a name="see-also"></a>Zobacz także

- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Przegląd procedur obsługi zdarzeń](event-handlers-overview-windows-forms.md)
- [Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
