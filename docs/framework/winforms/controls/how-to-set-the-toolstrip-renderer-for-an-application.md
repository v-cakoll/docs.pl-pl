---
title: 'Instrukcje: Ustawienie modułu renderowania ToolStrip dla aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Renderer property [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], customizing
ms.assetid: 46acef3e-9844-4ae8-9a2e-3006fe99cadf
ms.openlocfilehash: 2eaa917ff903c1d9e1579ac9c9caa3f3db516afb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577221"
---
# <a name="how-to-set-the-toolstrip-renderer-for-an-application"></a>Instrukcje: Ustawienie modułu renderowania ToolStrip dla aplikacji
Można dostosować wygląd Twojego <xref:System.Windows.Forms.ToolStrip> kontroluje indywidualnie lub dla wszystkich <xref:System.Windows.Forms.ToolStrip> formantów w aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób selektywnego stosowania niestandardowego modułu renderowania do <xref:System.Windows.Forms.ToolStrip> kontroli i <xref:System.Windows.Forms.MenuStrip> kontroli.  
  
 Aby wykorzystać ten przykład kodu, skompiluj i uruchom aplikację, a następnie wybierz powodującym niestandardowe z zakresu <xref:System.Windows.Forms.ComboBox> kontroli. Kliknij przycisk **Zastosuj** na ustawienie modułu renderowania.  
  
 Aby wyświetlić renderowanie elementów niestandardowych menu, wybierz <xref:System.Windows.Forms.MenuStrip> opcję <xref:System.Windows.Forms.ComboBox> sterowania, kliknij przycisk **Zastosuj**, a następnie otwórz **pliku** elementu menu.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#70)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#70)]  
  
 Ustaw <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> właściwości do stosowania niestandardowego modułu renderowania dla wszystkich <xref:System.Windows.Forms.ToolStrip> formantów w aplikacji.  
  
 Ustaw <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> właściwości do stosowania niestandardowego modułu renderowania z określoną osobą <xref:System.Windows.Forms.ToolStrip> kontroli.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
 Aby uzyskać informacje o tworzeniu tego przykładu z wiersza polecenia dla programu visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [jak: Skompilować i uruchomić przykładowy kod pełną Windows Forms przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- [ToolStrip, kontrolka](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
