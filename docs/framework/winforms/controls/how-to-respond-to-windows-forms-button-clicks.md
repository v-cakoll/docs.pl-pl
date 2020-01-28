---
title: Reagowanie na kliknięcia kontrolki Button
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
ms.openlocfilehash: dd6cf75a316257c86a23b44a818422336c12aa67
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735719"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>Porady: odpowiadanie na kliknięcia przycisków formularzy systemu Windows
Najbardziej podstawowym zastosowaniem formantu Windows Forms <xref:System.Windows.Forms.Button> jest uruchomienie pewnego kodu po kliknięciu przycisku.  
  
 Kliknięcie kontrolki <xref:System.Windows.Forms.Button> powoduje także wygenerowanie wielu innych zdarzeń, takich jak zdarzenia <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>i <xref:System.Windows.Forms.Control.MouseUp>. Jeśli zamierzasz dołączyć procedury obsługi zdarzeń dla tych powiązanych zdarzeń, upewnij się, że ich akcje nie powodują konfliktu. Jeśli na przykład klikniesz przycisk czyści informacje wpisane przez użytkownika w polu tekstowym, zatrzymując wskaźnik myszy nad przyciskiem nie powinien wyświetlać etykietki narzędzia z tym, że te informacje są teraz nieistniejące.  
  
 Jeśli użytkownik spróbuje dwukrotnie kliknąć kontrolkę <xref:System.Windows.Forms.Button>, każde kliknięcie zostanie przetworzone osobno; oznacza to, że formant nie obsługuje zdarzenia podwójnego kliknięcia.  
  
### <a name="to-respond-to-a-button-click"></a>Aby odpowiedzieć na przycisk kliknij  
  
- Na `Click` przycisku <xref:System.EventHandler> Napisz kod do uruchomienia. `Button1_Click` musi być powiązany z kontrolką. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie obsługi zdarzeń w czasie wykonywania dla Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
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

- [Button, kontrolka — omówienie](button-control-overview-windows-forms.md)
- [Sposoby wyboru kontrolki przycisku Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Button, kontrolka](button-control-windows-forms.md)
