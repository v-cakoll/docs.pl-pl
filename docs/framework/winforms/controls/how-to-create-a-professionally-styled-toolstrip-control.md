---
title: 'Porady: tworzenie profesjonalnego formantu ToolStrip'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ab44faf9e95a2ff5f1957bd6f46fc62944a4f44
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a>Porady: tworzenie profesjonalnego formantu ToolStrip
Umożliwia aplikacji <xref:System.Windows.Forms.ToolStrip> steruje profesjonalny wygląd i zachowanie (wygląd i działanie) przez pisanie własnych klas pochodnych <xref:System.Windows.Forms.ToolStripProfessionalRenderer> typu.  
  
 Brak kompleksową obsługę tej funkcji w [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].  
  
 Zobacz [wskazówki: tworzenie profesjonalnego formantu ToolStrip](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób użycia <xref:System.Windows.Forms.ToolStrip> służy do tworzenia złożonych kontrolek, które symuluje **okienka nawigacji** udostępniane przez Microsoft Outlook®.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów System.Drawing i System.Windows.Forms.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [wskazówki: tworzenie profesjonalnego styl formantu ToolStrip](http://msdn.microsoft.com/library/ms233664\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [ToolStrip, kontrolka](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [Instrukcje: zapewnianie elementów menu standardowego dla formularza](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
