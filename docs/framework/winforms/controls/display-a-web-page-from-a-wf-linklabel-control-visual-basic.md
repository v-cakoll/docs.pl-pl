---
title: "Porady: wyświetlanie strony sieci Web za pomocą formantu LinkLabel formularzy systemu Windows (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ba5ba3b29bab148087e0f8b80b3f1c43aa74e761
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a><span data-ttu-id="5887a-102">Porady: wyświetlanie strony sieci Web za pomocą formantu LinkLabel formularzy systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5887a-102">How to: Display a Web Page from a Windows Forms LinkLabel Control (Visual Basic)</span></span>
<span data-ttu-id="5887a-103">W tym przykładzie użytkownik klika formularzy systemu Windows wyświetla stronę sieci Web w domyślnej przeglądarce <xref:System.Windows.Forms.LinkLabel> formantu.</span><span class="sxs-lookup"><span data-stu-id="5887a-103">This example displays a Web page in the default browser when a user clicks a Windows Forms <xref:System.Windows.Forms.LinkLabel> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5887a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5887a-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="5887a-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5887a-105">Compiling the Code</span></span>  
 <span data-ttu-id="5887a-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="5887a-106">This example requires:</span></span>  
  
-   <span data-ttu-id="5887a-107">Formularz systemu Windows o nazwie `Form1`.</span><span class="sxs-lookup"><span data-stu-id="5887a-107">A Windows Form named `Form1`.</span></span>  
  
-   <span data-ttu-id="5887a-108">A <xref:System.Windows.Forms.LinkLabel> formantu o nazwie `LinkLabel1`.</span><span class="sxs-lookup"><span data-stu-id="5887a-108">A <xref:System.Windows.Forms.LinkLabel> control named `LinkLabel1`.</span></span>  
  
-   <span data-ttu-id="5887a-109">Aktywne połączenie internetowe.</span><span class="sxs-lookup"><span data-stu-id="5887a-109">An active Internet connection.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5887a-110">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="5887a-110">.NET Framework Security</span></span>  
 <span data-ttu-id="5887a-111">Wywołanie <xref:System.Diagnostics.Process.Start%2A> metoda wymaga pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="5887a-111">The call to the <xref:System.Diagnostics.Process.Start%2A> method requires full trust.</span></span> <span data-ttu-id="5887a-112">Aby uzyskać więcej informacji, zobacz <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="5887a-112">For more information, see <xref:System.Security.SecurityException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5887a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5887a-113">See Also</span></span>  
 <xref:System.Windows.Forms.LinkLabel>  
 [<span data-ttu-id="5887a-114">LinkLabel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="5887a-114">LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
