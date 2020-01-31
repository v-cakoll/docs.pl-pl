---
title: Utwórz obramowanie wokół kontrolki przy użyciu dopełnienia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- margins
- controls [Windows Forms], Margin property
- padding [Windows Forms], Windows Forms
- controls [Windows Forms], Padding property
- controls [Windows Forms], outlining
- Padding property [Windows Forms]
- margins [Windows Forms], Windows Forms
- Margin property [Windows Forms]
ms.assetid: bac7ed4d-a163-4259-98bd-155a36345890
ms.openlocfilehash: 114186ab5784cf892cb01e9fe2648ce22cecc4b7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742189"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>Porady: tworzenie obramowania wokoło formantu formularzy systemu Windows za pomocą wypełnienia
Poniższy przykład kodu pokazuje, jak utworzyć obramowanie lub kontur wokół kontrolki <xref:System.Windows.Forms.RichTextBox>. Przykład ustawia wartość właściwości <xref:System.Windows.Forms.Padding> kontrolki <xref:System.Windows.Forms.Panel> na 5 i ustawia właściwość <xref:System.Windows.Forms.Control.Dock%2A> podrzędnej kontrolki <xref:System.Windows.Forms.RichTextBox> na <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Control.BackColor%2A> kontrolki <xref:System.Windows.Forms.Panel> jest ustawiona na <xref:System.Drawing.Color.Blue%2A>, która tworzy niebieskie obramowanie wokół kontrolki <xref:System.Windows.Forms.RichTextBox>.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.Padding#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Padding>
- [Margines i wypełnienie w kontrolkach formularzy Windows Forms](margin-and-padding-in-windows-forms-controls.md)
