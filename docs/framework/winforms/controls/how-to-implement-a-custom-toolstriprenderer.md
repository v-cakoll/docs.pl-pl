---
title: 'Porady: implementowanie niestandardowego elementu ToolStripRenderer'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c66fd3f7-2377-4553-8f1b-006527f08f32
ms.openlocfilehash: 91c04ba41a02c7c620c2f6c621505a19e0302c19
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398118"
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a>Porady: implementowanie niestandardowego elementu ToolStripRenderer
Można dostosować wygląd <xref:System.Windows.Forms.ToolStrip> kontroli poprzez implementację klasy, która pochodzi od klasy <xref:System.Windows.Forms.ToolStripRenderer>. Daje to możliwość tworzenia wrażenie, że różni się od wyglądem, pod warunkiem <xref:System.Windows.Forms.ToolStripProfessionalRenderer> i <xref:System.Windows.Forms.ToolStripSystemRenderer> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób implementacji niestandardowego <xref:System.Windows.Forms.ToolStripRenderer> klasy. W tym przykładzie `GridStrip` kontrolka implementuje układanki przedłużanie Kafelek, który umożliwia użytkownikowi przenoszenie kafelków w układzie tabeli w celu utworzenia obrazu. Niestandardowy <xref:System.Windows.Forms.ToolStrip> rozmieszcza kontroli jego <xref:System.Windows.Forms.ToolStripButton> formantów w układzie siatki. Układ zawiera jedną pustą komórkę, do którego użytkownik może slajd sąsiadujących Kafelek przy użyciu operacji przeciągania i upuszczania. Kafelki, które użytkownik może przenieść są wyróżnione.  
  
 `GridStripRenderer` Klasy dostosowuje trzy aspekty `GridStrip` wygląd formantu:  
  
-   `GridStrip` Obramowanie  
  
-   <xref:System.Windows.Forms.ToolStripButton> Obramowanie  
  
-   <xref:System.Windows.Forms.ToolStripButton> Obraz  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/CS/GridStrip.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/VB/GridStrip.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów System.Drawing i pozycję System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.StatusStrip>  
 [ToolStrip, kontrolka](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
