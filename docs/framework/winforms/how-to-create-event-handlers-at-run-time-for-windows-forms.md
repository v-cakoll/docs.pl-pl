---
title: 'Instrukcje: Tworzenie procedur obsługi zdarzeń w czasie wykonywania dla formularzy Windows Forms'
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
ms.openlocfilehash: 7ebafd745290a40fa6f4f83910fb32d67cdcff75
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705271"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a>Instrukcje: Tworzenie procedur obsługi zdarzeń w czasie wykonywania dla formularzy Windows Forms
Oprócz tworzenia zdarzeń za pomocą programu Windows Forms Designer, możesz również utworzyć program obsługi zdarzeń w czasie wykonywania. Ta akcja umożliwia łączenie programów obsługi zdarzeń na podstawie warunków w kodzie w czasie wykonywania, a nie po ich połączone po początkowym uruchomieniu programu.  
  
### <a name="to-create-an-event-handler-at-run-time"></a>Aby utworzyć program obsługi zdarzeń w czasie wykonywania  
  
1.  Otwórz formularz w edytorze kodu, którą chcesz dodać program obsługi zdarzeń do.  
  
2.  Dodaj metodę do formularza przy użyciu podpisu metody dla zdarzenia, które mają być obsługiwane.  
  
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
  
3.  Dodaj kod do narzędzia obsługi zdarzeń, odpowiednio do swojej aplikacji.  
  
4.  Ustal, które formularza lub kontrolki, w której chcesz utworzyć program obsługi zdarzeń dla.  
  
5.  W przypadku metody w klasie formularza Dodaj kod, który określa program obsługi zdarzeń, aby obsłużyć zdarzenie. Na przykład, poniższy kod określa program obsługi zdarzeń `button1_Click` uchwyty <xref:System.Windows.Forms.Control.Click> zdarzenia <xref:System.Windows.Forms.Button> sterowania:  
  
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
