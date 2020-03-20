---
title: 'Porady: określanie elementu podrzędnego MDI Active'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- MDI [Windows Forms], child windows
- child forms
- MDI [Windows Forms], activating forms
- MDI [Windows Forms], locating focus
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
ms.openlocfilehash: 57491faa10c182630d41565ba236d65e393929b3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182543"
---
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="1098a-102">Porady: określanie elementu podrzędnego MDI Active</span><span class="sxs-lookup"><span data-stu-id="1098a-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="1098a-103">Czasami należy podać polecenie, które działa na formancie, który koncentruje się na aktualnie aktywnym formularzu podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="1098a-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="1098a-104">Załóżmy na przykład, że chcesz skopiować zaznaczony tekst z pola tekstowego formularza podrzędnego do Schowka.</span><span class="sxs-lookup"><span data-stu-id="1098a-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="1098a-105">Należy utworzyć procedurę kopiuje zaznaczony tekst do <xref:System.Windows.Forms.Control.Click> Schowka przy użyciu zdarzenia elementu menu Kopiuj w standardowym menu Edycja.</span><span class="sxs-lookup"><span data-stu-id="1098a-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="1098a-106">Ponieważ aplikacja MDI może mieć wiele wystąpień tego samego formularza podrzędnego, procedura musi wiedzieć, który formularz do użycia.</span><span class="sxs-lookup"><span data-stu-id="1098a-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="1098a-107">Aby określić poprawny <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> formularz, należy użyć właściwości, która zwraca formularz podrzędny, który ma fokus lub który był ostatnio aktywny.</span><span class="sxs-lookup"><span data-stu-id="1098a-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="1098a-108">Jeśli masz kilka formantów w formularzu, należy również określić, który formant jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="1098a-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="1098a-109">Podobnie <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> jak <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> właściwość, właściwość zwraca formant z fokusem na aktywnym formularzu podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="1098a-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="1098a-110">Poniższa procedura ilustruje procedurę kopiowania, którą można wywołać z menu formularza podrzędnego, menu w formularzu MDI lub przycisku paska narzędzi.</span><span class="sxs-lookup"><span data-stu-id="1098a-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="1098a-111">Aby określić aktywne dziecko MDI (skopiować jego tekst do Schowka)</span><span class="sxs-lookup"><span data-stu-id="1098a-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1. <span data-ttu-id="1098a-112">W ramach metody skopiuj tekst aktywnego formantu aktywnego formularza podrzędnego do Schowka.</span><span class="sxs-lookup"><span data-stu-id="1098a-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1098a-113">W tym przykładzie przyjęto założenie,`Form1`że istnieje formularz nadrzędny MDI <xref:System.Windows.Forms.RichTextBox> ( ), który ma co najmniej jedno podrzędne okna MDI zawierające formant.</span><span class="sxs-lookup"><span data-stu-id="1098a-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="1098a-114">Aby uzyskać więcej informacji, zobacz [Tworzenie formularzy nadrzędnych MDI](how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1098a-114">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
    ```vb  
    Public Sub mniCopy_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniCopy.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Dim theBox As RichTextBox = _  
            TryCast(activeChild.ActiveControl, RichTextBox)  
  
          If (Not theBox Is Nothing) Then  
             'Put selected text on Clipboard.  
             Clipboard.SetDataObject(theBox.SelectedText)  
          Else  
             MessageBox.Show("You need to select a RichTextBox.")  
          End If  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniCopy_Click (object sender, System.EventArgs e)  
    {  
       // Determine the active child form.  
       Form activeChild = this.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {
          try  
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Put the selected text on the Clipboard.  
                Clipboard.SetDataObject(theBox.SelectedText);  
  
             }  
          }  
          catch  
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1098a-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1098a-115">See also</span></span>

- [<span data-ttu-id="1098a-116">Aplikacje interfejsu wielu dokumentów (MDI)</span><span class="sxs-lookup"><span data-stu-id="1098a-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="1098a-117">Porady: tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="1098a-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="1098a-118">Porady: tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="1098a-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="1098a-119">Instrukcje: wysyłanie danych do Active MDI Child</span><span class="sxs-lookup"><span data-stu-id="1098a-119">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="1098a-120">Porady: aranżowanie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="1098a-120">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
