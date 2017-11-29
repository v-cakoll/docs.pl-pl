---
title: "Porady: użycie właściwości Spring interaktywnie w StatusStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
- status bars [Windows Forms], examples
- Spring property [Windows Forms]
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d51690c4e31e391cdba7980ee3a23771c92c2fca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a>Porady: użycie właściwości Spring interaktywnie w StatusStrip
Można użyć <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> ustaw dla właściwości <xref:System.Windows.Forms.ToolStripStatusLabel> kontroli w <xref:System.Windows.Forms.StatusStrip> formantu. <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> Właściwość określa, czy <xref:System.Windows.Forms.ToolStripStatusLabel> formant automatycznie wypełnienia dostępnego miejsca na <xref:System.Windows.Forms.StatusStrip> formantu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób użycia <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> ustaw dla właściwości <xref:System.Windows.Forms.ToolStripStatusLabel> kontroli w <xref:System.Windows.Forms.StatusStrip> formantu. <xref:System.Windows.Forms.ToolStripItem.Click> Wyłącznie wykonuje program obsługi zdarzeń — operacji (XOR), aby przełączyć wartość lub <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> właściwości.  
  
 Aby użyć w tym przykładzie kodu, skompiluj i uruchom aplikację, a następnie kliknij **bliski (Spring)** na <xref:System.Windows.Forms.StatusStrip> formantu, aby przełączyć wartość <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> właściwości.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów System.Design, System.Drawing i System.Windows.Forms.  
  
 Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [ToolStrip — formant](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
