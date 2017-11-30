---
title: "Porady: określanie elementu podrzędnego MDI Active"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 473cf67f01db8735eb3b32a7549296f827e66ef6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="698c7-102">Porady: określanie elementu podrzędnego MDI Active</span><span class="sxs-lookup"><span data-stu-id="698c7-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="698c7-103">Czasem można udostępnić polecenia, który działa na formant, który ma fokus w formularzu podrzędnym obecnie aktywne.</span><span class="sxs-lookup"><span data-stu-id="698c7-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="698c7-104">Na przykład załóżmy, że chcesz skopiować zaznaczonego tekstu w polu tekstowym formularz podrzędny do Schowka.</span><span class="sxs-lookup"><span data-stu-id="698c7-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="698c7-105">Należy utworzyć procedury, która kopiuje zaznaczonego tekstu do Schowka przy użyciu <xref:System.Windows.Forms.Control.Click> zdarzeń Kopiuj element menu standardowe menu Edycja.</span><span class="sxs-lookup"><span data-stu-id="698c7-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="698c7-106">Ponieważ aplikacja MDI może mieć wiele wystąpień tego samego formularza podrzędnego, procedury musi wiedzieć, który formularz do użycia.</span><span class="sxs-lookup"><span data-stu-id="698c7-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="698c7-107">Aby określić właściwego formularza, użyj <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> właściwość, która zwraca formularz podrzędny, który ma fokus lub który został ostatnio aktywne.</span><span class="sxs-lookup"><span data-stu-id="698c7-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="698c7-108">Jeśli masz kilka formantów w formularzu, należy również określić, które sterowania jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="698c7-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="698c7-109">Podobnie jak <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> właściwość <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> właściwość zwraca formantu z fokusem w formularzu podrzędnym aktywne.</span><span class="sxs-lookup"><span data-stu-id="698c7-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="698c7-110">Poniżej przedstawiono procedurę kopiowania, który można wywołać z menu formularza podrzędnego, menu MDI formularza lub przycisku paska narzędzi.</span><span class="sxs-lookup"><span data-stu-id="698c7-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="698c7-111">Aby określić podrzędnego MDI active (można skopiować tekstu do Schowka)</span><span class="sxs-lookup"><span data-stu-id="698c7-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1.  <span data-ttu-id="698c7-112">W metodzie należy skopiować tekst aktywnym formantem formularza podrzędnego active do Schowka.</span><span class="sxs-lookup"><span data-stu-id="698c7-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="698c7-113">W tym przykładzie założono Brak formularza nadrzędnego MDI (`Form1`) mający okien podrzędnych co najmniej jeden MDI zawierający <xref:System.Windows.Forms.RichTextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="698c7-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="698c7-114">Aby uzyskać więcej informacji, zobacz [tworzenie formularzy nadrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="698c7-114">For more information, see [Creating MDI Parent Forms](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="698c7-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="698c7-115">See Also</span></span>  
 [<span data-ttu-id="698c7-116">Aplikacje interfejsu wielu dokumentów (MDI)</span><span class="sxs-lookup"><span data-stu-id="698c7-116">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="698c7-117">Porady: tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="698c7-117">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="698c7-118">Porady: tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="698c7-118">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="698c7-119">Porady: wysyłanie danych do Active MDI Child</span><span class="sxs-lookup"><span data-stu-id="698c7-119">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [<span data-ttu-id="698c7-120">Porady: Aranżowanie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="698c7-120">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
