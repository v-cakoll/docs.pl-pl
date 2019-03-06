---
title: 'Instrukcje: Zastosuj styl do kontrolek na ToolBar'
ms.date: 03/30/2017
helpviewer_keywords:
- styling controls on toolbar [WPF]
- toolbars [WPF]
- customizing controls on toolbar [WPF]
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
ms.openlocfilehash: d81aa227eb1ffcb3dbaa119c41d561cbb066b704
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364453"
---
# <a name="how-to-style-controls-on-a-toolbar"></a><span data-ttu-id="e7b9e-102">Instrukcje: Zastosuj styl do kontrolek na ToolBar</span><span class="sxs-lookup"><span data-stu-id="e7b9e-102">How to: Style Controls on a ToolBar</span></span>
<span data-ttu-id="e7b9e-103"><xref:System.Windows.Controls.ToolBar> Definiuje <xref:System.Windows.ResourceKey> obiekty do określania stylu kontrolki w ramach <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="e7b9e-103">The <xref:System.Windows.Controls.ToolBar> defines <xref:System.Windows.ResourceKey> objects to specify the style of controls within the <xref:System.Windows.Controls.ToolBar>.</span></span>  <span data-ttu-id="e7b9e-104">Do określania stylu kontrolki w <xref:System.Windows.Controls.ToolBar>ustaw `x:key` atrybut stylu do <xref:System.Windows.ResourceKey> zdefiniowane w <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="e7b9e-104">To style a control in a <xref:System.Windows.Controls.ToolBar>, set the `x:key` attribute of the style to a <xref:System.Windows.ResourceKey> defined in <xref:System.Windows.Controls.ToolBar>.</span></span>  
  
 <span data-ttu-id="e7b9e-105"><xref:System.Windows.Controls.ToolBar> Definiuje następujące <xref:System.Windows.ResourceKey> obiektów:</span><span class="sxs-lookup"><span data-stu-id="e7b9e-105">The <xref:System.Windows.Controls.ToolBar> defines the following <xref:System.Windows.ResourceKey> objects:</span></span>  
  
-   <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## <a name="example"></a><span data-ttu-id="e7b9e-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7b9e-106">Example</span></span>  
 <span data-ttu-id="e7b9e-107">W poniższym przykładzie zdefiniowano stylów dla kontrolki w ramach <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="e7b9e-107">The following example defines styles for the controls within a <xref:System.Windows.Controls.ToolBar>.</span></span>  
  
 [!code-xaml[ToolBar_snip#ToolBarAllStyles](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xaml[ToolBar_snip#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## <a name="see-also"></a><span data-ttu-id="e7b9e-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7b9e-108">See also</span></span>
- [<span data-ttu-id="e7b9e-109">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="e7b9e-109">Styling and Templating</span></span>](styling-and-templating.md)
