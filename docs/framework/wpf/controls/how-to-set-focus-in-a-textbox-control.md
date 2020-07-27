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
# <a name="how-to-set-focus-in-a-textbox-control"></a><span data-ttu-id="e10ff-103">Jak ustawić ostrość w formancie TextBox</span><span class="sxs-lookup"><span data-stu-id="e10ff-103">How to: Set Focus in a TextBox Control</span></span>
<span data-ttu-id="e10ff-104">Ten przykład pokazuje, jak używać <xref:System.Windows.UIElement.Focus%2A> metody do ustawiania fokusu na <xref:System.Windows.Controls.TextBox> formancie.</span><span class="sxs-lookup"><span data-stu-id="e10ff-104">This example shows how to use the <xref:System.Windows.UIElement.Focus%2A> method to set focus on a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e10ff-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e10ff-105">Example</span></span>  
 <span data-ttu-id="e10ff-106">W poniższym [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie opisano prostą <xref:System.Windows.Controls.TextBox> kontrolkę o nazwie *tbFocusMe*</span><span class="sxs-lookup"><span data-stu-id="e10ff-106">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example describes a simple <xref:System.Windows.Controls.TextBox> control named *tbFocusMe*</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a><span data-ttu-id="e10ff-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="e10ff-107">Example</span></span>  
 <span data-ttu-id="e10ff-108">Poniższy przykład wywołuje metodę, <xref:System.Windows.UIElement.Focus%2A> Aby ustawić fokus na <xref:System.Windows.Controls.TextBox> kontrolce o nazwie *tbFocusMe*.</span><span class="sxs-lookup"><span data-stu-id="e10ff-108">The following example calls the <xref:System.Windows.UIElement.Focus%2A> method to set the focus on the <xref:System.Windows.Controls.TextBox> control with the Name *tbFocusMe*.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a><span data-ttu-id="e10ff-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e10ff-109">See also</span></span>

- <xref:System.Windows.UIElement.Focusable%2A>
- <xref:System.Windows.UIElement.IsFocused%2A>
- [<span data-ttu-id="e10ff-110">TextBox — Przegląd</span><span class="sxs-lookup"><span data-stu-id="e10ff-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="e10ff-111">RichTextBox — Przegląd</span><span class="sxs-lookup"><span data-stu-id="e10ff-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
