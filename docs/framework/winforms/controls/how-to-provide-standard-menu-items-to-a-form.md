---
title: 'Instrukcje: zapewnianie elementów menu standardowego dla formularza'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- menu items [Windows Forms], standard
- ToolStrip control [Windows Forms]
ms.assetid: 75db9126-e70c-4e81-921d-b83c0a4a9f50
ms.openlocfilehash: bb101c57cfb453e0419357741c5cf42dc29221b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086718"
---
# <a name="how-to-provide-standard-menu-items-to-a-form"></a>Instrukcje: zapewnianie elementów menu standardowego dla formularza
Możesz podać standardowe menu formularzy przy użyciu <xref:System.Windows.Forms.MenuStrip> kontroli.  
  
 Brak zaawansowaną obsługę dla tej funkcji w programie Visual Studio.  
  
 Zobacz też [instruktażu: Zapewnianie elementów Menu standardowego dla formularza](walkthrough-providing-standard-menu-items-to-a-form.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób używania <xref:System.Windows.Forms.MenuStrip> formantu, aby utworzyć formularz przy użyciu standardowego menu. Opcje elementu menu są wyświetlane w <xref:System.Windows.Forms.StatusStrip> kontroli.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [MenuStrip, kontrolka](menustrip-control-windows-forms.md)
