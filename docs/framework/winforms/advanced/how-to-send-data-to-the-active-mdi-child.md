---
title: 'Instrukcje: Wysyłanie danych do Active MDI Child'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms
- MDI [Windows Forms], sending data to forms
- Clipboard [Windows Forms], pasting
- Clipboard [Windows Forms], getting data from
ms.assetid: 1047d2fe-1235-46db-aad9-563aea1d743b
ms.openlocfilehash: a89956595ff98e8cda717c90a3f96c95abc8118a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707407"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a><span data-ttu-id="efb47-102">Instrukcje: Wysyłanie danych do Active MDI Child</span><span class="sxs-lookup"><span data-stu-id="efb47-102">How to: Send Data to the Active MDI Child</span></span>
<span data-ttu-id="efb47-103">Często w kontekście [aplikacje interfejsu wielu dokumentów (MDI)](multiple-document-interface-mdi-applications.md), konieczne będzie wysyłać dane do okno podrzędne aktywnego, na przykład gdy użytkownik wkleja danych ze Schowka w aplikacji MDI.</span><span class="sxs-lookup"><span data-stu-id="efb47-103">Often, within the context of [Multiple-Document Interface (MDI) Applications](multiple-document-interface-mdi-applications.md), you will need to send data to the active child window, such as when the user pastes data from the Clipboard into an MDI application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="efb47-104">Aby uzyskać informacji na temat weryfikowania okno podrzędne, które ma fokus, a następnie wysyłając jego zawartość do Schowka, zobacz [Określanie Active MDI Child](how-to-determine-the-active-mdi-child.md).</span><span class="sxs-lookup"><span data-stu-id="efb47-104">For information about verifying which child window has focus and sending its contents to the Clipboard, see [Determining the Active MDI Child](how-to-determine-the-active-mdi-child.md).</span></span>  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a><span data-ttu-id="efb47-105">Aby wysyłać dane do aktywnego okna podrzędnego MDI ze Schowka</span><span class="sxs-lookup"><span data-stu-id="efb47-105">To send data to the active MDI child window from the Clipboard</span></span>  
  
1.  <span data-ttu-id="efb47-106">Wewnątrz metody należy skopiować tekst do Schowka do aktywną kontrolkę formularza podrzędnego active.</span><span class="sxs-lookup"><span data-stu-id="efb47-106">Within a method, copy the text on the Clipboard to the active control of the active child form.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="efb47-107">W tym przykładzie przyjęto założenie, istnieje formularza nadrzędnego MDI (`Form1`) zawierający co najmniej jeden podrzędne MDI zawierający <xref:System.Windows.Forms.RichTextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="efb47-107">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="efb47-108">Aby uzyskać więcej informacji, zobacz [tworzenie formularzy nadrzędnych MDI](how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="efb47-108">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
    ```vb  
    Public Sub mniPaste_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniPaste.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ParentForm.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Try  
             Dim theBox As RichTextBox = Ctype(activeChild.ActiveControl, RichTextBox)  
             If (Not theBox Is Nothing) Then  
                ' Create a new instance of the DataObject interface.  
                Dim data As IDataObject = Clipboard.GetDataObject()  
                ' If the data is text, then set the text of the   
                ' RichTextBox to the text in the clipboard.  
                If (data.GetDataPresent(DataFormats.Text)) Then  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString()  
                End If  
             End If  
          Catch  
             MessageBox.Show("You need to select a RichTextBox.")  
          End Try  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniPaste_Click (object sender, System.EventArgs e)  
    {  
      // Determine the active child form.  
       Form activeChild = this.ParentForm.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {  
          try   
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Create a new instance of the DataObject interface.  
                IDataObject data = Clipboard.GetDataObject();  
                // If the data is text, then set the text of the   
                // RichTextBox to the text in the clipboard.  
                if (data.GetDataPresent(DataFormats.Text))  
                {  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString();                 
                }  
             }  
          }  
          catch   
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="efb47-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efb47-109">See also</span></span>
- [<span data-ttu-id="efb47-110">Aplikacje interfejsu wielu dokumentów (MDI)</span><span class="sxs-lookup"><span data-stu-id="efb47-110">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="efb47-111">Instrukcje: Tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="efb47-111">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="efb47-112">Instrukcje: Tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="efb47-112">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="efb47-113">Instrukcje: Określanie elementu podrzędnego Active MDI</span><span class="sxs-lookup"><span data-stu-id="efb47-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="efb47-114">Instrukcje: Aranżowanie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="efb47-114">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
