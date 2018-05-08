---
title: 'Porady: łączenie z obiektem lub stroną sieci Web za pomocą formantu LinkLabel formularzy systemu Windows'
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
ms.openlocfilehash: 9957eae7e15c99ec259574b435402420c6bcf5f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>Porady: łączenie z obiektem lub stroną sieci Web za pomocą formantu LinkLabel formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.LinkLabel> formant służy do tworzenia łączy stylu sieci Web w formularzu. Po kliknięciu łącza, można zmienić jego kolor, aby wskazać, że odwiedzeniu łącza. Aby uzyskać więcej informacji na zmianę koloru, zobacz [porady: Zmienianie wyglądu formantu LinkLabel formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).  
  
## <a name="linking-to-another-form"></a>Łączenie z innej formy  
  
#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>Aby utworzyć link do innego formularza za pomocą formantu LinkLabel  
  
1.  Ustaw <xref:System.Windows.Forms.LinkLabel.Text%2A> właściwości odpowiedni podpis.  
  
2.  Ustaw <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> właściwości w celu określenia, która część podpis zostanie wskazany jako łącze. Jak wskazane zależy od właściwości związanych z wygląd etykiety łącza. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Wartość jest reprezentowana przez <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> obiektu zawierającego dwóch liczb, pozycję początkową znaku i liczbę znaków. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Właściwość można ustawić w oknie właściwości lub w kodzie w sposób podobny do następującego:  
  
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
  
3.  W <xref:System.Windows.Forms.LinkLabel.LinkClicked> program obsługi zdarzeń, wywołaj <xref:System.Windows.Forms.Form.Show%2A> metodę, aby otworzyć formularz innego projektu i ustawić <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> właściwości `true`.  
  
    > [!NOTE]
    >  Wystąpienie <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> klasy zawiera odwołanie do <xref:System.Windows.Forms.LinkLabel> formant, który został kliknięty, a więc nie trzeba rzutowania `sender` obiektu.  
  
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
  
## <a name="linking-to-a-web-page"></a>Łączenie do stron sieci Web  
 <xref:System.Windows.Forms.LinkLabel> Formantu można również wyświetlić stronę sieci Web z domyślnej przeglądarki.  
  
#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>Aby uruchomić program Internet Explorer i łącze do strony sieci Web za pomocą formantu LinkLabel  
  
1.  Ustaw <xref:System.Windows.Forms.LinkLabel.Text%2A> właściwości odpowiedni podpis.  
  
2.  Ustaw <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> właściwości w celu określenia, która część podpis zostanie wskazany jako łącze.  
  
3.  W <xref:System.Windows.Forms.LinkLabel.LinkClicked> program obsługi zdarzeń, pośrodku bloku obsługi wyjątków, wywołań drugiej procedury, która ustawia <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> właściwości `true` i używa <xref:System.Diagnostics.Process.Start%2A> metody można uruchomić domyślnej przeglądarki z adresem URL. Aby użyć <xref:System.Diagnostics.Process.Start%2A> musisz dodać odwołanie do metody <xref:System.Diagnostics?displayProperty=nameWithType> przestrzeni nazw.  
  
    > [!IMPORTANT]
    >  Jeśli poniższy kod uruchamiany w środowisku częściowego zaufania (takich jak udostępnionego dysku), przy użyciu kompilatora JIT nie powiedzie się po `VisitLink` metoda jest wywoływana. `System.Diagnostics.Process.Start` Instrukcja powoduje, że żądanie łącza, który zakończy się niepowodzeniem. Przez przechwytywanie wyjątku podczas `VisitLink` metoda jest wywoływana, poniższy kod zapewnia, że jeśli kompilator JIT nie powiedzie się, kod błędu jest obsługiwane bezpiecznie.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>  
 [LinkLabel, kontrolka — omówienie](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)  
 [Instrukcje: zmienianie wyglądu kontrolki LinkLabel formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)  
 [LinkLabel, kontrolka](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
