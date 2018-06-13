---
title: Jak umieścić kursor na początku lub na końcu tekstu w formancie TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: 79ecf1d5dccee0dacef8e288c0c2e044334e65d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556041"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a>Jak umieścić kursor na początku lub na końcu tekstu w formancie TextBox
W tym przykładzie pokazano, jak umieść kursor na początku lub na końcu zawartość tekstową <xref:System.Windows.Controls.TextBox> formantu.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kod opisuje <xref:System.Windows.Controls.TextBox> kontroli i przypisuje mu nazwę.  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a>Przykład  
 Aby umieść kursor na początku zawartość <xref:System.Windows.Controls.TextBox> kontrolować, wywołaj <xref:System.Windows.Controls.TextBox.Select%2A> — metoda i określ uruchamiania zaznaczenie pozycji 0, a długość wybór 0.  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a>Przykład  
 Aby umieść kursor na końcu zawartości <xref:System.Windows.Controls.TextBox> kontrolować, wywołaj <xref:System.Windows.Controls.TextBox.Select%2A> — metoda i określ pozycja początkowa wybranego równy długości zawartości tekstu i wybór długość 0.  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a>Zobacz też  
 [TextBox — omówienie](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox — omówienie](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
