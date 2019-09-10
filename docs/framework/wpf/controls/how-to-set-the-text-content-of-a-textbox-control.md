---
title: 'Instrukcje: Ustawianie zawartości tekstu dla kontrolki TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 2e2bc70b108991fd4e3c138bfac5bff942173e33
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856112"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Instrukcje: Ustawianie zawartości tekstu dla kontrolki TextBox

Ten przykład pokazuje, jak użyć <xref:System.Windows.Controls.TextBox.Text%2A> właściwości, aby ustawić początkową zawartość <xref:System.Windows.Controls.TextBox> tekstu kontrolki.

> [!NOTE]
> <xref:System.Windows.Markup.ContentPropertyAttribute> <xref:System.Windows.Controls.TextBox> `<TextBox.Text>` <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox.Text%2A> Mimo że [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] wersja przykładu może używać tagów wokół tekstu zawartości przycisku, nie jest to konieczne, ponieważ stosuje atrybut do właściwości . Aby uzyskać więcej informacji, zobacz [XAML — Omówienie (WPF)](../advanced/xaml-overview-wpf.md).

## <a name="example"></a>Przykład

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>Przykład

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>Zobacz także

- [TextBox — omówienie](textbox-overview.md)
- [RichTextBox — omówienie](richtextbox-overview.md)
