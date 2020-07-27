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
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="ee6c0-103">Jak ustawić zawartość tekstu dla formantu TextBox</span><span class="sxs-lookup"><span data-stu-id="ee6c0-103">How to: Set the Text Content of a TextBox Control</span></span>

<span data-ttu-id="ee6c0-104">Ten przykład pokazuje, jak użyć <xref:System.Windows.Controls.TextBox.Text%2A> właściwości, aby ustawić początkową zawartość tekstu <xref:System.Windows.Controls.TextBox> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ee6c0-104">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>

> [!NOTE]
> <span data-ttu-id="ee6c0-105">Mimo że [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] wersja przykładu może używać `<TextBox.Text>` tagów wokół tekstu <xref:System.Windows.Controls.TextBox> zawartości przycisku, nie jest to konieczne, ponieważ <xref:System.Windows.Controls.TextBox> stosuje <xref:System.Windows.Markup.ContentPropertyAttribute> atrybut do <xref:System.Windows.Controls.TextBox.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ee6c0-105">Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="ee6c0-106">Aby uzyskać więcej informacji, zobacz [XAML — Omówienie (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="ee6c0-106">For more information, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span></span>

## <a name="example"></a><span data-ttu-id="ee6c0-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee6c0-107">Example</span></span>

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a><span data-ttu-id="ee6c0-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee6c0-108">Example</span></span>

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a><span data-ttu-id="ee6c0-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee6c0-109">See also</span></span>

- [<span data-ttu-id="ee6c0-110">TextBox — Przegląd</span><span class="sxs-lookup"><span data-stu-id="ee6c0-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="ee6c0-111">RichTextBox — Przegląd</span><span class="sxs-lookup"><span data-stu-id="ee6c0-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
