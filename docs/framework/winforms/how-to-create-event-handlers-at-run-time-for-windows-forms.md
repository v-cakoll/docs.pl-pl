---
title: 'Instrukcje: tworzenie programów obsługi zdarzeń w czasie wykonywania'
description: Dowiedz się, jak utworzyć procedurę obsługi zdarzeń w czasie wykonywania przy użyciu Projektant formularzy systemu Windows w programie Visual Studio. Ta akcja umożliwia nawiązanie połączenia programów obsługi zdarzeń w czasie wykonywania.
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
ms.openlocfilehash: 857076c46377b3276154d9b193d4bbe51841828f
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325807"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a>Instrukcje: Tworzenie programów obsługi zdarzeń w czasie wykonywania dla formularzy Windows Forms

Oprócz tworzenia zdarzeń przy użyciu Projektant formularzy systemu Windows w programie Visual Studio, można również utworzyć procedurę obsługi zdarzeń w czasie wykonywania. Ta akcja umożliwia nawiązanie połączenia programów obsługi zdarzeń na podstawie warunków w kodzie w czasie wykonywania, które nie są połączone podczas początkowego uruchamiania programu.

## <a name="create-an-event-handler-at-run-time"></a>Utwórz procedurę obsługi zdarzeń w czasie wykonywania

1. Otwórz formularz, do którego chcesz dodać procedurę obsługi zdarzeń.

2. Dodaj metodę do formularza z podpisem metody dla zdarzenia, które chcesz obsłużyć.

     Na przykład w przypadku obsługi <xref:System.Windows.Forms.Control.Click> zdarzenia <xref:System.Windows.Forms.Button> kontrolki należy utworzyć metodę taką jak następujące:

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

5. W metodzie w klasie formularza Dodaj kod, który określa procedurę obsługi zdarzeń, aby obsłużyć zdarzenie. Na przykład poniższy kod określa, że program obsługi zdarzeń `button1_Click` obsługuje <xref:System.Windows.Forms.Control.Click> zdarzenie <xref:System.Windows.Forms.Button> formantu:

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     <xref:System.ComponentModel.EventHandlerList.AddHandler%2A>Metoda pokazana w kodzie Visual Basic powyżej określa procedurę obsługi zdarzeń kliknięcia dla przycisku.

## <a name="see-also"></a>Zobacz też

- [Tworzenie programów obsługi zdarzeń w formularzach systemu Windows](creating-event-handlers-in-windows-forms.md)
- [Przegląd programów obsługi zdarzeń](event-handlers-overview-windows-forms.md)
- [Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
