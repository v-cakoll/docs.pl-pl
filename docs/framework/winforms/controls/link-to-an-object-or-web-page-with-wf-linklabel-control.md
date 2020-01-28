---
title: Link do obiektu lub strony sieci Web z kontrolką LinkLabel
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
ms.openlocfilehash: 1669a9d6aba39b02d228c735701ca4e31c8f8291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745208"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>Porady: łączenie z obiektem lub stroną sieci Web za pomocą formantu LinkLabel formularzy systemu Windows

Kontrolka <xref:System.Windows.Forms.LinkLabel> Windows Forms umożliwia tworzenie łączy w stylu sieci Web w formularzu. Po kliknięciu linku można zmienić jego kolor, aby wskazać, że łącze zostało odwiedzone. Aby uzyskać więcej informacji na temat zmiany koloru, zobacz [How to: Change the Windows Forms Control LinkLabel](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).

## <a name="linking-to-another-form"></a>Łączenie z innym formularzem

#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>Aby połączyć się z innym formularzem za pomocą kontrolki LinkLabel

1. Ustaw właściwość <xref:System.Windows.Forms.LinkLabel.Text%2A> na odpowiedni podpis.

2. Ustaw właściwość <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, aby określić, która część podpisu będzie wskazywana jako link. Sposób wskazywania zależy od właściwości etykiety linku dotyczącej wyglądu. Wartość <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> jest reprezentowana przez obiekt <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> zawierający dwie liczby, początkową pozycję znaku i liczbę znaków. Właściwość <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> można ustawić w okno Właściwości lub w kodzie w sposób podobny do poniższego:

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

3. W obsłudze zdarzeń <xref:System.Windows.Forms.LinkLabel.LinkClicked> Wywołaj metodę <xref:System.Windows.Forms.Form.Show%2A>, aby otworzyć inny formularz w projekcie, i ustaw właściwość <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> na `true`.

    > [!NOTE]
    > Wystąpienie klasy <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> przenosi odwołanie do kontrolki <xref:System.Windows.Forms.LinkLabel>, która została kliknięta, więc nie trzeba rzutować obiektu `sender`.

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

Formant <xref:System.Windows.Forms.LinkLabel> może być również używany do wyświetlania strony sieci Web z domyślną przeglądarką.

#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>Aby uruchomić program Internet Explorer i połączyć się ze stroną sieci Web za pomocą kontrolki LinkLabel

1. Ustaw właściwość <xref:System.Windows.Forms.LinkLabel.Text%2A> na odpowiedni podpis.

2. Ustaw właściwość <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, aby określić, która część podpisu będzie wskazywana jako link.

3. W obsłudze zdarzeń <xref:System.Windows.Forms.LinkLabel.LinkClicked>, w pośrodku bloku obsługi wyjątków, wywołaj drugą procedurę, która ustawia właściwość <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> na `true` i używa metody <xref:System.Diagnostics.Process.Start%2A> do uruchamiania domyślnej przeglądarki z adresem URL. Aby użyć metody <xref:System.Diagnostics.Process.Start%2A> należy dodać odwołanie do przestrzeni nazw <xref:System.Diagnostics?displayProperty=nameWithType>.

    > [!IMPORTANT]
    > Jeśli Poniższy kod jest uruchamiany w środowisku częściowego zaufania (na przykład na dysku udostępnionym), kompilator JIT kończy się niepowodzeniem, gdy wywoływana jest metoda `VisitLink`. Instrukcja `System.Diagnostics.Process.Start` powoduje, że żądanie linku kończy się niepowodzeniem. Zwracając wyjątek w przypadku wywołania metody `VisitLink`, poniższy kod gwarantuje, że jeśli kompilator JIT nie powiedzie się, błąd jest prawidłowo obsługiwany.

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
- [Instrukcje: zmienianie wyglądu kontrolki LinkLabel formularzy Windows Forms](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [LinkLabel, kontrolka](linklabel-control-windows-forms.md)
