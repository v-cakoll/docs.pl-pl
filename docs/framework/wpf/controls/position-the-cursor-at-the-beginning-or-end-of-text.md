---
title: Jak umieścić kursor na początku lub na końcu tekstu w formancie TextBox
description: Dowiedz się, jak umieścić kursor na początku lub na końcu zawartości tekstowej kontrolki TextBox Windows Presentation Foundation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: afe8b11d032b5d61fa91cbf324f02cd8415d2ea8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167518"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a>Jak umieścić kursor na początku lub na końcu tekstu w formancie TextBox
Ten przykład pokazuje, jak umieścić kursor na początku lub na końcu zawartości tekstowej <xref:System.Windows.Controls.TextBox> formantu.  
  
## <a name="example"></a>Przykład  
 Poniższy [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kod opisuje <xref:System.Windows.Controls.TextBox> formant i przypisuje mu nazwę.  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a>Przykład  
 Aby ustawić położenie kursora na początku zawartości <xref:System.Windows.Controls.TextBox> kontrolki, wywołaj <xref:System.Windows.Controls.TextBox.Select%2A> metodę i określ pozycję początkową wyboru równą 0 i wybierz wartość 0.  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a>Przykład  
 Aby ustawić położenie kursora na końcu zawartości <xref:System.Windows.Controls.TextBox> kontrolki, należy wywołać <xref:System.Windows.Controls.TextBox.Select%2A> metodę i określić pozycję początkową wyboru równą długości zawartości tekstowej, a wybór wynosi 0.  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a>Zobacz także

- [TextBox — Przegląd](textbox-overview.md)
- [RichTextBox — Przegląd](richtextbox-overview.md)
