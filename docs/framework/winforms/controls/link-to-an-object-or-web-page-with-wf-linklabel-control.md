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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344016"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a><span data-ttu-id="767f4-102">Instrukcje: łączenie z obiektem lub stroną sieci Web za pomocą kontrolki LinkLabel formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="767f4-102">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>
<span data-ttu-id="767f4-103">Formularze Windows <xref:System.Windows.Forms.LinkLabel> formantu służy do tworzenia łączy stylu sieci Web w formularzu.</span><span class="sxs-lookup"><span data-stu-id="767f4-103">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to create Web-style links on your form.</span></span> <span data-ttu-id="767f4-104">Po kliknięciu łącza, można zmienić jego kolor, aby wskazać, że link został odwiedzony.</span><span class="sxs-lookup"><span data-stu-id="767f4-104">When the link is clicked, you can change its color to indicate the link has been visited.</span></span> <span data-ttu-id="767f4-105">Aby uzyskać więcej informacji o zmienianiu kolorów, zobacz [jak: Zmienianie wyglądu formantu LinkLabel formularzy Windows](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span><span class="sxs-lookup"><span data-stu-id="767f4-105">For more information on changing the color, see [How to: Change the Appearance of the Windows Forms LinkLabel Control](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span></span>  
  
## <a name="linking-to-another-form"></a><span data-ttu-id="767f4-106">Łączenie z innej formy</span><span class="sxs-lookup"><span data-stu-id="767f4-106">Linking to Another Form</span></span>  
  
#### <a name="to-link-to-another-form-with-a-linklabel-control"></a><span data-ttu-id="767f4-107">Aby połączyć innego formularza za pomocą kontrolki LinkLabel</span><span class="sxs-lookup"><span data-stu-id="767f4-107">To link to another form with a LinkLabel control</span></span>  
  
1. <span data-ttu-id="767f4-108">Ustaw <xref:System.Windows.Forms.LinkLabel.Text%2A> właściwość odpowiedni podpis.</span><span class="sxs-lookup"><span data-stu-id="767f4-108">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
2. <span data-ttu-id="767f4-109">Ustaw <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> właściwości w celu określenia, która część podpisu zostanie wskazany jako link.</span><span class="sxs-lookup"><span data-stu-id="767f4-109">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span> <span data-ttu-id="767f4-110">Jak jest oznaczany zależy od właściwości powiązane z wyglądem etykieta linku.</span><span class="sxs-lookup"><span data-stu-id="767f4-110">How it is indicated depends on the appearance-related properties of the link label.</span></span> <span data-ttu-id="767f4-111"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Wartość jest reprezentowana przez <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> obiekt zawierający dwie liczby, począwszy od pozycji znaku i liczbę znaków.</span><span class="sxs-lookup"><span data-stu-id="767f4-111">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented by a <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> object containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="767f4-112"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Właściwość można ustawić w oknie dialogowym właściwości lub w kodzie w sposób podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="767f4-112">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property can be set in the Properties window or in code in a manner similar to the following:</span></span>  
  
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
  
3. <span data-ttu-id="767f4-113">W <xref:System.Windows.Forms.LinkLabel.LinkClicked> procedura obsługi zdarzeń, wywołaj <xref:System.Windows.Forms.Form.Show%2A> metodę, aby otworzyć formularz innego w projekcie i ustaw <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="767f4-113">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, invoke the <xref:System.Windows.Forms.Form.Show%2A> method to open another form in the project, and set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="767f4-114">Wystąpienie <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> klasa przenosi odwołanie do <xref:System.Windows.Forms.LinkLabel> formant, który został kliknięty, więc nie ma potrzeby rzutowanie `sender` obiektu.</span><span class="sxs-lookup"><span data-stu-id="767f4-114">An instance of the <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> class carries a reference to the <xref:System.Windows.Forms.LinkLabel> control that was clicked, so there is no need to cast the `sender` object.</span></span>  
  
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
  
## <a name="linking-to-a-web-page"></a><span data-ttu-id="767f4-115">Łączenie ze stroną sieci Web</span><span class="sxs-lookup"><span data-stu-id="767f4-115">Linking to a Web Page</span></span>  
 <span data-ttu-id="767f4-116"><xref:System.Windows.Forms.LinkLabel> Kontrolki można również wyświetlić stronę sieci Web za pomocą domyślnej przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="767f4-116">The <xref:System.Windows.Forms.LinkLabel> control can also be used to display a Web page with the default browser.</span></span>  
  
#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a><span data-ttu-id="767f4-117">Aby uruchomić program Internet Explorer i link do strony sieci Web za pomocą kontrolki LinkLabel</span><span class="sxs-lookup"><span data-stu-id="767f4-117">To start Internet Explorer and link to a Web page with a LinkLabel control</span></span>  
  
1. <span data-ttu-id="767f4-118">Ustaw <xref:System.Windows.Forms.LinkLabel.Text%2A> właściwość odpowiedni podpis.</span><span class="sxs-lookup"><span data-stu-id="767f4-118">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
2. <span data-ttu-id="767f4-119">Ustaw <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> właściwości w celu określenia, która część podpisu zostanie wskazany jako link.</span><span class="sxs-lookup"><span data-stu-id="767f4-119">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>  
  
3. <span data-ttu-id="767f4-120">W <xref:System.Windows.Forms.LinkLabel.LinkClicked> procedura obsługi zdarzeń, która znajduje się w środku bloku obsługi wyjątków, wywołań Druga procedura, która ustawia <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> właściwości `true` i używa <xref:System.Diagnostics.Process.Start%2A> metodę, aby uruchomić domyślnej przeglądarki z adresem URL.</span><span class="sxs-lookup"><span data-stu-id="767f4-120">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, in the midst of an exception-handling block, call a second procedure that sets the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true` and uses the <xref:System.Diagnostics.Process.Start%2A> method to start the default browser with a URL.</span></span> <span data-ttu-id="767f4-121">Aby użyć <xref:System.Diagnostics.Process.Start%2A> należy dodać odwołanie do metody <xref:System.Diagnostics?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="767f4-121">To use the <xref:System.Diagnostics.Process.Start%2A> method you need to add a reference to the <xref:System.Diagnostics?displayProperty=nameWithType> namespace.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="767f4-122">Jeśli poniższy kod jest uruchamiane w środowisku częściowego zaufania (takich jak na udostępnionym dysku), kompilator JIT zakończy się niepowodzeniem kiedy `VisitLink` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="767f4-122">If the code below is run in a partial-trust environment (such as on a shared drive), the JIT compiler fails when the `VisitLink` method is called.</span></span> <span data-ttu-id="767f4-123">`System.Diagnostics.Process.Start` Instrukcji powoduje, że żądanie łącza, który zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="767f4-123">The `System.Diagnostics.Process.Start` statement causes a link demand that fails.</span></span> <span data-ttu-id="767f4-124">Przez przechwytywanie wyjątku podczas `VisitLink` poniższy kod pewność, że jeśli kompilator JIT nie powiedzie się, błąd odbywa się bez problemu zmieniała, metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="767f4-124">By catching the exception when the `VisitLink` method is called, the code below ensures that if the JIT compiler fails, the error is handled gracefully.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="767f4-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="767f4-125">See also</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="767f4-126">LinkLabel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="767f4-126">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="767f4-127">Instrukcje: Zmienianie wyglądu kontrolki LinkLabel formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="767f4-127">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [<span data-ttu-id="767f4-128">LinkLabel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="767f4-128">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
