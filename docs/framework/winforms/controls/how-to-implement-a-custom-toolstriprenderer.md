---
title: 'Porady: implementowanie niestandardowego elementu ToolStripRenderer'
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
- toolbars [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c66fd3f7-2377-4553-8f1b-006527f08f32
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ecd8953d6fe2e4a22e6c3b5fcc294855ef3a1c8a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a>Porady: implementowanie niestandardowego elementu ToolStripRenderer
Można dostosować wygląd <xref:System.Windows.Forms.ToolStrip> kontroli dzięki implementacji klasy, która jest pochodną <xref:System.Windows.Forms.ToolStripRenderer>. Daje to możliwość tworzenia wyglądu, która różni się od wygląd podane <xref:System.Windows.Forms.ToolStripProfessionalRenderer> i <xref:System.Windows.Forms.ToolStripSystemRenderer> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób zaimplementowania niestandardowego <xref:System.Windows.Forms.ToolStripRenderer> klasy. W tym przykładzie `GridStrip` kontroli implementuje układanki przedłużanie kafelka, dzięki czemu użytkownik może przechodzić Kafelki w układzie tabeli do utworzenia obrazu. Niestandardowy <xref:System.Windows.Forms.ToolStrip> rozmieszcza kontroli jego <xref:System.Windows.Forms.ToolStripButton> formantów w układzie siatki. Układ zawiera jedną komórkę pusta, do którego użytkownik może slajd kafelka sąsiadujących ze sobą przy użyciu operacji przeciągania i upuszczania. Kafelki, które użytkownik może przenieść są wyróżnione.  
  
 `GridStripRenderer` Klasy dostosowuje trzy aspekty `GridStrip` wygląd formantu:  
  
-   `GridStrip`obramowania  
  
-   <xref:System.Windows.Forms.ToolStripButton>obramowania  
  
-   <xref:System.Windows.Forms.ToolStripButton>Obraz  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/CS/GridStrip.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/VB/GridStrip.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów System.Drawing i System.Windows.Forms.  
  
 Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.StatusStrip>  
 [ToolStrip — formant](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
