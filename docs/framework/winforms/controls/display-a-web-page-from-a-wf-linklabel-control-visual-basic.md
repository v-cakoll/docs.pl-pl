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
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a>Porady: wyświetlanie strony sieci Web za pomocą formantu LinkLabel formularzy systemu Windows (Visual Basic)
Ten przykład wyświetla stronę sieci Web w domyślnej przeglądarce, gdy użytkownik kliknie kontrolkę <xref:System.Windows.Forms.LinkLabel> Windows Forms.  
  
## <a name="example"></a>Przykład  
  
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
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Formularz systemu Windows o nazwie `Form1`.  
  
- Kontrolka <xref:System.Windows.Forms.LinkLabel> o nazwie `LinkLabel1`.  
  
- Aktywne połączenie internetowe.  
  
## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework  
 Wywołanie metody <xref:System.Diagnostics.Process.Start%2A> wymaga pełnego zaufania. Aby uzyskać więcej informacji, zobacz temat <xref:System.Security.SecurityException>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.LinkLabel>
- [LinkLabel, kontrolka](linklabel-control-windows-forms.md)
