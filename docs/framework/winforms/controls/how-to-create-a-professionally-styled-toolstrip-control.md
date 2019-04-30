---
title: 'Instrukcje: tworzenie profesjonalnej kontrolki ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
ms.openlocfilehash: 6da6e113867efed79dfcd02f3b89ee1f9ae13c4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746670"
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a>Instrukcje: tworzenie profesjonalnej kontrolki ToolStrip
Możesz nadać aplikacji <xref:System.Windows.Forms.ToolStrip> kontroluje profesjonalny wygląd i zachowanie (wygląd i działanie), pisząc własne klasy pochodzącej od <xref:System.Windows.Forms.ToolStripProfessionalRenderer> typu.  
  
 Brak zaawansowaną obsługę dla tej funkcji w programie Visual Studio.  
  
 Zobacz [instruktażu: Tworzenie profesjonalnego formantu ToolStrip](walkthrough-creating-a-professionally-styled-toolstrip-control.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób używania <xref:System.Windows.Forms.ToolStrip> formantów, aby utworzyć formant złożony, który naśladuje **okienka nawigacji** udostępniane przez Microsoft Outlook®.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów System.Drawing i pozycję System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [instruktażu: Tworzenie profesjonalnego formantu ToolStrip](walkthrough-creating-a-professionally-styled-toolstrip-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [ToolStrip, kontrolka](toolstrip-control-windows-forms.md)
- [Instrukcje: Zapewnianie elementów Menu standardowego dla formularza](how-to-provide-standard-menu-items-to-a-form.md)
