---
title: Jak ustawić zawartość tekstu dla formantu TextBox
description: Dowiedz się, jak ustawić początkową zawartość tekstową kontrolki TextBox Windows Presentation Foundation za pomocą właściwości text.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 41efb69e297b3c6fdb1203c358dcc72d7a9f806f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168051"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Jak ustawić zawartość tekstu dla formantu TextBox

Ten przykład pokazuje, jak użyć <xref:System.Windows.Controls.TextBox.Text%2A> właściwości, aby ustawić początkową zawartość tekstu <xref:System.Windows.Controls.TextBox> kontrolki.

> [!NOTE]
> Mimo że [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] wersja przykładu może używać `<TextBox.Text>` tagów wokół tekstu <xref:System.Windows.Controls.TextBox> zawartości przycisku, nie jest to konieczne, ponieważ <xref:System.Windows.Controls.TextBox> stosuje <xref:System.Windows.Markup.ContentPropertyAttribute> atrybut do <xref:System.Windows.Controls.TextBox.Text%2A> właściwości. Aby uzyskać więcej informacji, zobacz [XAML — Omówienie (WPF)](../../../desktop-wpf/fundamentals/xaml.md).

## <a name="example"></a>Przykład

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>Przykład

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>Zobacz także

- [TextBox — Przegląd](textbox-overview.md)
- [RichTextBox — Przegląd](richtextbox-overview.md)
