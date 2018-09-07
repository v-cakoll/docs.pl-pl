---
title: Jak zdefiniować szablon GroupBox
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: a47ce896be4d1c38147584dd80b1bc841737d526
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44062509"
---
# <a name="how-to-define-a-groupbox-template"></a><span data-ttu-id="cab49-102">Jak zdefiniować szablon GroupBox</span><span class="sxs-lookup"><span data-stu-id="cab49-102">How to: Define a GroupBox Template</span></span>
<span data-ttu-id="cab49-103">W tym przykładzie pokazano, jak utworzyć szablon dla <xref:System.Windows.Controls.GroupBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="cab49-103">This example shows how to create a template for a <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cab49-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cab49-104">Example</span></span>  
 <span data-ttu-id="cab49-105">W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.GroupBox> szablonu kontrolki przy użyciu <xref:System.Windows.Controls.Grid> kontroli dla układu.</span><span class="sxs-lookup"><span data-stu-id="cab49-105">The following example defines a <xref:System.Windows.Controls.GroupBox> control template by using a <xref:System.Windows.Controls.Grid> control for layout.</span></span> <span data-ttu-id="cab49-106">Szablon używa <xref:System.Windows.Controls.BorderGapMaskConverter> do definiowania obramowania <xref:System.Windows.Controls.GroupBox> tak, aby obramowania nie mogą zasłaniać <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> zawartości.</span><span class="sxs-lookup"><span data-stu-id="cab49-106">The template uses a <xref:System.Windows.Controls.BorderGapMaskConverter> to define the border of the <xref:System.Windows.Controls.GroupBox> so that the border does not obscure the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> content.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a><span data-ttu-id="cab49-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cab49-107">See Also</span></span>  
 <xref:System.Windows.Controls.GroupBox>  
 [<span data-ttu-id="cab49-108">Tematy porad GroupBox</span><span class="sxs-lookup"><span data-stu-id="cab49-108">GroupBox How-to Topics</span></span>](https://msdn.microsoft.com/library/7692e155-a4c6-428c-b7e0-64b3740daca7)
