---
title: 'Instrukcje: Zmienianie wyglądu kontrolki LinkLabel formularzy Windows Forms'
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
ms.openlocfilehash: 2e36bdc051ec83985bd508499640c9f97bdefc91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632130"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Instrukcje: Zmienianie wyglądu kontrolki LinkLabel formularzy Windows Forms
Możesz zmienić tekst wyświetlany przez <xref:System.Windows.Forms.LinkLabel> kontroli dostosowanych do różnych celów. Na przykład jest powszechną praktyką, aby poinformować użytkownika, czy tekst można kliknąć, ustawiając tekst wyświetlany w kolorze określonej za pomocą podkreślenia. Po kliknięciu tego tekstu zmienia kolor na inny kolor. Aby kontrolować to zachowanie, należy ustawić pięć różnych właściwości: <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, i <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> właściwości.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>Aby zmienić wygląd formantu LinkLabel  
  
1.  Ustaw <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> i <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> właściwości kolory mają.  
  
     Można to zrobić albo programowo, albo w czasie projektowania w **właściwości** okna.  
  
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
  
2.  Ustaw <xref:System.Windows.Forms.LinkLabel.Text%2A> właściwość odpowiedni podpis.  
  
     Można to zrobić albo programowo, albo w czasie projektowania w **właściwości** okna.  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3.  Ustaw <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> właściwości w celu określenia, która część podpisu zostanie wskazany jako link.  
  
     <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Wartość jest reprezentowane przez <xref:System.Windows.Forms.LinkArea> zawierający dwie liczby, począwszy od pozycji znaku i liczbę znaków. Można to zrobić albo programowo, albo w czasie projektowania w **właściwości** okna.  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4.  Ustaw <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> właściwości <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, lub <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.  
  
     Jeśli jest równa <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, część podpisu ustalany na podstawie <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> zostanie podkreślone tylko po zatrzymaniu na nim wskaźnika.  
  
5.  W <xref:System.Windows.Forms.LinkLabel.LinkClicked> ustawić programu obsługi zdarzeń <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> właściwość `true`.  
  
     Po odwiedzeniu łącza jest powszechną praktyką było jej zmiany w jakiś sposób, zwykle według kolorów. Tekst zmieni się na kolor określony przy użyciu <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> właściwości.  
  
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
- [LinkLabel, kontrolka — omówienie](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)
- [Instrukcje: Łączenie do obiektu lub strony za pomocą formantu LinkLabel formularzy Windows w sieci Web](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [LinkLabel, kontrolka](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
