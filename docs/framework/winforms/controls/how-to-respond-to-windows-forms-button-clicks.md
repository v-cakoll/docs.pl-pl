---
title: 'Porady: odpowiadanie na kliknięcia przycisków formularzy systemu Windows'
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
ms.openlocfilehash: 14a880c34f163dc6fece44c24d377822a741b0f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>Porady: odpowiadanie na kliknięcia przycisków formularzy systemu Windows
Najbardziej podstawowa funkcja formularzy systemu Windows <xref:System.Windows.Forms.Button> formant jest do uruchomienia kodu po kliknięciu przycisku.  
  
 Kliknięcie przycisku <xref:System.Windows.Forms.Button> kontroli generowany jest również liczba innych zdarzeń, takich jak <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, i <xref:System.Windows.Forms.Control.MouseUp> zdarzenia. Jeśli zamierzasz dołączyć obsługi zdarzeń dla tych zdarzeń powiązanych, należy się upewnić, że ich działania nie pozostają w konflikcie. Na przykład jeśli kliknięcie przycisku czyści informacje, które użytkownik ma wpisane w polu tekstowym, wstrzymanie wskaźnik myszy nad przyciskiem powinien nie zawiera podpowiedzi z nieistniejącą teraz informacje.  
  
 Jeśli użytkownik próbuje kliknij dwukrotnie <xref:System.Windows.Forms.Button> formantu, kliknij każdy będą przetwarzane oddzielnie; oznacza to, formantu nie obsługuje kliknij dwukrotnie zdarzenie.  
  
### <a name="to-respond-to-a-button-click"></a>Aby odpowiedzieć kliknij przycisk  
  
-   Przycisk `Click` <xref:System.EventHandler> pisania kodu do uruchomienia. `Button1_Click` muszą być powiązane z formantem. Aby uzyskać więcej informacji, zobacz [porady: tworzenie obsługi zdarzeń w Uruchom czasu dla formularzy systemu Windows](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Button, kontrolka — omówienie](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Sposoby wyboru kontrolki przycisku Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Button, kontrolka](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
