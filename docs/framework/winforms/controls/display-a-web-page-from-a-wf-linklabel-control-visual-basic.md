---
title: 'Instrukcje: Wyświetlanie strony sieci Web formantu LinkLabel formularzy Windows (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- LinkLabel1_LinkClicked
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Web pages [Windows Forms], displaying
- linking [Windows Forms], to Web pages from forms
- Windows Forms, linking to Web pages
- LinkLabel control [Windows Forms], examples
ms.assetid: 477a7398-5971-4de3-b24c-f49f32bdb28a
ms.openlocfilehash: 05b127099b85188b0df2f1f7821ceb147cc41e1d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698963"
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a><span data-ttu-id="3959b-102">Instrukcje: Wyświetlanie strony sieci Web formantu LinkLabel formularzy Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3959b-102">How to: Display a Web Page from a Windows Forms LinkLabel Control (Visual Basic)</span></span>
<span data-ttu-id="3959b-103">W tym przykładzie wyświetla stronę sieci Web w domyślnej przeglądarce, gdy użytkownik kliknie formularze Windows <xref:System.Windows.Forms.LinkLabel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="3959b-103">This example displays a Web page in the default browser when a user clicks a Windows Forms <xref:System.Windows.Forms.LinkLabel> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3959b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3959b-104">Example</span></span>  
  
```vb  
Private Sub Form1_Load(ByVal sender As System.Object, ByVal e _  
As System.EventArgs) Handles MyBase.Load  
    LinkLabel1.Text = "Click here to get more info."  
    LinkLabel1.Links.Add(6, 4, "www.microsoft.com")  
End Sub  
Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, ByVal _  
e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) Handles _  
LinkLabel1.LinkClicked  
    System.Diagnostics.Process.Start(e.Link.LinkData.ToString())  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3959b-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3959b-105">Compiling the Code</span></span>  
 <span data-ttu-id="3959b-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="3959b-106">This example requires:</span></span>  
  
-   <span data-ttu-id="3959b-107">Formularz Windows o nazwie `Form1`.</span><span class="sxs-lookup"><span data-stu-id="3959b-107">A Windows Form named `Form1`.</span></span>  
  
-   <span data-ttu-id="3959b-108">A <xref:System.Windows.Forms.LinkLabel> formantu o nazwie `LinkLabel1`.</span><span class="sxs-lookup"><span data-stu-id="3959b-108">A <xref:System.Windows.Forms.LinkLabel> control named `LinkLabel1`.</span></span>  
  
-   <span data-ttu-id="3959b-109">Aktywne połączenie z Internetem.</span><span class="sxs-lookup"><span data-stu-id="3959b-109">An active Internet connection.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3959b-110">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="3959b-110">.NET Framework Security</span></span>  
 <span data-ttu-id="3959b-111">Wywołanie <xref:System.Diagnostics.Process.Start%2A> metoda wymaga pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="3959b-111">The call to the <xref:System.Diagnostics.Process.Start%2A> method requires full trust.</span></span> <span data-ttu-id="3959b-112">Aby uzyskać więcej informacji, zobacz <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="3959b-112">For more information, see <xref:System.Security.SecurityException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3959b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3959b-113">See also</span></span>
- <xref:System.Windows.Forms.LinkLabel>
- [<span data-ttu-id="3959b-114">LinkLabel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="3959b-114">LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
