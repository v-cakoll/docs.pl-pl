---
title: 'Porady: tworzenie tekstu o zmiennym rozmiarze w formancie ComboBox'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- text [Windows Forms], drawing in combo boxes
- examples [Windows Forms], ComboBox control
- combo boxes [Windows Forms], drawing text
- ComboBox control [Windows Forms], examples [C#]
- ComboBox control [Windows Forms], drawing custom text
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a6f0dcfd24414ef868a1a5414af4fcde1b9a14ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a>Porady: tworzenie tekstu o zmiennym rozmiarze w formancie ComboBox
W tym przykładzie przedstawiono rysowanie niestandardowego tekstu w <xref:System.Windows.Forms.ComboBox> formantu. Jeśli element spełnia określone kryteria, jest rysowana w większej czcionki i włączone czerwony.  
  
## <a name="example"></a>Przykład  
  
```vb  
Private Sub ComboBox1_MeasureItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.MeasureItemEventArgs) Handles ComboBox1.MeasureItem  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
    Dim siText As SizeF  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), _  
lFont)  
    Else  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), bFont)  
    End If  
  
    e.ItemHeight = siText.Height  
    e.ItemWidth = siText.Width  
End Sub  
  
Private Sub ComboBox1_DrawItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.DrawItemEventArgs) Handles ComboBox1.DrawItem  
    Dim g As Graphics = e.Graphics  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        g.DrawString(ComboBox1.Items.Item(e.Index), lfont, Brushes.Red, _  
e.Bounds.X, e.Bounds.Y)  
    Else  
        g.DrawString(ComboBox1.Items.Item(e.Index), bFont, Brushes.Black, e.Bounds.X, e.Bounds.Y)  
    End If  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Formularz systemu Windows.  
  
-   A <xref:System.Windows.Forms.ComboBox> formantu o nazwie `ListBox1` z trzema elementami w <xref:System.Windows.Forms.ComboBox.Items%2A> właściwości. W tym przykładzie trzy elementy są nazywane `"One", Two", and Three"`. <xref:System.Windows.Forms.ComboBox.DrawMode%2A> Właściwość `ComboBox1` musi mieć ustawioną <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.  
  
    > [!NOTE]
    >  Ta technika mają też zastosowanie do <xref:System.Windows.Forms.ListBox> kontroli — można zastąpić <xref:System.Windows.Forms.ListBox> dla <xref:System.Windows.Forms.ComboBox>.  
  
-   Odwołuje się do <xref:System.Windows.Forms?displayProperty=nameWithType> i <xref:System.Drawing?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ComboBox.DrawItem>  
 <xref:System.Windows.Forms.DrawItemEventArgs>  
 <xref:System.Windows.Forms.ComboBox.MeasureItem>  
 [Formanty z wbudowaną obsługą rysowania przez właściciela](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)  
 [ListBox — formant](../../../../docs/framework/winforms/controls/listbox-control-windows-forms.md)  
 [ComboBox — formant](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)
