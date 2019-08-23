---
title: 'Instrukcje: tworzenie tekstu o zmiennym rozmiarze w kontrolce ComboBox'
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
ms.openlocfilehash: 7c0dc40f6cac0af1f88e72089865caa3a17fcf2a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914745"
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a>Instrukcje: tworzenie tekstu o zmiennym rozmiarze w kontrolce ComboBox
Ten przykład ilustruje niestandardowy rysunek tekstu w <xref:System.Windows.Forms.ComboBox> kontrolce. Gdy element spełnia określone kryteria, jest rysowany przy użyciu większej czcionki i kolor czerwony.  
  
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
  
- Formularz systemu Windows.  
  
- Kontrolka o `ListBox1` nazwie<xref:System.Windows.Forms.ComboBox.Items%2A> z trzema elementami we właściwości. <xref:System.Windows.Forms.ComboBox> W tym przykładzie trzy elementy mają nazwę `"One", Two", and Three"`. Właściwość musi być ustawiona na <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>wartość. `ComboBox1` <xref:System.Windows.Forms.ComboBox.DrawMode%2A>  
  
    > [!NOTE]
    > Ta technika ma również zastosowanie do <xref:System.Windows.Forms.ListBox> kontrolki — można <xref:System.Windows.Forms.ListBox> zastąpić dla <xref:System.Windows.Forms.ComboBox>.  
  
- Odwołania do <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw <xref:System.Drawing?displayProperty=nameWithType> i.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ComboBox.DrawItem>
- <xref:System.Windows.Forms.DrawItemEventArgs>
- <xref:System.Windows.Forms.ComboBox.MeasureItem>
- [Kontrolki z wbudowaną obsługą rysowania przez właściciela](controls-with-built-in-owner-drawing-support.md)
- [ListBox, kontrolka](listbox-control-windows-forms.md)
- [ComboBox, kontrolka](combobox-control-windows-forms.md)
