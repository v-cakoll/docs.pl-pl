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
ms.openlocfilehash: da91e27b804d649f5b8010bc9d7c074425be26f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212196"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="e20e9-102">Instrukcje: Ustawianie zawartości tekstu dla kontrolki TextBox</span><span class="sxs-lookup"><span data-stu-id="e20e9-102">How to: Set the Text Content of a TextBox Control</span></span>
<span data-ttu-id="e20e9-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Controls.TextBox.Text%2A> właściwość umożliwiająca ustawienie zawartość tekstową początkowej <xref:System.Windows.Controls.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="e20e9-103">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 <span data-ttu-id="e20e9-104">**Uwaga** mimo że [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] wersja przykładu można użyć `<TextBox.Text>` tagi wokół tekstu każdy przycisk <xref:System.Windows.Controls.TextBox> zawartości, nie jest konieczne, ponieważ <xref:System.Windows.Controls.TextBox> stosuje <xref:System.Windows.Markup.ContentPropertyAttribute> atrybutu <xref:System.Windows.Controls.TextBox.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e20e9-104">**Note** Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="e20e9-105">Aby uzyskać więcej informacji, zobacz [Przegląd XAML (WPF)](../advanced/xaml-overview-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="e20e9-105">For more information, see [XAML Overview (WPF)](../advanced/xaml-overview-wpf.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e20e9-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e20e9-106">Example</span></span>  
 [!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## <a name="example"></a><span data-ttu-id="e20e9-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="e20e9-107">Example</span></span>  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## <a name="see-also"></a><span data-ttu-id="e20e9-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e20e9-108">See also</span></span>

- [<span data-ttu-id="e20e9-109">TextBox — Przegląd</span><span class="sxs-lookup"><span data-stu-id="e20e9-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="e20e9-110">RichTextBox — Przegląd</span><span class="sxs-lookup"><span data-stu-id="e20e9-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
