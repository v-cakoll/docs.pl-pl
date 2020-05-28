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
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="6e46d-102">Porady: wyświetlanie łączy stylu sieci Web za pomocą formantu RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6e46d-102">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="6e46d-103"><xref:System.Windows.Forms.RichTextBox>Kontrolka Windows Forms może wyświetlać linki sieci Web jako kolorowe i podkreślane.</span><span class="sxs-lookup"><span data-stu-id="6e46d-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display Web links as colored and underlined.</span></span> <span data-ttu-id="6e46d-104">Można napisać kod, który otwiera okno przeglądarki pokazujące witrynę sieci Web określoną w polu tekst linku po kliknięciu linku.</span><span class="sxs-lookup"><span data-stu-id="6e46d-104">You can write code that opens a browser window showing the Web site specified in the link text when the link is clicked.</span></span>

### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a><span data-ttu-id="6e46d-105">Aby utworzyć link do strony sieci Web z kontrolką RichTextBox</span><span class="sxs-lookup"><span data-stu-id="6e46d-105">To link to a Web page with the RichTextBox control</span></span>

1. <span data-ttu-id="6e46d-106">Ustaw <xref:System.Windows.Forms.RichTextBox.Text%2A> Właściwość na ciąg, który zawiera prawidłowy adres URL (na przykład " https://www.microsoft.com/ ").</span><span class="sxs-lookup"><span data-stu-id="6e46d-106">Set the <xref:System.Windows.Forms.RichTextBox.Text%2A> property to a string that includes a valid URL (for example, "https://www.microsoft.com/").</span></span>

2. <span data-ttu-id="6e46d-107">Upewnij się, że <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> Właściwość jest ustawiona na `true` (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="6e46d-107">Make sure the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property is set to `true` (the default).</span></span>

3. <span data-ttu-id="6e46d-108">Utwórz nowe wystąpienie globalne <xref:System.Diagnostics.Process> obiektu.</span><span class="sxs-lookup"><span data-stu-id="6e46d-108">Create a new global instance of the <xref:System.Diagnostics.Process> object.</span></span>

4. <span data-ttu-id="6e46d-109">Napisz procedurę obsługi zdarzeń <xref:System.Windows.Forms.RichTextBox.LinkClicked> , która wysyła do przeglądarki żądany tekst.</span><span class="sxs-lookup"><span data-stu-id="6e46d-109">Write an event handler for the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event that sends the browser the desired text.</span></span>

    <span data-ttu-id="6e46d-110">W poniższym przykładzie <xref:System.Windows.Forms.RichTextBox.LinkClicked> zdarzenie otwiera wystąpienie programu Internet Explorer na adres URL określony we <xref:System.Windows.Forms.RichTextBox.Text%2A> właściwości <xref:System.Windows.Forms.RichTextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="6e46d-110">In the example below, the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event opens an instance of Internet Explorer to the URL specified in the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="6e46d-111">W tym przykładzie założono formularz z <xref:System.Windows.Forms.RichTextBox> kontrolką.</span><span class="sxs-lookup"><span data-stu-id="6e46d-111">This example assumes a form with a <xref:System.Windows.Forms.RichTextBox> control.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="6e46d-112">W wywołaniu <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> metody, wystąpi wyjątek, jeśli używasz <xref:System.Security.SecurityException> kodu w kontekście częściowego zaufania z powodu niewystarczających uprawnień.</span><span class="sxs-lookup"><span data-stu-id="6e46d-112">In calling the <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> method, you will encounter a <xref:System.Security.SecurityException> exception if you are running the code in a partial-trust context because of insufficient privileges.</span></span> <span data-ttu-id="6e46d-113">Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="6e46d-113">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

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

    <span data-ttu-id="6e46d-114">(Visual C++) Należy zainicjować proces `p` , który można wykonać, dołączając następujące instrukcje w Konstruktorze formularza:</span><span class="sxs-lookup"><span data-stu-id="6e46d-114">(Visual C++) You must initialize process `p`, which you can do by including the following statement in the constructor of your form:</span></span>

    ```cpp
    p = gcnew System::Diagnostics::Process();
    ```

    <span data-ttu-id="6e46d-115">(Visual C#, Visual C++) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6e46d-115">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

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

    <span data-ttu-id="6e46d-116">Ważne jest, aby natychmiast przerwać proces utworzony po zakończeniu pracy z nim.</span><span class="sxs-lookup"><span data-stu-id="6e46d-116">It is important to immediately stop the process you have created once you have finished working with it.</span></span> <span data-ttu-id="6e46d-117">W odniesieniu do kodu przedstawionego powyżej kod, aby zatrzymać proces, może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="6e46d-117">Referring to the code presented above, your code to stop the process might look like this:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6e46d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e46d-118">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="6e46d-119">RichTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="6e46d-119">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="6e46d-120">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6e46d-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
