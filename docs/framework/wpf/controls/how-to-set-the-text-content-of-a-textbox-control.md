---
title: Jak ustawić zawartość tekstu dla formantu TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 9b16f2d99295a28725255361b0be3ef7f4245fd2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459304"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Jak ustawić zawartość tekstu dla formantu TextBox

Ten przykład pokazuje, jak użyć właściwości <xref:System.Windows.Controls.TextBox.Text%2A> do ustawienia początkowej zawartości tekstowej kontrolki <xref:System.Windows.Controls.TextBox>.

> [!NOTE]
> Mimo że [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] wersja przykładu może używać tagów `<TextBox.Text>` wokół tekstu zawartości <xref:System.Windows.Controls.TextBox> poszczególnych przycisków, nie jest to konieczne, ponieważ <xref:System.Windows.Controls.TextBox> stosuje atrybut <xref:System.Windows.Markup.ContentPropertyAttribute> do właściwości <xref:System.Windows.Controls.TextBox.Text%2A>. Aby uzyskać więcej informacji, zobacz [XAML — Omówienie (WPF)](../../../desktop-wpf/fundamentals/xaml.md).

## <a name="example"></a>Przykład

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>Przykład

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>Zobacz także

- [TextBox — omówienie](textbox-overview.md)
- [RichTextBox — omówienie](richtextbox-overview.md)
