---
title: 'Instrukcje: Tworzenie obramowania Wokoło formularze Windows kontrolować za pomocą wypełnienia'
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
ms.openlocfilehash: 26d5dd086828df94c1ea0808d2f72723344b0702
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614657"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>Instrukcje: Tworzenie obramowania Wokoło formularze Windows kontrolować za pomocą wypełnienia
Poniższy przykład kodu pokazuje, jak utworzyć obramowanie lub konspektu wokół <xref:System.Windows.Forms.RichTextBox> kontroli. W przykładzie ustawiono wartość <xref:System.Windows.Forms.Panel> kontrolki <xref:System.Windows.Forms.Padding> właściwości to 5, a zestawy <xref:System.Windows.Forms.Control.Dock%2A> właściwość elementu podrzędnego <xref:System.Windows.Forms.RichTextBox> kontrolę <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Control.BackColor%2A> z <xref:System.Windows.Forms.Panel> kontrolki jest ustawiona na <xref:System.Drawing.Color.Blue%2A>, co powoduje utworzenie niebieskie obramowanie wokół <xref:System.Windows.Forms.RichTextBox> kontroli.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.Padding#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.Padding>
- [Margines i wypełnienie w kontrolkach formularzy Windows Forms](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)
