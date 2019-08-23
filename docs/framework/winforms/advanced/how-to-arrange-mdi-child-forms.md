---
title: 'Instrukcje: Rozmieszczanie formularzy podrzędnych MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
ms.openlocfilehash: 7e4d5a80961ae37951251dffa30cb8e75b20be27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955114"
---
# <a name="how-to-arrange-mdi-child-forms"></a>Instrukcje: Rozmieszczanie formularzy podrzędnych MDI
Często aplikacje będą mieć polecenia menu dla akcji, takich jak kafelki, Kaskada i rozmieszczenia, które kontrolują układ otwartych formularzy podrzędnych MDI. Możesz użyć <xref:System.Windows.Forms.Form.LayoutMdi%2A> metody z jedną <xref:System.Windows.Forms.MdiLayout> z wartości wyliczenia, aby zmienić rozmieszczenie formularzy podrzędnych w formularzu nadrzędnym MDI.  
  
 Wartości <xref:System.Windows.Forms.MdiLayout> wyliczenia wyświetlają formularze podrzędne jako kaskadowe, tak jak w poziomie lub w pionie, lub jako ikony formularza podrzędnego ułożone wzdłuż dolnej części formularza MDI. Te wartości mają ten sam efekt, co okna poleceń **kaskadowych systemu**Windows, **Pokaż okna obok siebie**, **pokazuje stosy systemu Windows**, a **także wyświetla pulpit**.  
  
 Często te metody są używane jako programy obsługi zdarzeń wywoływane przez <xref:System.Windows.Forms.Control.Click> zdarzenie elementu menu. W ten sposób element menu z tekstem "Kaskada Windows" może mieć żądany efekt w oknach podrzędnych MDI.  
  
### <a name="to-arrange-child-forms"></a>Aby rozmieścić formularze podrzędne  
  
1. W metodzie Użyj <xref:System.Windows.Forms.Form.LayoutMdi%2A> metody, aby <xref:System.Windows.Forms.MdiLayout> ustawić Wyliczenie dla formularza nadrzędnego MDI. W poniższym przykładzie użyta <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> zostanie wartość wyliczenia dla okien podrzędnych nadrzędnego formularza MDI (`Form1`). Wyliczenie jest używane w kodzie podczas obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia elementu menu kaskadowego **systemu Windows** .  
  
    ```vb  
    Protected Sub CascadeWindows_Click(ByVal sender As System.Object, ByVal e As System.EventArgs)  
       Me.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade)  
    End Sub  
    ```  
  
    ```csharp  
    protected void CascadeWindows_Click(object sender, System.EventArgs e){  
       this.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade);  
    }  
    ```  
  
    > [!NOTE]
    > Możesz również kafelki okna i rozmieszczać okna jako ikony, zmieniając <xref:System.Windows.Forms.MdiLayout> użytą wartość wyliczenia.  
  
2. Jeśli używasz wizualizacji C#, Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Aplikacje interfejsu wielu dokumentów (MDI)](multiple-document-interface-mdi-applications.md)
- [Instrukcje: Tworzenie formularzy nadrzędnych MDI](how-to-create-mdi-parent-forms.md)
- [Instrukcje: Tworzenie formularzy podrzędnych MDI](how-to-create-mdi-child-forms.md)
- [Instrukcje: Określanie aktywnego elementu podrzędnego MDI](how-to-determine-the-active-mdi-child.md)
- [Instrukcje: Wyślij dane do aktywnego elementu podrzędnego MDI](how-to-send-data-to-the-active-mdi-child.md)
