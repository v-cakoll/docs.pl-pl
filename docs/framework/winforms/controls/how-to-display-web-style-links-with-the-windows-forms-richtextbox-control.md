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
ms.openlocfilehash: 78a07a250744018f121b03f2973b1661ed6bf764
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745530"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a>Porady: wyświetlanie łączy stylu sieci Web za pomocą formantu RichTextBox formularzy systemu Windows

Kontrolka <xref:System.Windows.Forms.RichTextBox> Windows Forms może wyświetlać linki sieci Web jako kolorowe i podkreślone. Można napisać kod, który otwiera okno przeglądarki pokazujące witrynę sieci Web określoną w polu tekst linku po kliknięciu linku.

### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a>Aby utworzyć link do strony sieci Web z kontrolką RichTextBox

1. Ustaw właściwość <xref:System.Windows.Forms.RichTextBox.Text%2A> na ciąg zawierający prawidłowy adres URL (na przykład "http://www.microsoft.com/").

2. Upewnij się, że właściwość <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> jest ustawiona na `true` (wartość domyślna).

3. Utwórz nowe wystąpienie globalne obiektu <xref:System.Diagnostics.Process>.

4. Napisz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.RichTextBox.LinkClicked>, które wysyła przeglądarkę do żądanego tekstu.

    W poniższym przykładzie zdarzenie <xref:System.Windows.Forms.RichTextBox.LinkClicked> otwiera wystąpienie programu Internet Explorer na adres URL określony we właściwości <xref:System.Windows.Forms.RichTextBox.Text%2A> kontrolki <xref:System.Windows.Forms.RichTextBox>. W tym przykładzie przyjęto, że formularz z kontrolką <xref:System.Windows.Forms.RichTextBox>.

    > [!IMPORTANT]
    > W wywołaniu metody <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> wystąpi wyjątek <xref:System.Security.SecurityException>, jeśli używasz kodu w kontekście częściowego zaufania z powodu niewystarczających uprawnień. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../misc/code-access-security-basics.md).

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

    (Wizualizacja C++) Należy zainicjować `p`procesu, który można wykonać, dołączając następujące instrukcje w Konstruktorze formularza:

    ```cpp
    p = gcnew System::Diagnostics::Process();
    ```

    (Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.

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
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
