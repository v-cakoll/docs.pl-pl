---
title: "Jak ustawić ostrość w formancie TextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe07633e41986e383d5f40dc66c0689a91e33116
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-focus-in-a-textbox-control"></a><span data-ttu-id="6bc31-102">Jak ustawić ostrość w formancie TextBox</span><span class="sxs-lookup"><span data-stu-id="6bc31-102">How to: Set Focus in a TextBox Control</span></span>
<span data-ttu-id="6bc31-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.UIElement.Focus%2A> metodę, aby ustawić fokus na <xref:System.Windows.Controls.TextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="6bc31-103">This example shows how to use the <xref:System.Windows.UIElement.Focus%2A> method to set focus on a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bc31-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6bc31-104">Example</span></span>  
 <span data-ttu-id="6bc31-105">Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie przedstawiono prosty <xref:System.Windows.Controls.TextBox> formantu o nazwie *tbFocusMe*</span><span class="sxs-lookup"><span data-stu-id="6bc31-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example describes a simple <xref:System.Windows.Controls.TextBox> control named *tbFocusMe*</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a><span data-ttu-id="6bc31-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="6bc31-106">Example</span></span>  
 <span data-ttu-id="6bc31-107">Następujące przykładowe wywołania <xref:System.Windows.UIElement.Focus%2A> metodę, aby ustawić fokus na <xref:System.Windows.Controls.TextBox> formantu o nazwie *tbFocusMe*.</span><span class="sxs-lookup"><span data-stu-id="6bc31-107">The following example calls the <xref:System.Windows.UIElement.Focus%2A> method to set the focus on the <xref:System.Windows.Controls.TextBox> control with the Name *tbFocusMe*.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a><span data-ttu-id="6bc31-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6bc31-108">See Also</span></span>  
 <xref:System.Windows.UIElement.Focusable%2A>  
 <xref:System.Windows.UIElement.IsFocused%2A>  
 [<span data-ttu-id="6bc31-109">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="6bc31-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="6bc31-110">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="6bc31-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
