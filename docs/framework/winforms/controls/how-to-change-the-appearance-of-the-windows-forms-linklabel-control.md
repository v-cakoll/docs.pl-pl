---
title: Zmiana wyglądu kontrolki LinkLabel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- LinkLabel properties
- LinkLabel control [Windows Forms], changing appearance of links
- links [Windows Forms], changing appearance
- examples [Windows Forms], LinkLabel control
- LinkLabel control [Windows Forms], examples
ms.assetid: fdc5854f-5162-4457-8cbe-1042feb2d132
ms.openlocfilehash: 0b38722fb1647ea215c3bb8978dd3f54b300a0e0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746622"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Porady: zmienianie wyglądu formantu LinkLabel formularzy systemu Windows
Możesz zmienić tekst wyświetlany przez formant <xref:System.Windows.Forms.LinkLabel>, aby dopasować go do różnych celów. Na przykład typowym celem jest wskazanie użytkownikowi, który tekst może być kliknięty przez ustawienie tekstu, który ma być wyświetlany w określonym kolorze z podkreśleniem. Gdy użytkownik kliknie tekst, kolor zmieni się na inny kolor. Aby kontrolować to zachowanie, można ustawić pięć różnych właściwości: właściwości <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>i <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>Aby zmienić wygląd formantu LinkLabel  
  
1. Ustaw <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> i <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> właściwości na żądane kolory.  
  
     Można to zrobić programowo lub w czasie projektowania w oknie **Właściwości** .  
  
    ```vb  
    ' You can set the color using decimal values for red, green, and blue  
    LinkLabel1.LinkColor = Color.FromArgb(0, 0, 255)  
    ' Or you can set the color using defined constants  
    LinkLabel1.VisitedLinkColor = Color.Purple  
    ```  
  
    ```csharp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1.LinkColor = Color.FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1.VisitedLinkColor = Color.Purple;  
    ```  
  
    ```cpp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1->LinkColor = Color::FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1->VisitedLinkColor = Color::Purple;  
    ```  
  
2. Ustaw właściwość <xref:System.Windows.Forms.LinkLabel.Text%2A> na odpowiedni podpis.  
  
     Można to zrobić programowo lub w czasie projektowania w oknie **Właściwości** .  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. Ustaw właściwość <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, aby określić, która część podpisu będzie wskazywana jako link.  
  
     Wartość <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> jest reprezentowana przy użyciu <xref:System.Windows.Forms.LinkArea> zawierającej dwie liczby, początkową pozycję znaku i liczbę znaków. Można to zrobić programowo lub w czasie projektowania w oknie **Właściwości** .  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. Ustaw właściwość <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> na <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>lub <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.  
  
     Jeśli jest ustawiona na <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, część podpisu określoną przez <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> zostanie podkreślona tylko wtedy, gdy wskaźnik zatrzyma się na nim.  
  
5. W obsłudze zdarzeń <xref:System.Windows.Forms.LinkLabel.LinkClicked> ustaw właściwość <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> na `true`.  
  
     Po odwiedzeniu łącza, często można zmienić jego wygląd w jakiś sposób, zazwyczaj przez kolor. Tekst zostanie zmieniony na kolor określony przez właściwość <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>.  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked (ByVal sender As Object, _  
       ByVal e As EventArgs) Handles LinkLabel1.LinkClicked  
       ' Change the color of the link text  
       ' by setting LinkVisited to True.  
       LinkLabel1.LinkVisited = True  
       ' Then do whatever other action is appropriate  
    End Sub  
    ```  
  
    ```csharp  
    protected void LinkLabel1_LinkClicked(object sender, System.EventArgs e)  
    {  
       // Change the color of the link text by setting LinkVisited   
       // to True.  
       linkLabel1.LinkVisited = true;  
       // Then do whatever other action is appropriate  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Change the color of the link text by setting LinkVisited   
          // to True.  
          linkLabel1->LinkVisited = true;  
          // Then do whatever other action is appropriate  
       }  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [LinkLabel, kontrolka — omówienie](linklabel-control-overview-windows-forms.md)
- [Instrukcje: łączenie z obiektem lub stroną internetową za pomocą kontrolki LinkLabel formularzy Windows Forms](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [LinkLabel, kontrolka](linklabel-control-windows-forms.md)
