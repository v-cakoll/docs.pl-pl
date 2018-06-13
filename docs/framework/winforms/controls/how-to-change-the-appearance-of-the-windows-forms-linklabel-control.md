---
title: 'Porady: zmienianie wyglądu formantu LinkLabel formularzy systemu Windows'
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
ms.openlocfilehash: e1bb0ecba6fd8ddf66c6debb90ef4dd94641a97e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531489"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Porady: zmienianie wyglądu formantu LinkLabel formularzy systemu Windows
Można zmienić tekst wyświetlany przez <xref:System.Windows.Forms.LinkLabel> kontroli dostosowanych do różnych celów. Na przykład jest typowym rozwiązaniem, aby poinformować użytkownika, można kliknąć przez ustawienie tekst wyświetlany w kolorze określonych podkreślony tekst. Po kliknięciu tekst zmienia kolor na inny kolor. Aby kontrolować to zachowanie, można ustawić pięciu różnych właściwości: <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, i <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> właściwości.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>Zmiana wyglądu formantu LinkLabel  
  
1.  Ustaw <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> i <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> właściwości do kolorów ma.  
  
     Można to zrobić albo programowo lub w czasie projektowania w **właściwości** okna.  
  
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
  
2.  Ustaw <xref:System.Windows.Forms.LinkLabel.Text%2A> właściwości odpowiedni podpis.  
  
     Można to zrobić albo programowo lub w czasie projektowania w **właściwości** okna.  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3.  Ustaw <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> właściwości w celu określenia, która część podpis zostanie wskazany jako łącze.  
  
     <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Wartość odpowiada z <xref:System.Windows.Forms.LinkArea> zawierającego dwóch liczb, pozycję początkową znaku i liczbę znaków. Można to zrobić albo programowo lub w czasie projektowania w **właściwości** okna.  
  
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
  
     Jeśli wartość jest ustawiona na <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, część podpisu ustaleniami <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> tylko zostanie podkreślone, gdy wskaźnik znajduje się na nim.  
  
5.  W <xref:System.Windows.Forms.LinkLabel.LinkClicked> ustawiony program obsługi zdarzeń, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> właściwości `true`.  
  
     Po odwiedzeniu łącza, jest powszechną praktyką było zmienić jego wyglądu w jakiś sposób zazwyczaj kolorów. Tekst zmieni kolor określone przez <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> właściwości.  
  
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
 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>  
 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>  
 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>  
 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>  
 [LinkLabel, kontrolka — omówienie](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)  
 [Instrukcje: łączenie z obiektem lub stroną internetową za pomocą kontrolki LinkLabel formularzy Windows Forms](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [LinkLabel, kontrolka](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
