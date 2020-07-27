---
title: Jak ustawić ostrość w formancie TextBox
description: Dowiedz się, jak używać metody focus do ustawiania fokusu na Windows Presentation Foundation formancie TextBox.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
ms.openlocfilehash: e107c22a3c5b701e02cbc8506d10fa35ee15c79d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168064"
---
# <a name="how-to-set-focus-in-a-textbox-control"></a>Jak ustawić ostrość w formancie TextBox
Ten przykład pokazuje, jak używać <xref:System.Windows.UIElement.Focus%2A> metody do ustawiania fokusu na <xref:System.Windows.Controls.TextBox> formancie.  
  
## <a name="example"></a>Przykład  
 W poniższym [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie opisano prostą <xref:System.Windows.Controls.TextBox> kontrolkę o nazwie *tbFocusMe*  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wywołuje metodę, <xref:System.Windows.UIElement.Focus%2A> Aby ustawić fokus na <xref:System.Windows.Controls.TextBox> kontrolce o nazwie *tbFocusMe*.  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.UIElement.Focusable%2A>
- <xref:System.Windows.UIElement.IsFocused%2A>
- [TextBox — Przegląd](textbox-overview.md)
- [RichTextBox — Przegląd](richtextbox-overview.md)
