---
title: 'Instrukcje: wyświetlanie strony sieci Web za pomocą kontrolki LinkLabel formularzy systemu Windows (Visual Basic)'
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
ms.openlocfilehash: f36f5bbaaf28963fc95440a4f3a174b8b48f6276
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651801"
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a>Instrukcje: wyświetlanie strony sieci Web za pomocą kontrolki LinkLabel formularzy systemu Windows (Visual Basic)
W tym przykładzie wyświetla stronę sieci Web w domyślnej przeglądarce, gdy użytkownik kliknie formularze Windows <xref:System.Windows.Forms.LinkLabel> kontroli.  
  
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
  
- Formularz Windows o nazwie `Form1`.  
  
- A <xref:System.Windows.Forms.LinkLabel> formantu o nazwie `LinkLabel1`.  
  
- Aktywne połączenie z Internetem.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Wywołanie <xref:System.Diagnostics.Process.Start%2A> metoda wymaga pełnego zaufania. Aby uzyskać więcej informacji, zobacz <xref:System.Security.SecurityException>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.LinkLabel>
- [LinkLabel, kontrolka](linklabel-control-windows-forms.md)
