---
title: 'Instrukcje: Ustawianie fokusu w kontrolce TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
ms.openlocfilehash: f4ba367ea9bdfcd6dbab7a5015472ec33adfe46f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115508"
---
# <a name="how-to-set-focus-in-a-textbox-control"></a>Instrukcje: Ustawianie fokusu w kontrolce TextBox
W tym przykładzie pokazano, jak używać <xref:System.Windows.UIElement.Focus%2A> metodę, aby ustawić fokus na <xref:System.Windows.Controls.TextBox> kontroli.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie przedstawiono prosty <xref:System.Windows.Controls.TextBox> formantu o nazwie *tbFocusMe*  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wywołuje <xref:System.Windows.UIElement.Focus%2A> metodę, aby ustawić fokus na <xref:System.Windows.Controls.TextBox> formant o nazwie *tbFocusMe*.  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.UIElement.Focusable%2A>
- <xref:System.Windows.UIElement.IsFocused%2A>
- [TextBox — omówienie](textbox-overview.md)
- [RichTextBox — omówienie](richtextbox-overview.md)
