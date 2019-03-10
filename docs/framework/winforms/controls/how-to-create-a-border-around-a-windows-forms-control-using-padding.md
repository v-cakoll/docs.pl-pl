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
ms.openlocfilehash: 66748eef299c9175814fb130a7eda359c5de0546
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720309"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>Instrukcje: Tworzenie obramowania Wokoło formularze Windows kontrolować za pomocą wypełnienia
Poniższy przykład kodu pokazuje, jak utworzyć obramowanie lub konspektu wokół <xref:System.Windows.Forms.RichTextBox> kontroli. W przykładzie ustawiono wartość <xref:System.Windows.Forms.Panel> kontrolki <xref:System.Windows.Forms.Padding> właściwości to 5, a zestawy <xref:System.Windows.Forms.Control.Dock%2A> właściwość elementu podrzędnego <xref:System.Windows.Forms.RichTextBox> kontrolę <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Control.BackColor%2A> z <xref:System.Windows.Forms.Panel> kontrolki jest ustawiona na <xref:System.Drawing.Color.Blue%2A>, co powoduje utworzenie niebieskie obramowanie wokół <xref:System.Windows.Forms.RichTextBox> kontroli.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.Padding#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.Padding>
- [Margines i wypełnienie w kontrolkach formularzy Windows Forms](margin-and-padding-in-windows-forms-controls.md)
