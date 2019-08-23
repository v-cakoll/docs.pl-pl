---
title: 'Instrukcje: łączenie z obiektem lub stroną sieci Web za pomocą kontrolki LinkLabel formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Windows Forms, linking to objects
- Web page link control
- linking [Windows Forms], to other forms
- Windows Forms, linking to Web pages
- links [Windows Forms], to other forms
- LinkLabel control [Windows Forms], linking to object or Web page
- LinkLabel control [Windows Forms], examples
ms.assetid: 6c91c975-3cb7-4504-82f0-fc6255f8fb85
ms.openlocfilehash: 1ed27826b92d34f05055ab7fdda2a16eb4a79b17
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952174"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>Instrukcje: łączenie z obiektem lub stroną sieci Web za pomocą kontrolki LinkLabel formularzy systemu Windows
Formant Windows Forms <xref:System.Windows.Forms.LinkLabel> umożliwia tworzenie łączy w stylu sieci Web w formularzu. Po kliknięciu linku można zmienić jego kolor, aby wskazać, że łącze zostało odwiedzone. Aby uzyskać więcej informacji na temat zmiany koloru, [zobacz How to: Zmień wygląd formantu](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)LinkLabel Windows Forms.  
  
## <a name="linking-to-another-form"></a>Łączenie z innym formularzem  
  
#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>Aby połączyć się z innym formularzem za pomocą kontrolki LinkLabel  
  
1. <xref:System.Windows.Forms.LinkLabel.Text%2A> Ustaw właściwość na odpowiedni podpis.  
  
2. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Ustaw właściwość, aby określić, która część podpisu będzie wskazywana jako link. Sposób wskazywania zależy od właściwości etykiety linku dotyczącej wyglądu. Wartość jest reprezentowana <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> przez obiekt zawierający dwie liczby, początkową pozycję znaku i liczbę znaków. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Właściwość można ustawić w okno właściwości lub w kodzie w sposób podobny do poniższego:  
  
    ```vb  
    ' In this code example, the link area has been set to begin  
    ' at the first character and extend for eight characters.  
    ' You may need to modify this based on the text entered in Step 1.  
    LinkLabel1.LinkArea = New LinkArea(0, 8)  
    ```  
  
    ```csharp  
    // In this code example, the link area has been set to begin  
    // at the first character and extend for eight characters.  
    // You may need to modify this based on the text entered in Step 1.  
    linkLabel1.LinkArea = new LinkArea(0,8);  
    ```  
  
    ```cpp  
    // In this code example, the link area has been set to begin  
    // at the first character and extend for eight characters.  
    // You may need to modify this based on the text entered in Step 1.  
    linkLabel1->LinkArea = LinkArea(0,8);  
    ```  
  
3. W programie obsługi <xref:System.Windows.Forms.Form.Show%2A> <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> `true`zdarzeń Wywołaj metodę, aby otworzyć inny formularz w projekcie, i ustaw właściwość na. <xref:System.Windows.Forms.LinkLabel.LinkClicked>  
  
    > [!NOTE]
    > Wystąpienie <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> klasy przenosi odwołanie <xref:System.Windows.Forms.LinkLabel> do formantu, który został kliknięty, więc `sender` nie trzeba rzutować obiektu.  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked(ByVal Sender As System.Object, _  
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _  
       Handles LinkLabel1.LinkClicked  
       ' Show another form.  
       Dim f2 As New Form()  
       f2.Show  
       LinkLabel1.LinkVisited = True  
    End Sub  
    ```  
  
    ```csharp  
    protected void linkLabel1_LinkClicked(object sender, System. Windows.Forms.LinkLabelLinkClickedEventArgs e)  
    {  
       // Show another form.  
       Form f2 = new Form();  
       f2.Show();  
       linkLabel1.LinkVisited = true;  
    }  
    ```  
  
    ```cpp  
    private:  
       void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Show another form.  
          Form ^ f2 = new Form();  
          f2->Show();  
          linkLabel1->LinkVisited = true;  
       }  
    ```  
  
## <a name="linking-to-a-web-page"></a>Łączenie ze stroną sieci Web  
 <xref:System.Windows.Forms.LinkLabel> Kontrolka może również służyć do wyświetlania strony sieci Web z domyślną przeglądarką.  
  
#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>Aby uruchomić program Internet Explorer i połączyć się ze stroną sieci Web za pomocą kontrolki LinkLabel  
  
1. <xref:System.Windows.Forms.LinkLabel.Text%2A> Ustaw właściwość na odpowiedni podpis.  
  
2. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Ustaw właściwość, aby określić, która część podpisu będzie wskazywana jako link.  
  
3. W obsłudze <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> `true` <xref:System.Diagnostics.Process.Start%2A> zdarzeń, w pośrodku bloku obsługi wyjątków, wywołaj drugą procedurę, która ustawia właściwość na i używa metody do uruchamiania domyślnej przeglądarki z adresem URL. <xref:System.Windows.Forms.LinkLabel.LinkClicked> Aby użyć <xref:System.Diagnostics.Process.Start%2A> metody, musisz dodać odwołanie <xref:System.Diagnostics?displayProperty=nameWithType> do przestrzeni nazw.  
  
    > [!IMPORTANT]
    >  Jeśli Poniższy kod jest uruchamiany w środowisku częściowego zaufania (na przykład na dysku udostępnionym), kompilator JIT kończy się niepowodzeniem, gdy `VisitLink` wywoływana jest metoda. `System.Diagnostics.Process.Start` Instrukcja powoduje, że żądanie linku kończy się niepowodzeniem. Zwracając wyjątek, gdy `VisitLink` wywoływana jest metoda, poniższy kod gwarantuje, że jeśli kompilator JIT nie powiedzie się, błąd jest poprawnie obsługiwany.  
  
    ```vb  
    Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, _  
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _  
       Handles LinkLabel1.LinkClicked  
       Try  
          VisitLink()  
       Catch ex As Exception  
          ' The error message  
          MessageBox.Show("Unable to open link that was clicked.")  
       End Try  
    End Sub  
  
    Sub VisitLink()  
       ' Change the color of the link text by setting LinkVisited   
       ' to True.  
       LinkLabel1.LinkVisited = True  
       ' Call the Process.Start method to open the default browser   
       ' with a URL:  
       System.Diagnostics.Process.Start("http://www.microsoft.com")  
    End Sub  
    ```  
  
    ```csharp  
    private void linkLabel1_LinkClicked(object sender, System.Windows.Forms.LinkLabelLinkClickedEventArgs e)  
    {  
       try  
       {  
          VisitLink();  
       }  
       catch (Exception ex )  
       {  
          MessageBox.Show("Unable to open link that was clicked.");  
       }  
    }  
  
    private void VisitLink()  
    {  
       // Change the color of the link text by setting LinkVisited   
       // to true.  
       linkLabel1.LinkVisited = true;  
       //Call the Process.Start method to open the default browser   
       //with a URL:  
       System.Diagnostics.Process.Start("http://www.microsoft.com");  
    }  
    ```  
  
    ```cpp  
    private:  
       void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          try  
          {  
             VisitLink();  
          }  
          catch (Exception ^ ex)  
          {  
             MessageBox::Show("Unable to open link that was clicked.");  
          }  
       }  
    private:  
       void VisitLink()  
       {  
          // Change the color of the link text by setting LinkVisited   
          // to true.  
          linkLabel1->LinkVisited = true;  
          // Call the Process.Start method to open the default browser   
          // with a URL:  
          System::Diagnostics::Process::Start("http://www.microsoft.com");  
       }  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- [LinkLabel, kontrolka — omówienie](linklabel-control-overview-windows-forms.md)
- [Instrukcje: Zmiana wyglądu kontrolki LinkLabel Windows Forms](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [LinkLabel, kontrolka](linklabel-control-windows-forms.md)
