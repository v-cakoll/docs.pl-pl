---
title: 'Porady: tworzenie programów do obsługi zdarzeń w czasie wykonywania dla formularzy systemu Windows'
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
ms.openlocfilehash: 38453c751e6cc63827f3f1e9d20ad2ebdfc841d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a>Porady: tworzenie programów do obsługi zdarzeń w czasie wykonywania dla formularzy systemu Windows
Oprócz tworzenia zdarzeń przy użyciu narzędzia Projektant formularzy systemu Windows, można również utworzyć program obsługi zdarzeń w czasie wykonywania. Ta akcja umożliwia łączenie z na podstawie warunków w kodzie w czasie wykonywania, a nie przejdą oni połączone po początkowym uruchomieniu programu obsługi zdarzeń.  
  
### <a name="to-create-an-event-handler-at-run-time"></a>Aby utworzyć program obsługi zdarzeń w czasie wykonywania  
  
1.  Otwórz go w edytorze kodu, który chcesz dodać do obsługi zdarzeń.  
  
2.  Dodawanie metody do formularza z podpis metody dla zdarzenia, które mają być obsługiwane.  
  
     Na przykład, jeśli zostały obsługi <xref:System.Windows.Forms.Control.Click> zdarzenie <xref:System.Windows.Forms.Button> formantu, należy utworzyć metody, takie jak następujące:  
  
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
  
3.  Dodaj kod, aby program obsługi zdarzeń, zależnie od potrzeb aplikacji.  
  
4.  Określ, które formularza lub kontrolki, w którym chcesz utworzyć program obsługi zdarzeń dla.  
  
5.  W przypadku metody w klasie formularza Dodaj kod, który określa program obsługi zdarzeń do obsługi zdarzenia. Na przykład następujący kod określa program obsługi zdarzeń `button1_Click` dojść <xref:System.Windows.Forms.Control.Click> zdarzenie <xref:System.Windows.Forms.Button> sterowania:  
  
    ```vb  
    AddHandler Button1.Click, AddressOf Button1_Click  
    ```  
  
    ```csharp  
    button1.Click += new EventHandler(button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> Metody zostało to pokazane w powyższym kodzie Visual Basic ustanawia obsługi zdarzenia kliknięcia dla przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Przegląd procedur obsługi zdarzeń](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 [Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
