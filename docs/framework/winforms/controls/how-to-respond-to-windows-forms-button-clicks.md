---
title: Reagowanie na kliknięcia kontrolki Button
description: Dowiedz się, jak reagować na kliknięcia przycisku Windows Forms. Najbardziej podstawowym zastosowaniem kontrolki przycisku Windows Forms jest uruchomienie pewnego kodu po kliknięciu przycisku.
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
ms.openlocfilehash: 5c458d56dbd6f1cab8e88bdbb86ede958367e5c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619731"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>Porady: odpowiadanie na kliknięcia przycisków formularzy systemu Windows
Najbardziej podstawowym <xref:System.Windows.Forms.Button> sposobem użycia formantu Windows Forms jest uruchomienie pewnego kodu po kliknięciu przycisku.  
  
 Kliknięcie <xref:System.Windows.Forms.Button> kontrolki powoduje także wygenerowanie wielu innych zdarzeń, takich jak <xref:System.Windows.Forms.Control.MouseEnter> zdarzenia, <xref:System.Windows.Forms.Control.MouseDown> i <xref:System.Windows.Forms.Control.MouseUp> . Jeśli zamierzasz dołączyć procedury obsługi zdarzeń dla tych powiązanych zdarzeń, upewnij się, że ich akcje nie powodują konfliktu. Jeśli na przykład klikniesz przycisk czyści informacje wpisane przez użytkownika w polu tekstowym, zatrzymując wskaźnik myszy nad przyciskiem nie powinien wyświetlać etykietki narzędzia z tym, że te informacje są teraz nieistniejące.  
  
 Jeśli użytkownik spróbuje dwukrotnie kliknąć <xref:System.Windows.Forms.Button> kontrolkę, każde kliknięcie zostanie przetworzone oddzielnie. oznacza to, że formant nie obsługuje zdarzenia podwójnego kliknięcia.  
  
### <a name="to-respond-to-a-button-click"></a>Aby odpowiedzieć na przycisk kliknij  
  
- Na przycisku `Click` <xref:System.EventHandler> Napisz kod do uruchomienia. `Button1_Click`musi być powiązany z kontrolką. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie obsługi zdarzeń w czasie wykonywania dla Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
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

- [Button — Informacje o formancie](button-control-overview-windows-forms.md)
- [Sposoby wyboru kontrolki przycisku Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Button, kontrolka](button-control-windows-forms.md)
