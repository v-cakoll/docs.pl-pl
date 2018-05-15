---
title: Jak zdefiniować szablon GroupBox
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: ed66d51e87a25f74e646d0d535ac9e4ee9c8a056
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-a-groupbox-template"></a><span data-ttu-id="5dfe8-102">Jak zdefiniować szablon GroupBox</span><span class="sxs-lookup"><span data-stu-id="5dfe8-102">How to: Define a GroupBox Template</span></span>
<span data-ttu-id="5dfe8-103">W tym przykładzie pokazano, jak utworzyć szablon <xref:System.Windows.Controls.GroupBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="5dfe8-103">This example shows how to create a template for a <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5dfe8-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5dfe8-104">Example</span></span>  
 <span data-ttu-id="5dfe8-105">W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.GroupBox> szablon formantu przy użyciu <xref:System.Windows.Controls.Grid> kontroli dla układu.</span><span class="sxs-lookup"><span data-stu-id="5dfe8-105">The following example defines a <xref:System.Windows.Controls.GroupBox> control template by using a <xref:System.Windows.Controls.Grid> control for layout.</span></span> <span data-ttu-id="5dfe8-106">Szablon używa <xref:System.Windows.Controls.BorderGapMaskConverter> do definiowania obramowania <xref:System.Windows.Controls.GroupBox> tak, aby obramowania nie może zasłaniać <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> zawartości.</span><span class="sxs-lookup"><span data-stu-id="5dfe8-106">The template uses a <xref:System.Windows.Controls.BorderGapMaskConverter> to define the border of the <xref:System.Windows.Controls.GroupBox> so that the border does not obscure the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> content.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a><span data-ttu-id="5dfe8-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5dfe8-107">See Also</span></span>  
 <xref:System.Windows.Controls.GroupBox>  
 [<span data-ttu-id="5dfe8-108">Porada GroupBox — tematy</span><span class="sxs-lookup"><span data-stu-id="5dfe8-108">GroupBox How-to Topics</span></span>](http://msdn.microsoft.com/library/7692e155-a4c6-428c-b7e0-64b3740daca7)
