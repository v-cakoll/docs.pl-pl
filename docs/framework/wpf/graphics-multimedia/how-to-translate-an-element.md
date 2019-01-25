---
title: 'Instrukcje: Przesuń element'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: 75b8f72647b1597396fde5d21f8378d3ce586a25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672876"
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="635cf-102">Instrukcje: Przesuń element</span><span class="sxs-lookup"><span data-stu-id="635cf-102">How to: Translate an Element</span></span>
<span data-ttu-id="635cf-103">W tym przykładzie pokazano, jak do tłumaczenia (przenoszenie) elementu za pomocą <xref:System.Windows.Media.TranslateTransform>.</span><span class="sxs-lookup"><span data-stu-id="635cf-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="635cf-104"><xref:System.Windows.Media.TranslateTransform> Klasa jest szczególnie przydatne w przypadku przenoszenia elementy wewnątrz paneli, które nie obsługują pozycjonowanie absolutne.</span><span class="sxs-lookup"><span data-stu-id="635cf-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="635cf-105">Na przykład, stosując <xref:System.Windows.Media.TranslateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwość elementu, można przenieść elementu z <xref:System.Windows.Controls.StackPanel> lub <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="635cf-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="635cf-106">Użyj <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość <xref:System.Windows.Media.TranslateTransform> Aby określić czas, w pikselach, aby przenieść element na osi x.</span><span class="sxs-lookup"><span data-stu-id="635cf-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="635cf-107">Użyj <xref:System.Windows.Media.TranslateTransform.Y%2A> właściwość, aby określić czas, w pikselach, aby przenieść element wzdłuż osi y.</span><span class="sxs-lookup"><span data-stu-id="635cf-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="635cf-108">Na koniec Zastosuj <xref:System.Windows.Media.TranslateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości elementu.</span><span class="sxs-lookup"><span data-stu-id="635cf-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="635cf-109">W poniższym przykładzie użyto <xref:System.Windows.Media.TranslateTransform> aby przejść do kolejnego elementu 50 pikseli na prawo do 50 pikseli.</span><span class="sxs-lookup"><span data-stu-id="635cf-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="635cf-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="635cf-110">Example</span></span>  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="635cf-111">Aby uzyskać pełny przykład, zobacz [przykładowych przekształceń 2-D](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="635cf-111">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="635cf-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="635cf-112">See also</span></span>
- [<span data-ttu-id="635cf-113">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="635cf-113">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
