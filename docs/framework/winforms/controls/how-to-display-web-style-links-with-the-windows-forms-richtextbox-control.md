---
title: Wyświetlanie łączy w stylu sieci Web z kontrolką RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying Web links
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], linking to Web pages
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
ms.openlocfilehash: 06ed304e566bb437a2353dd330d7de5328f2a729
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144828"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a>Porady: wyświetlanie łączy stylu sieci Web za pomocą formantu RichTextBox formularzy systemu Windows

<xref:System.Windows.Forms.RichTextBox>Kontrolka Windows Forms może wyświetlać linki sieci Web jako kolorowe i podkreślane. Można napisać kod, który otwiera okno przeglądarki pokazujące witrynę sieci Web określoną w polu tekst linku po kliknięciu linku.

### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a>Aby utworzyć link do strony sieci Web z kontrolką RichTextBox

1. Ustaw <xref:System.Windows.Forms.RichTextBox.Text%2A> Właściwość na ciąg, który zawiera prawidłowy adres URL (na przykład " https://www.microsoft.com/ ").

2. Upewnij się, że <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> Właściwość jest ustawiona na `true` (wartość domyślna).

3. Utwórz nowe wystąpienie globalne <xref:System.Diagnostics.Process> obiektu.

4. Napisz procedurę obsługi zdarzeń <xref:System.Windows.Forms.RichTextBox.LinkClicked> , która wysyła do przeglądarki żądany tekst.

    W poniższym przykładzie <xref:System.Windows.Forms.RichTextBox.LinkClicked> zdarzenie otwiera wystąpienie programu Internet Explorer na adres URL określony we <xref:System.Windows.Forms.RichTextBox.Text%2A> właściwości <xref:System.Windows.Forms.RichTextBox> formantu. W tym przykładzie założono formularz z <xref:System.Windows.Forms.RichTextBox> kontrolką.

    > [!IMPORTANT]
    > W wywołaniu <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> metody, wystąpi wyjątek, jeśli używasz <xref:System.Security.SecurityException> kodu w kontekście częściowego zaufania z powodu niewystarczających uprawnień. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../misc/code-access-security-basics.md).

    ```vb
    Public p As New System.Diagnostics.Process
    Private Sub RichTextBox1_LinkClicked _
       (ByVal sender As Object, ByVal e As _
       System.Windows.Forms.LinkClickedEventArgs) _
       Handles RichTextBox1.LinkClicked
          ' Call Process.Start method to open a browser
          ' with link text as URL.
          p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText)
    End Sub
    ```

    ```csharp
    public System.Diagnostics.Process p = new System.Diagnostics.Process();

    private void richTextBox1_LinkClicked(object sender,
    System.Windows.Forms.LinkClickedEventArgs e)
    {
       // Call Process.Start method to open a browser
       // with link text as URL.
       p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText);
    }
    ```

    ```cpp
    public:
       System::Diagnostics::Process ^ p;

    private:
       void richTextBox1_LinkClicked(System::Object ^  sender,
          System::Windows::Forms::LinkClickedEventArgs ^  e)
       {
          // Call Process.Start method to open a browser
          // with link text as URL.
          p = System::Diagnostics::Process::Start("IExplore.exe",
             e->LinkText);
       }
    ```

    (Visual C++) Należy zainicjować proces `p` , który można wykonać, dołączając następujące instrukcje w Konstruktorze formularza:

    ```cpp
    p = gcnew System::Diagnostics::Process();
    ```

    (Visual C#, Visual C++) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.

    ```csharp
    this.richTextBox1.LinkClicked += new
       System.Windows.Forms.LinkClickedEventHandler
       (this.richTextBox1_LinkClicked);
    ```

    ```cpp
    this->richTextBox1->LinkClicked += gcnew
       System::Windows::Forms::LinkClickedEventHandler
       (this, &Form1::richTextBox1_LinkClicked);
    ```

    Ważne jest, aby natychmiast przerwać proces utworzony po zakończeniu pracy z nim. W odniesieniu do kodu przedstawionego powyżej kod, aby zatrzymać proces, może wyglądać następująco:

    ```vb
    Public Sub StopWebProcess()
       p.Kill()
    End Sub
    ```

    ```csharp
    public void StopWebProcess()
    {
       p.Kill();
    }
    ```

    ```cpp
    public: void StopWebProcess()
    {
       p->Kill();
    }
    ```

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [Formanty do użycia w formularzach systemu Windows](controls-to-use-on-windows-forms.md)
