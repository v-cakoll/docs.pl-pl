---
title: Wyświetl stronę internetową z formantu LinkLabel (Visual Basic)
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
ms.openlocfilehash: 75373d55b7bc5ef11e39d5b9546996cb1c4f6f7c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745924"
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a><span data-ttu-id="7431d-102">Porady: wyświetlanie strony sieci Web za pomocą formantu LinkLabel formularzy systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7431d-102">How to: Display a Web Page from a Windows Forms LinkLabel Control (Visual Basic)</span></span>
<span data-ttu-id="7431d-103">Ten przykład wyświetla stronę sieci Web w domyślnej przeglądarce, gdy użytkownik kliknie kontrolkę <xref:System.Windows.Forms.LinkLabel> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7431d-103">This example displays a Web page in the default browser when a user clicks a Windows Forms <xref:System.Windows.Forms.LinkLabel> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7431d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7431d-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="7431d-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7431d-105">Compiling the Code</span></span>  
 <span data-ttu-id="7431d-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="7431d-106">This example requires:</span></span>  
  
- <span data-ttu-id="7431d-107">Formularz systemu Windows o nazwie `Form1`.</span><span class="sxs-lookup"><span data-stu-id="7431d-107">A Windows Form named `Form1`.</span></span>  
  
- <span data-ttu-id="7431d-108">Kontrolka <xref:System.Windows.Forms.LinkLabel> o nazwie `LinkLabel1`.</span><span class="sxs-lookup"><span data-stu-id="7431d-108">A <xref:System.Windows.Forms.LinkLabel> control named `LinkLabel1`.</span></span>  
  
- <span data-ttu-id="7431d-109">Aktywne połączenie internetowe.</span><span class="sxs-lookup"><span data-stu-id="7431d-109">An active Internet connection.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7431d-110">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="7431d-110">.NET Framework Security</span></span>  
 <span data-ttu-id="7431d-111">Wywołanie metody <xref:System.Diagnostics.Process.Start%2A> wymaga pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="7431d-111">The call to the <xref:System.Diagnostics.Process.Start%2A> method requires full trust.</span></span> <span data-ttu-id="7431d-112">Aby uzyskać więcej informacji, zobacz <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="7431d-112">For more information, see <xref:System.Security.SecurityException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7431d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7431d-113">See also</span></span>

- <xref:System.Windows.Forms.LinkLabel>
- [<span data-ttu-id="7431d-114">LinkLabel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="7431d-114">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
