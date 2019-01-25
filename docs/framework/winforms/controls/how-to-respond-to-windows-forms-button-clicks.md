---
title: 'Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], responding to Click events
- events [Windows Forms], Click events
- Click event [Windows Forms], Button control
- MouseDown event
- Button control [Windows Forms], click response
- double-clicks
- examples [Windows Forms], controls
- Click event [Windows Forms], responding to
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
ms.openlocfilehash: 98b52e914a891baec0b52dcc7b38d4f9f2198c90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539554"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows
Najbardziej podstawowa funkcja formularzy Windows <xref:System.Windows.Forms.Button> formant jest do uruchomienia kodu po kliknięciu przycisku.  
  
 Klikając <xref:System.Windows.Forms.Button> kontroli również generuje liczba innych zdarzeń, takich jak <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, i <xref:System.Windows.Forms.Control.MouseUp> zdarzenia. Jeśli zamierzasz dołączyć procedury obsługi zdarzeń dla tych zdarzeń powiązanych, pamiętaj, że ich działania nie wchodzą w konflikt. Na przykład jeśli kliknięcie przycisku powoduje wyczyszczenie informacji wpisany w polu tekstowym, przytrzymanie wskaźnika myszy nad przyciskiem powinien Wyświetla etykietki narzędzia, dzięki tym informacjom nieistniejącej teraz.  
  
 Jeśli użytkownik próbuje kliknij dwukrotnie <xref:System.Windows.Forms.Button> kontrolki, każde kliknięcie będą przetwarzane oddzielnie; oznacza to, formant nie obsługuje zdarzeń kliknij dwukrotnie plik.  
  
### <a name="to-respond-to-a-button-click"></a>Aby odpowiedzieć na kliknięcie przycisku  
  
-   W przycisku `Click` <xref:System.EventHandler> pisanie kodu do uruchomienia. `Button1_Click` musi być powiązany do kontroli. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie procedur obsługi zdarzeń w czasie wykonywania dla formularzy Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       MessageBox.Show("Button1 was clicked")  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       MessageBox.Show("button1 was clicked");  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## <a name="see-also"></a>Zobacz także
- [Button, kontrolka — omówienie](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)
- [Sposoby wyboru kontrolki przycisku Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)
- [Button, kontrolka](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
