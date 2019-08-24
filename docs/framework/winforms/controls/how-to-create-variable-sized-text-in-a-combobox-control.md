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
ms.openlocfilehash: acc5ee47536772d98fcfe98849335933c24a41d7
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015907"
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a><span data-ttu-id="86dd7-102">Instrukcje: tworzenie tekstu o zmiennym rozmiarze w kontrolce ComboBox</span><span class="sxs-lookup"><span data-stu-id="86dd7-102">How to: Create Variable Sized Text in a ComboBox Control</span></span>
<span data-ttu-id="86dd7-103">Ten przykład ilustruje niestandardowy rysunek tekstu w <xref:System.Windows.Forms.ComboBox> kontrolce.</span><span class="sxs-lookup"><span data-stu-id="86dd7-103">This example demonstrates custom drawing of text in a <xref:System.Windows.Forms.ComboBox> control.</span></span> <span data-ttu-id="86dd7-104">Gdy element spełnia określone kryteria, jest rysowany przy użyciu większej czcionki i kolor czerwony.</span><span class="sxs-lookup"><span data-stu-id="86dd7-104">When an item meets a certain criteria, it is drawn in a larger font and turned red.</span></span>

## <a name="example"></a><span data-ttu-id="86dd7-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="86dd7-105">Example</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="86dd7-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="86dd7-106">Compiling the Code</span></span>
 <span data-ttu-id="86dd7-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="86dd7-107">This example requires:</span></span>

- <span data-ttu-id="86dd7-108">Formularz systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="86dd7-108">A Windows form.</span></span>

- <span data-ttu-id="86dd7-109">Kontrolka o `ListBox1` nazwie<xref:System.Windows.Forms.ComboBox.Items%2A> z trzema elementami we właściwości. <xref:System.Windows.Forms.ComboBox></span><span class="sxs-lookup"><span data-stu-id="86dd7-109">A <xref:System.Windows.Forms.ComboBox> control named `ListBox1` with three items in the <xref:System.Windows.Forms.ComboBox.Items%2A> property.</span></span> <span data-ttu-id="86dd7-110">W tym przykładzie trzy elementy mają nazwę `"One", Two", and Three"`.</span><span class="sxs-lookup"><span data-stu-id="86dd7-110">In this example, the three items are named `"One", Two", and Three"`.</span></span> <span data-ttu-id="86dd7-111">Właściwość musi być ustawiona na <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>wartość. `ComboBox1` <xref:System.Windows.Forms.ComboBox.DrawMode%2A></span><span class="sxs-lookup"><span data-stu-id="86dd7-111">The <xref:System.Windows.Forms.ComboBox.DrawMode%2A> property of `ComboBox1` must be set to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="86dd7-112">Ta technika ma również zastosowanie do <xref:System.Windows.Forms.ListBox> kontrolki — można <xref:System.Windows.Forms.ListBox> zastąpić dla <xref:System.Windows.Forms.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="86dd7-112">This technique is also applicable to the <xref:System.Windows.Forms.ListBox> control — you can substitute a <xref:System.Windows.Forms.ListBox> for the <xref:System.Windows.Forms.ComboBox>.</span></span>

- <span data-ttu-id="86dd7-113">Odwołania do <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw <xref:System.Drawing?displayProperty=nameWithType> i.</span><span class="sxs-lookup"><span data-stu-id="86dd7-113">References to the <xref:System.Windows.Forms?displayProperty=nameWithType> and <xref:System.Drawing?displayProperty=nameWithType> namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="86dd7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86dd7-114">See also</span></span>

- <xref:System.Windows.Forms.ComboBox.DrawItem>
- <xref:System.Windows.Forms.DrawItemEventArgs>
- <xref:System.Windows.Forms.ComboBox.MeasureItem>
- [<span data-ttu-id="86dd7-115">Kontrolki z wbudowaną obsługą rysowania przez właściciela</span><span class="sxs-lookup"><span data-stu-id="86dd7-115">Controls with Built-In Owner-Drawing Support</span></span>](controls-with-built-in-owner-drawing-support.md)
- [<span data-ttu-id="86dd7-116">ListBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="86dd7-116">ListBox Control</span></span>](listbox-control-windows-forms.md)
- [<span data-ttu-id="86dd7-117">ComboBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="86dd7-117">ComboBox Control</span></span>](combobox-control-windows-forms.md)
