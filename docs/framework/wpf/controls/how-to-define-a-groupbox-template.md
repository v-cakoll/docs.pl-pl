---
title: 'Instrukcje: Definiowanie szablonu GroupBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: dd53af87ec2d12b2ed0dcf2b23374d76e8f631a9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225719"
---
# <a name="how-to-define-a-groupbox-template"></a><span data-ttu-id="cfa85-102">Instrukcje: Definiowanie szablonu GroupBox</span><span class="sxs-lookup"><span data-stu-id="cfa85-102">How to: Define a GroupBox Template</span></span>
<span data-ttu-id="cfa85-103">W tym przykładzie pokazano, jak utworzyć szablon dla <xref:System.Windows.Controls.GroupBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="cfa85-103">This example shows how to create a template for a <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfa85-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cfa85-104">Example</span></span>  
 <span data-ttu-id="cfa85-105">W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.GroupBox> szablonu kontrolki przy użyciu <xref:System.Windows.Controls.Grid> kontroli dla układu.</span><span class="sxs-lookup"><span data-stu-id="cfa85-105">The following example defines a <xref:System.Windows.Controls.GroupBox> control template by using a <xref:System.Windows.Controls.Grid> control for layout.</span></span> <span data-ttu-id="cfa85-106">Szablon używa <xref:System.Windows.Controls.BorderGapMaskConverter> do definiowania obramowania <xref:System.Windows.Controls.GroupBox> tak, aby obramowania nie mogą zasłaniać <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> zawartości.</span><span class="sxs-lookup"><span data-stu-id="cfa85-106">The template uses a <xref:System.Windows.Controls.BorderGapMaskConverter> to define the border of the <xref:System.Windows.Controls.GroupBox> so that the border does not obscure the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> content.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a><span data-ttu-id="cfa85-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfa85-107">See also</span></span>

- <xref:System.Windows.Controls.GroupBox>
- [<span data-ttu-id="cfa85-108">Instrukcje: Utwórz element GroupBox</span><span class="sxs-lookup"><span data-stu-id="cfa85-108">How to: Create a GroupBox</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748321(v=vs.90))
