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
# <a name="how-to-set-focus-in-a-textbox-control"></a><span data-ttu-id="b8e47-102">Instrukcje: Ustawianie fokusu w kontrolce TextBox</span><span class="sxs-lookup"><span data-stu-id="b8e47-102">How to: Set Focus in a TextBox Control</span></span>
<span data-ttu-id="b8e47-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.UIElement.Focus%2A> metodę, aby ustawić fokus na <xref:System.Windows.Controls.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="b8e47-103">This example shows how to use the <xref:System.Windows.UIElement.Focus%2A> method to set focus on a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8e47-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8e47-104">Example</span></span>  
 <span data-ttu-id="b8e47-105">Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie przedstawiono prosty <xref:System.Windows.Controls.TextBox> formantu o nazwie *tbFocusMe*</span><span class="sxs-lookup"><span data-stu-id="b8e47-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example describes a simple <xref:System.Windows.Controls.TextBox> control named *tbFocusMe*</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a><span data-ttu-id="b8e47-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8e47-106">Example</span></span>  
 <span data-ttu-id="b8e47-107">Poniższy przykład wywołuje <xref:System.Windows.UIElement.Focus%2A> metodę, aby ustawić fokus na <xref:System.Windows.Controls.TextBox> formant o nazwie *tbFocusMe*.</span><span class="sxs-lookup"><span data-stu-id="b8e47-107">The following example calls the <xref:System.Windows.UIElement.Focus%2A> method to set the focus on the <xref:System.Windows.Controls.TextBox> control with the Name *tbFocusMe*.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a><span data-ttu-id="b8e47-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8e47-108">See also</span></span>

- <xref:System.Windows.UIElement.Focusable%2A>
- <xref:System.Windows.UIElement.IsFocused%2A>
- [<span data-ttu-id="b8e47-109">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="b8e47-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="b8e47-110">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="b8e47-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
