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
ms.openlocfilehash: edebfaee6f0da6826f4b757568408662f3208d41
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012868"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>Instrukcje: łączenie z obiektem lub stroną sieci Web za pomocą kontrolki LinkLabel formularzy systemu Windows
Formularze Windows <xref:System.Windows.Forms.LinkLabel> formantu służy do tworzenia łączy stylu sieci Web w formularzu. Po kliknięciu łącza, można zmienić jego kolor, aby wskazać, że link został odwiedzony. Aby uzyskać więcej informacji o zmienianiu kolorów, zobacz [jak: Zmienianie wyglądu formantu LinkLabel formularzy Windows](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).  
  
## <a name="linking-to-another-form"></a>Łączenie z innej formy  
  
#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>Aby połączyć innego formularza za pomocą kontrolki LinkLabel  
  
1. Ustaw <xref:System.Windows.Forms.LinkLabel.Text%2A> właściwość odpowiedni podpis.  
  
2. Ustaw <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> właściwości w celu określenia, która część podpisu zostanie wskazany jako link. Jak jest oznaczany zależy od właściwości powiązane z wyglądem etykieta linku. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Wartość jest reprezentowana przez <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> obiekt zawierający dwie liczby, począwszy od pozycji znaku i liczbę znaków. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Właściwość można ustawić w oknie dialogowym właściwości lub w kodzie w sposób podobny do następującego:  
  
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
  
3. W <xref:System.Windows.Forms.LinkLabel.LinkClicked> procedura obsługi zdarzeń, wywołaj <xref:System.Windows.Forms.Form.Show%2A> metodę, aby otworzyć formularz innego w projekcie i ustaw <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> właściwość `true`.  
  
    > [!NOTE]
    >  Wystąpienie <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> klasa przenosi odwołanie do <xref:System.Windows.Forms.LinkLabel> formant, który został kliknięty, więc nie ma potrzeby rzutowanie `sender` obiektu.  
  
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
 <xref:System.Windows.Forms.LinkLabel> Kontrolki można również wyświetlić stronę sieci Web za pomocą domyślnej przeglądarki.  
  
#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>Aby uruchomić program Internet Explorer i link do strony sieci Web za pomocą kontrolki LinkLabel  
  
1. Ustaw <xref:System.Windows.Forms.LinkLabel.Text%2A> właściwość odpowiedni podpis.  
  
2. Ustaw <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> właściwości w celu określenia, która część podpisu zostanie wskazany jako link.  
  
3. W <xref:System.Windows.Forms.LinkLabel.LinkClicked> procedura obsługi zdarzeń, która znajduje się w środku bloku obsługi wyjątków, wywołań Druga procedura, która ustawia <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> właściwości `true` i używa <xref:System.Diagnostics.Process.Start%2A> metodę, aby uruchomić domyślnej przeglądarki z adresem URL. Aby użyć <xref:System.Diagnostics.Process.Start%2A> należy dodać odwołanie do metody <xref:System.Diagnostics?displayProperty=nameWithType> przestrzeni nazw.  
  
    > [!IMPORTANT]
    >  Jeśli poniższy kod jest uruchamiane w środowisku częściowego zaufania (takich jak na udostępnionym dysku), kompilator JIT zakończy się niepowodzeniem kiedy `VisitLink` metoda jest wywoływana. `System.Diagnostics.Process.Start` Instrukcji powoduje, że żądanie łącza, który zakończy się niepowodzeniem. Przez przechwytywanie wyjątku podczas `VisitLink` poniższy kod pewność, że jeśli kompilator JIT nie powiedzie się, błąd odbywa się bez problemu zmieniała, metoda jest wywoływana.  
  
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
- [Instrukcje: Zmienianie wyglądu kontrolki LinkLabel formularzy Windows Forms](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [LinkLabel, kontrolka](linklabel-control-windows-forms.md)
