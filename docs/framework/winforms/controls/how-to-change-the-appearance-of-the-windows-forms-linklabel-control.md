---
title: Zmienianie wyglądu kontrolki LinkLabel
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
ms.openlocfilehash: df66991289373a05fc7c27b7768a96643e3bbae0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142133"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Porady: zmienianie wyglądu formantu LinkLabel formularzy systemu Windows
Można zmienić tekst wyświetlany <xref:System.Windows.Forms.LinkLabel> przez formant, aby dopasować go do różnych celów. Na przykład powszechną praktyką jest wskazanie użytkownikowi, że tekst można kliknąć, ustawiając tekst wyświetlany w określonym kolorze z podkreśleniem. Po kliknięciu tekstu kolor zmieni się na inny kolor. Aby kontrolować to zachowanie, można ustawić pięć <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>różnych <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>właściwości: <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> , , , i właściwości.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>Aby zmienić wygląd formantu LinkLabel  
  
1. Ustaw <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> i <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> właściwości na żądane kolory.  
  
     Można to zrobić programowo lub w czasie projektowania w oknie **Właściwości.**  
  
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
  
2. Ustaw <xref:System.Windows.Forms.LinkLabel.Text%2A> właściwość na odpowiedni podpis.  
  
     Można to zrobić programowo lub w czasie projektowania w oknie **Właściwości.**  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. Ustaw <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> właściwość, aby określić, która część podpisu będzie oznaczona jako łącze.  
  
     Wartość <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> jest reprezentowana <xref:System.Windows.Forms.LinkArea> z zawierającą dwie liczby, pozycję znaku początkowego i liczbę znaków. Można to zrobić programowo lub w czasie projektowania w oknie **Właściwości.**  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. Ustaw <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> właściwość <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline> <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>na <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>, lub .  
  
     Jeśli jest ustawiona na <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, część <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> podpisu określona przez zostanie podkreślona tylko wtedy, gdy wskaźnik spoczywa na nim.  
  
5. W <xref:System.Windows.Forms.LinkLabel.LinkClicked> programie obsługi zdarzeń <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> ustaw `true`właściwość na .  
  
     Gdy link został odwiedzony, powszechną praktyką jest zmiana jego wyglądu w jakiś sposób, zwykle według koloru. Tekst zmieni się na kolor <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> określony przez właściwość.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [LinkLabel, kontrolka — omówienie](linklabel-control-overview-windows-forms.md)
- [Instrukcje: łączenie z obiektem lub stroną internetową za pomocą kontrolki LinkLabel formularzy Windows Forms](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [LinkLabel, kontrolka](linklabel-control-windows-forms.md)
