---
title: 'Instrukcje: Tworzenie tekstu o zmiennym rozmiarze w formancie ComboBox'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- text [Windows Forms], drawing in combo boxes
- examples [Windows Forms], ComboBox control
- combo boxes [Windows Forms], drawing text
- ComboBox control [Windows Forms], examples [C#]
- ComboBox control [Windows Forms], drawing custom text
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
ms.openlocfilehash: 2a9f6e8a1c96c2a9bf9e56c1c6acefc4181a18dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526993"
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a>Instrukcje: Tworzenie tekstu o zmiennym rozmiarze w formancie ComboBox
W tym przykładzie przedstawiono rysowanie niestandardowego tekstu w <xref:System.Windows.Forms.ComboBox> kontroli. Jeśli element spełnia określone kryteria, jest rysowane w większej czcionki i włączone czerwony.  
  
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
  
-   Formularz Windows.  
  
-   A <xref:System.Windows.Forms.ComboBox> formantu o nazwie `ListBox1` z trzema elementami w <xref:System.Windows.Forms.ComboBox.Items%2A> właściwości. W tym przykładzie trzy elementy są nazywane `"One", Two", and Three"`. <xref:System.Windows.Forms.ComboBox.DrawMode%2A> Właściwość `ComboBox1` musi być równa <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.  
  
    > [!NOTE]
    >  Ta metoda ma również zastosowanie do <xref:System.Windows.Forms.ListBox> kontroli — można zastąpić <xref:System.Windows.Forms.ListBox> dla <xref:System.Windows.Forms.ComboBox>.  
  
-   Odwołuje się do <xref:System.Windows.Forms?displayProperty=nameWithType> i <xref:System.Drawing?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ComboBox.DrawItem>
- <xref:System.Windows.Forms.DrawItemEventArgs>
- <xref:System.Windows.Forms.ComboBox.MeasureItem>
- [Kontrolki z wbudowaną obsługą rysowania przez właściciela](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)
- [ListBox, kontrolka](../../../../docs/framework/winforms/controls/listbox-control-windows-forms.md)
- [ComboBox, kontrolka](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)
